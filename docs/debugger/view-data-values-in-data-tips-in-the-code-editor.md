---
title: Anzeigen von Variablenwerten in DataTips | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Informationen zu Variablen (z. B. Arrays und Strukturen) problemlos während des Debuggens anzeigen können. Außerdem können Sie Werte ändern.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5c9d0449fca38371e07ddaca6cef8758f53a2aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904927"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Anzeigen von Datenwerten als DataTips im Code-Editor

DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen. Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) sowie [Debugverfahren und -tools](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.

## <a name="work-with-datatips"></a>Arbeiten mit DataTips

DataTips werden nur im Unterbrechungsmodus angezeigt und nur für Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden.

### <a name="display-a-datatip"></a>Anzeigen eines DataTip

1. Legen Sie einen Haltepunkt im Code fest, und starten Sie das Debuggen, indem Sie **F5** drücken oder **Debuggen** > **Debuggen starten** auswählen.

1. Wenn die Ausführung am Haltepunkt angehalten wird, zeigen Sie auf eine beliebige Variable im aktuellen Gültigkeitsbereich. Ein DataTip wird mit dem Namen und dem aktuellen Wert der Variablen angezeigt.

### <a name="make-a-datatip-transparent"></a>Festlegen von Transparenz für einen DataTip

Um einen DataTip transparent zu machen, damit der darunter vorhandene Code angezeigt wird, drücken Sie im DataTip **STRG**. Der DataTip bleibt solange transparent, wie Sie die **STRG**-Taste gedrückt halten. Dies funktioniert nicht für angeheftete oder unverankerte DataTips.
### <a name="pin-a-datatip"></a>Anheften eines DataTip

Um einen DataTip so anzuheften, dass er geöffnet bleibt, wählen Sie das Pinsymbol **An Quelle heften** aus.

![Anheften eines DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "Anheften eines DataTip")

Sie können einen angehefteten DataTip verschieben, indem Sie ihn im Codefenster ziehen. Im Bundsteg neben der Zeile, an die der DataTip angeheftet ist, wird ein Pinsymbol angezeigt.

>[!NOTE]
>DataTips werden immer in dem Kontext ausgewertet, in dem die Ausführung angehalten wird, und nicht an der aktuellen Cursor- oder DataTip-Position. Wenn Sie in einer anderen Funktion auf eine Variable zeigen, deren Name mit dem Namen einer Variablen im aktuellen Kontext identisch ist, wird der Wert der Variablen im aktuellen Kontext angezeigt.

### <a name="unpin-a-datatip-from-source"></a>Lösen eines DataTip von der Quelle

Um einen angehefteten DataTip zu lösen, bewegen Sie den Mauszeiger über den DataTip, und wählen Sie im Kontextmenü das Pinsymbol aus.

Das Pinsymbol ändert sich in die gelöste Position, und der DataTip ist jetzt unverankert oder kann über alle geöffneten Fenster gezogen werden. Unverankerte DataTip werden geschlossen, wenn die Debugsitzung endet.

### <a name="repin-a-datatip"></a>Erneutes Anheften eines DataTip

Um einen unverankerten DataTip erneut an die Quelle zu heften, bewegen Sie im Code-Editor den Mauszeiger über den DataTip, und wählen Sie das Pinsymbol aus. Das Pinsymbol ändert sich in die angeheftete Position, und der DataTip ist erneut ausschließlich an das Codefenster geheftet.

Wenn ein DataTip unverankert in einem anderen Fenster als einem Quellcodefenster angezeigt wird, ist das Pinsymbol nicht verfügbar, und der DataTip kann nicht erneut angeheftet werden. Um auf das Pinsymbol zuzugreifen, verschieben Sie den DataTip wieder in das Code-Editor-Fenster, indem Sie ihn ziehen oder den Fokus auf das Codefenster setzen.

### <a name="close-a-datatip"></a>Schließen eines DataTip

Um einen DataTip zu schließen, bewegen Sie den Mauszeiger über den DataTip, und wählen Sie im Kontextmenü das Symbol „Schließen“ (**x**) aus.

### <a name="close-all-datatips"></a>Schließen aller DataTips

Wenn Sie alle DataTips schließen möchten, wählen Sie im Menü **Debuggen** die Option **Alle DataTips löschen** aus.

### <a name="close-all-datatips-for-a-specific-file"></a>Schließen aller DataTips für eine bestimmte Datei

Wenn Sie alle DataTips für eine bestimmte Datei schließen möchten, wählen Sie im Menü **Debuggen** die Option **Alle an \<Filename>angehefteten DataTips löschen** aus.

## <a name="expand-and-edit-information"></a>Erweitern und Bearbeiten von Informationen
Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen. Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.

### <a name="expand-a-variable"></a>Erweitern einer Variablen

Wenn Sie ein Objekt in einem DataTip erweitern möchten, um dessen Elemente anzuzeigen, zeigen Sie mit dem Mauszeiger auf die Erweiterungspfeile vor den Elementnamen, damit die Elemente im Strukturformat angezeigt werden. Wählen Sie für einen angehefteten DataTip das Symbol **+** vor dem Variablennamen aus, und erweitern Sie dann die Struktur.

![Erweitern eines DataTip](../debugger/media/dbg-tour-data-tips.png "Erweitern eines DataTip")

Sie können die Maus oder die Pfeiltasten der Tastatur verwenden, um die erweiterte Ansicht nach oben und unten zu verschieben.

Sie können auch erweiterte Elemente an den angehefteten DataTip anheften, indem Sie auf sie zeigen und ihre Pinsymbole auswählen. Die Elemente werden dann im angehefteten DataTip angezeigt, nachdem die Struktur reduziert wurde.

### <a name="edit-the-value-of-a-variable"></a>Bearbeiten des Werts einer Variablen

Wenn Sie den Wert einer Variablen oder eines Elements in einem DataTip bearbeiten möchten, wählen Sie den Wert aus, geben Sie einen neuen Wert ein, und drücken Sie die **EINGABETASTE**. Für schreibgeschützte Werte ist die Auswahl deaktiviert.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Anheften von Eigenschaften in DataTips

> [!NOTE]
> Diese Funktion wird für .NET Core 3.0 und höher unterstützt.

Mit dem Tool **Anheftbare Eigenschaften** können Sie Objekte schnell anhand ihrer Eigenschaften in DataTips überprüfen.  Um dieses Tool zu verwenden, zeigen Sie auf eine Eigenschaft, und wählen das daraufhin angezeigte Pinsymbol aus, oder klicken Sie mit der rechten Maustaste, und wählen Sie im resultierenden Kontextmenü die Option **Member als Favorit anheften** aus.  Dadurch wird diese Eigenschaft in der Eigenschaftenliste des Objekts an erste Stelle gesetzt, und der Eigenschaftsname und -wert wird in der rechten Spalte des DataTip angezeigt.  Wenn Sie eine Eigenschaft lösen möchten, wählen Sie das Pinsymbol erneut aus, oder wählen Sie im Kontextmenü die Option **Member als Favorit lösen** aus.

![Anheften einer Eigenschaft in einem DataTip](../debugger/media/basic-pin-datatip.gif "Anheften einer Eigenschaft in einem DataTip")

Sie können beim Anzeigen der Eigenschaftenliste des Objekts in einem DataTip auch Eigenschaftsnamen umschalten und nicht angeheftete Eigenschaften herausfiltern.  Sie können auf eine der beiden Optionen zugreifen, indem Sie mit der rechten Maustaste auf eine Zeile mit einer Eigenschaft klicken und im Kontextmenü die Option **Nur angeheftete Member anzeigen** oder **Angeheftete Membernamen in Werten ausblenden** auswählen.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visuelles Darstellen von komplexen Datentypen

Ein Lupensymbol neben einer Variablen oder einem Element in einem DataTip bedeutet, dass eine oder mehrere [Schnellansichten](../debugger/create-custom-visualizers-of-data.md), z. B. die [Text-Schnellansicht](../debugger/string-visualizer-dialog-box.md), für die Variable verfügbar sind. In Schnellansichten werden Informationen auf verständlichere Weise angezeigt, manchmal in grafischem Format.

Um das Element mit der Standardschnellansicht für den Datentyp anzuzeigen, wählen Sie das Lupensymbol ![Symbol „Schnellansicht“](../debugger/media/dbg-tips-visualizer-icon.png "Symbol der Schnellansicht") aus. Wählen Sie den Pfeil neben dem Lupensymbol aus, um aus einer Liste von Schnellansichten für den Datentyp eine Schnellansicht auszuwählen.

## <a name="add-a-variable-to-a-watch-window"></a>Hinzufügen einer Variablen zu einem Überwachungsfenster

Wenn Sie eine Variable weiter überwachen möchten, können Sie sie aus einem DataTip einem **Überwachungsfenster** hinzufügen. Klicken Sie mit der rechten Maustaste auf die Variable im DataTip, und wählen Sie **Überwachung hinzufügen** aus.

Die Variable wird im Fenster **Überwachung** angezeigt. Wenn Ihre Visual Studio-Edition mehrere **Überwachungsfenster** unterstützt, wird die Variable in **Überwachen 1** angezeigt.

## <a name="import-and-export-datatips"></a>Importieren und Exportieren von DataTips

Sie können DataTips in eine XML-Datei exportieren, die Sie freigeben oder in einem Text-Editor bearbeiten. Sie können auch eine DataTip-XML-Datei importieren, die Sie erhalten oder bearbeitet haben.

**Exportieren von DataTips:**

1. Wählen Sie **Debuggen** > **DataTips exportieren** aus.

1. Navigieren Sie im Dialogfeld **DataTips exportieren** zu dem Speicherort, an dem die XML-Datei gespeichert werden soll, geben Sie einen Namen für die Datei ein, und wählen Sie dann **Speichern** aus.

**Importieren von DataTips:**

1. Wählen Sie **Debuggen** > **DataTips importieren** aus.

1. Wählen Sie im Dialogfeld **DataTips importieren** die DataTips-XML-Datei aus, die Sie öffnen möchten, und wählen Sie dann **Öffnen** aus.

## <a name="see-also"></a>Siehe auch
- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
