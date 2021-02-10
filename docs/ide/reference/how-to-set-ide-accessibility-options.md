---
title: 'Vorgehensweise: Festlegen von IDE-Barrierefreiheitsoptionen'
description: Informationen zum Festlegen von Barrierefreiheitsoptionen in Visual Studio, die die Verwendung der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) für jeden vereinfachen, auch für Benutzer mit eingeschränktem Seh- und Schreibvermögen
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d7cc99747571feb5b443f10355d867da7c22f44
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952914"
---
# <a name="how-to-set-ide-accessibility-options"></a>Vorgehensweise: Festlegen von IDE-Barrierefreiheitsoptionen

Visual Studio umfasst Features zur Unterstützung von Personen mit eingeschränktem Seh- und Schreibvermögen. Sie können z. B. die Größe und Farbe von Text in Editoren, die Größe von Text und Schaltflächen auf Symbolleisten sowie Einstellungen zum Vervollständigen einer Funktion oder Anweisung ändern.

Visual Studio unterstützt außerdem Dvorak-Tastaturlayouts, die den Zugriff auf die am häufigsten eingetippten Zeichen vereinfachen. Sie können auch die Standardtastenkombinationen anpassen, die für Visual Studio verfügbar sind. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den hier beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Weitere Informationen zu aktuellen Barrierefreiheitupdates finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Verbesserungen der Barrierefreiheit in Visual Studio 2017 [Version 15.3]).

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Editors, Dialogfelder und Toolfenster

Standardmäßig werden in Visual Studio für Dialogfelder und Toolfenster die gleiche Schriftgröße und Schriftfarbe verwendet wie für das Betriebssystem. Die Farbeinstellungen für den Rahmen der IDE, die Dialogfelder, Symbolleisten und Toolfenster basieren auf einem Farbschema: hell oder dunkel. Sie können das aktuelle Farbschema hier ändern: [Dialogfeld „Optionen“: Umgebung > Allgemein](../../ide/reference/general-environment-options-dialog-box.md).

Sie können auch festlegen, dass in der Codeansicht des Editors Popupfenster angezeigt werden. Diese Fenster zeigen Ihnen möglicherweise verfügbare Member für das aktuelle Objekt und die Parameter, die für eine Funktion oder Anweisung benötigt werden. Sie können besonders hilfreich sein, wenn Sie Schwierigkeiten bei der Eingabe über die Tastatur haben. Allerdings kollidiert diese Funktion mit dem Fokus im Code-Editor, was für manche Benutzer problematisch sein kann.

So schalten Sie die Popupfenster ab:

1. Wählen Sie im Menü **Extras** den Befehl **Optionen**.

1. Wählen Sie **Text-Editor** > **Alle Sprachen** > **Allgemein** aus.

1. Deaktivieren Sie die Kontrollkästchen **Member automatisch auflisten** und **Parameterinformationen**.

Sie können die Fenster in der IDE (Integrated Development Environment, Integrierte Entwicklungsumgebung) so anordnen, dass sie Ihrer individuellen Arbeitsweise entgegenkommen. Sie können jedes Toolfenster andocken, verschieben, ausblenden oder automatisch ausblenden. Weitere Informationen zum Ändern des Fensterlayouts finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Ändern der Größe von Text

Sie können die Einstellungen für textbasierte Toolfenster, z. B. das Fenster **Befehl**, das Fenster **Direkt** und das Fenster **Ausgabe**, über **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben** ändern.

Wenn Sie in der Dropdownliste **Einstellungen anzeigen für** den Eintrag **[Alle Texttoolfenster]** auswählen, wird in den Dropdownlisten **Elementvordergrund** und **Elementhintergrund** die Standardeinstellung als **Standard** angezeigt. Klicken Sie auf die Schaltfläche **Benutzerdefiniert**, um diese Einstellungen zu ändern.

Sie können auch festlegen, wie Text im Editor angezeigt werden soll. Gehen Sie folgendermaßen vor:

1. Wählen Sie im Menü **Extras** den Befehl **Optionen**.

1. Klicken Sie auf **Umgebung** > **Schriftarten und Farben**.

