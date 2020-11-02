---
title: So erstellt MSBuild Projekte
description: Erfahren Sie, wie MSBuild Ihre Projektdateien verarbeitet, die über Visual Studio, eine Befehlszeile oder ein Skript aufgerufen werden.
ms.custom: SEO-VS-2020
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4374e6763933e2da3e6a11c5609b76e3341e1050
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353251"
---
# <a name="how-msbuild-builds-projects"></a>So erstellt MSBuild Projekte

Funktionsweise von MSBuild In diesem Artikel erfahren Sie, wie MSBuild Ihre Projektdateien verarbeitet, die über Visual Studio, eine Befehlszeile oder ein Skript aufgerufen werden. Wenn Sie die genaue Funktionsweise von MSBuild kennen, können Sie Probleme besser diagnostizieren und Ihren Buildprozess besser anpassen. In diesem Artikel wird der Buildprozess beschrieben. Er ist weitgehend für alle Projekttypen anwendbar.

Der vollständige Buildprozess umfasst den [ersten Start](#startup), die [Auswertung](#evaluation-phase) und die [Ausführung](#execution-phase) der Ziele und Aufgaben, aus denen sich das Projekt zusammensetzt. Zusätzlich zu diesen Eingaben werden die Details des Buildprozesses über externe Importe definiert. Dazu zählen sowohl [Standardimporte](#standard-imports) wie *Microsoft.Common.targets* als auch [vom Benutzer konfigurierbare Importe](#user-configurable-imports) auf Projektmappen- oder Projektebene.

## <a name="startup"></a>Start

MSBuild kann aus Visual Studio über das MSBuild-Objektmodell in *Microsoft.Build.dll* oder durch einen direkten Aufruf der ausführbaren Datei über die Befehlszeile bzw. in einem Skript (z. B. in CI-Systemen) aufgerufen werden. In jedem dieser Fälle wirken sich folgende Eingaben auf den Buildprozess aus: die Projektdatei (oder ein internes Visual Studio-Projektobjekt), möglicherweise eine Projektmappendatei, Umgebungsvariablen sowie Befehlszeilenoptionen oder ihre Entsprechungen im Objektmodell. Während der Startphase werden die Befehlszeilenoptionen oder ihre Entsprechungen im Objektmodell verwendet, um MSBuild-Einstellungen zu konfigurieren (z. B. die Protokollierung). Eigenschaften, die in der Befehlszeile mit der Option `-property` oder `-p` festgelegt werden, werden als globale Eigenschaften festgelegt. Diese Eigenschaften setzen Werte in den Projektdateien außer Kraft, obwohl die Projektdateien später eingelesen werden.

In den nächsten Abschnitten werden die Eingabedateien erläutert (z. B. Projektmappen- oder Projektdateien).

### <a name="solutions-and-projects"></a>Projektmappen und Projekte

MSBuild-Instanzen können über ein einzelnes oder über eine Vielzahl von Projekten verfügen, die Teil einer Projektmappe sind. Die Projektmappendatei ist keine MSBuild-XML-Datei, wird jedoch von MSBuild interpretiert, um alle Projekte zu ermitteln, die für die jeweilige Konfiguration und die jeweiligen Plattformeinstellungen erforderlich sind. Wenn MSBuild diese XML-Eingabe verarbeitet, wird sie als Projektmappenbuild bezeichnet. Sie verfügt über erweiterbare Punkte, mit denen Sie Elemente für jeden Projektmappenbuild ausführen können. Da es sich bei diesem Build jedoch um eine separate Ausführung handelt, die getrennt von den einzelnen Projektbuilds erfolgt, sind die Einstellungen von Eigenschaften oder Zieldefinitionen des Projektmappenbuilds für die einzelnen Projektbuilds nicht relevant.

Informationen zum Erweitern des Projektmappenbuilds finden Sie unter [Anpassen des Projektmappenbuilds](customize-your-build.md#customize-the-solution-build).

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio-Builds im Vergleich zu MSBuild.exe-Builds

Bei Projekten, die in Visual Studio erstellt werden, müssen gegenüber einem direkten Aufruf von MSBuild (über die ausführbare MSBuild-Datei oder bei Verwendung des MSBuild-Objektmodells zum Starten eines Builds) einige wichtige Unterschiede berücksichtigt werden. Visual Studio verwaltet die Projektbuildreihenfolge für Visual Studio-Builds. MSBuild wird nur auf Ebene der einzelnen Projekte aufgerufen. Bei einem solchen Aufruf werden eine Reihe von booleschen Eigenschaften (`BuildingInsideVisualStudio`, `BuildProjectReferences`) festgelegt, die sich erheblich auf die Abläufe von MSBuild auswirken. Innerhalb der einzelnen Projekte erfolgt die Ausführung auf dieselbe Weise wie bei einem Aufruf über MSBuild. Die Unterschiede treten jedoch bei referenzierten Projekten auf. Wenn in MSBuild referenzierte Projekte erforderlich sind, erfolgt tatsächlich ein Build. Es werden also Aufgaben und Tools ausgeführt, und die Ausgabe wird generiert. Wenn ein Visual Studio-Build ein referenziertes Projekt findet, gibt MSBuild lediglich die erwarteten Ausgaben des referenzierten Projekts zurück. Die Erstellung der anderen Projekte wird Visual Studio überlassen. Visual Studio bestimmt die Buildreihenfolge und Aufrufe von MSBuild separat (nach Bedarf). Der gesamte Vorgang wird von Visual Studio gesteuert.

Ein weiterer Unterschied tritt auf, wenn MSBuild mit einer Projektmappendatei aufgerufen wird. MSBuild analysiert die Projektmappendatei, erstellt eine standardmäßige XML-Eingabedatei, wertet diese Datei aus und führt sie als Projekt aus. Der Projektmappenbuild wird vor den Projekten ausgeführt. Bei der Erstellung über Visual Studio werden diese Schritte nicht ausgeführt. MSBuild hat zu keinem Zeitpunkt Zugang zur Projektmappendatei. Folglich gilt die Anpassung von Projektmappenbuilds (über *before.SolutionName.sln.targets* und *after.SolutionName.sln.targets* ) nur für Builds, die über MSBuild.exe oder ein Objektmodell gestartet werden, nicht jedoch für Visual Studio-Builds.

### <a name="project-sdks"></a>Projekt-SDKs

Das SDK-Feature für MSBuild-Projektdateien ist recht neu. Vor dieser Änderung wurden die *.targets* - und *.props* -Dateien, die den Buildprozess für einen bestimmten Projekttyp definiert haben, explizit von Projektdateien importiert.

.NET Core-Projekte importieren die Version des jeweils geeigneten .NET SDK. Weitere Informationen finden Sie in der Übersicht [.NET Core-Projekt-SDKs](/dotnet/core/project-sdk/overview) und in der Referenz zu den [Eigenschaften](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Auswertungsphase

In diesem Abschnitt wird erläutert, wie die Eingabedateien verarbeitet und analysiert werden, um Objekte im Arbeitsspeicher zu erzeugen, die bestimmen, was erstellt wird.

Zweck der Auswertungsphase ist die Erstellung der Objektstrukturen im Arbeitsspeicher basierend auf den XML-Eingabedateien und der lokalen Umgebung. Diese Auswertungsphase umfasst sechs Durchläufe, in denen die Eingabedateien verarbeitet werden. Dazu zählen z. B. die XML-Projektdateien oder die importierten XML-Dateien, bei denen es sich üblicherweise um *PROPS* - oder *TARGETS* -Dateien handelt (abhängig davon, ob sie primär zum Festlegen von Eigenschaften oder zum Definieren der Buildziele dienen). Bei jedem Durchlauf wird ein Teil der Objekte im Arbeitsspeicher erstellt, die später in der Ausführungsphase zum Erstellen der Projekte verwendet werden. Tatsächliche Erstellungsaktionen werden während der Auswertungsphase jedoch nicht durchgeführt. Innerhalb der einzelnen Durchläufe werden Elemente in der Reihenfolge verarbeitet, in der sie auftauchen.

Die Auswertungsphase umfasst die folgenden Durchläufe:

- Auswerten von Umgebungsvariablen
- Auswerten von Importen und Eigenschaften
- Auswerten von Elementdefinitionen
- Auswerten von Elementen
- Auswerten von [UsingTask](usingtask-element-msbuild.md)-Elementen
- Auswerten von Zielen

Die Reihenfolge dieser Durchläufe hat erhebliche Auswirkungen. Daher ist es wichtig, diese Reihenfolge zu kennen, wenn Sie die Projektdatei anpassen. Weitere Informationen finden Sie unter [Auswertungsreihenfolge von Eigenschaften und Elementen](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Auswerten von Umgebungsvariablen

In dieser Phase werden Umgebungsvariablen verwendet, um äquivalente Eigenschaften festzulegen. Die PATH-Umgebungsvariable wird beispielsweise als Eigenschaft `$(PATH)` verfügbar gemacht. Bei Ausführung über die Befehlszeile oder ein Skript wird die Befehlsumgebung wie üblich verwendet. Bei Ausführung über Visual Studio wird die Umgebung verwendet, die beim Start von Visual Studio aktiv ist.

### <a name="evaluate-imports-and-properties"></a>Auswerten von Importen und Eigenschaften

In dieser Phase wird die gesamte XML-Eingabe eingelesen, einschließlich Projektdateien und die gesamte Kette an Importen. MSBuild erstellt eine XML-Struktur im Arbeitsspeicher, die die XML des Projekts und alle importierten Dateien widerspiegelt. Aktuell werden Eigenschaften, die sich nicht in Zielen befinden, ausgewertet und festgelegt.

Da MSBuild alle XML-Eingabedateien bereits in einer frühen Phase des Prozesses liest, wirken sich Änderungen an diesen Eingaben während des Buildprozesses nicht auf den aktuellen Build aus.

Eigenschaften außerhalb von Zielen werden anders behandelt als Eigenschaften innerhalb von Zielen. In dieser Phase werden nur die Eigenschaften ausgewertet, die außerhalb eines Ziels definiert sind.

Da Eigenschaften im Eigenschaftendurchlauf mit einer bestimmten Reihenfolge verarbeitet werden, kann eine Eigenschaft an einem beliebigen Punkt in der Eingabe auf Eigenschaftswerte zugreifen, die an früherer Stelle in der Eingabe auftauchen. Ein Zugriff auf Eigenschaften, die später erscheinen, ist jedoch nicht möglich.

Da die Eigenschaften verarbeitet werden, bevor Elemente ausgewertet werden, können Sie während des Eigenschaftendurchlaufs nicht auf die Werte von Elementen zugreifen. 

### <a name="evaluate-item-definitions"></a>Auswerten von Elementdefinitionen

In dieser Phase werden [Elementdefinitionen](item-definitions.md) interpretiert, und es wird eine Darstellung im Arbeitsspeicher für diese Definitionen erstellt.

### <a name="evaluate-items"></a>Auswerten von Elementen

Elemente, die innerhalb eines Ziels definiert sind, werden anders behandelt als Elemente außerhalb von Zielen. In dieser Phase werden Elemente außerhalb von Zielen und die zugehörigen Metadaten verarbeitet.  Metadaten, die durch Elementdefinitionen festgelegt sind, werden durch die Metadateneinstellung der Elemente außer Kraft gesetzt. Da Elemente in der Reihenfolge verarbeitet werden, in der sie erscheinen, können Sie auf Elemente verweisen, die zuvor definiert wurden. Ein Verweis auf Elemente, die später angezeigt werden, ist jedoch nicht möglich. Da der Elementdurchlauf nach dem Eigenschaftendurchlauf erfolgt, können Elemente auf Eigenschaften zugreifen, die außerhalb von Zielen definiert wurden. Dies gilt unabhängig davon, ob die Eigenschaftendefinition früher oder später erscheint.

### <a name="evaluate-usingtask-elements"></a>Auswerten von `UsingTask`-Elementen

In dieser Phase werden [UsingTask](usingtask-element-msbuild.md)-Elemente gelesen. Außerdem werden die Aufgaben zur späteren Verwendung während der Ausführungsphase deklariert.

### <a name="evaluate-targets"></a>Auswerten von Zielen

In dieser Phase werden alle Zielobjektstrukturen im Arbeitsspeicher erstellt, um die Ausführung vorzubereiten. Eine tatsächliche Ausführung findet nicht statt. 

## <a name="execution-phase"></a>Ausführungsphase

In der Ausführungsphase werden die Ziele geordnet und ausgeführt, und alle Aufgaben werden ausgeführt. Zunächst werden jedoch Eigenschaften und Elemente, die in Zielen definiert sind, gemeinsam in einer einzigen Phase und in der Reihenfolge ausgewertet, in der sie erscheinen. Die Verarbeitungsreihenfolge unterscheidet sich dabei deutlich von der Verarbeitung von Eigenschaften und Elementen außerhalb von Zielen: In separaten Durchläufen werden zunächst alle Eigenschaften, anschließend alle Elemente verarbeitet. Änderungen an Eigenschaften und Elementen innerhalb eines Ziels werden nach dem Ziel sichtbar, in dem sie geändert wurden.

### <a name="target-build-order"></a>Buildreihenfolge für Ziele

In einem einzelnen Projekt werden Ziele seriell ausgeführt. Das Hauptproblem bei dieser Vorgehensweise ist das Bestimmen der Reihenfolge, mit der die Elemente erstellt werden sollen, damit Abhängigkeiten zum Erstellen der Ziele in der richtigen Reihenfolge verwendet werden.  

Die Buildreihenfolge der Ziele wird durch die Attribute `BeforeTargets`, `DependsOnTargets` und `AfterTargets` für die einzelnen Ziele bestimmt. Die Reihenfolge späterer Ziele kann während der Ausführung eines früheren Ziels beeinflusst werden, wenn das frühere Ziel eine Eigenschaft ändert, die in diesen Attributen referenziert wird.

Die Regeln für das Festlegen der Reihenfolge sind unter [Bestimmen der Buildreihenfolge für Ziele](target-build-order.md#determine-the-target-build-order) beschrieben. Der Prozess wird durch eine Stapelstruktur bestimmt, die zu erstellende Ziele umfasst. Die Ausführung wird durch das oberste Ziel dieser Aufgabe gestartet. Wenn dieses Ziel von anderen Zielen abhängt, werden diese Ziele an die oberen Positionen des Stapels verschoben und ebenfalls ausgeführt.  Bei Zielen ohne Abhängigkeiten wird die Ausführung abgeschlossen, und anschließend wird das übergeordnete Ziel fortgesetzt.

### <a name="project-references"></a>Projektverweise

Für MSBuild können zwei Codepfade genutzt werden: der normale, hier beschriebene Pfad und die Diagrammoption, die im nächsten Abschnitt erläutert wird.

Für einzelne Projekte kann eine Abhängigkeit von anderen Projekten über `ProjectReference`-Elemente angegeben werden. Wenn ein Projekt am Anfang des Stapels erstellt wird, wird der Punkt erreicht, an dem das `ResolveProjectReferences`-Ziel ausgeführt wird: ein Standardziel, das in den gemeinsamen Zieldateien definiert ist.

`ResolveProjectReferences` ruft die MSBuild-Aufgabe mit Eingaben der `ProjectReference`-Elemente auf, um die Ausgaben zu erhalten. Die `ProjectReference`-Elemente werden in lokale Elemente wie `Reference` umgewandelt. Die MSBuild-Ausführungsphase für das aktuelle Projekt wird unterbrochen, wenn die Ausführungsphase mit der Verarbeitung des referenzierten Projekts beginnt (nach Bedarf erfolgt zunächst die Auswertungsphase). Das referenzierte Projekt wird erst erstellt, nachdem Sie mit der Erstellung des abhängigen Projekts begonnen haben. Es entsteht also eine Struktur aus Projekten, die erstellt werden.

Visual Studio ermöglicht das Erstellen von Projektabhängigkeiten in Projektmappendateien (.sln). Die Abhängigkeiten werden in der Projektmappendatei angegeben und nur beim Erstellen einer Projektmappe bzw. bei der Erstellung innerhalb von Visual Studio berücksichtigt. Wenn Sie ein einzelnes Projekt erstellen, wird diese Art von Abhängigkeit ignoriert. Projektmappenverweise werden von MSBuild in `ProjectReference`-Elemente umgewandelt und anschließend auf die gleiche Weise behandelt.

### <a name="graph-option"></a>Die Diagrammoption

Wenn Sie die Diagrammerstellungsoption (`-graphBuild` oder `-graph`) angeben, wird `ProjectReference` ein von MSBuild verwendetes Konzept der ersten Klasse. MSBuild analysiert alle Projekte und erstellt das Diagramm mit der Buildreihenfolge, ein Abhängigkeitsdiagramm mit Projekten, anhand dessen anschließend die Buildreihenfolge bestimmt wird. Wie bei Zielen in einzelnen Projekten stellt MSBuild sicher, dass referenzierte Projekte nach den Projekten erstellt werden, von denen sie abhängig sind.

## <a name="parallel-execution"></a>Parallele Ausführung

Bei Verwendung von Multiprozessorunterstützung (Option `-maxCpuCount` oder `-m`) erstellt MSBuild Knoten, bei denen es sich um MSBuild-Prozesse handelt, die die verfügbaren CPU-Kerne nutzen. Jedes Projekt wird an einen verfügbaren Knoten übermittelt. Innerhalb eines Knotens werden einzelne Projektbuilds seriell ausgeführt.

Für Aufgaben kann eine parallele Ausführung aktiviert werden, indem die boolesche Variable <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> gesetzt wird. Diese Variable wird in Übereinstimmung mit dem Wert der `$(BuildInParallel)`-Eigenschaft in MSBuild festgelegt. Bei Aufgaben, die für eine parallele Ausführung aktiviert sind, wird ein Auftragsplaner eingesetzt, um Knoten zu verwalten und Aufgaben zu Knoten zuzuweisen.

Weitere Informationen finden Sie unter [Paralleles Erstellen von mehreren Projekten mit MSBuild](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Standardimporte

*Microsoft.Common.props* und *Microsoft.Common.targets* werden von .NET-Projektdateien importiert (explizit oder implizit in SDK-Projekten) und befinden sich in einer Visual Studio-Installation im Ordner *MSBuild\Current\bin* . C++-Projekte verfügen über eine eigene Hierarchie für Importe. Weitere Informationen finden Sie unter [MSBuild-Interna für C++-Projekte](/cpp/build/reference/msbuild-visual-cpp-overview).

Mit der Datei *Microsoft.Common.props* werden Standardwerte festgelegt, die Sie außer Kraft setzen können. Sie wird (explizit oder implizit) am Anfang einer Projektdatei importiert. Dadurch erscheinen die Einstellungen Ihres Projekts nach den Standardeinstellungen, sodass diese außer Kraft gesetzt werden können.

Die Datei *Microsoft.Common.targets* und die Zieldateien, die von dieser Datei importiert werden, definieren den Standardbuildprozess für .NET-Projekte. Darüber hinaus enthält sie Erweiterungspunkte, die Sie zum Anpassen des Builds verwenden können.

Bei der Implementierung ist *Microsoft.Common.targets* ein schlanker Wrapper, der *Microsoft.Common.CurrentVersion.targets* importiert. Diese Datei enthält Einstellungen für Standardeigenschaften und definiert die eigentlichen Ziele, die den Buildprozess definieren. Hier wird zwar das Ziel `Build` definiert, dieses Ziel ist jedoch eigentlich leer. Das Ziel `Build` enthält jedoch das Attribut `DependsOn`, mit dem die einzelnen Ziele angegeben werden, aus denen sich die eigentlichen Buildschritte zusammensetzen (`BeforeBuild`, `CoreBuild` und `AfterBuild`). Nachfolgend ist die Definition des `Build`-Ziels gezeigt:

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild` und `AfterBuild` sind Erweiterungspunkte. In der Datei *Microsoft.Common.CurrentVersion.targets* sind sie leer, in Projekten können jedoch eigene `BeforeBuild`- und `AfterBuild`-Ziele mit Aufgaben angegeben werden, die vor oder nach dem Hauptbuildprozess ausgeführt werden müssen. `AfterBuild` wird vor dem No-op-Ziel (`Build`) ausgeführt, da `AfterBuild` im Attribut `DependsOn` für das Ziel `Build` erscheint, jedoch nach `CoreBuild` auftritt.

Das `CoreBuild`-Ziel beinhaltet die Aufrufe der Buildtools, wie nachfolgend gezeigt:

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

Diese Ziele sind in der folgenden Tabelle beschrieben. Einige Ziele gelten nur für bestimmte Projekttypen.

| Target | Beschreibung |
|--------|-------------|
| BuildOnlySettings | Einstellungen, die nur für reale Builds gelten, nicht für Aufrufe von MSBuild beim Laden von Projekten durch Visual Studio. |
| PrepareForBuild | Vorbereiten der erforderlichen Elemente für die Erstellung. |
| PreBuildEvent | Erweiterungspunkt für Projekte, um Aufgaben zu definieren, die vor dem Build ausgeführt werden sollen. |
| ResolveProjectReferences | Analysieren von Projektabhängigkeiten und referenzierten Projekten im Build. |
| ResolveAssemblyReferences| Suchen nach referenzierten Assemblys. |
| ResolveReferences | Umfasst `ResolveProjectReferences` und `ResolveAssemblyReferences`, um nach allen Abhängigkeiten zu suchen. |
| PrepareResources | Verarbeiten von Ressourcendateien. |
| ResolveKeySource| Auflösen des Schlüssels mit starkem Namen, der zum Signieren der Assembly und des Zertifikats verwendet wird, mit dem die [ClickOnce](../deployment/clickonce-security-and-deployment.md)-Manifeste signiert werden. |
| Compile | Aufruf des Compilers. |
| ExportWindowsMDFile | Generieren einer [WinMD](/uwp/winrt-cref/winmd-files)-Datei aus den WinMDModule-Dateien, die vom Compiler generiert werden. |
| UnmanagedUnregistration | Entfernen/Bereinigen der [COM-Interop](/dotnet/standard/native-interop/cominterop)-Registrierungseinträge aus einem vorherigen Build. |
| GenerateSerializationAssemblies | Generieren einer XML-Serialisierungsassembly mithilfe von [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Erstellen einer Satellitenassembly für jede eindeutige Kultur in den Ressourcen. |
| GenerateManifests | Generiert eine [ClickOnce](../deployment/clickonce-security-and-deployment.md)-Anwendung und Bereitstellungsmanifeste oder ein natives Manifest. |
| GetTargetPath | Zurückgeben eines Elements, das das Buildprodukt (ausführbare Datei oder Assembly) für dieses Projekt enthält, mit Metadaten. |
| PrepareForRun | Kopieren der Buildausgaben in das finale Verzeichnis, wenn sich die Ausgaben geändert haben. |
| UnmanagedRegistration | Festlegen der Registrierungseinträge für [COM-Interop](/dotnet/standard/native-interop/cominterop). |
| IncrementalClean | Entfernen von Dateien, die in einem vorherigen Build, jedoch nicht im aktuellen Build erzeugt wurden. Dies ist erforderlich, damit `Clean` in inkrementellen Builds funktioniert. |
| PostBuildEvent | Erweiterungspunkt für Projekte, um Aufgaben zu definieren, die nach dem Build ausgeführt werden sollen. |

Viele der in der obigen Tabelle aufgeführten Ziele befinden sich in sprachspezifischen Importen wie *Microsoft.CSharp.targets* . Dadurch werden die Schritte im Standardbuildprozess für C# .NET-Projekte definiert. Beispielsweise ist das Ziel `Compile` enthalten, mit dem der C#-Compiler aufgerufen wird.

## <a name="user-configurable-imports"></a>Vom Benutzer konfigurierbare Importe

Zusätzlich zu den Standardimporten sind eine Reihe von Importen verfügbar, die Sie hinzufügen können, um den Buildprozess anzupassen.

- *Directory.Build.props*
- *Directory.Build.targets*

Diese Dateien werden von den Standardimporten für Projekte in einem zugehörigen Unterordner eingelesen. Üblicherweise erfolgt dies auf Projektmappenebene für Einstellungen, mit denen alle Projekte innerhalb der Projektmappe gesteuert werden. Es kann sich aber auch um eine höhere Ebene innerhalb des Dateisystems handeln (bis hin zum Stamm des Laufwerks).

Da die Datei *Directory.Build.props* von *Microsoft.Common.props* importiert wird, sind die darin definierten Eigenschaften in der Projektdatei verfügbar. Um die Werte auf Projektbasis anzupassen, können sie in der Projektdatei neu definiert werden. Die Datei *Directory.Build.targets* wird nach der Projektdatei eingelesen. Sie enthält üblicherweise Ziele, Sie können jedoch auch Eigenschaften definieren, die in einzelnen Projekten nicht neu definiert werden sollen.

## <a name="customizations-in-a-project-file"></a>Anpassungen in Projektdateien

Wenn Sie im **Projektmappen-Explorer** , im Fenster **Eigenschaften** oder unter **Projekteigenschaften** Änderungen vornehmen, aktualisiert Visual Studio Ihre Projektdateien. Sie können die Projektdatei jedoch auch direkt bearbeiten, um Änderungen vorzunehmen.

Viele Buildverhaltensweisen können durch das Festlegen von MSBuild-Eigenschaften konfiguriert werden. Dieser Schritt kann für lokale Projekteinstellungen in der Projektdatei erfolgen oder, wie im vorherigen Abschnitt beschrieben, durch das Erstellen einer *Directory.Build.props* -Datei, um Eigenschaften global für einen vollständigen Ordner mit Projekten und Projektmappen festzulegen. Für Ad-hoc-Builds in der Befehlszeile oder in Skripts können Sie außerdem die Option `/p` in der Befehlszeile verwenden, um Eigenschaften für einen bestimmten Aufruf von MSBuild festzulegen. Informationen zu den Eigenschaften, die Sie festlegen können, finden Sie unter [Gemeinsame MSBuild-Projekteigenschaften](common-msbuild-project-properties.md).

## <a name="next-steps"></a>Nächste Schritte

Der MSBuild-Prozess verfügt über eine Reihe zusätzlicher Erweiterungspunkte, die in diesem Artikel nicht beschrieben wurden. Weitere Informationen finden Sie unter [Anpassen Ihres Builds](customize-your-build.md) und [Vorgehensweise: Erweitern des Visual Studio-Buildprozesses](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Siehe auch

[MSBuild](msbuild.md)
