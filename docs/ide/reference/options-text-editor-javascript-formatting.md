---
title: Optionen, Text-Editor, JavaScript, Formatierung
description: Hier erfahren Sie, wie Sie die Seite „Formatierung“ im Dialogfeld „Optionen“ verwenden, um Optionen zur Formatierung von Code im Code-Editor festzulegen.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 27b2c5765f041252e62defd15a3c7b6d7b460b43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932461"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Dialogfeld „Optionen“: Text-Editor \> JavaScript \> Formatierung

Verwenden Sie die Seite **Formatierung** im Dialogfeld **Optionen**, um Optionen zur Formatierung von Code im Code-Editor festzulegen. Öffnen Sie diese Seite, indem Sie auf der Menüleiste auf **Extras** > **Optionen** klicken und anschließend den Bereich **Text-Editor** >  **JavaScript/TypeScript** > **Formatierung** erweitern.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatische Formatierung

Diese Optionen bestimmen, wann die Formatierung in der **Quellansicht** vorgenommen wird.

### <a name="uielement-list"></a>UIElement-Liste

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Abgeschlossene Zeile durch Eingabe formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor nach Drücken der EINGABETASTE automatisch die Zeile.|
|**Abgeschlossene Anweisung bei ";" formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor nach Drücken der SEMIKOLONTASTE automatisch die Zeile.|
|**Geöffneten Block bei { formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor beim Auswählen der öffnenden geschweiften Klammer automatisch die Zeile.|
|**Abgeschlossenen Block bei "}" formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor nach Drücken der schließenden geschweiften Klammer automatisch die Zeile.|
|**Beim Einfügen formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor den Code beim Einfügen in den Editor erneut. Der Editor verwendet die aktuell definierten Formatierungsregeln. Wenn diese Option nicht ausgewählt ist, verwendet der Editor die ursprüngliche Formatierung des eingefügten Codes.|

## <a name="new-lines"></a>Neue Zeilen

Diese Optionen bestimmen, ob der Code-Editor eine öffnende geschweifte Klammer für Funktionen und Kontrollblöcke in einer neuen Zeile einfügt.

### <a name="uielement-list"></a>UIElement-Liste

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Öffnende geschweifte Klammer für Funktionen in neuer Zeile platzieren**|Wenn diese Option ausgewählt ist, verschiebt der Code-Editor die mit einer Funktion verknüpfte öffnende geschweifte Klammer in eine neue Zeile.|
|**Öffnende geschweifte Klammer für Kontrollblöcke in neuer Zeile platzieren**|Wenn diese Option ausgewählt ist, verschiebt der Code-Editor die mit einem Kontrollblock verknüpfte öffnende geschweifte Klammer (z. B. `if`- und `while`-Kontrollblöcke) in eine neue Zeile.|

## <a name="spacing"></a>Abstand

Diese Optionen bestimmen, wie Leerzeichen in die **Quellansicht** eingefügt werden.

### <a name="uielement-list"></a>UIElement-Liste

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Leerzeichen nach Trennzeichen einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen nach einem Kommatrennzeichen eingefügt.|
|**In for-Anweisungen Leerzeichen nach Semikolon einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor hinter jedem Semikolon in der ersten Zeile einer `for`-Schleife ein Leerzeichen eingefügt.|
|**Leerzeichen vor und nach binären Operatoren einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen vor und nach einem binären Operator (z.B. +, -, &&, &#124;&#124;) eingefügt.|
|**Leerzeichen nach Schlüsselwörtern in Anweisungen für die Ablaufsteuerung einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor in Anweisungen für die Ablaufsteuerung ein Leerzeichen nach JavaScript-Schüsselwörtern eingefügt.|
|**Leerzeichen nach function-Schlüsselwort für anonyme Funktionen einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen hinter dem `function`-Schlüsselwort für anonyme Funktionen eingefügt.|
|**Leerzeichen nach öffnender und vor schließender nicht leerer Klammer einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen hinter die öffnende Klammer und vor der schließenden Klammer eingefügt, sofern nicht leere Zeichen innerhalb der Klammern vorhanden sind.|

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)