---
title: Toolbox, Registerkarte „HTML“
description: Hier erfahren Sie mehr über die HTML-Komponenten auf der Registerkarte „HTML“ im Fenster „Toolbox“.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f91e832e33d6a65d9fc70ee594d0c0670242306e
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560459"
---
# <a name="toolbox-html-tab"></a>Toolbox, Registerkarte „HTML“

Die Registerkarte **HTML** der Toolbox stellt Komponenten bereit, die für Webseiten und Webformulare nützlich sind. Öffnen Sie zuerst ein Dokument zur Bearbeitung im HTML-Designer, um diese Registerkarte anzuzeigen. Klicken Sie im Menü **Ansicht** auf **Toolbox** und dann auf die Registerkarte **HTML**.

Erstellen Sie eine Instanz eines Tools auf der Registerkarte **HTML**, indem Sie entweder auf das Tool doppelklicken und es zu ihrem Dokument an der aktuellen Einfügemarke hinzufügen oder das Tool auswählen und es an die gewünschte Position auf der Bearbeitungsoberfläche ziehen.

## <a name="ui-elements"></a>Benutzeroberflächenelemente

Die folgenden Tools sind standardmäßig auf der Registerkarte „HTML“ verfügbar.

**Zeiger**

![ASP.NET Mobile-Designer, HTML-Seite, Zeiger](../../ide/reference/media/vxpointer.gif)

Dieses Tool ist standardmäßig ausgewählt, wenn eine Toolboxregisterkarte geöffnet wird. Er kann nicht gelöscht werden. Mithilfe des Zeigers können Sie Objekte auf die Entwurfsoberfläche ziehen, die Größe der Objekte ändern und sie auf der Seite oder dem Formular neu anordnen. Weitere Informationen finden Sie unter [Toolbox](../../ide/reference/toolbox.md).

**Input (Button)**

![Schaltfläche auf HTML-Webseite](../../ide/reference/media/vxbutton.gif)

Fügt ein `input`-Element vom Typ `type="button"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Button1"` für die erste Schaltfläche eingefügt, `id="Button2"` für die zweite usw.

Wenn Sie **Input (Button)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Input (Reset)**

![HTMLpageResetButton-Bildschirmabbildung](../../ide/reference/media/vxreset.gif)

Fügt ein `input`-Element vom Typ `type="reset"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Reset1"` für die erste Reset-Schaltfläche eingefügt, `id="Reset2"` für die zweite usw.

Wenn Sie **Input (Reset)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Input (Submit)**

![HTMLpageToolbarSubmitButton-Bildschirmabbildung](../../ide/reference/media/vxsubmit.gif)

Fügt ein `input`-Element vom Typ `type="submit"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Submit1"` für die erste Submit-Schaltfläche eingefügt, `id="Submit2"` für die zweite usw.

Wenn Sie **Input (Submit)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Input (Text)**

![HTMLpageToolbarTextField-Bildschirmabbildung](../../ide/reference/media/vxtextfield.gif)

Fügt ein `input`-Element vom Typ `type="text"` in das Dokument ein. Bearbeiten Sie das `value`-Attribut, um den angezeigten Standardtext zu ändern. In der Standardeinstellung wird `id="Text1"` für das erste Textfeld eingefügt, `id="Text2"` für das zweite usw.

