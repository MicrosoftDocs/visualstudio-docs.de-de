---
title: Identifizieren und Anpassen von Tastenkombinationen
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d78a86c64cd85ea8738ec9038c5e64642ca950
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935949"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identifizieren und Anpassen von Tastenkombinationen in Visual Studio

Sie können Tastenkombinationen für Visual Studio-Befehle nachschlagen, diese Tastenkombinationen anpassen und sie dann exportieren, damit andere Benutzer sie verwenden können. Viele Tastenkombinationen rufen immer dieselben Befehle auf, aber das Verhalten einer Tastenkombination kann auf der Grundlage von Bedingungen unterschiedlich sein, die von folgenden Fragen abhängen:

- Welche Standardumgebungseinstellungen wurde beim erstmaligen Öffnen von Visual Studio ausgewählt (beispielsweise „Allgemeine Entwicklung“ oder Visual C#)? (Weitere Informationen zum Ändern oder Zurücksetzen Ihrer Einstellungen finden Sie unter [Umgebungseinstellungen](environment-settings.md).)

- Wurde das Verhalten der Tastenkombination angepasst?

- In welchem Kontext wird die Tastenkombination angewendet? Beispielsweise ruft die Taste **F2** den Befehl `Edit.EditCell` auf, wenn Sie den **Einstellungs-Designer** verwenden, aber den Befehl `File.Rename`, wenn Sie mit **Team Explorer** arbeiten.

Unabhängig von Einstellungen, Anpassungen und Kontext können Sie eine Tastenkombination im Dialogfeld **Optionen** immer nachschlagen und ändern. Sie können in [Beliebte Tastenkombinationen](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) auch die Standardtastenkombinationen für mehrere Dutzend Befehle nachschlagen. Eine vollständige Liste aller Standardtastenkombinationen (basierend auf den Einstellungen in **Allgemeine Entwicklung**) finden Sie unter [Alle Tastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Wenn eine Tastenkombinationen einem Befehl im *globalen* Kontext und in keinem anderen zugewiesen ist, ruft diese Tastenkombination immer diesen Befehl auf. Aber eine Tastenkombination kann einem Befehl im globalen Kontext und einem anderen Befehl in einem speziellen Kontext zugewiesen werden. Wenn Sie eine solche Tastenkombination in dem speziellen Kontext verwenden, ruft sie den Befehl für diesen Kontext auf und nicht den Befehl für den globalen Kontext.

> [!NOTE]
> Je nach Ihren Einstellungen und der Edition von Visual Studio ändern sich möglicherweise auch die Namen und Positionen von Menübefehlen oder die Optionen in Dialogfeldern. Diese Seite basiert auf den Einstellungen des Profils **Allgemeine Entwicklung**.

## <a name="identify-a-keyboard-shortcut"></a>Nachschlagen einer Tastenkombination

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus.

2. Erweitern Sie **Umgebung**, und klicken Sie dann auf **Tastatur**.

   ![Tastenkombinationen im Dialogfeld "Optionen" anzeigen](../ide/media/optionskeyboard.png)

3. Geben Sie in das Feld **Befehle mit folgendem Inhalt anzeigen** den gesamten Befehlsnamen ohne Leerzeichen ein.

   Beispielsweise können Sie Befehle für `solutionexplorer` suchen.

4. Wählen Sie in der Liste den richtigen Befehl aus.

    Sie können beispielsweise `View.SolutionExplorer` auswählen.

5. Wenn dem Befehl eine Tastenkombination zugeordnet ist, wird sie in der Liste **Shortcut(s) for selected command** (Tastenkombination für ausgewählten Befehl) aufgeführt.

   ![Tastenkombination für einen bestimmten Befehl anzeigen](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Anpassen einer Tastenkombination

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus.

2. Erweitern Sie **Umgebung**, und klicken Sie dann auf **Tastatur**.

3. Optional: Filtern Sie die Liste mit Befehlen, indem Sie in das Feld **Befehle mit folgendem Inhalt anzeigen** den gesamten Befehlsnamen oder Teile des Befehlsnamens ohne Leerzeichen eingeben.

4. Wählen Sie in der Liste den Befehl aus, dem Sie eine Tastenkombination zuweisen möchten.

   Wählen Sie in der Liste **Use new shortcut in** (Neue Tastenkombination verwenden in) den Funktionsbereich aus, in dem die Tastenkombination verwendet werden soll.

   Wählen Sie beispielsweise **Global** aus, wenn die Tastenkombination in allen Zusammenhängen funktionieren soll. Sie können jede Tastenkombination verwenden, die in keinem anderen Editor (als Global) zugeordnet ist. Andernfalls wird die Tastenkombination vom Editor überschrieben.

   > [!NOTE]
   > Die folgenden Tasten können Sie nicht als Teil einer **globalen** Tastenkombination zuweisen:
   >
   > - EINGABETASTE, TAB-TASTE, FESTSTELLTASTE
   > - DRUCK-TASTE, S-ABF-TASTE, ROLLEN-TASTE, PAUSE/UNTERBRECHEN-TASTE
   > - EINFG-TASTE, POS1-TASTE, BILD-AUF-TASTE, BILD-AB-TASTE
   > - WINDOWS-LOGO-TASTE, ANWENDUNGSTASTE, beliebige der PFEILTASTEN
   > - NUM-TASTE oder ENTF-TASTE auf der Zehnertastatur
   > - Die Tastenkombination STRG+ALT+ENTF

6. Geben Sie in das Feld **Press shortcut key(s)** (Tastenkombination drücken) die Tastenkombination ein, die Sie verwenden möchten.

    > [!NOTE]
    > Sie können eine Tastenkombination erstellen, die einen Buchstaben mit **ALT**, **STRG** oder mit beiden Tasten kombiniert. Sie können auch eine Tastenkombination erstellen, die **UMSCHALT** und einen Buchstaben mit **ALT**, **STRG** oder mit beiden Tasten kombiniert.

     Wenn eine Tastenkombination bereits einem anderen Befehl zugeordnet ist, wird sie im Feld **Tastenkombination wird momentan verwendet von** angezeigt. Löschen Sie in diesem Fall die Tastenkombination mit der **RÜCKTASTE**, und versuchen Sie es mit einer anderen Tastenkombination.

    ![Eine andere Tastenkombination für einen Befehl angeben](../ide/media/reassignshortcut.png)

7. Klicken Sie auf **Zuweisen**.

    > [!NOTE]
    > Wenn Sie eine andere Tastenkombination für einen Befehl angeben, klicken Sie auf **Zuweisen** und dann auf **Abbrechen**, um das Dialogfeld zu schließen. Die von Ihnen zugewiesene Tastenkombination wird nicht zurückgesetzt.

## <a name="share-custom-keyboard-shortcuts"></a>Freigeben benutzerdefinierter Tastenkombinationen

Sie können Ihre selbstdefinierten Tastenkombinationen freigeben, indem Sie sie in eine Datei exportieren und die Datei dann anderen Benutzern zur Verfügung stellen, sodass diese die Daten importieren können.

### <a name="to-export-only-keyboard-shortcuts"></a>So exportieren Sie nur Tastenkombinationen

1. Klicken Sie in der Menüleiste auf **Extras** > **Einstellungen importieren und exportieren**.

2. Klicken Sie auf **Ausgewählte Umgebungseinstellungen exportieren** und dann auf **Weiter**.

3. Deaktivieren Sie unter **Welche Einstellungen sollen exportiert werden?** das Kontrollkästchen **Alle Einstellungen**, und erweitern Sie **Optionen** sowie **Umgebung**.

4. Aktivieren Sie das Kontrollkästchen **Tastatur**, und klicken Sie dann auf **Weiter**.

   ![Nur angepasste Tastenkombinationen exportieren](../ide/media/exportshortcuts.png)

5. Übernehmen Sie in den Feldern **Geben Sie den Namen der Einstellungsdatei ein** und **Einstellungsdatei in folgendem Verzeichnis speichern** entweder die Standardwerte, oder geben Sie andere Werte ein, und klicken Sie dann auf die Schaltfläche **Fertigstellen**.

::: moniker range="vs-2017"

Standardmäßig werden die Tastenkombinationen in einer Datei im Ordner *%USERPROFILE%\Dokumente\Visual Studio 2017\Settings* gespeichert. Der Name der Datei entspricht dem Datum, an dem Sie die Einstellungen exportiert haben, und die Erweiterung ist *.vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Standardmäßig werden die Tastenkombinationen in einer Datei im Ordner *%USERPROFILE%\Dokumente\Visual Studio 2019\Settings* gespeichert. Der Name der Datei entspricht dem Datum, an dem Sie die Einstellungen exportiert haben, und die Erweiterung ist *.vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>So importieren Sie nur Tastenkombinationen

1. Klicken Sie in der Menüleiste auf **Extras** > **Einstellungen importieren und exportieren**.

2. Klicken Sie auf das Optionsfeld **Ausgewählte Umgebungseinstellungen importieren** und dann auf **Weiter**.

3. Klicken Sie auf das Optionsfeld **Nein, neue Einstellungen importieren und aktuelle Einstellungen überschreiben** und dann auf **Weiter**.

4. Wählen Sie unter **Meine Einstellungen** die Datei mit den Tastenkombinationen aus, die Sie importieren möchten, oder klicken Sie auf **Durchsuchen**, um die gewünschte Datei zu suchen.

5. Wählen Sie **Weiter** aus.

6. Deaktivieren Sie unter **Welche Einstellungen sollen importiert werden?** das Kontrollkästchen **Alle Einstellungen**, und erweitern Sie dann **Optionen** sowie **Umgebung**.

7. Aktivieren Sie das Kontrollkästchen **Tastatur**, und klicken Sie dann auf **Fertig stellen**.

   ![Nur angepasste Tastenkombinationen importieren](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Weitere Informationen

- [Barrierefreiheitsfeatures in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
