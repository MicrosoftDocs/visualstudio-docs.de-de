---
title: Optionen, Text-Editor, JavaScript, IntelliSense
description: In diesem Artikel erhalten Sie Informationen zur Verwendung der IntelliSense-Seite des Dialogfelds „Optionen“, um Einstellungen zu bearbeiten, die das Verhalten von IntelliSense für JavaScript beeinflussen.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 051711a9d6dfe861f37e741ae9ecabfbf741012e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932357"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Dialogfeld „Optionen“: Text-Editor \> JavaScript \> IntelliSense

Verwenden Sie die Seite **IntelliSense** des Dialogfelds **Optionen** , um Einstellungen zu ändern, die das Verhalten von IntelliSense für JavaScript beeinflussen. Sie erreichen die Seite **IntelliSense**, indem Sie in der Menüleiste auf **Extras** > **Optionen** klicken und anschließend den Bereich **Text-Editor** > **JavaScript/TypeScript** > **IntelliSense** erweitern.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Die Seite **IntelliSense** enthält folgende Abschnitte:

## <a name="statement-completion"></a>Anweisungsabschluss

Sie können diese Optionen verwenden, um das Verhalten der IntelliSense-Anweisungsvervollständigung zu ändern.

### <a name="uielement-list"></a>UIElement-Liste

**Nur mit TAB- oder EINGABETASTE Commit ausführen**

Wenn Sie dieses Kontrollkästchen aktivieren, erweitert der JavaScript-Code-Editor Anweisungen nur dann mit Elementen, die Sie in der Vervollständigungsliste ausgewählt haben, wenn Sie auf die **TAB-TASTE** oder die **EINGABETASTE** drücken. Wenn Sie dieses Kontrollkästchen deaktivieren, können auch andere Zeichen wie Punkt, Komma, Doppelpunkt, öffnende runde Klammer und öffnende geschweifte Klammer ({) Anweisungen mit den ausgewählten Elementen erweitern.

## <a name="references"></a>References

Sie können diese Optionen verwenden, um die Typen von IntelliSense-JS-Dateien anzugeben, die für verschiedene JavaScript-Projekttypen verfügbar sind. Die IntelliSense-Verweise werden normalerweise verwendet, um die IntelliSense-Unterstützung für globale Objekte bereitzustellen. Sie können diese Seite auch verwenden, um die Ladereihenfolge für Skripts festlegen, die zur Laufzeit geladen werden müssen, und um IntelliSense-Erweiterungsdateien hinzuzufügen.

### <a name="uielement-list"></a>UIElement-Liste

**Verweisgruppen**

Diese Option gibt den Verweisgruppentyp an. Drei Verweisgruppen werden unterstützt:

Sie können vordefinierte Verweisgruppen verwenden, um anzugeben, dass bestimmte IntelliSense-JS-Dateien für verschiedene JavaScript-Projekte verfügbar sind. Vier Verweisgruppen sind verfügbar:

- Implizit (Windows- *Version*) für [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] -Apps, die JavaScript verwenden. Die in dieser Gruppe enthalten Dateien sind für jede im Code-Editor geöffnete JS-Datei für [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]-Apps mit JavaScript verfügbar.

- Implizit (Internet), für HTML5-Projekte. Die Dateien, die in dieser Gruppe enthalten sind, sind im Bereich für jede JS-Datei, die im Code-Editor für die Projekttypen geöffnet ist.

- Dedizierte Workerverweisgruppen, für HTML5-Web-Worker. Die Dateien, die in dieser Gruppe angegeben werden, sind für JS-Dateien verfügbar, die einen expliziten Verweis auf eine dedizierte Workerverweisgruppe haben.

- Generisch, für andere JavaScript-Projekttypen.

**Eingeschlossene Dateien**

Diese Option gibt die Reihenfolge an, in der Dateien in den Kontext des Sprachdiensts geladen werden. Sie können die Reihenfolge konfigurieren, indem Sie die Schaltflächen **Entfernen**, **Nach oben** und **Nach unten** verwenden. Damit IntelliSense ordnungsgemäß funktioniert, muss eine Datei, die von einer anderen abhängig ist, im Anschluss an diese geladen werden.

> [!CAUTION]
> Wenn ein Objekt ohne Einschränkung in zwei oder mehr impliziten Verweisen definiert ist, wird der letzte Verweis in dieser Liste verwendet, um das Objekt zu definieren.

**Fügen Sie der Gruppe einen Verweis hinzu**

Diese Option bietet die Möglichkeit, nach zusätzlichen IntelliSense-JS-Dateien zu suchen und solche Dateien hinzuzufügen.

**Remoteverweise (z. B. http://) für Dateien im Projekt "Sonstige Dateien" herunterladen**

Wenn dieses Kontrollkästchen aktiviert ist und Sie eine JavaScript-Datei außerhalb des Kontexts eines Projekts geöffnet haben, lädt Visual Studio remote JavaScript-Dateien herunter, auf die in der Datei verwiesen wird, um IntelliSense-Informationen bereitzustellen. Wenn diese Option ausgewählt ist, werden Dateien heruntergeladen, wenn Sie diese als Verweis in der JavaScript-Datei eingeschlossen haben.

> [!NOTE]
> Für Webprojekte werden die Remotedateien, auf die im Projekt verwiesen wird, standardmäßig heruntergeladen.

## <a name="see-also"></a>Siehe auch

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)