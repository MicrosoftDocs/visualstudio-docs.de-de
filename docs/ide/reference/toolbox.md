---
title: Fenster „Toolbox“
description: Hier erfahren Sie mehr über das Fenster „Toolbox“ und die dort angezeigten Steuerelemente, die Sie zu Visual Studio-Projekten hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 905288d4a580f5633196273666fbea3954d1767c
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560277"
---
# <a name="toolbox"></a>Werkzeugkasten

Im Fenster **Toolbox** werden Steuerelemente angezeigt, die Sie zu Visual Studio-Projekten hinzufügen können. Wählen Sie zum Öffnen der **Toolbox** auf der Menüleiste **Ansicht** > **Toolbox** aus, oder drücken Sie **STRG**+**ALT**+**X**.

![Screenshot: Fenster „Toolbox“ mit den Optionen im Abschnitt „Container“](media/vs-2019/toolbox.png "Screenshot des Fensters „Toolbox“")

Sie können verschiedene Steuerelemente per Drag & Drop auf die Oberfläche des verwendeten Designers verschieben und die Größe und Position der Steuerelemente ändern.

Die Toolbox wird in Verbindung mit Designeransichten angezeigt, z. B. der Designeransicht einer XAML-Datei oder eines Windows Forms-App-Projekts. In **Toolbox** werden nur die Steuerelemente angezeigt, die im aktuellen Designer verwendet werden können. Sie können eine Suche in **Toolbox** durchführen, um die Elemente zu filtern, die angezeigt werden.

> [!NOTE]
> Bei einigen Projekttypen werden in **Toolbox** möglicherweise keine Elemente angezeigt.

Die .NET-Version, auf die Ihr Projekt ausgerichtet ist, wirkt sich auch auf die Gruppe der Steuerelemente aus, die in Toolbox angezeigt wird. Sie können die Frameworkzielversion bei Bedarf über die Eigenschaftenseite des Projekts ändern. Wählen Sie den Projektknoten im **Projektmappen-Explorer** aus, und klicken Sie dann in der Menüleiste auf **Projekt** > **Projektname-Eigenschaften**. Verwenden Sie auf der Registerkarte **Anwendung** die Dropdownliste **Zielframework**.

::: moniker range="vs-2019"

![Screenshot: Dialogfeld „Anwendung“ mit den Optionen in der Dropdownliste „Zielframework“](media/vs-2019/toolbox-change-dotnet-version.png "Screenshot des Dialogfelds, in dem Sie die .NET-Version ändern können")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Verwalten des Toolbox-Fensters und dessen Steuerelemente

Standardmäßig ist die **Toolbox** auf der linken Seite der Visual Studio IDE zugeklappt und wird angezeigt, wenn der Cursor darüber bewegt wird. Sie können **Toolbox** anheften (indem Sie auf das Symbol **Anheften** auf der Symbolleiste klicken), sodass diese geöffnet bleibt, wenn Sie den Cursor bewegen. Sie können das **Toolbox**-Fenster auch abdocken und es an eine beliebige Stelle auf dem Bildschirm ziehen. Sie können **Toolbox** andocken, abdocken und ausblenden, indem Sie mit der rechten Maustaste auf die Symbolleiste klicken und eine der Optionen auswählen.

> [!TIP]
> Wenn die Toolbox nicht mehr entlang der linken Seite der Visual Studio IDE zusammengeklappt angezeigt wird, können Sie sie wieder hinzufügen, indem Sie auf der Menüleiste **Fenster** > **Fensterlayout zurücksetzen** wählen.

Mithilfe der folgenden Befehle im Kontextmenü können Sie die Elemente auf einer Registerkarte der **Toolbox** neu anordnen oder benutzerdefinierte Registerkarten und Elemente hinzufügen:

- **Element umbenennen**: benennt das ausgewählte Element um.

- **Listenansicht**: zeigt die Steuerelemente in einer vertikalen Liste an. Wenn dieses Kontrollkästchen deaktiviert ist, werden die Steuerelemente horizontal angezeigt.

- **Alle anzeigen**: zeigt alle möglichen Steuerelemente an (nicht nur die für den aktuellen Designer).

- **Elemente auswählen**: öffnet das Dialogfeld **Toolboxelemente auswählen**, sodass Sie die Elemente festlegen können, die in der **Toolbox** angezeigt werden. Sie können ein Element ein- oder ausblenden, indem Sie dessen Kontrollkästchen aktivieren oder deaktivieren.

- **Elemente alphabetisch sortieren**: sortiert die Elemente nach Namen.

- **Toolbox zurücksetzen**: Stellt die Standardeinstellungen von **Toolbox** und die Standardelemente wieder her.

- **Registerkarte hinzufügen**: Fügt eine neue **Toolbox**-Registerkarte hinzu.

- **Nach oben**: verschiebt das ausgewählte Element nach oben.

- **Nach unten**: verschiebt das ausgewählte Element nach unten.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Erstellen und Verteilen von benutzerdefinierten Toolbox-Steuerelementen

Sie können benutzerdefinierte **Toolbox**-Steuerelemente erstellen und mit einer Projektvorlage beginnen, die auf [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) oder [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md) basiert. Sie können Ihr benutzerdefiniertes Steuerelement dann an Ihre Teamkollegen verteilen oder es im Internet mithilfe des [Installationsprogramms für Toolboxsteuerelemente](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx) veröffentlichen.

## <a name="next-steps"></a>Nächste Schritte

Über die folgenden Links erfahren Sie mehr zu den verschiedenen Registerkarten der **Toolbox**:

- [Toolbox, Registerkarte „Daten“](../../ide/reference/toolbox-data-tab.md)
- [Toolbox, Registerkarte „Komponenten“](../../ide/reference/toolbox-components-tab.md)
- [Toolbox, Registerkarte „HTML“](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Siehe auch

- [Toolboxelemente auswählen, WPF-Komponenten](choose-toolbox-items-wpf-components.md)
