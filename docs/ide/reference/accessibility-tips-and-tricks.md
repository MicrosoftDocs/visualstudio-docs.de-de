---
title: Tipps und Tricks zur Barrierefreiheit für Visual Studio
description: Informationen zu Tipps und Tricks, die Ihnen dabei helfen sollen, die Visual Studio-IDE für jeden Benutzer, einschließlich Benutzer mit einer Behinderung, leichter zugänglich zu machen
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59206c206f04aaf3506771ee2310daebd0af273a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939746"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Tipps und Tricks zur Barrierefreiheit für Visual Studio

Visual Studio verfügt über integrierte Barrierefreiheitsfunktionen, die mit Sprachausgaben und anderen Hilfstechnologien kompatibel sind. Egal, ob Sie Tastenkombinationen zum Navigieren in der IDE verwenden möchten oder kontrastreiche Designs zur Verbesserung der Sichtbarkeit verwenden möchten – auf dieser Seite finden Sie dazu einige Tipps und Tricks.

Außerdem erfahren Sie, wie Anmerkungen verwendet werden, um nützliche Informationen über Ihren Code anzuzeigen. Sie erhalten ebenfalls Informationen darüber, wie Sie Sounds für Build- und Breakpointereignisse festlegen.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Barrierefreiheit für Visual Studio für Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Speichern Ihrer IDE-Einstellungen

Sie können Ihre IDE-Umgebung anpassen, indem Sie Fensterlayout, Tastaturzuordnungsschema und andere Einstellungen speichern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Ändern Ihrer IDE für die Ansicht mit hohem Kontrast

Einige Personen haben Schwierigkeiten damit, manche Farben zu erkennen. Wenn Sie beim Schreiben von Code einen höheren Kontrast wünschen, aber nicht die üblichen Themen für hohen Kontrast verwenden möchten, bieten wir nun das Design „Blau (zusätzlicher Kontrast)“ an.

  ![Vergleich der Designs „Blau“ und „Blau (zusätzlicher Kontrast)“](media/blue-extra-contrast-theme.png "Screenshot: Vergleich zwischen den Designs „Blau“ und „Blau (zusätzlicher Kontrast)“")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Verwenden von Anmerkungen, um nützliche Informationen über Ihren Code anzuzeigen

Der Visual Studio-Editor enthält viele Randsteuerelemente für den Text, die Sie über Charakteristiken und Funktionen an bestimmten Punkten einer Codezeile informieren, z. B. die Schraubendreher- und Glühbirnensymbole, Wellenlinien für Fehler und Warnungen, Lesezeichen usw. Sie können den Befehlssatz „Zeilenanmerkungen anzeigen“ verwenden, um diese Randsteuerelemente zu ermitteln und zwischen diesen zu navigieren.

  ![Verwenden des Befehlssatzes „Zeilenanmerkungen anzeigen“](media/show-line-annotations-command-set.png "Screenshot: Menüelement „Zeilenanmerkungen anzeigen“")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Zugreifen auf Symbolleisten mithilfe von Tastenkombinationen

Die Visual Studio-IDE verfügt genau wie viele andere Toolfenster über Symbolleisten. Mithilfe der folgenden Tastenkombinationen können Sie darauf zugreifen.

|Feature|Beschreibung|Tastenkombination|
|-------------|-----------------| - |
|IDE-Symbolleisten|Wählen Sie die erste Schaltfläche in der Standardsymbolleiste.|**ALT**, **STRG**+**TAB**|
|Symbolleisten des Toolfensters|Verschieben Sie den Fokus zu den Symbolleisten in einem Toolfenster. <br> <br> **HINWEIS:** Dies funktioniert für die meisten Toolfenster, jedoch nur, wenn sich der Fokus in einem Toolfenster befindet. Sie müssen außerdem die UMSCHALTTASTE vor der ALT-TASTE drücken. In einigen Toolfenstern wie Team Explorer müssen Sie die UMSCHALTTASTE einen Moment gedrückt halten, bevor Sie die ALT-TASTE drücken.|**UMSCHALT**+**ALT**|
|Symbolleisten|Wechseln Sie zum ersten Element in der nächsten Symbolleiste (wenn eine Symbolleiste über Fokus verfügt).|**STRG**+**TAB**|

### <a name="other-useful-keyboard-shortcuts"></a>Weitere nützliche Tastenkombinationen

Einige weitere nützliche Tastenkombinationen sind folgende:

