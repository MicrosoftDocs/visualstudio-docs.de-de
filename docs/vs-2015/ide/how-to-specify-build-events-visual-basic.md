---
title: 'Vorgehensweise: Festlegen von Buildereignissen (Visual Basic) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 820f4ac8b154579664e01b12aa8146e4668cc17b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670666"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Gewusst wie: Festlegen von Buildereignissen (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Buildereignisse in Visual Basic können für das Ausführen von Skripts, Makros oder anderen Aktionen als Teil des Kompilierungsprozesses verwendet werden. Präbuildereignisse treten vor der Kompilierung auf, während Postbuildereignisse nach der Kompilierung auftreten.

 Buildereignisse werden im Dialogfeld **Buildereignisse** angegeben, das über die Seite **Kompilieren** des **Projekt-Designers** verfügbar ist.

> [!NOTE]
> Visual Basic Express unterstützt keine Eingabe von Buildereignissen. Dies wird nur in der Vollversion von Visual Studio unterstützt.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>So legen Sie Prä- und Postbuildereignisse fest

#### <a name="to-specify-a-build-event"></a>Angeben eines Buildereignisses

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Kompilieren**.

3. Klicken Sie auf die Schaltfläche **Buildereignisse**, um das Dialogfeld **Buildereignisse** zu öffnen.

4. Geben Sie die Befehlszeilenargumente für Ihre Prä- oder Postbuildaktion ein, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Fügen Sie allen Postbuildbefehlen, die BAT-Dateien ausführen, eine `call`-Anweisung hinzu. Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Wenn Ihr Prä- oder Postbuildereignis nicht erfolgreich abgeschlossen wird, können Sie den Build abschließen, indem Sie Ihre Ereignisaktion mit einem Code, der nicht 0 (null) ist, beenden. Dies gibt eine erfolgreiche Aktion an.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Beispiel: Ändern von Manifestinformationen mithilfe eines Postbuildereignisses
 In der folgenden Prozedur wird veranschaulicht, wie Sie das mindestens erforderliche Betriebssystem im Anwendungsmanifest mit einem EXE-Befehl festlegen, der von einem Postbuildereignis aufgerufen wird (die EXE.MANIFEST-Datei im Projektverzeichnis). Das mindestens erforderliche Betriebssystem ist eine Zahlenfolge mit vier Teilen wie z.B. 4.10.0.0. Um dies zu erreichen, ändert der Befehl den `<dependentOS>`-Abschnitt des Manifests:

```
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>So erstellen Sie einen EXE-Befehl zum Ändern des Anwendungsmanifests

1. Erstellen Sie eine Konsolenanwendung für den Befehl. Klicken Sie im Menü **Datei** auf **Neu**und dann auf **Projekt**.

2. Klicken Sie im Dialogfeld **Neues Projekt** im Knoten **Visual Basic** auf **Windows**, und wählen Sie dann die Vorlage **Konsolenanwendung** aus. Benennen Sie das Projekt mit `ChangeOSVersionVB`.

3. Fügen Sie in „Module1.vb“ die folgende Zeile in die andere `Imports`-Anweisung am Anfang der Datei ein:

   ```
   Imports System.Xml
   ```

4. Fügen Sie den folgenden Code zu `Sub Main` hinzu:

   ```
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

    Der Befehl benötigt zwei Argumente. Beim ersten Argument handelt es sich um den Pfad zum Anwendungsmanifest (also den Ordner, in dem der Buildprozess das Manifest erstellt, üblicherweise „Projectname.publish“). Beim zweiten Argument handelt es sich um die neue Version des Betriebssystems.

5. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

6. Kopieren Sie die EXE-Datei in ein Verzeichnis wie z.B. `C:\TEMP\ChangeOSVersionVB.exe`.

   Rufen Sie anschließend den Befehl in einem Postbuildereignis auf, um das Anwendungsmanifest zu ändern.

#### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Aufrufen eines Postbuildereignisses zum Ändern des Anwendungsmanifests

1. Erstellen Sie eine Windows-Anwendung für das zu veröffentlichende Projekt. Klicken Sie im Menü **Datei** auf **Neu**und dann auf **Projekt**.

2. Wählen Sie im Dialogfeld **Neues Projekt** im Knoten **Visual Basic** die Option **Windows** und dann die Vorlage **Windows-Anwendung** aus. Benennen Sie das Projekt mit `VBWinApp`.

3. Klicken Sie für das im **Projektmappen-Explorer** ausgewählte Projekt im Menü **Projekt** auf **Eigenschaften**.

4. Wechseln Sie im Projekt-Designer zur Seite **Veröffentlichen**, und legen Sie den **Veröffentlichungsort** auf `C:\TEMP\` fest.

5. Veröffentlichen Sie das Projekt, indem Sie auf **Jetzt veröffentlichen** klicken.

     Die Manifestdatei wird erstellt und in `C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest` eingefügt. Klicken Sie mit der rechten Maustaste auf die Datei, und klicken Sie dann auf **Öffnen mit** > **Programm aus einer Liste auswählen** und anschließend auf **Editor**, um das Manifest anzuzeigen.

     Durchsuchen Sie die Datei nach dem `<osVersionInfo>`-Element. Die Version kann z.B. folgende sein:

    ```
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. Wechseln Sie im Projekt-Designer zur Registerkarte **Kompilieren** , und klicken Sie auf die Schaltfläche **Ereignisse erstellen** , um das Dialogfeld Buildereignisse zu öffnen. **Build Events**

7. Geben Sie im Feld **Befehlszeile für Postbuildereignis** den folgenden Befehl ein:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Wenn Sie das Projekt erstellen, ändert dieser Befehl das mindestens erforderliche Betriebssystem im Anwendungsmanifest in 5.1.2600.0.

     Das `$(TargetPath)`-Makro gibt den vollständigen Pfad für die ausführbare Datei an, die erstellt wird. Deshalb gibt „$(TargetPath).manifest“ das Anwendungsmanifest an, das im bin-Verzeichnis erstellt wird. Durch die Veröffentlichung wird dieses Manifest an den Veröffentlichungsspeicherort kopiert, den Sie in einem vorherigen Schritt festgelegt haben.

8. Veröffentlichen Sie das Projekt erneut. Wechseln Sie zur Seite **Veröffentlichen**, und klicken Sie anschließen auf **Jetzt veröffentlichen**.

     Zeigen Sie das Manifest erneut an. Klicken Sie mit der rechten Maustaste auf die Datei, wechseln Sie zum Veröffentlichungsverzeichnis, und klicken Sie auf **Öffnen mit** > **Programm aus einer Liste auswählen** und anschließend auf **Editor**, um das Manifest anzuzeigen.

     Jetzt sollte die Version folgendermaßen lauten:

    ```
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Weitere Informationen
 [Verwalten der Kompilierungs Eigenschaften](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c) [Seite "kompilieren", Projekt-Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md) [Seite "veröffentlichen", Projekt-Designer](../ide/reference/publish-page-project-designer.md) [Präbuildereignis/Postbuildereignis-Dialog Feld](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) "Gewusst [wie: Angeben von Buildereignissen](../ide/how-to-specify-build-events-csharp.md) "
