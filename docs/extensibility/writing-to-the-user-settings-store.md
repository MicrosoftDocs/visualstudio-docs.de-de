---
title: Schreiben in den Benutzer Einstellungs Speicher | Microsoft-Dokumentation
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie Visual Studio als externes Tool Notepad hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55e17693bee1ced0354b21ee5cc736961a994c6f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876921"
---
# <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen
Benutzereinstellungen sind beschreibbare Einstellungen wie diejenigen im Dialogfeld Extras **/Optionen** , Eigenschaften Fenster und bestimmte andere Dialogfelder. In Visual Studio-Erweiterungen können diese zum Speichern kleiner Datenmengen verwendet werden. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in Visual Studio Notepad als externes Tool hinzufügen, indem Sie aus dem Benutzer Einstellungs Speicher lesen und darin schreiben.

## <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen

1. Erstellen Sie ein VSIX-Projekt namens usersettingsstoreextension, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen usersettingsstorecommand hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) .

2. Fügen Sie in UserSettingsStoreCommand.cs die folgenden using-Direktiven hinzu:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. Löschen Sie in MenuItemCallBack den Text der-Methode, und rufen Sie den Benutzer Einstellungs Speicher wie folgt ab:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Stellen Sie nun fest, ob Notepad bereits als externes Tool festgelegt ist. Sie müssen alle externen Tools durchlaufen, um zu bestimmen, ob die toolcmd-Einstellung wie folgt "Notepad" lautet:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Wenn Notepad nicht als externes Tool festgelegt wurde, legen Sie es wie folgt fest:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Testen des Codes Beachten Sie, dass Sie Notepad als externes Tool hinzufügt, sodass Sie ein Rollback der Registrierung ausführen müssen, bevor Sie ein zweites Mal ausgeführt wird.

7. Erstellen Sie den Code, und starten Sie das Debugging.

8. Klicken Sie **im Menü Extras** auf **usersettingsstorecommand aufrufen**. Dadurch wird Notepad **zum Menü Extras** hinzugefügt.

9. Nun sollte im Menü Extras/Optionen Notepad angezeigt werden, und durch Klicken auf **Notepad** sollte eine Instanz von Notepad angezeigt werden.
