---
title: Optionen, Text-Editor, HTML (Web Forms), Formatierung
description: Hier erfahren Sie, wie Sie mithilfe der Formatierungsseite im HTML-Abschnitt die HTML-Projektoptionen für das Formatieren von Code im Code-Editor festlegen.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c8fe85b7bce856867802d43411816ae2df5d2c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040978"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Optionen, Text-Editor, HTML (Web Forms), Formatierung

Auf der Optionsseite **Formatierung** können Sie HTML-Projektoptionen zur Formatierung von Code im Code-Editor festlegen. Öffnen Sie diese Seite, indem Sie auf der Menüleiste auf **Tools** > **Optionen** klicken und anschließend **Text-Editor** > **HTML (Web Forms)**  > **Formatierung** erweitern.

## <a name="capitalization"></a>Großbuchstaben

Bei Auswahl dieser Optionen wird in der Quellansicht und den XML-Editoren beim ersten Erstellen von Elementen und während der automatischen Formatierung ein Standardformat für die Groß- und Kleinschreibung auf Element- und Attributnamen angewendet. Die Einstellungen für die Option **Automatische Formatierung übernehmen** bestimmen den Zeitpunkt der automatischen Neuformatierung.

> [!WARNING]
> Bei XML muss die Groß- und Kleinschreibung beachtet werden. Eine diesbezügliche Standardeinstellung kann zur Beeinträchtigung von XML-Parsern führen.

### <a name="uielement-list"></a>UIElement-Liste

**Servertag, Serverattribute**

Diese Optionen geben an, wie beim Markup für Webserversteuerelemente mit der Groß-/Kleinschreibung verfahren wird.

|Option|Ergebnis|
|---------------------------------|------------------------------|
|**Wie eingegeben**|Die Groß-/Kleinschreibung des Elements entspricht Ihren Eingaben.|
|**Großbuchstaben**|Elementnamen werden in Großbuchstaben umformatiert.|
|**Kleinbuchstaben**|Elementnamen werden in Kleinbuchstaben umformatiert.|
|**Assemblydefinition**|Die Groß-/Kleinschreibung eines Elements wird dadurch bestimmt, wie dieses in der entsprechenden Typklasse definiert ist.|

**Clienttag, Clientattribute**

Diese Optionen geben an, ob bei der automatischen Formatierung die Schreibweise der Namen von HTML-Attributen und -Eigenschaften in Groß- oder Kleinschreibung geändert wird oder nicht.

|Option|Ergebnis|
|---------------------------------|------------------------------|
|**Wie eingegeben**|Die Groß-/Kleinschreibung des Attributs entspricht Ihren Eingaben.|
|**Großbuchstaben**|Die Namen der Attribute werden in Großbuchstaben umformatiert.|
|**Kleinbuchstaben**|Die Namen der Attribute werden in Kleinbuchstaben umformatiert.|

## <a name="automatic-formatting-options"></a>Automatische Formatierungsoptionen

Diese Optionen legen fest, ob der Quellansicht-Editor während der automatischen Formatierung physische Zeilenumbrüche hinzufügt oder entfernt. Sie können auch angeben, ob Attribute in Anführungszeichen eingeschlossen werden.

> [!NOTE]
> Diese Einstellungen bewirken keine Änderung an Leerräumen innerhalb des XML-Markups.

### <a name="uielement-list"></a>UIElement-Liste

- **Anführungszeichen für Attributwerte bei der Eingabe einfügen**

   Bei Auswahl dieser Option werden Attribute bei der Eingabe automatisch vom Editor in Anführungszeichen eingeschlossen (z.B.: ID="Select1"). Wenn Sie Anführungszeichen manuell in das Markup einfügen möchten, können Sie diese Option deaktivieren.

   > [!NOTE]
   > Unabhängig von der Auswahl dieser Option bleiben alle im Markup vorhandenen Anführungszeichen erhalten. Anführungszeichen werden niemals entfernt.

- **Anführungszeichen für Attributwerte bei der Formatierung einfügen**

   Bei Auswahl dieser Option werden Attributwerte bei der automatischen Formatierung in Anführungszeichen eingeschlossen (z.B.: ID="Select1").

   > [!NOTE]
   > Unabhängig von der Auswahl dieser Option bleiben alle im Markup vorhandenen Anführungszeichen erhalten.

- **Endtag automatisch einfügen**

   Bei Auswahl dieser Option erstellt der Editor beim Schließen des Starttags automatisch ein Endtag (z. B. **\</b>** ).

## <a name="tag-wrapping"></a>Tagumbrüche

Diese Optionen bestimmen, ob der Editor Tags in Zeilen umbricht, wenn sie eine bestimmte Länge überschreiten.

### <a name="uielement-list"></a>UIElement-Liste

- **Tags bei Überschreitung der angegebenen Länge umbrechen**

   Wenn die Option aktiviert ist, bricht der Editor Tags in Zeilen um, wenn das Tag die von Ihnen im Textfeld **Länge** angegebene Länge überschreitet. Dies geschieht nur beim Formatieren des Tags, aber nicht beim Eingeben eines neuen Tags.

   > [!NOTE]
   > Der von Ihnen angegebene Wert wird als Minimalwert verwendet. Der Editor führt keinen Umbruch einzelner Attribute durch.

- **Länge**

   Gibt die Anzahl von Zeichen an, die angezeigt werden sollen, bevor die Zeile umbrochen wird. Dieses Eingabefeld ist nur aktiviert, wenn das Feld **Tags bei Überschreitung der angegebenen Länge umbrechen** aktiviert ist.

- **Tagspezifische Optionen**

   Zeigt das Dialogfeld **Tagspezifische Optionen** an, in dem Sie die Formatierungsoptionen für einzelne Tags und Gruppen von Tags festlegen können.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
