---
title: Optionen, Text-Editor, XAML, Formatierung
description: Hier erfahren Sie, wie Sie über die Seite mit den Formatierungsoptionen und die zugehörigen Unterseiten die Optionen für die Codeformatierung beim Programmieren in XAML im Code-Editor festlegen.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: f550499545fda3250f4d2449697513fbc8c09fa2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970789"
---
# <a name="options-text-editor-xaml-formatting"></a>Optionen, Text-Editor, XAML, Formatierung

Verwenden Sie die **Formatierung**-Eigenschaftenseite, um anzugeben, wie Elemente und Attribute in Ihren XAML-Dokumenten formatiert werden. Klicken Sie zum Öffnen des Dialogfelds **Optionen** auf das Menü **Tools** und anschließend auf **Optionen**. Erweitern Sie für den Zugriff auf die Eigenschaftenseite **Formatierung** den Knoten **Text-Editor** > **XAML** > **Formatierung**.

## <a name="auto-formatting-events"></a>Autoformatierungsereignisse

Die automatische Formatierung kann auftreten, wenn eines der folgenden Ereignisse erkannt wird.

- Bei Vervollständigung des Endtags oder eines einfachen Tags

- Bei Vervollständigung des Starttags

- Bei Einfügen aus der Zwischenablage

- Formatieren von Tastaturbefehlen

Sie können angeben, welche Ereignisse automatische Formatierung verursachen.

**Bei Vervollständigung des Endtags oder eines einfachen Tags**

Die automatische Formatierung tritt auf, wenn Sie ein Endtag oder ein einfaches Tag eingegeben haben. Ein einfaches Tag verfügt über keine Attribute, z.B. `<Button />`.

**Bei Vervollständigung des Starttags**

Die automatische Formatierung tritt auf, wenn Sie ein Starttag eingegeben haben.

**Bei Einfügen aus der Zwischenablage**

Die automatische Formatierung tritt auf, wenn Sie XAML aus der Zwischenablage in die XAML-Ansicht einfügen.

## <a name="quotation-mark-style"></a>Anführungszeichenformat

Diese Einstellung gibt an, ob Attributwerte in einfache oder doppelte Anführungszeichen eingeschlossen werden. Die automatische Formatierung und die automatische Vervollständigung von IntelliSense verwenden diese Einstellung.

Nachdem Sie diese Option festgelegt haben, sind nur Attribute betroffen, die später entweder mithilfe des Designers oder manuell in die XAML-Ansicht hinzugefügt werden.

**Doppelte Anführungszeichen (")**

Attributwerte werden in doppelte Anführungszeichen eingeschlossen.
`<Button Name="button1">Hello</Button>`

**Einfache Anführungszeichen (')**

Attributwerte werden in einfache Anführungszeichen eingeschlossen.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Tagumbrüche

Sie können eine Zeilenlänge für Tagumbrüche angeben. Wenn Tagumbrüche aktiviert sind, wird jedes XAML, das später mithilfe des Designers hinzugefügt wird, entsprechend umgebrochen.

**Tags bei Überschreitung der angegebenen Länge umbrechen**

Gibt an, ob Zeilen bei der durch **Länge** angegebenen Zeilenlänge umgebrochen werden.

**Länge**

Die Anzahl der Zeichen, die eine Zeile enthalten kann. Falls erforderlich, könnten einige XAML-Zeilen die angegebene Zeilenlänge überschreiten.

## <a name="attribute-spacing"></a>Attributabstand

Mit dieser Einstellung können Sie steuern, wie Attribute im XAML-Dokument angeordnet sind

**Neue Zeilen und Leerzeichen zwischen Attributen beibehalten**

Neue Zeilen und Leerzeichen zwischen Attributen sind von der automatischen Formatierung nicht betroffen.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Ein Leerzeichen zwischen Attributen einfügen**

Attribute umfassen eine Zeile mit durch ein Leerzeichen getrennten benachbarten Attributen. Die Einstellungen für Tagumbrüche werden angewendet.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Jedes Attribut in einer eigenen Zeile anordnen**

Jedes Attribut befindet sich in einer eigenen Zeile, was nützlich ist, wenn viele Attribute vorhanden sind.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Erstes Attribut in derselben Zeile wie Starttag positionieren**

Wenn dieses Kontrollkästchen aktiviert ist, wird das erste Attribut auf derselben Zeile wie der Starttag des Elements angezeigt.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Elementabstand

Mit dieser Einstellung können Sie steuern, wie Attribute in Ihrem XAML-Dokument angeordnet sind.

**Neue Zeilen im Inhalt beibehalten**

Leerzeilen im Elementinhalt werden nicht entfernt.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Mehrere Leerzeilen im Inhalt auf eine Zeile reduzieren**

Leerzeilen im Elementinhalt werden zu einer einzelnen Zeile reduziert.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Leerzeilen im Inhalt entfernen**

Alle Leerzeilen im Elementinhalt werden entfernt.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Siehe auch

- [XAML in WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
