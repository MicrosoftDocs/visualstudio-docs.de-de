---
title: Gehe zu Datei, Gehe zu Symbol, Gehe zu Zeile
description: Erfahren Sie mehr über die „Gehe zu“-Befehle in Visual Studio und darüber, wie Sie sie verwenden können, um fokussierte Suchvorgänge in Ihrem Code auszuführen.
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 257db632c095027d9fa4be667a30e809ecb2fff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946617"
---
# <a name="find-code-using-go-to-commands"></a>Suchen von Code mithilfe von Gehe zu-Befehlen

Die **Gehe zu**-Befehle von Visual Studio führen eine zielgerichtete Suche in Ihrem Code aus, damit Sie angegebene Elemente schneller finden. Sie können über eine einfache und einheitliche Oberfläche zu einer bestimmten Zeile, einem bestimmten Typ, einem bestimmten Symbol oder einer bestimmten Datei gehen.

## <a name="how-to-use-it"></a>Verwendung

Eingabe | Funktion
------------ | ---
**Tastatur** | Drücken Sie **STRG**+**T** oder **STRG**+ **,**
**Maus** | Klicken Sie auf **Bearbeiten** > **Gehe zu** > **Gehe zu allen**.

Ein kleines Fenster wird oben rechts in Ihrem Code-Editor angezeigt.

![Fenster „Gehe zu allen“](media/go-to-all.png)

Während der Eingabe in das Textfeld werden die Ergebnisse in einer Dropdownliste unterhalb des Textfelds angezeigt. Um zu einem Element zu wechseln, wählen Sie es in der Liste aus.

![Fenster "Navigieren zu"](../ide/media/vside_navigatetowindow.png)

Sie können auch ein Fragezeichen ( **?** ) eingeben, um weitere Hilfe anzufordern.

![Gehe zu allen: Hilfe](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Gefilterte Suchvorgänge

Standardmäßig wird das angegebene Element in allen Projektmappenelementen gesucht. Sie können jedoch die Codesuche auf bestimmte Elementtypen einschränken, indem Sie den Suchbegriffen bestimmte Zeichen voranstellen. Sie können auch schnell Suchfilter ändern, indem Sie Schaltflächen auf der Symbolleiste des Dialogfelds **Gehe zu** auswählen. Schaltflächen zum Ändern der Typfilter befinden sich auf der linken Seite, und die Schaltflächen zum Ändern des Suchbereichs auf der rechten.

![Go to members (Elemente von „Gehe zu“)](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtern eines bestimmten Codeelementtyps

Um Ihre Suche auf einen bestimmten Typ von Codeelement einzugrenzen, können Sie entweder ein Präfix in das Suchfeld eingeben oder eines der fünf Filtersymbole auswählen:

Präfix | Symbol | Verknüpfung | Beschreibung
:-: | - | - | -
:| ![Symbol „Zeile“](media/gotoall-line-icon.png) | **STRG**+**G** | Zur angegebenen Zeilennummer wechseln
f| ![Symbol „Dateien“](media/gotoall-files-icon.png) | **STRG**+**1**, **STRG**+**F** | Zur angegebenen Datei wechseln
r| ![Symbol „Zuletzt verwendete Dateien“](media/gotoall-recent-files-icon.png) | **STRG**+**1**, **STRG**+**R** | Zur angegebenen zuletzt besuchten Datei wechseln
t| ![Symbol „Typen“](media/gotoall-types-icon.png) | **STRG**+**1**, **STRG**+**T** | Zum angegebenen Typ wechseln
m| ![Symbol „Member“](media/gotoall-members-icon.png) | **STRG**+**1**, **STRG**+**M** | Zum angegebenen Member wechseln
\#| ![Symbol „Symbole“](media/gotoall-symbols-icon.png) | **STRG**+**1**, **STRG**+**S** | Zum angegebenen Symbol wechseln

### <a name="filter-to-a-specific-location"></a>Filtern an einem bestimmten Speicherort

Um die Suche auf bestimmte Speicherorte einzugrenzen, wählen Sie eines der zwei Dokumentsymbole aus:

Symbol | BESCHREIBUNG
---- | ---
![Aktuelles Dokument](media/gotoall_currentdocument.png) | Nur im aktuellen Dokument suchen
![Externe Dokumente](media/gotoall_external.png) | In externen Dokumenten suchen, zusätzlich zu den unter Projekt/Projektmappe gespeicherten

## <a name="camel-casing"></a>Camel-Case-Schreibweise

Wenn Sie die [Camel-Case-Schreibweise](https://en.wikipedia.org/wiki/Camel_case) in Ihrem Code verwenden, können Sie Codeelemente schneller finden, indem Sie nur die Großbuchstaben des Codeelementnamens eingeben. Wenn Ihr Code beispielsweise über den Typ `CredentialViewModel` verfügt, können Sie die Suche eingrenzen, indem Sie den **Typfilter** (**t**) auswählen und anschließend nur die Großbuchstaben des Namens (`CVM`) in das Dialogfeld „Gehe zu“ eingeben. Diese Funktion ist nützlich, wenn der Code lange Namen aufweist.

![Fenster „Navigieren zu“ - Suchvorgänge mit Großbuchstaben](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Einstellungen

Über das Zahnradsymbol ![Zahnradsymbol](media/gotoall_gear.png) können Sie die Funktionsweise dieser Funktion ändern:

Einstellung | BESCHREIBUNG
------- | ---
Vorschauregisterkarte verwenden | Das ausgewählte Element sofort auf der Vorschauregisterkarte der IDE anzeigen
Details anzeigen | Zeigt Projekt-, Datei-, Zeilen- und Zusammenfassungsinformationen aus Dokumentationskommentaren im Fenster an
Fenster zentrieren | Verschieben Sie dieses Fenster in die Mitte des Code-Editors, statt an die Standardposition.

## <a name="see-also"></a>Siehe auch

- [Navigieren durch den Code](../ide/navigating-code.md)
- [Gehe zu Zeile (Dialogfeld)](../ide/reference/go-to-line.md)
- [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md)
