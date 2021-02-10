---
title: Verwenden des Einstellungs Speicher | Microsoft-Dokumentation
description: 'Erfahren Sie, wie Sie Daten aus dem Konfigurations Einstellungs Speicher lesen. diese Einstellungen sind schreibgeschützt: Visual Studio-und VSPackage-Einstellungen.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 752a912fd9a565e4b3e8dcb5c4c142e8f37dffc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934037"
---
# <a name="using-the-settings-store"></a>Verwenden des Einstellungsspeichers
Es gibt zwei Arten von Einstellungs speichern:

- Konfigurationseinstellungen, bei denen es sich um schreibgeschützte Visual Studio-und VSPackage-Einstellungen handelt. In Visual Studio werden Einstellungen aus allen bekannten pkgdef-Dateien in diesem Speicher zusammengeführt.

- Benutzereinstellungen, bei denen es sich um beschreibbare Einstellungen handelt, z. b. diejenigen, die auf Seiten im Dialogfeld **Optionen** , Eigenschaften Seiten und bestimmte andere Dialogfelder angezeigt werden. Diese können von Visual Studio-Erweiterungen für die lokale Speicherung von kleinen Datenmengen verwendet werden.

  In dieser exemplarischen Vorgehensweise wird das Lesen von Daten aus dem Konfigurations Einstellungs Speicher erläutert. Eine Erläuterung zum Schreiben in den Benutzer Einstellungs Speicher finden Sie unter [Schreiben in den Benutzer Einstellungs Speicher](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Erstellen des Beispielprojekts
 In diesem Abschnitt wird gezeigt, wie ein einfaches Erweiterungsprojekt mit einem Menübefehl für die Demonstration erstellt wird.

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungs Projekt, das die Erweiterungs Ressourcen enthält. Erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt mit dem Namen `SettingsStoreExtension` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** " unter **Visual c#/Erweiterbarkeit**.

2. Fügen Sie nun eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **settingsstorecommand** hinzu. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in **SettingsStoreCommand.cs**. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) .

## <a name="using-the-configuration-settings-store"></a>Verwenden des Speicher für Konfigurationseinstellungen
 In diesem Abschnitt wird gezeigt, wie Konfigurationseinstellungen erkannt und angezeigt werden.

1. Fügen Sie in der Datei SettingsStorageCommand.cs die folgenden using-Direktiven hinzu:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. `MenuItemCallback`Entfernen Sie in den Text der-Methode, und fügen Sie die folgenden Zeilen hinzu, um den Konfigurations Einstellungs Speicher zu erhalten:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>Ist eine verwaltete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Hilfsklasse über den Dienst.

3. Erfahren Sie nun, ob Windows Phone Tools installiert sind. Der Code sollte wie folgt aussehen:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Testen des Codes Erstellen Sie das Projekt, und starten Sie das Debugging.

5. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **settingsstorecommand aufrufen**.

    Es sollte ein Meldungs Feld mit der Meldung " **Microsoft Windows Phone Entwicklertools:**  gefolgt von **true** oder **false**" angezeigt werden.

   Visual Studio speichert den Einstellungs Speicher in der Systemregistrierung.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>So verwenden Sie einen Registrierungs-Editor zum Überprüfen der Konfigurationseinstellungen

1. Öffnen Sie Regedit.exe.

2. Navigieren Sie zu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Stellen Sie sicher, dass Sie den Schlüssel sehen, der \ 14.0Exp_Config \ und Not \ 14.0_Config enthält \\ . Wenn Sie die experimentelle Instanz von Visual Studio ausführen, befinden sich die Konfigurationseinstellungen in der Registrierungs Struktur "14.0Exp_Config".

3. Erweitern Sie den Knoten \installierte Produkte \. Wenn die Meldung in den vorherigen Schritten **Microsoft Windows Phone Entwicklertools installiert ist: true**, dann sollte \installierte Produkte \ einen Microsoft Windows Phone Entwicklertools-Knoten enthalten. Wenn die Nachricht **Microsoft Windows Phone Entwicklertools installiert ist: "false**", sollte "\installierte Produkte \" keinen Knoten "Microsoft Windows Phone Entwicklertools" enthalten.