|Feature|Beschreibung|Tastenkombination|
|-------------|-----------------| - |
|IDE|Hohen Kontrast ein- und ausschalten <br> <br> **HINWEIS:** Windows-Standardtastenkombination|**Linke ALT**+**Linke UMSCHALT**+**DRUCK**|
|Dialogfeld|Aktivieren oder deaktivieren Sie die Kontrollkästchenoption in einem Dialogfeld. <br> <br> **HINWEIS:** Windows-Standardtastenkombination|**LEERTASTE**|
|Kontextmenüs|Öffnen Sie ein Kontextmenü (Rechtsklick). <br> <br> **HINWEIS:** Windows-Standardtastenkombination|**UMSCHALT**+**F10**|
|Menüs|Greifen Sie schnell auf ein Menüelement mithilfe der Zugriffstasten zu. Drücken Sie die **ALT**-Taste gefolgt von den unterstrichenen Buchstaben in einem Menü, um den Befehl zu aktivieren. Wenn z.B. das Dialogfeld „Projekt öffnen“ in Visual Studio angezeigt werden soll, wählen Sie **ALT**+**F**+**O**+**P** aus.  <br><br> **HINWEIS:** Windows-Standardtastenkombination|**ALT** +  **[Buchstabe]**|
|Suchfeld|Verwenden des Suchfeatures in Visual Studio|**Strg**+**Q**|
|Fenster „Toolbox“|Wechseln Sie zwischen Toolboxregisterkarten.|**STRG**+**NACH-OBEN-TASTE**<br /><br /> und<br /><br /> **STRG**+**NACH-UNTEN-TASTE**|
|Fenster „Toolbox“|Fügen Sie ein Steuerelement aus der Toolbox zu einem Formular oder einem Designer hinzu.|**EINGABETASTE**|
|Dialogfeld „Optionen“: Umgebung > Tastatur|Löschen Sie die Tastenkombination, die unter **Tastenkombination drücken** eingegeben wurde.|**RÜCKTASTE**|
|Fenster „Benachrichtigungstool“|Öffnen Sie das Fenster des Benachrichtigungstools, indem Sie nacheinander zwei Tastaturkombinationen verwenden. Zeigen Sie dann eine Benachrichtigung an, indem Sie sie über die Pfeiltasten auszuwählen.| **STRG**+ **&#92;** , **STRG**+**N**|

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Zugreifen auf Benachrichtigungen mithilfe von Tastenkombinationen

Wenn in der IDE eine Benachrichtigung angezeigt wird, können Sie so über Tastenkombinationen auf das Benachrichtigungsfenster zugreifen:

1. Drücken Sie an einer beliebigen Stelle in der IDE nacheinander die folgenden beiden Tastenkombinationen: **STRG**+ **&#92;** und dann **STRG**+**N**.

   Das Fenster **Benachrichtigungen** wird geöffnet.

   ![Fenster „Benachrichtigungstools“ in der Visual Studio-IDE](media/toast-notification.png "Screenshot: Fenster „Benachrichtigungen“ in der Visual Studio-IDE")

1. Über die **Tabulatortaste** oder die Pfeiltasten können Sie eine Benachrichtigung auswählen.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Verwenden des Sound-Applets, um Hinweise für Builds und Breakpoints festzulegen

Sie können das Sound-Applet in Windows verwenden, um Visual Studio-Programmereignissen einen Sound zuzuweisen. Insbesondere können Sie folgenden Programmereignissen Sounds zuweisen:

* Haltepunkt erreicht
* Buildvorgang abgebrochen
* Fehler beim Buildvorgang
* Buildvorgang erfolgreich

Gehen Sie dabei folgendermaßen vor:

1. Geben Sie auf einem Computer mit Windows 10 **Systemsounds ändern** in das Feld **Suche** ein.

   ![Suchfeld in Windows 10](media/type-here-to-search.png "Screenshot: Suchfeld in Windows 10")

   (Falls Sie Cortana aktiviert haben, können Sie alternativ „Hey Cortana“ und anschließend „Systemsounds ändern“ sagen.)

1. Doppelklicken Sie auf **Systemsounds ändern**.

   ![Suchergebnisse in Windows 10](media/change-system-sounds.png "Screenshot: Suchergebnisse für „Systemsounds ändern“ in Windows 10")

1. Klicken Sie im Dialogfeld **Sound** auf die Registerkarte **Sounds**.

1. Scrollen Sie dann in **Programmereignisse** zu **Microsoft Visual Studio**, und wählen Sie die Sounds aus, die Sie auf die gewünschten Ereignisse anwenden möchten.

   ![Registerkarte „Sounds“ des Sound-Applets in Windows 10](media/sound-applet.png "Registerkarte „Sounds“ des Sound-Applets in Windows 10")

1. Klicken Sie auf **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Weitere Informationen zu Updates zur Barrierefreiheit finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3 (Verbesserungen der Barrierefreiheit in Visual Studio 2017, Version 15.3)](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/).

::: moniker-end

## <a name="see-also"></a>Siehe auch

* [Barrierefreiheitsfeatures in Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [How to: Anpassen von Menüs und Symbolleisten in Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
* [Barrierefreiheit (Visual Studio für Mac)](/visualstudio/mac/accessibility)
* [Microsoft Accessibility (Microsoft-Barrierefreiheit)](https://www.microsoft.com/Accessibility)
