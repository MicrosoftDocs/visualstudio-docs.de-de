---
title: 'Exemplarische Vorgehensweise: Erweitern von Visual Studio für Mac'
description: Hier erfahren Sie, wie Sie ein einfaches Erweiterungspaket für Visual Studio für Mac erstellen, das einen neuen Befehl im Menü „Bearbeiten“ erstellt.
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: 9274f86e8ade5b49b5db0c7f4773cf6fd57ea353
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876193"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Exemplarische Vorgehensweise: Erweitern von Visual Studio für Mac

In diesem Thema lernen Sie, wie Sie ein [einfaches Erweiterungspaket](https://github.com/mjh4/AddIns/tree/master/DateInserter) erstellen. Das Erweiterungspaket erstellt einen neuen Befehl im Menü "Bearbeiten" von Visual Studio für Mac, mit dem der Benutzer das aktuelle Datum und die aktuelle Zeit in ein offenes Textdokument einfügen kann.

Dieses Beispiel verwendet den Add-In-Maker. Der Add-In-Maker erstellt eine neue Projektvorlage und füllt diese mit den erforderlichen Dateien für das benutzerdefinierte Erweiterungspaket auf.

1. Beginnen Sie, indem Sie Visual Studio für Mac starten, wenn es nicht bereits geöffnet ist:

   ![Screenshot Visual Studio für Mac](media/extending-visual-studio-mac-addin3.png)

2. Installieren Sie das _Erweiterungspaket „Add-In-Maker“_ mit dem Erweiterungs-Manager. Klicken Sie im Menü von Visual Studio auf **Erweiterungen...**.

   ![Registerkarte „Add-In-Manager“](media/extending-visual-studio-mac-addin4.png)

3. Navigieren Sie zur Registerkarte „Katalog“, und geben Sie `Addin Maker` in die Suchleiste oben rechts ein. Klicken Sie auf den Add-In-Maker in der Kategorie „Add-In-Entwicklung“ und dann auf <kbd>Installieren</kbd>. Wenn nichts angezeigt wird, drücken Sie auf „Aktualisieren“, und versuchen Sie es erneut.

   ![Add-In-Manager](media/extending-visual-studio-mac-addin5.png)

4. Nach der Installation des Add-In-Managers können Sie mit dem Erstellen des Erweiterungspakets beginnen. Beginnen Sie mit dem Erstellen einer neuen Projektmappe.

5. Klicken Sie im **Dialogfeld "Neue Projektmappe"** auf die Vorlage **Other > Miscellaneous > General > Xamarin Studio Addin > C#** (Sonstige > Verschiedenes > Allgemein > Xamarin Studio-Add-In > C#), und geben Sie der neuen Projektmappe auf der folgenden Seite den Namen `DateInserter`:

   ![Erstellen einer neuen Projektmappe](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio für Mac füllt die neue Projektmappe auf:

   ![Aufgefüllte Projektmappe](media/extending-visual-studio-mac-addin8.png)

7. Entfernen Sie den Vorlagencode in `Manifest.addin.xml`, und ersetzen Sie Ihn durch den folgenden:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. Jetzt müssen Sie die Dateien einrichten, die später das Einfügen des Datums und der Zeit im Text-Editor verarbeiten. Klicken Sie mit der rechten Maustaste auf den Knoten „Projekte“, und fügen Sie dann eine neue Datei hinzu. Klicken Sie auf **Allgemein > Leere Klasse**, und geben Sie der neuen Datei den Namen *InsertDateHandler*:

   ![Insert Date Handler](media/extending-visual-studio-mac-addin9.png)

9. Entfernen Sie den Vorlagencode in `InsertDateHandler.cs`, und ersetzen Sie Ihn durch den folgenden:

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   Später erweitern Sie diese beiden Platzhaltermethoden.

10. Klicken Sie mit der rechten Maustaste auf das Projekt **DataInserter** und dann auf **Hinzufügen > Neues Element**. Klicken Sie auf **Allgemein > Leere Enumeration**, und geben Sie der neuen Datei den Namen *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Fügen Sie den Befehl `InsertDate` als neue Enumeration in die `DateInserterCommands.cs`-Datei ein:

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. Nun sollten Sie ein funktionierendes Erweiterungspaket haben. Sie können es ausprobieren, indem Sie das gerade Durchgeführt speichert und die Anwendung ausführen. Die IDE startet eine neue Instanz von Visual Studio für Mac mit dem installierten Erweiterungspaket. Wenn Sie zum **Menü "Bearbeiten"** navigieren, sehen Sie, dass Visual Studio für Mac über die neue Option **Datum einfügen** verfügt, wie im unten stehende Screenshot veranschaulicht:

    ![Befehl "Datum einfügen"](media/extending-visual-studio-mac-addin11.png)

    Beachten Sie, dass das Auswählen der Option im Moment noch keine Auswirkungen hat, da die aktuelle Implementierung noch Platzhaltermethoden enthält.

13. Das Framework für das Erweiterungspaket wurde erstellt. Nun können Sie den Code schreiben, der für das Einfügen des Datums verantwortlich ist. Stellen Sie zunächst sicher, dass der **Befehl "Datum einfügen"** nur aktiviert ist, wenn der Benutzer eine offene Textdatei hat, indem Sie die `Update`-Methode in `InsertDateHandler.cs` durch den folgenden Code ersetzen:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Aktualisieren Sie die `Run`-Methode des Befehls, um das Datum und die Zeit mit folgendem Code einzufügen:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Führen Sie zum Schluss das Erweiterungspaket aus, um es zu testen. Klicken Sie in der neuen Instanz von Visual Studio für Mac auf **Bearbeiten > Datum einfügen**. Das aktuelle Datum und die aktuelle Uhrzeit werden an der Einfügemarke eingefügt, wie im unten stehenden Screenshot veranschaulicht:

    ![Screenshot vom Einfügen des Datums](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Weitere Informationen:

- [Erstellen Ihrer ersten Erweiterung (Visual Studio unter Windows)](/visualstudio/extensibility/extensibility-hello-world)