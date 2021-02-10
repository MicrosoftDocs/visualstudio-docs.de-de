---
title: MSBuild-Aufgabenverweis | Microsoft-Dokumentation
description: Erfahren Sie mehr über die in MSBuild enthaltenen Aufgaben, die Code bereitstellen, der während des Buildprozesses ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f26c3c1b8256597c795fa8bcd815fd605f895fa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878382"
---
# <a name="msbuild-task-reference"></a>Referenz zu MSBuild-Tasks

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Die Aufgaben in der folgenden Liste sind in MSBuild enthalten. Wenn die C++-Workload installiert wurde, sind zusätzliche Aufgaben verfügbar, die für das Erstellen von C++-Projekten verwendet werden. Weitere Informationen finden Sie unter [C++-Aufgaben](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Zusätzlich zu den Parametern, die in den Themen in diesem Abschnitt aufgeführt sind, verfügt jeder Task ebenfalls über folgende Parameter:

| Parameter | Beschreibung |
|-------------------| - |
| `Condition` | Optionaler `String`-Parameter.<br /><br /> Ein `Boolean`-Ausdruck, mit dem die MSBuild-Engine bestimmt, ob diese Aufgabe ausgeführt wird. Informationen zu den von MSBuild unterstützten Bedingungen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Dieser Parameter ist optional. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>In diesem Abschnitt

- [Aufgabenbasisklasse](../msbuild/task-base-class.md)

 Fügt mehrere Parameter zu den Aufgaben hinzu, die von der <xref:Microsoft.Build.Utilities.Task>-Klasse abgeleitet werden Ist nicht dafür vorgesehen, direkt verwendet zu werden.

- [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md)

 Fügt mehrere Parameter zu den Aufgaben hinzu, die von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse abgeleitet werden Ist nicht dafür vorgesehen, direkt verwendet zu werden.

- [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md)

 Fügt mehrere Parameter zu den Aufgaben hinzu, die von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse abgeleitet werden Ist nicht dafür vorgesehen, direkt verwendet zu werden.

- [AL-Aufgabe (Assembly Linker)](../msbuild/al-assembly-linker-task.md)

 Erstellt eine Assembly mit einem Manifest aus einer oder mehreren Dateien, die entweder Module oder Ressourcendateien darstellen

- [AspNetCompiler-Aufgabe](../msbuild/aspnetcompiler-task.md)

 Umfasst *aspnet_compiler.exe*, wobei es sich um ein Hilfsprogramm zum Vorkompilieren von ASP.NET-Anwendungen handelt.

- [AssignCulture-Aufgabe](../msbuild/assignculture-task.md)

 Weist Elementen Kulturbezeichner zu

- [AssignProjectConfiguration-Aufgabe](../msbuild/assignprojectconfiguration-task.md)

 Akzeptiert eine Liste von Konfigurationszeichenfolgen und weist diese den angegebenen Projekten zu

- [AssignTargetPath-Aufgabe](../msbuild/assigntargetpath-task.md)

 Akzeptiert eine Liste von Dateien und fügt `<TargetPath>`-Attribute hinzu, wenn diese nicht bereits angegeben wurden

- [CallTarget-Aufgabe](../msbuild/calltarget-task.md)

 Ruft ein Ziel in der Projektdatei auf

- [CombinePath-Aufgabe](../msbuild/combinepath-task.md)

 Kombiniert die angegebenen Pfade zu einem einzigen Pfad.

- [ConvertToAbsolutePath-Aufgabe](../msbuild/converttoabsolutepath-task.md)

 Konvertiert einen relativen Pfad oder einen Verweis in einen absoluten Pfad

- [Copy-Aufgabe](../msbuild/copy-task.md)

 Kopiert Dateien an einen neuen Speicherort

- [CreateCSharpManifestResourceName-Aufgabe](../msbuild/createcsharpmanifestresourcename-task.md)

 Erstellt einen Manifestnamen im C#-Stil aus einem angegebenen *RESX*-Dateinamen oder aus einer anderen Ressource.

- [CreateItem-Aufgabe](../msbuild/createitem-task.md)

 Füllt die Elementauflistungen mithilfe der Eingabeelemente auf. Dadurch können Elemente von einer Liste in eine andere kopiert werden

- [CreateProperty-Aufgabe](../msbuild/createproperty-task.md)

 Füllt Eigenschaften mithilfe der Eingabewerte auf. Dadurch können Werte von einer Eigenschaft oder Zeichenfolge in eine andere kopiert werden

- [CreateVisualBasicManifestResourceName-Aufgabe](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Erstellt einen Manifestnamen im Visual Basic-Stil aus einem angegebenen *RESX*-Dateinamen oder aus einer anderen Ressource.

- [Csc-Aufgabe](../msbuild/csc-task.md)

 Ruft den Visual C#-Compiler auf, um ausführbare Dateien, DLLs oder Codemodule zu erzeugen

- [Delete-Aufgabe](../msbuild/delete-task.md)

 Löscht die angegebene Datei.

- [DownloadFile-Aufgabe](../msbuild/downloadfile-task.md)

 Lädt eine Datei herunter und speichert diese am angegebenen Speicherort.

- [Fehleraufgabe](../msbuild/error-task.md)

 Beendet einen Build, und protokolliert einen Fehler basierend auf einer ausgewerteten Bedingungsanweisung.

- [Exec-Aufgabe](../msbuild/exec-task.md)

 Führt das angegebene Programm oder den Befehl mit den angegebenen Argumenten aus

- [FindAppConfigFile-Aufgabe](../msbuild/findappconfigfile-task.md)

 Sucht nach der Datei *app.config* (falls vorhanden) in den angegebenen Listen.

- [FindInList-Aufgabe](../msbuild/findinlist-task.md)

 Sucht ein Element in einer angegebenen Liste, das über die entsprechende Elementspezifikation verfügt

- [FindUnderPath-Aufgabe](../msbuild/findunderpath-task.md)

 Bestimmt, welche Elemente in der angegebenen Elementauflistung im angegebenen Ordner und allen Unterordnern vorhanden sind

- [FormatUrl-Aufgabe](../msbuild/formaturl-task.md)

 Konvertiert eine URL in ein gültiges URL-Format

- [FormatVersion-Aufgabe](../msbuild/formatversion-task.md)

 Fügt die Revisionsnummer an die Versionsnummer an.

- [GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md)

 Generiert ein ClickOnce-Anwendungsmanifest oder ein natives Manifest.

- [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md)

 Bietet eine automatisierte Methode zum Erkennen, Herunterladen und Installieren einer Anwendung sowie ihrer erforderlichen Komponenten.

- [GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md)

 Generiert ein ClickOnce-Bereitstellungsmanifest.

- [GenerateResource-Aufgabe](../msbuild/generateresource-task.md)

 Konvertiert *TXT*- und *RESX*-Dateien in binäre *RESOURCES*-Dateien der Common Language Runtime.

- [GenerateTrustInfo-Aufgabe](../msbuild/generatetrustinfo-task.md)

 Generiert die Anwendungsvertrauensstellung aus dem Basismanifest und aus den Parametern `TargetZone` und `ExcludedPermissions`

- [GetAssemblyIdentity-Aufgabe](../msbuild/getassemblyidentity-task.md)

 Ruft die Assemblyidentitäten aus den angegebenen Dateien ab und gibt die Identitätsinformation aus

- [GetFileHash-Aufgabe](../msbuild/getfilehash-task.md)

 Berechnet Prüfsummen der Inhalte einer Datei oder mehrerer Dateien.

- [GetFrameworkPath-Aufgabe](../msbuild/getframeworkpath-task.md)

 Ruft den Pfad zu den .NET Framework-Assemblys ab.

- [GetFrameworkSdkPath-Aufgabe](../msbuild/getframeworksdkpath-task.md)

 Ruft den Pfad zum Windows Software Development Kit (SDK) ab.

- [GetReferenceAssemblyPaths-Aufgabe](../msbuild/getreferenceassemblypaths-task.md)

 Gibt den Verweisassemblypfad der verschiedenen Frameworks zurück

- [LC-Aufgabe](../msbuild/lc-task.md)

 Generiert eine *LICENSE*-Datei aus einer *LICX*-Datei.

- [MakeDir-Aufgabe](../msbuild/makedir-task.md)

 Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse

- [Meldungsaufgabe](../msbuild/message-task.md)

 Protokolliert eine Meldung während eines Builds

- [Move-Aufgabe](../msbuild/move-task.md)

 Verschiebt Dateien in einen neuen Speicherort.

- [MSBuild-Aufgabe](../msbuild/msbuild-task.md)

 Erstellt MSBuild-Projekte aus einem anderen MSBuild-Projekt.

- [ReadLinesFromFile-Aufgabe](../msbuild/readlinesfromfile-task.md)

 Liest eine Liste von Elementen aus einer Textdatei

- [RegisterAssembly-Aufgabe](../msbuild/registerassembly-task.md)

 Liest die Metadaten in der angegebenen Assembly und fügt der Registrierung die notwendigen Einträge hinzu

- [RemoveDir-Aufgabe](../msbuild/removedir-task.md)

 Entfernt die angegebenen Verzeichnisse und alle enthaltenen Dateien und Unterverzeichnisse

- [RemoveDuplicates-Aufgabe](../msbuild/removeduplicates-task.md)

 Entfernt doppelte Elemente aus der angegebenen Elementauflistung

- [RequiresFramework35SP1Assembly-Aufgabe](../msbuild/requiresframework35sp1assembly-task.md)

 Bestimmt, ob die Anwendung .NET Framework 3.5 SP1 erfordert

- ResGen-Aufgabe

 Veraltet. Verwenden Sie die [GenerateResource-Aufgabe](../msbuild/generateresource-task.md), um *TXT*- und *RESX*-Dateien in und aus binären *RESOURCES*-Dateien der Common Language Runtime zu konvertieren.

- [ResolveAssemblyReference-Aufgabe](../msbuild/resolveassemblyreference-task.md)

 Bestimmt alle Assemblys, die von den angegebenen Assemblys abhängig sind.

- [ResolveComReference-Aufgabe](../msbuild/resolvecomreference-task.md)

 Akzeptiert eine Liste aus mindestens einem Typbibliotheksnamen oder mindestens einer *TLB*-Datei und löst diese Bibliotheken an Speicherorten auf Datenträgern auf.

- [ResolveKeySource-Aufgabe](../msbuild/resolvekeysource-task.md)

 Bestimmt die Schlüsselquelle mit starkem Namen

- [ResolveManifestFiles-Aufgabe](../msbuild/resolvemanifestfiles-task.md)

 Löst folgende Elemente im Buildprozess in Dateien für die Manifestgenerierung auf: erstellte Elemente, Abhängigkeiten, Satelliten, Inhalte, Debugsymbole und Dokumentationen

- [ResolveNativeReference-Aufgabe](../msbuild/resolvenativereference-task.md)

 Löst native Verweise auf.

- [ResolveNonMSBuildProjectOutput-Aufgabe](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Bestimmt die Ausgabedateien für Nicht-MSBuild-Projektverweise

- [SGen-Aufgabe](../msbuild/sgen-task.md)

 Erstellt eine XML-Serialisierungsassembly für Typen in der angegebenen Assembly.

- [SignFile-Aufgabe](../msbuild/signfile-task.md)

 Signiert die angegebene Datei mit dem angegebenen Zertifikat.

- [Touch-Aufgabe](../msbuild/touch-task.md)

 Legt den Zugriff und den Änderungszeitpunkt für Dateien fest

- [UnregisterAssembly-Aufgabe](../msbuild/unregisterassembly-task.md)

 Hebt die Registrierung der angegebenen Assemblys für COM-Interop-Zwecke auf

- [Unzip-Aufgabe](../msbuild/unzip-task.md)

 Entzippt ein *ZIP*-Archiv am angegebenen Speicherort.

- [UpdateManifest-Aufgabe](../msbuild/updatemanifest-task.md)

 Aktualisiert die ausgewählten Eigenschaften in einem Manifest und führt das Signieren erneut aus.

- [Vbc-Aufgabe](../msbuild/vbc-task.md)

 Ruft den Visual Basic-Compiler auf, um ausführbare Dateien, DLLs oder Codemodule zu erzeugen

- [VerifyFileHash-Aufgabe](../msbuild/verifyfilehash-task.md)

 Überprüft, ob die Datei mit dem erwarteten Dateihash übereinstimmt.

- [Warnungsaufgabe](../msbuild/warning-task.md)

 Protokolliert während eines Builds eine Warnung, die auf einer ausgewerteten Bedingungsanweisung basiert

- [WriteCodeFragment-Aufgabe](../msbuild/writecodefragment-task.md)

 Generiert eine temporäre Codedatei, indem das angegebene generierte Codefragment verwendet wird. Die Datei wird nicht gelöscht.

- [WriteLinesToFile-Aufgabe](../msbuild/writelinestofile-task.md)

 Schreibt die angegebenen Elemente in die angegebene Textdatei

- [XmlPeek-Aufgabe](../msbuild/xmlpeek-task.md)

 Gibt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben zurück

- [XmlPoke-Aufgabe](../msbuild/xmlpoke-task.md)

 Legt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben fest

- [XslTransformation-Aufgabe](../msbuild/xsltransformation-task.md)

 Transformiert eine XML-Eingabe mithilfe von *Extensible Stylesheet Language Transformation* (XSLT) oder kompiliertem XSLT-Code bzw. kompilierten XSLT-Ausgaben für ein Ausgabegerät oder eine Ausgabedatei

- [ZipDirectory-Aufgabe](../msbuild/zipdirectory-task.md)

 Erstellt ein *ZIP*-Archiv aus den Inhalten eines Verzeichnisses.

## <a name="see-also"></a>Siehe auch

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Schreiben von Aufgaben](../msbuild/task-writing.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
