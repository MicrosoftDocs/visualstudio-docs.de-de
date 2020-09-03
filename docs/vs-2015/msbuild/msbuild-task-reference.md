---
title: MSBuild-Aufgabenverweis | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fe581985ec173099790311517c0442a9c29c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154108"
---
# <a name="msbuild-task-reference"></a>Referenz zu MSBuild-Aufgaben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Die Aufgaben in der folgenden Liste sind in [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] enthalten. Wenn [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] installiert wird, sind zusätzliche Aufgaben verfügbar, die für das Erstellen von [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Projekten verwendet werden. Weitere Informationen finden Sie unter [Visual C++ Tasks](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Zusätzlich zu den Parametern, die in den Themen in diesem Abschnitt aufgeführt sind, verfügt jeder Task ebenfalls über folgende Parameter:  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionaler `String`-Parameter.<br /><br /> Ein `Boolean`-Ausdruck, den die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Engine verwendet, um zu bestimmen, ob diese Aufgabe ausgeführt wird. Informationen zu den Bedingungen, die von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] unterstützt werden, finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Optionaler Parameter. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Aufgaben Basisklasse](../msbuild/task-base-class.md)  
 Fügt mehrere Parameter zu den Aufgaben hinzu, die von der <xref:Microsoft.Build.Utilities.Task>-Klasse abgeleitet werden  
  
 [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md)  
 Fügt mehrere Parameter zu den Aufgaben hinzu, die von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse abgeleitet werden  
  
 [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md)  
 Fügt mehrere Parameter zu den Aufgaben hinzu, die von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse abgeleitet werden  
  
 [Al (Assembly Linker)-Aufgabe](../msbuild/al-assembly-linker-task.md)  
 Erstellt eine Assembly mit einem Manifest aus einer oder mehreren Dateien, die entweder Module oder Ressourcendateien darstellen  
  
 [AspNetCompiler-Aufgabe](../msbuild/aspnetcompiler-task.md)  
 Umfasst „aspnet_compiler.exe“, bei dem es sich um ein Hilfsprogramm zum Vorkompilieren von ASP.NET-Anwendungen handelt  
  
 [Zutragculture-Aufgabe](../msbuild/assignculture-task.md)  
 Weist Elementen Kulturbezeichner zu  
  
 [Zutragprojectconfiguration-Aufgabe](../msbuild/assignprojectconfiguration-task.md)  
 Akzeptiert eine Liste von Konfigurationszeichenfolgen und weist diese den angegebenen Projekten zu  
  
 [Zutragpfad-Aufgabe](../msbuild/assigntargetpath-task.md)  
 Akzeptiert eine Liste von Dateien und fügt `<TargetPath>`-Attribute hinzu, wenn diese nicht bereits angegeben wurden  
  
 [CallTarget-Aufgabe](../msbuild/calltarget-task.md)  
 Ruft ein Ziel in der Projektdatei auf  
  
 [CombinePath-Aufgabe](../msbuild/combinepath-task.md)  
 Kombiniert die angegebenen Pfade zu einem einzigen Pfad.  
  
 [Convertdeabsolutepath-Aufgabe](../msbuild/converttoabsolutepath-task.md)  
 Konvertiert einen relativen Pfad oder einen Verweis in einen absoluten Pfad  
  
 [Aufgabe kopieren](../msbuild/copy-task.md)  
 Kopiert Dateien an einen neuen Speicherort  
  
 [Aufgabe "| atecsharpmanifestresourcename"](../msbuild/createcsharpmanifestresourcename-task.md)  
 Erstellt einen Manifestnamen im [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Stil aus einem angegebenen RESX-Dateinamen oder aus einer anderen Ressource  
  
 [Aufgabe "anateitem"](../msbuild/createitem-task.md)  
 Füllt die Elementauflistungen mithilfe der Eingabeelemente auf. Dadurch können Elemente von einer Liste in eine andere kopiert werden  
  
 ["Up Property"-Aufgabe](../msbuild/createproperty-task.md)  
 Füllt Eigenschaften mithilfe der Eingabewerte auf. Dadurch können Werte von einer Eigenschaft oder Zeichenfolge in eine andere kopiert werden  
  
 [Aufgabe "" von "" für ""](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Erstellt einen Manifestnamen im [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Stil aus einem angegebenen RESX-Dateinamen oder aus einer anderen Ressource  
  
 [Csc-Aufgabe](../msbuild/csc-task.md)  
 Ruft den Visual C#-Compiler auf, um ausführbare Dateien, DLLs oder Codemodule zu erzeugen  
  
 [Task löschen](../msbuild/delete-task.md)  
 Löscht die angegebene Datei.  
  
 [Fehler Aufgabe](../msbuild/error-task.md)  
 Beendet einen Build, und protokolliert einen Fehler basierend auf einer ausgewerteten Bedingungsanweisung.  
  
 [Exec-Aufgabe](../msbuild/exec-task.md)  
 Führt das angegebene Programm oder den Befehl mit den angegebenen Argumenten aus  
  
 [FindAppConfigFile-Aufgabe](../msbuild/findappconfigfile-task.md)  
 Sucht nach der Datei „app.config“ (falls vorhanden) in den angegebenen Listen  
  
 [FindInList-Aufgabe](../msbuild/findinlist-task.md)  
 Sucht ein Element in einer angegebenen Liste, das über die entsprechende Elementspezifikation verfügt  
  
 [FindUnderPath-Aufgabe](../msbuild/findunderpath-task.md)  
 Bestimmt, welche Elemente in der angegebenen Elementauflistung im angegebenen Ordner und allen Unterordnern vorhanden sind  
  
 [FormatUrl-Aufgabe](../msbuild/formaturl-task.md)  
 Konvertiert eine URL in ein gültiges URL-Format  
  
 [FormatVersion-Aufgabe](../msbuild/formatversion-task.md)  
 Fügt die Revisionsnummer an die Versionsnummer an.  
  
 [GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md)  
 Generiert ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendungsmanifest oder ein systemeigenes Manifest.  
  
 [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md)  
 Bietet eine automatisierte Methode zum Erkennen, Herunterladen und Installieren einer Anwendung sowie ihrer erforderlichen Komponenten.  
  
 [GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md)  
 Generiert ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Bereitstellungsmanifest.  
  
 [GenerateResource-Aufgabe](../msbuild/generateresource-task.md)  
 Konvertiert TXT- und RESX-Dateien in binäre RESOURCES-Dateien der Common Language Runtime  
  
 [Generatetrustinfo-Aufgabe](../msbuild/generatetrustinfo-task.md)  
 Generiert die Anwendungsvertrauensstellung aus dem Basismanifest und aus den Parametern `TargetZone` und `ExcludedPermissions`  
  
 [GetAssemblyIdentity-Aufgabe](../msbuild/getassemblyidentity-task.md)  
 Ruft die Assemblyidentitäten aus den angegebenen Dateien ab und gibt die Identitätsinformation aus  
  
 [GetFrameworkPath-Aufgabe](../msbuild/getframeworkpath-task.md)  
 Ruft den Pfad zur [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Assembly ab  
  
 [GetFrameworkSdkPath-Aufgabe](../msbuild/getframeworksdkpath-task.md)  
 Ruft den Pfad zum [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] ab  
  
 [Getreferenceassemblypath-Aufgabe](../msbuild/getreferenceassemblypaths-task.md)  
 Gibt den Verweisassemblypfad der verschiedenen Frameworks zurück  
  
 [LC-Aufgabe](../msbuild/lc-task.md)  
 Generiert eine LICENSE-Datei aus einer LICX-Datei  
  
 [MakeDir-Aufgabe](../msbuild/makedir-task.md)  
 Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse  
  
 [Message-Aufgabe](../msbuild/message-task.md)  
 Protokolliert eine Meldung während eines Builds  
  
 [Aufgabe verschieben](../msbuild/move-task.md)  
 Verschiebt Dateien in einen neuen Speicherort.  
  
 [MSBuild-Aufgabe](../msbuild/msbuild-task.md)  
 Erstellt [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekte aus einem anderen [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekt.  
  
 [Aufgabe "infolinesfromfile"](../msbuild/readlinesfromfile-task.md)  
 Liest eine Liste von Elementen aus einer Textdatei  
  
 [RegisterAssembly-Aufgabe](../msbuild/registerassembly-task.md)  
 Liest die Metadaten in der angegebenen Assembly und fügt der Registrierung die notwendigen Einträge hinzu  
  
 [RemoveDir-Aufgabe](../msbuild/removedir-task.md)  
 Entfernt die angegebenen Verzeichnisse und alle enthaltenen Dateien und Unterverzeichnisse  
  
 [RemoveDuplicates-Aufgabe](../msbuild/removeduplicates-task.md)  
 Entfernt doppelte Elemente aus der angegebenen Elementauflistung  
  
 [RequiresFramework35SP1Assembly-Aufgabe](../msbuild/requiresframework35sp1assembly-task.md)  
 Bestimmt, ob die Anwendung .NET Framework 3.5 SP1 erfordert  
  
 ResGen-Aufgabe  
 Veraltet. Verwenden Sie den Task [GenerateResource Task](../msbuild/generateresource-task.md) , um txt-und RESX-Dateien in und aus Common Language Runtime binären resources-Dateien zu konvertieren.  
  
 [ResolveAssemblyReference-Aufgabe](../msbuild/resolveassemblyreference-task.md)  
 Bestimmt alle Assemblys, die von den angegebenen Assemblys abhängig sind.  
  
 [ResolveComReference-Aufgabe](../msbuild/resolvecomreference-task.md)  
 Akzeptiert eine Liste aus mindestens einem Typbibliotheksnamen oder mindestens einer TLB-Datei und löst diese Bibliotheken an Speicherorten auf Datenträgern auf  
  
 [ResolveKeySource-Aufgabe](../msbuild/resolvekeysource-task.md)  
 Bestimmt die Schlüsselquelle mit starkem Namen  
  
 [ResolveManifestFiles-Aufgabe](../msbuild/resolvemanifestfiles-task.md)  
 Löst folgende Elemente im Buildprozess in Dateien für die Manifestgenerierung auf: erstellte Elemente, Abhängigkeiten, Satelliten, Inhalte, Debugsymbole und Dokumentationen  
  
 [Resolvenativereferenzierungsaufgabe](../msbuild/resolvenativereference-task.md)  
 Löst native Verweise auf.  
  
 [ResolveNonMSBuildProjectOutput-Aufgabe](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Bestimmt die Ausgabedateien für Nicht-MSBuild-Projektverweise  
  
 [SGen-Aufgabe](../msbuild/sgen-task.md)  
 Erstellt eine XML-Serialisierungsassembly für Typen in der angegebenen Assembly.  
  
 [SignFile-Aufgabe](../msbuild/signfile-task.md)  
 Signiert die angegebene Datei mit dem angegebenen Zertifikat.  
  
 [Berührungs Aufgabe](../msbuild/touch-task.md)  
 Legt den Zugriff und den Änderungszeitpunkt für Dateien fest  
  
 [UnregisterAssembly-Aufgabe](../msbuild/unregisterassembly-task.md)  
 Hebt die Registrierung der angegebenen Assemblys für COM-Interop-Zwecke auf  
  
 [UpdateManifest-Aufgabe](../msbuild/updatemanifest-task.md)  
 Aktualisiert die ausgewählten Eigenschaften in einem Manifest und führt das Signieren erneut aus.  
  
 [Vbc-Aufgabe](../msbuild/vbc-task.md)  
 Ruft den Visual Basic-Compiler auf, um ausführbare Dateien, DLLs oder Codemodule zu erzeugen  
  
 [Warnungs Aufgabe](../msbuild/warning-task.md)  
 Protokolliert während eines Builds eine Warnung, die auf einer ausgewerteten Bedingungsanweisung basiert  
  
 ["Write-Codefragment"-Aufgabe](../msbuild/writecodefragment-task.md)  
 Generiert eine temporäre Codedatei, indem das angegebene generierte Codefragment verwendet wird. Die Datei wird nicht gelöscht.  
  
 [Task ' Write telinestofile '](../msbuild/writelinestofile-task.md)  
 Schreibt die angegebenen Elemente in die angegebene Textdatei  
  
 [XmlPeek-Aufgabe](../msbuild/xmlpeek-task.md)  
 Gibt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben zurück  
  
 [XmlPoke-Aufgabe](../msbuild/xmlpoke-task.md)  
 Legt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben fest  
  
 [XslTransformation-Aufgabe](../msbuild/xsltransformation-task.md)  
 Transformiert eine XML-Eingabe mithilfe von *Extensible Stylesheet Language Transformation* (XSLT) oder kompiliertem XSLT-Code bzw. kompilierten XSLT-Ausgaben für ein Ausgabegerät oder eine Ausgabedatei  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Schreiben von Aufgaben](../msbuild/task-writing.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)
