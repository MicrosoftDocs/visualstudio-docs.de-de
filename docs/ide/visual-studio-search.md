---
title: Verwenden der Suche in Visual Studio
description: Hier erfahren Sie, wie Sie die Visual Studio-Suche verwenden, um nach Einstellungen, Menüs und Code zu suchen.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9f8182646af4facb0f2f86c74f95dff091d55d1
ms.sourcegitcommit: cea9e5787ff33e0e18aa1942bf4236748e0ef547
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92199684"
---
# <a name="use-visual-studio-search"></a>Verwenden der Visual Studio-Suche

Die integrierte Entwicklungsumgebung (IDE) von Visual Studio umfasst viele Menüs, Optionen und Features, die man sich nur schwer merken kann. Die Visual Studio-Suchfunktion ist ein einzelnes Suchfeld, das Entwicklern dabei hilft, IDE-Menüs und -Optionen zu finden und gleichzeitig Code zu durchsuchen. Unabhängig davon, ob Sie noch nicht mit Visual Studio vertraut oder ein erfahrenen Entwickler sind, bietet diese Funktion eine schnelle Möglichkeit, IDE-Features und Ihren Code zu durchsuchen.

Verwenden Sie den Tastaturkurzbefehl **STRG**+**Q** , um auf das Suchfeld zuzugreifen, oder klicken Sie in das Visual Studio-Sucheingabefeld, das sich standardmäßig neben der Menüleiste befindet:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Visual Studio-Suchfeld" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Der Befehl, der von der Visual Studio-Suche ausgeführt wird, ist `Window.QuickLaunch`, und Sie sehen möglicherweise, dass diese Funktion als Schnellsuche oder Schnellstart bezeichnet wird.

Im Gegensatz zu anderen Suchfunktionen wie „In Dateien suchen“ oder „Projektmappen-Explorer-Suche“ umfassen die Ergebnisse der Visual Studio-Suche unter anderem auch IDE-Features, Menüoptionen und Dateinamen. In den folgenden Abschnitten werden die verschiedenen Arten von Ergebnissen erläutert, die im Rahmen der Visual Studio-Suche gefunden werden können.

## <a name="search-menus-options-and-windows"></a>Suchen von Menüs, Optionen und Fenstern

Sie können das Visual Studio-Suchfeld verwenden, um Einstellungen, Optionen und ähnliche Konfigurationselemente zu suchen. Suchen Sie beispielsweise nach *Design ändern* , um schnell das Dialogfeld zu finden und zu öffnen, in dem Sie das Visual Studio-Farbschema wie im folgenden Screenshot gezeigt ändern können:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Visual Studio-Suchfeld":::

> [!TIP]
> In den meisten Fällen werden Sie bei der Visual Studio-Suche in den Ergebnissen auch über das Menü, die Tastenkombinationen und den Speicherort der einzelnen Elemente informiert.

Sie können das Visual Studio-Suchfeld verwenden, um Menüelemente und Befehle zu suchen. Suchen Sie beispielsweise nach *clean sol* , um den „Clean Solution“-Befehl schnell zu finden und auszuführen. Die Suchergebnisse enthalten wie im folgenden Screenshot gezeigt außerdem eine Erinnerung, wo Sie diesen Befehl in den Menüs finden:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Visual Studio-Suchfeld":::

Schließlich können Sie nach Fenstern oder Bereichen suchen, die Sie möglicherweise versehentlich geschlossen haben. Suchen Sie beispielsweise nach *Test* , um das Test-Explorer-Fenster zu suchen und zu öffnen:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Visual Studio-Suchfeld":::

## <a name="search-files-and-code"></a>Suchen von Dateien und Code

Die Visual Studio-Suche durchsucht auch die Projektmappenelemente nach Dateinamen, Code, Methoden und anderen Übereinstimmungen. Im folgenden Screenshot wurden bei der Suche nach *markdown* die Datei „MarkdownMetaExtractor.cs“, die `MarkdownMetaExtractor`-Klasse und zwei Methoden in der Lösung gefunden:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Visual Studio-Suchfeld":::

Sie können auch eine Suche mit gemischter Groß- und Kleinschreibung durchführen. Im folgenden Screenshot wurde für die Suche nach *FSS* eine **F** older **S** ize **S** canner-Datei, -Klasse und -Methode gefunden:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Visual Studio-Suchfeld":::

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](reference/visual-studio-commands.md)