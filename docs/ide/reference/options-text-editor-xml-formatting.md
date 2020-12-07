---
title: Optionen, Text-Editor, XML, Formatierung
description: Hier erfahren Sie, wie Sie mit der Seite „Formatierung“ im XML-Abschnitt angeben, wie Elemente und Attribute in Ihren XML-Dokumenten formatiert werden sollen.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9aac9420d084c64a4bd5d9199f6a7ca96b8c4281
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040510"
---
# <a name="options-text-editor-xml-formatting"></a>Optionen, Text-Editor, XML, Formatierung

Verwenden Sie die Optionsseite **Formatierung**, um anzugeben, wie Elemente und Attribute in Ihren XML-Dokumenten formatiert werden. Wählen Sie für den Zugriff auf XML-Formatierungsoptionen **Extras** > **Optionen** > **Text-Editor** > **XML** und dann **Formatierung** aus.

## <a name="attributes"></a>Attributes

**Manuelle Attributformatierung beibehalten**

Nimmt keine Neuformatierung von Attributen vor. Dies ist die Standardeinstellung.

> [!NOTE]
> Wenn die Attribute auf mehrere Zeilen verteilt sind, richtet der Editor jede Attributzeile am Einzug des jeweils übergeordneten Elements aus.

**Attribute jeweils in einer eigenen Zeile ausrichten**

Richtet das zweite und alle nachfolgenden Attribute vertikal am Einzug des ersten Attributs aus. Der folgende XML-Text veranschaulicht, wie die Attribute ausgerichtet werden:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatisch neu formatieren

**Bei Einfügen aus der Zwischenablage**

Formatiert den aus der Zwischenablage eingefügten XML-Text neu.

**Bei Komplettierung des Endtags**

Formatiert das Element nach Abschluss des Endtags neu.

## <a name="mixed-content"></a>Gemischter Inhalt

**Standardformat: gemischter Inhalt**

Versucht, gemischten Inhalt neu zu formatieren. Der Inhalt von `xml:space="preserve"`-Bereichen wird dabei jedoch nicht berücksichtigt. Dies ist die Standardeinstellung.

Wenn ein Element sowohl Text als auch Markup enthält, wird sein Inhalt wie gemischter Inhalt behandelt. Das folgende Beispiel zeigt ein Element mit gemischtem Inhalt.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Siehe auch

- [XML-Optionen – Sonstiges](options-text-editor-xml-miscellaneous.md)
- [XML-Tools in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