Wenn Sie **Input (Text)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages (Razor) Sites (Überprüfen der Benutzereingabe in ASP.NET-Webseiten (Razor-Websites))](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (File)**

![HTML-Seite, Dateifeld](../../ide/reference/media/vxfilefield.gif)

Fügt ein `input`-Element vom Typ `type="file"` in das Dokument ein. In der Standardeinstellung wird `id="File1"` für das erste Dateifeld eingefügt, `id="File2"` für das zweite usw.

Wenn Sie **Input (File)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages (Razor) Sites (Überprüfen der Benutzereingabe in ASP.NET-Webseiten (Razor-Websites))](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (Password)**

![Visual Studio, Password Field](../../ide/reference/media/vxpassword.gif)

Fügt ein `input`-Element vom Typ `type="password"` ein. In der Standardeinstellung wird `id="Password1"` für das erste Kennwortfeld eingefügt, `id="Password2"` für das zweite usw.

Wenn Sie **Input (Password)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Wenn Ihre Anwendung Benutzernamen und Kennwörter überträgt, sollten Sie Ihre Webseite so konfigurieren, dass sie Secure Sockets Layer (SSL) verwendet, um die Übertragung zu verschlüsseln. Weitere Informationen finden Sie unter [Sichern von Verbindungen](/previous-versions/tn-archive/bb418917(v=technet.10)). Es wird außerdem empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages (Razor) Sites (Überprüfen der Benutzereingabe in ASP.NET-Webseiten (Razor-Websites))](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (Check box)**

![HTML-Webseiten-Toolbox, Option "Checkbox"](../../ide/reference/media/vxcheckbox.gif)

Fügt ein `input`-Element vom Typ `type="checkbox"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Checkbox1"` für das erste Kontrollkästchen eingefügt, `id="Checkbox2"` für das zweite usw.

Wenn Sie **Input (Check box)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Input (Radio)**

![VisualStudioHTMLpageRadioButton-Bildschirmabbildung](../../ide/reference/media/vxradio.gif)

Fügt ein `input`-Element vom Typ `type="radio"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Radio1"` für das erste Optionsfeld eingefügt, `id="Radio2"` für das zweite usw.

Wenn Sie **Input (Radio)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Input (Hidden)**

![HTML-Seite, Hidden-Element](../../ide/reference/media/vxhidden.gif)

Fügt ein `input`-Element vom Typ `type="hidden"` ein. In der Standardeinstellung wird `id="Hidden1"` für das erste ausgeblendete Feld eingefügt, `id="Hidden2"` für das zweite usw.

Wenn Sie **Input (Hidden)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Textarea**

![HTML-Seiten-Toolbox, Text Area](../../ide/reference/media/vxtextarea.gif)

Fügt ein `textarea`-Element ein. Sie können die Größe des Textbereichs ändern oder die Bildlaufleisten verwenden, um Text außerhalb des Anzeigebereichs anzuzeigen. Bearbeiten Sie das `value`-Attribut, um den angezeigten Standardtext zu ändern. In der Standardeinstellung wird `id="textarea1"` für den ersten Textbereich eingefügt, `id=" textarea 2"` für den zweiten usw.

Wenn Sie **Textarea** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages (Razor) Sites (Überprüfen der Benutzereingabe in ASP.NET-Webseiten (Razor-Websites))](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tabelle**

![HTMLpageToolbarTable-Bildschirmabbildung](../../ide/reference/media/vxtable.gif)

Fügt ein `table`-Element ein.

Wenn Sie **Table** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Bild**

![HTML-Seite, Image-Element](../../ide/reference/media/vximage.gif)

Fügt ein `img`-Element ein. Bearbeiten Sie dieses Element, und geben Sie dessen `src` und `alt`-Text an.

Wenn Sie **Image** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<img alt="" src="">
```

**Auswählen**

![HTML-Seiten-Toolbox, Dropdownfeld](../../ide/reference/media/vxdropdown.gif)

Fügt ein Dropdown-`select`-Element ein (ohne `size`-Attribut). In der Standardeinstellung wird `id="select1"` für das erste Listenfeld eingefügt, `id="select2"` für das zweite usw.

Wenn Sie **Select** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Sie können ein mehrzeiliges `select`-Element erstellen, indem Sie den Wert der size-Eigenschaft erhöhen.

**Horizontal Rule**

![HTML-Seite, Horizontal Rule-Element](../../ide/reference/media/vxhorizontal.gif)

Fügt ein `hr`-Element ein. Um die Stärke der Linie zu erhöhen, bearbeiten Sie das `size`-Attribut.

Wenn Sie **Horizontal Rule** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<hr width="100%" size=1>
```

**Div**

![HTML-Seite, Label](../../ide/reference/media/vxlabel.gif)

Fügt ein `div`-Element ein, das ein `ms_positioning="FlowLayout"`-Attribut enthält. Mit Ausnahme der Breite und Höhe ist dieses Element mit einem Flow Layout Panel identisch. Fügen Sie dem Starttag ein `class="stylename"`-Attribut hinzu, um den Text zu formatieren, der im `div`-Element enthalten ist.

Wenn Sie **Div** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Weitere Informationen

- [Werkzeugkasten](../../ide/reference/toolbox.md)