1. Wählen Sie im Dropdownmenü **Einstellungen anzeigen für** eine Option aus.

    Um die Schriftgröße von Text in einem Editor zu ändern, klicken Sie auf den **Text-Editor**.

    Um die Schriftgröße von Text in textbasierten Toolfenstern zu ändern, wählen Sie die Option **[Alle Texttoolfenster]** aus.

    Um die Schriftgröße von QuickInfos in einem Editor zu ändern, wählen Sie die Option **Editor-QuickInfo** aus.

    Um die Schriftgröße von Text in den Popupfenstern für die automatische Vervollständigung von Anweisungen zu ändern, wählen Sie die Option **Anweisungsvervollständigung** aus.

1. Wählen Sie unter **Elemente anzeigen** die Option **Nur Text** aus.

1. Wählen Sie in der Dropdownliste **Schriftart** eine andere Schriftart aus.

1. Wählen Sie in der Dropdownliste Schriftgrad eine andere **Schriftgröße** aus.

    > [!TIP]
    > Um die Textgröße für textbasierte Toolfenster und Editoren zurückzusetzen, wählen Sie die Option **Standard verwenden** aus.

7. Klicken Sie auf **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Ändern der Farben, die in der IDE verwendet werden

Sie können auch die Standardfarben für Text, Indikatorränder, Leerräume und Codeelemente im Editor anpassen. Gehen Sie folgendermaßen vor:

1. Wählen Sie im Menü **Extras** den Befehl **Optionen**.

1. Klicken Sie im Ordner **Umgebung** auf die Option **Schriftarten und Farben**.

1. Wählen Sie unter **Einstellungen anzeigen** für die Option **Text-Editor** aus.

1. Wählen Sie unter **Elemente anzeigen** das Element aus, das Sie anpassen möchten, z.B. **Nur Text**, **Indikatorrand**, **Sichtbare Leerstellen**, **HTML-Attributname** oder **XML-Attribut**.

1. Wählen Sie die Anzeigeeinstellungen in den folgenden Optionen aus: **Elementvordergrund**, **Elementhintergrund** und **Fett**.

1. Klicken Sie auf **OK**.

> [!TIP]
> Um in allen Anwendungsfenstern des Betriebssystems kontrastreiche Farben zu verwenden, drücken Sie **LINKE ALT-TASTE**+**LINKE UMSCHALTTASTE**+**DRUCK**. Wenn Visual Studio geöffnet ist, schließen Sie das Programm und öffnen es erneut, damit die hohen Kontraste ordnungsgemäß übernommen werden.

## <a name="toolbars"></a>Symbolleisten

Zur Verbesserung der Benutzerfreundlichkeit und Barrierefreiheit der Symbolleisten können Sie Text zu den Symbolleisten-Schaltflächen hinzufügen.

### <a name="to-assign-text-to-toolbar-buttons"></a>So weisen Sie Symbolleisten-Schaltflächen Text zu

1. Wählen Sie im Menü **Extras** die Option **Anpassen**.

1. Wählen Sie im Dialogfeld **Anpassen** die Registerkarte **Befehle** aus.

1. Wählen Sie die Option **Symbolleiste** und anschließend den Namen der Symbolleiste aus, auf der sich die Schaltfläche befindet, für die Text angezeigt werden soll.

1. Wählen Sie in der Liste den Befehl aus, den Sie ändern möchten.

1. Wählen Sie **Auswahl ändern** aus.

1. Wählen Sie **Symbol und Text** aus.

### <a name="to-modify-the-displayed-text-in-a-button"></a>So ändern Sie den in einer Schaltfläche angezeigten Text

1. Wählen Sie erneut **Auswahl ändern** aus.

1. Geben Sie direkt neben **Name** eine neue Beschriftung für die ausgewählte Schaltfläche ein.

## <a name="see-also"></a>Siehe auch

* [Barrierefreiheitsfeatures in Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Barrierefreiheit für Visual Studio für Mac](/visualstudio/mac/accessibility/)
* [Ressourcen für das Entwerfen von Anwendungen mit Barrierefreiheit](../../ide/reference/resources-for-designing-accessible-applications.md)
