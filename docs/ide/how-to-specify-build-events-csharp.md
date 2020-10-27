---
title: 'Vorgehensweise: Angeben von Buildereignissen (C#)'
description: Hier erfahren Sie, wie Sie Buildereignisse verwenden, um Befehle festzulegen, die vor Beginn oder nach Beenden des Builds ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7bac7b2b293cd508931304b1e6cdd237234001e3
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136939"
---
# <a name="how-to-specify-build-events-c"></a>Vorgehensweise: Angeben von Buildereignissen (C#)

Verwenden Sie Buildereignisse, um Befehle festzulegen, die vor Beginn oder nach Beenden des Builds ausgeführt werden. Buildereignisse werden nur ausgeführt, wenn der Build die betreffenden Punkte im Buildprozess erfolgreich erreicht.

Wenn ein Projekt erstellt wird, werden Präbuildereignisse in eine Datei mit dem Namen *PreBuildEvent.bat* und Postbuildereignisse in eine Datei mit dem Namen *PostBuildEvent.bat* eingefügt. Wenn Sie das Prüfen auf Fehler festlegen möchten, fügen Sie Ihre eigenen Befehle für die Fehlerprüfung den Buildschritten hinzu.

## <a name="specify-a-build-event"></a>Angeben eines Buildereignisses

1. Klicken Sie im **Projektmappen-Explorer** auf das Projekt, für das Sie das Buildereignis angeben möchten.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften** .

3. Klicken Sie auf die Registerkarte **Buildereignisse** .

4. Geben Sie im Feld **Befehlszeile für Präbuildereignis** die Syntax des Buildereignisses an.

   > [!NOTE]
   > Präbuildereignisse werden nicht ausgeführt, wenn das Projekt auf dem neuesten Stand ist, und es wird kein Build gestartet.

5. Geben Sie im Feld **Befehlszeile für Postbuildereignis** die Syntax des Buildereignisses an.

   > [!NOTE]
   > Fügen Sie allen Postbuildbefehlen, die *BAT* -Dateien ausführen, eine `call`-Anweisung hinzu. Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.

6. Geben Sie im Feld **Postbuildereignis ausführen** das Postbuildereignis als auszuführende Bedingung an.

   > [!NOTE]
   > Um umfangreiche Syntax hinzuzufügen oder Buildmakros aus den [Dialogfeldern „Befehlszeile für Präbuildereignis“ und. „Befehlszeile für Postbuildereignis“](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) auszuwählen, klicken Sie auf das Symbol mit den Auslassungszeichen ( **...** ), damit ein Bearbeitungsfeld angezeigt wird.

   Die Syntax des Buildereignisses kann beliebige Befehle enthalten, die für eine Eingabeaufforderung oder eine *BAT* -Datei zulässig sind. Dem Namen der Batchdatei sollte ein `call` vorangestellt sein, um sicherzustellen, dass alle nachfolgenden Befehle ausgeführt werden.

   > [!NOTE]
   > Wenn Ihr Prä- oder Postbuildereignis nicht erfolgreich abgeschlossen wird, können Sie den Build abschließen, indem Sie Ihre Ereignisaktion mit einem Code, der nicht 0 (null) ist, beenden. Dies gibt eine erfolgreiche Aktion an.

## <a name="example"></a>Beispiel

In der folgenden Prozedur wird veranschaulicht, wie Sie das mindestens erforderliche Betriebssystem im Anwendungsmanifest mit einem *EXE* -Befehl festlegen, der von einem Postbuildereignis aus aufgerufen wird (die *EXE.MANIFEST* -Datei im Projektverzeichnis). Das mindestens erforderliche Betriebssystem ist eine Zahlenfolge mit vier Teilen wie z.B. 4.10.0.0. Der Befehl ändert den Abschnitt `<dependentOS>` des Manifests, um die mindestens erforderliche Betriebssystemversion festzulegen:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Erstellen eines EXE-Befehls zum Ändern des Anwendungsmanifests

1. Erstellen Sie ein neues **Konsolen-App** -Projekt für den Befehl. Nennen Sie das Projekt **ChangeOSVersionCS** .

2. Fügen Sie in *Program.cs* die folgende Zeile in die anderen `using`-Anweisungen am Anfang der Datei ein:

   ```csharp
   using System.Xml;
   ```

3. Ersetzen Sie im `ChangeOSVersionCS`-Namespace die `Program`-Klassenimplementierung durch den folgenden Code:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

   Der Befehl akzeptiert zwei Argumente: den Pfad des Anwendungsmanifests (also den Ordner, in dem der Buildprozess das Manifest erstellt, in der Regel *projektname.publish* ), und die neue Version des Betriebssystems.

4. Erstellen Sie das Projekt.

5. Kopieren Sie die *EXE* -Datei z.B. in das Verzeichnis *C:\TEMP\ChangeOSVersionVB.exe* .

Rufen Sie als Nächstes den Befehl in einem Postbuildereignis auf, um das Anwendungsmanifest zu modifizieren.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Aufrufen eines Postbuildereignisses, um das Anwendungsmanifest zu ändern

1. Erstellen Sie ein neues **Windows Forms-App** t, und benennen Sie es **CSWinApp** .

2. Wählen Sie für das im **Projektmappen-Explorer** ausgewählte Projekt im Menü **Projekt****Eigenschaften** aus.

3. Suchen Sie im **Projekt-Designer** die Seite **Veröffentlichen** , und legen Sie den **Veröffentlichungsort** auf *C:\TEMP* fest.

4. Veröffentlichen Sie das Projekt, indem Sie auf **Jetzt veröffentlichen** klicken.

   Dann wird die Manifestdatei erstellt und unter *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest* gespeichert. Um die Manifestdatei anzuzeigen, klicken Sie mit der rechten Maustaste auf die Datei, klicken Sie auf **Öffnen mit** , dann auf **Programm aus einer Liste auswählen** und anschließend auf **Editor** .

   Durchsuchen Sie die Datei nach dem `<osVersionInfo>`-Element. Die Version kann z.B. folgende sein:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. Klicken Sie jetzt wieder im **Projekt-Designer** auf die Registerkarte **Buildereignisse** , und klicken Sie anschließend auf **Postbuild bearbeiten** .

6. Geben Sie im Feld **Befehlszeile für Postbuildereignis** den folgenden Befehl ein:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Wenn Sie das Projekt erstellen, ändert dieser Befehl das mindestens erforderliche Betriebssystem im Anwendungsmanifest in 5.1.2600.0.

   Da das Makro `$(TargetPath)` den vollständigen Pfad für das ausführbare Element angibt, das gerade erstellt wird, gibt `$(TargetPath).manifest` das im Verzeichnis *bin* erstellte Anwendungsmanifest an. Durch die Veröffentlichung wird dieses Manifest an den Veröffentlichungsspeicherort kopiert, den Sie in einem vorherigen Schritt festgelegt haben.

7. Veröffentlichen Sie das Projekt erneut.

   Jetzt sollte die Manifestversion folgendermaßen lauten:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Siehe auch

- [Seite „Buildereignisse“, Projekt-Designer (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Pre-build Event/Post-build Event command line dialog box (Dialogfelder „Befehlszeile für Präbuildereignis“ und „Befehlszeile für Postbuildereignis“)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Vorgehensweise: Angeben von Buildereignissen (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
