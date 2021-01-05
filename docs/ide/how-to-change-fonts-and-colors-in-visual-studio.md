---
title: Ändern von Designs, Schriftarten, Text und Kontrast für Barrierefreiheit
description: Erfahren Sie, wie Sie zugunsten von Benutzerfreundlichkeit und Barrierefreiheit Farbdesigns, Schriftfarben und Textgrößen ändern und besonders kontrastreiche Farben verwenden können.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c52be25c007a16d7e6221663c434767c02d8d50
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683901"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Vorgehensweise: Ändern von Schriftarten, Farben und Designs in Visual Studio

Sie können die Schriftarten und Farben in Visual Studio auf viele Arten ändern. Beispielsweise können Sie das standardmäßige blaue Farbdesign in das (auch als „dunkler Modus“ bezeichnete) dunkle Design ändern. Sie können auch ein besonders kontrastreiches Design auswählen, wenn dies Ihren Anforderungen am besten entspricht. Außerdem können Sie standardmäßige Schriftart und Textgröße sowohl in der IDE als auch im Code-Editor ändern.

## <a name="change-the-color-theme"></a>Ändern des Farbdesigns

Sie können das Farbdesign des IDE-Rahmens- und der Toolfenster in Visual Studio wie folgt ändern.

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

1. Klicken Sie in der Optionsliste auf **Umgebung** > **Allgemein**.

1. Wählen Sie in der Liste **Farbdesign** entweder das Standarddesign **Blau**, das Design **Hell**, das Design **Dunkel** oder das Design **Blau (zusätzlicher Kontrast)** .

   ![Screenshot des Dialogfelds „Optionen“, in dem das Farbdesign geändert wird](media/fonts-colors-theme.png "Screenshot des Dialogfelds „Optionen“, in dem Sie das Farbdesign ändern können")

    > [!NOTE]
    > Wenn Sie ein Farbdesign ändern, wird der Text in der IDE auf die Standardeinstellung oder zuvor benutzerdefinierte Schriftarten und -größen für dieses Design zurückgesetzt.

    :::moniker range="vs-2017"

    > [!TIP]
    > Sie können Ihre eigenen Visual Studio-Designs erstellen und bearbeiten, indem Sie den [Farbdesign-Editor für Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) installieren.

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > Sie können eigene Visual Studio-Designs erstellen und bearbeiten, indem Sie den [Farbdesign-Designer für Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner) installieren.

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Ändern von Schriftarten und Textgröße

Sie können die Schriftart und Textgröße für alle IDE-Rahmen- und Toolfenster oder nur für bestimmte Fenster oder Textelemente ändern. Sie können die Schriftart und Textgröße auch im Editor ändern.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>So ändern Sie Schriftart und Textgröße in der IDE

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

1. Klicken Sie in der Optionsliste auf **Umgebung** > **Schriftarten und Farben**.

1. Wählen Sie in der Liste **Einstellungen anzeigen für** den Eintrag **Umgebung** aus.

   ![Screenshot des Dialogfelds „Optionen“ zum Ändern von Schriftarten und Farben in der IDE](media/fonts-colors-environment.png "Screenshot des Dialogfelds „Optionen“ zum Ändern von Schriftarten und Farben in der IDE")

    > [!NOTE]
    > Wenn Sie die Schriftart nur für die Toolfenster ändern möchten, wählen Sie in der Liste **Einstellungen anzeigen für** den Eintrag **Alle Texttoolfenster** aus.

1. Ändern Sie die Optionen **Schriftart** und **Größe**, um die Schriftart und Textgröße für die IDE zu ändern.

1. Wählen Sie unter **Elemente anzeigen** das entsprechende Element aus, und ändern Sie anschließend die Optionen **Elementvordergrund** und **Elementhintergrund**.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>So ändern Sie Schriftart und Textgröße im Editor

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

1. Klicken Sie in der Optionsliste auf **Umgebung** > **Schriftarten und Farben**.

1. Wählen Sie in der Liste **Einstellungen anzeigen für** die Option **Text-Editor** aus.

   ![Screenshot des Dialogfelds „Optionen“ zum Ändern von Schriftarten und Farben im Editor](media/fonts-colors-text-editor.png "Screenshot des Dialogfelds „Optionen“ zum Ändern von Schriftarten und Farben im Editor")

1. Ändern Sie die Optionen **Schriftart** und **Größe**, um die Schriftart und Textgröße für den Editor zu ändern.

1. Wählen Sie unter **Elemente anzeigen** das entsprechende Element aus, und ändern Sie anschließend die Optionen **Elementvordergrund** und **Elementhintergrund**.

Weitere Informationen finden Sie auf der Seite [Ändern von Schriftarten und Farben für den Editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="accessibility-options"></a>Barrierefreiheitsoptionen

Wenn Sie unter Sehschwäche leiden, haben Sie die Wahl zwischen verschiedenen Optionen für das Farbdesign. Sie können eine Option mit hohem Kontrast für *alle* Apps und die Benutzeroberfläche auf einem Computer oder eine Option für zusätzlichen Kontrast nur für Visual Studio angeben.

### <a name="use-windows-high-contrast"></a>Verwenden von hohem Kontrast unter Windows

Gehen Sie wie folgt vor, um die Windows-Option „Hoher Kontrast“ zu aktivieren:

- Drücken Sie unter Windows oder in einer beliebigen Microsoft-Anwendung **Linke ALT**+**Linke UMSCHALT**+**DRUCK**.

- Wählen Sie unter Windows **Start** > **Einstellungen** > **Erleichterte Bedienung** > **Hoher Kontrast**.

    > [!WARNING]
    > Diese Windows-Einstellung „Hoher Kontrast“ gilt für alle Anwendungen und die Benutzeroberfläche auf dem Computer.

### <a name="use-visual-studio-extra-contrast"></a>Verwenden von „Zusätzlicher Kontrast“ in Visual Studio

Gehen Sie wie folgt vor, um die Visual Studio-Option „Zusätzlicher Kontrast“ zu aktivieren:

1. Wählen Sie in Visual Studio auf der Menüleiste **Tools** > **Optionen** und dann in der Liste „Optionen“ **Umgebung** > **Allgemein** aus.

1. Wählen Sie in der Dropdownliste **Farbdesign** das Design **Blau (zusätzlicher Kontrast)** und dann **OK** aus.

Weitere Informationen zu anderen Visual Studio-Barrierefreiheitsoptionen, die Ihnen zur Verfügung stehen, finden Sie auf der Seite [Barrierefreiheitsfeatures in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md).

> [!TIP]
> Wenn es eine Barrierefreiheitsoption für Farben oder Schriftarten gibt, die Ihrer Meinung nach sinnvoll sein könnte, aber derzeit nicht in Visual Studio verfügbar ist, teilen Sie uns dies mit, indem Sie **Feature vorschlagen** in der [Visual Studio-Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) auswählen. Weitere Informationen zu diesem Forum und seiner Funktionsweise finden Sie auf der Seite [Vorschlagen eines Features für Visual Studio](../ide/suggest-a-feature.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Einzelheiten zu allen Elementen der Benutzeroberfläche, für die Sie Schriftart und Farbschemas ändern können, finden Sie auf Seite [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Ändern der im Editor in Visual Studio verwendeten Schriftarten und Farben](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Features des Visual Studio-Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
- [Personalisieren von Visual Studio-IDE und Editor](../ide/quickstart-personalize-the-ide.md)
