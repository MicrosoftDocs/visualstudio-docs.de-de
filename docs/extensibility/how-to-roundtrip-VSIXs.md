---
title: Roundtrip-Erweiterungen
description: Erfahren Sie, wie Sie Visual Studio-Erweiterbarkeits Projekte zwischen Visual Studio 2015 und Visual Studio 2019 oder Visual Studio 2017 Roundtrip machen.
ms.custom: SEO-VS-2020
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 3db3264bf5226b5679452659928e451e7975b001
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993613"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Gewusst wie: Erstellen von mit Visual Studio 2019/2017 und Visual Studio 2015 kompatiblen Erweiterungen

In diesem Dokument wird erläutert, wie Sie den Roundtrip von Erweiterbarkeits Projekten zwischen Visual Studio 2015 und Visual Studio 2019 oder Visual Studio 2017 durchführen können. Nach Abschluss dieses Upgrades kann ein Projekt sowohl in Visual Studio 2015 als auch in Visual Studio 2019 oder 2017 geöffnet, erstellt, installiert und ausgeführt werden. Als Referenz finden Sie einige Erweiterungen, die einen Roundtrip zwischen Visual Studio 2015 und Visual Studio 2019 oder 2017 durchgehen können, finden Sie unter Visual Studio [SDK-Erweiterbarkeits Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Wenn Sie nur in Visual Studio 2019/2017 erstellen möchten, aber die Ausgabe-VSIX sowohl in Visual Studio 2015 als auch in Visual Studio 2019/2017 ausgeführt werden sollen, lesen Sie das [Dokument zur Erweiterungs Migration](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Aufgrund von Änderungen in Visual Studio Zwischenversionen funktionieren einige Dinge, die in einer Version funktionieren, nicht in einer anderen Version. Stellen Sie sicher, dass die Features, auf die Sie zugreifen möchten, in beiden Versionen verfügbar sind oder dass die Erweiterung unerwartete Ergebnisse hat.

Im folgenden finden Sie einen Überblick über die Schritte, die Sie in diesem Dokument durchführen, um einen Roundtrip für eine VSIX durchzuführen:

1. Importieren Sie richtige nuget-Pakete.
2. Erweiterungs Manifest aktualisieren:
    * Installationsziel
    * Voraussetzungen
3. Aktualisieren Sie csproj:
    * Aktualisieren Sie `<MinimumVisualStudioVersion>`.
    * Hinzufügen der `<VsixType>`-Eigenschaft
    * Fügen Sie die Debugeigenschaft `($DevEnvDir)` 3 Mal hinzu.
    * Fügen Sie Bedingungen zum Importieren von Buildtools und Zielen hinzu.

4. Kompilieren und testen

## <a name="environment-setup"></a>Einrichten der Umgebung

In diesem Dokument wird davon ausgegangen, dass Sie Folgendes auf Ihrem Computer installiert haben:

* Visual Studio 2015 mit installiertem vs SDK
* Visual Studio 2019 oder 2017 mit installierter Erweiterbarkeits Arbeitsauslastung

## <a name="recommended-approach"></a>Empfohlener Ansatz

Es wird dringend empfohlen, dieses Upgrade mit Visual Studio 2015 anstelle von Visual Studio 2019 oder 2017 zu starten. Der Hauptvorteil der Entwicklung in Visual Studio 2015 besteht darin, sicherzustellen, dass Sie nicht auf Assemblys verweisen, die in Visual Studio 2015 nicht verfügbar sind. Wenn Sie in Visual Studio 2019 oder 2017 entwickeln, besteht das Risiko, dass Sie eine Abhängigkeit von einer Assembly einführen, die nur in Visual Studio 2019 oder 2017 vorhanden ist.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Stellen Sie sicher, dass kein Verweis auf project.jsvorhanden ist.

Später in diesem Dokument fügen wir Anweisungen für den bedingten Import in die *csproj* -Datei ein. Dies funktioniert nicht, wenn Ihre nuget-Verweise in *project.js* gespeichert werden. Daher wird empfohlen, alle nuget-Verweise in die *packages.config* Datei zu verschieben.
Wenn das Projekt einen *project.jsfür* die Datei enthält:

* Notieren Sie sich die Verweise in *project.js*.
* Löschen Sie aus dem **Projektmappen-Explorer** den *project.jsfür* die Datei aus dem Projekt. Dadurch wird der *project.jsfür* die Datei gelöscht und aus dem Projekt entfernt.
* Fügen Sie dem Projekt die nuget-Verweise wieder hinzu:
  * Klicken Sie mit der rechten Maustaste auf die **Lösung** , und wählen Sie **nuget-Pakete für** Projekt Mappe verwalten.
  * Visual Studio erstellt die *packages.config* Datei automatisch für Sie.

> [!NOTE]
> Wenn in Ihrem Projekt die Option zum Hinzufügen von Paketen enthalten ist, müssen Sie möglicherweise hinzugefügt werden, indem Sie mit der rechten Maustaste auf **Verweise** **Verweis hinzufügen** und den entsprechenden Verweis hinzufügen Die Verwendung von nuget-Paketen kann beim Erstellen des Projekts zu Fehlern führen.

## <a name="add-appropriate-build-tools"></a>Geeignete Buildtools hinzufügen

Wir müssen die Buildtools hinzufügen, mit denen wir entsprechend erstellen und Debuggen können. Microsoft hat eine Assembly für den Namen Microsoft. VisualStudio. SDK. BuildTasks erstellt.

Zum Erstellen und Bereitstellen eines VSIXv3 in Visual Studio 2015 und 2019/2017 benötigen Sie die folgenden nuget-Pakete:

Version | Integrierte Tools
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. SDK. BuildTasks. 14,0
Visual Studio 2019 oder 2017 | Microsoft. VSSDK. Buildtool

Gehen Sie folgendermaßen vor:

* Fügen Sie das nuget-Paket "Microsoft. VisualStudio. SDK. BuildTasks. 14,0" zu Ihrem Projekt hinzu.
* Wenn das Projekt nicht Microsoft. VSSDK. Buildtools enthält, fügen Sie es hinzu.
* Stellen Sie sicher, dass die Version Microsoft. VSSDK. Buildtools 15. x oder höher ist.

## <a name="update-extension-manifest"></a>Erweiterungs Manifest aktualisieren

### <a name="1-installation-targets"></a>1. Installations Ziele

Wir müssen Visual Studio mitteilen, welche Versionen für das Entwickeln einer VSIX als Zielversion vorgesehen sind. In der Regel sind diese Verweise entweder auf Version 14,0 (Visual Studio 2015), Version 15,0 (Visual Studio 2017) oder Version 16,0 (Visual Studio 2019). In unserem Fall möchten wir eine VSIX erstellen, mit der eine Erweiterung für beides installiert wird. Daher müssen wir beide Versionen als Ziel haben. Wenn Sie möchten, dass Ihre VSIX in früheren Versionen als 14,0 erstellt und installiert wird, können Sie dies durch Festlegen der früheren Versionsnummer tun. Version 10,0 und frühere Versionen werden jedoch nicht mehr unterstützt.

* Öffnen Sie die Datei " *Source. Extension. vsixmanifest* " in Visual Studio.
* Öffnen Sie die Registerkarte **Ziele installieren** .
* Ändern Sie den **Versions Bereich** in [14,0, 17,0). "[" Weist Visual Studio an, 14,0 und alle Versionen in der Vergangenheit einzubeziehen. Das ') ' weist Visual Studio an, alle Versionen bis einschließlich, Version 17,0, einzubeziehen.
* Speichern Sie alle Änderungen, und schließen Sie alle Instanzen von Visual Studio.

![Image der Installations Ziele](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Hinzufügen von Voraussetzungen zur Datei *Erweiterung. vsixmanifest*

Wir benötigen den Visual Studio-Kern-Editor als Voraussetzung. Öffnen Sie Visual Studio, und verwenden Sie den aktualisierten Manifest-Designer, um die erforderlichen Komponenten einzufügen.

Gehen Sie hierzu wie folgt vor:

* Navigieren Sie im Datei-Explorer zum Projektverzeichnis.
* Öffnen Sie die Datei " *Extension. vsixmanifest* " mit einem Text-Editor.
* Fügen Sie das folgende-Tag hinzu:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Speichern und schließen Sie die Datei.

> [!NOTE]
> Möglicherweise müssen Sie die erforderliche Version manuell bearbeiten, um sicherzustellen, dass Sie mit allen Versionen von Visual Studio 2019 oder 2017 kompatibel ist. Dies liegt daran, dass der Designer die Mindestversion in die aktuelle Version von Visual Studio einfügt (z. b. 15.0.26208.0). Da andere Benutzer jedoch möglicherweise über eine frühere Version verfügen, empfiehlt es sich, diese manuell in 15,0 zu bearbeiten.

An diesem Punkt sollte die Manifestressource in etwa wie folgt aussehen:

![Beispiel für erforderliche Komponenten](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Ändern der Projektdatei ("MyProject. csproj")

Es wird dringend empfohlen, während dieses Schritts einen Verweis auf eine geänderte Datei ". csproj" zu verwenden. [Hier](https://github.com/Microsoft/VSSDK-Extensibility-Samples)finden Sie einige Beispiele. Wählen Sie ein beliebiges Erweiterbarkeits Beispiel aus, suchen Sie die *csproj* -Datei als Referenz, und führen Sie die folgenden Schritte aus:

* Navigieren Sie im **Datei-Explorer** zum Projektverzeichnis.
* Öffnen Sie die Datei " *MyProject. csproj* " mit einem Text-Editor.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. aktualisieren Sie die minimumvisualstudioversion.

* Legen Sie die minimale Visual Studio-Version auf fest, `$(VisualStudioVersion)` und fügen Sie dafür eine bedingte Anweisung hinzu. Fügen Sie diese Tags hinzu, wenn Sie nicht vorhanden sind. Stellen Sie Folgendes sicher:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Fügen Sie die vsixtype-Eigenschaft hinzu.

* Fügen Sie das folgende-Tag `<VsixType>v3</VsixType>` zu einer Eigenschaften Gruppe hinzu.

> [!NOTE]
> Es wird empfohlen, dieses unter dem- `<OutputType></OutputType>` Tag hinzuzufügen.

### <a name="3-add-the-debugging-properties"></a>3. Hinzufügen der Debugeigenschaften

* Fügen Sie die folgende Eigenschaften Gruppe hinzu:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Löschen Sie alle Instanzen des folgenden Code Beispiels aus der *csproj* -Datei und allen *csproj. User* -Dateien:

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Hinzufügen von Bedingungen zu den Build Tools Imports

* Fügen Sie den `<import>` Tags, die über eine Microsoft. VSSDK. Buildtools-Referenz verfügen, zusätzliche bedingte Anweisungen hinzu. INSERT `'$(VisualStudioVersion)' != '14.0' And` an der Vorderseite der Bedingungs Anweisung. Diese Anweisungen werden in der Kopfzeile und Fußzeile der CSPROJ-Datei angezeigt.

Beispiel:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Fügen Sie den `<import>` Tags, die über eine Microsoft. VisualStudio. SDK. BuildTasks. 14,0 verfügen, zusätzliche Bedingungs Anweisungen hinzu. INSERT `'$(VisualStudioVersion)' == '14.0' And` an der Vorderseite der Bedingungs Anweisung. Diese Anweisungen werden in der Kopfzeile und Fußzeile der CSPROJ-Datei angezeigt.

Beispiel:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Fügen Sie den `<Error>` Tags, die über eine Microsoft. VSSDK. Buildtools-Referenz verfügen, zusätzliche bedingte Anweisungen hinzu. Fügen Sie hierzu `'$(VisualStudioVersion)' != '14.0' And` am Anfang der Condition-Anweisung ein. Diese Anweisungen werden in der Fußzeile der CSPROJ-Datei angezeigt.

Beispiel:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Fügen Sie den `<Error>` Tags, die über eine Microsoft. VisualStudio. SDK. BuildTasks. 14,0 verfügen, zusätzliche Bedingungs Anweisungen hinzu. INSERT `'$(VisualStudioVersion)' == '14.0' And` an der Vorderseite der Bedingungs Anweisung. Diese Anweisungen werden in der Fußzeile der CSPROJ-Datei angezeigt.

Beispiel:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Speichern Sie die CSPROJ-Datei, und schließen Sie Sie. 
  * Beachten Sie Folgendes: Wenn Sie mehr als ein Projekt in der Projekt Mappe verwenden, legen Sie dieses Projekt als Startprojekt fest, indem Sie im Kontextmenü des Projekts die Option "als Startprojekt festlegen" verwenden.) Dadurch wird sichergestellt, dass Visual Studio das Projekt nach dem Entladen erneut öffnet.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Testen der Erweiterungs Installationen in Visual Studio 2015 und Visual Studio 2019 oder 2017

An diesem Punkt sollte Ihr Projekt bereit sein, ein VSIXv3 zu erstellen, das sowohl in Visual Studio 2015 als auch in Visual Studio 2017 installiert werden kann.

* Öffnen Sie Ihr Projekt in Visual Studio 2015.
* Erstellen Sie das Projekt, und bestätigen Sie in der Ausgabe, dass eine VSIX ordnungsgemäß erstellt wird.
* Navigieren Sie zu Ihrem Projektverzeichnis.
* Öffnen Sie den Ordner *\bin\debug* .
* Doppelklicken Sie auf die vsix-Datei, und installieren Sie die Erweiterung in Visual Studio 2015 und Visual Studio 2019/2017.
* Stellen Sie sicher, dass die **Erweiterung unter Extras**  >  **Erweiterungen und Updates** im Abschnitt **installiert** angezeigt wird.
* Versuchen Sie, die Erweiterung auszuführen, und überprüfen Sie, ob die Erweiterung funktioniert.

![VSIX suchen](media/finding-a-VSIX-example.png)

> [!NOTE]
> Wenn das Projekt nicht mehr mit der Meldung antwortet, **die die Datei öffnet**, erzwingen Sie das Herunterfahren von Visual Studio, navigieren Sie zu Ihrem Projektverzeichnis, zeigen Sie ausgeblendete Ordner an, und löschen Sie den Ordner *.*
