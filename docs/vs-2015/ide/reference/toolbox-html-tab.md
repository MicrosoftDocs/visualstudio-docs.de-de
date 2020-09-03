---
title: Toolbox, Registerkarte „HTML“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4474f2a0823b5599da30706daedff6e5cd1fc0f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851663"
---
# <a name="toolbox-html-tab"></a>Toolbox, Registerkarte „HTML“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Registerkarte **HTML** der Toolbox stellt Komponenten bereit, die für Webseiten und Web Forms nützlich sind. Öffnen Sie zuerst ein Dokument zur Bearbeitung im HTML-Designer, um diese Registerkarte anzuzeigen. Klicken Sie im Menü **Ansicht** auf **Toolbox** und dann auf die Registerkarte **HTML**.

 Erstellen Sie eine Instanz eines Tools auf der Registerkarte **HTML**, indem Sie entweder auf das Tool doppelklicken und es zu ihrem Dokument an der aktuellen Einfügemarke hinzufügen oder das Tool auswählen und es an die gewünschte Position auf der Bearbeitungsoberfläche ziehen.

## <a name="tasks"></a>Aufgaben

- [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [Vorgehensweise: Ändern von Registerkarten der Toolbox](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>Benutzeroberflächenelemente
 Die folgenden Tools sind standardmäßig auf der Registerkarte „HTML“ verfügbar.

 **Zeiger** ![ASP.NET Mobile Designer HtmlPage-Zeiger](../../ide/reference/media/vxpointer.gif "vxpointer")

 Dieses Tool ist standardmäßig ausgewählt, wenn eine Toolboxregisterkarte geöffnet wird. Er kann nicht gelöscht werden. Mithilfe des Zeigers können Sie Objekte auf die Entwurfsoberfläche ziehen, die Größe der Objekte ändern und sie auf der Seite oder dem Formular neu anordnen. Weitere Informationen finden Sie unter [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) und [Vorgehensweise: Ändern von Registerkarten der Toolbox](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 ![Schaltfläche](../../ide/reference/media/vxbutton.gif "vxbutton") " **Eingabe (Schaltfläche)** HTML-Webseite"

 Fügt ein `input`-Element vom Typ `type="button"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Button1"` für die erste Schaltfläche eingefügt, `id="Button2"` für die zweite usw.

 Wenn Sie **Input (Button)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputButton-Serversteuerelements](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: Vorgehensweise: Erstellen von Skripts und Bearbeiten von Ereignishandlern](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Übersicht über die Button-Webserversteuerelemente](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> und <xref:System.Web.UI.WebControls.Button>.

 **Eingabe (zurücksetzen)** ![HTMLpageResetButton Screenshot](../../ide/reference/media/vxreset.gif "vxreset")

 Fügt ein `input`-Element vom Typ `type="reset"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Reset1"` für die erste Reset-Schaltfläche eingefügt, `id="Reset2"` für die zweite usw.

 Wenn Sie **Input (Reset)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputReset-Serversteuerelements](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> und <xref:System.Web.UI.WebControls.Button>.

 **Eingabe (Submit)** ![htmlpagetoolbarsubmitbutton-Bildschirm](../../ide/reference/media/vxsubmit.gif "vxsubmit") Foto

 Fügt ein `input`-Element vom Typ `type="submit"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Submit1"` für die erste Submit-Schaltfläche eingefügt, `id="Submit2"` für die zweite usw.

 Wenn Sie **Input (Submit)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputSubmit-Serversteuerelements](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> und <xref:System.Web.UI.WebControls.Button>.

 **Eingabe (Text)** ![HTMLpageToolbarTextField-Bildschirm](../../ide/reference/media/vxtextfield.gif "vxtextfield") Foto

 Fügt ein `input`-Element vom Typ `type="text"` in das Dokument ein. Bearbeiten Sie das `value`-Attribut, um den angezeigten Standardtext zu ändern. In der Standardeinstellung wird `id="Text1"` für das erste Textfeld eingefügt, `id="Text2"` für das zweite usw.

 Wenn Sie **Input (Text)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputText-Serversteuerelements](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [Übersicht über das TextBox-Webserversteuerelement](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> und <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 HTML-Auslagerungs ![Datei Feld](../../ide/reference/media/vxfilefield.gif "vxfilefield") der **Eingabedatei**

 Fügt ein `input`-Element vom Typ `type="file"` in das Dokument ein. In der Standardeinstellung wird `id="File1"` für das erste Dateifeld eingefügt, `id="File2"` für das zweite usw.

 Wenn Sie **Input (File)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="File1" type="file" name="File1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputFile-Serversteuerelements](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) und <xref:System.Web.UI.HtmlControls.HtmlInputFile>.

> [!IMPORTANT]
> Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Eingabe (Kennwort)** ![Visual Studio-Kennwort-Feld](../../ide/reference/media/vxpassword.gif "vxpassword")

 Fügt ein `input`-Element vom Typ `type="password"` ein. In der Standardeinstellung wird `id="Password1"` für das erste Kennwortfeld eingefügt, `id="Password2"` für das zweite usw.

 Wenn Sie **Input (Password)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Password1" type="password" name="Password1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputPassword-Serversteuerelements](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Vorgehensweise: Einrichten eines TextBox-Webserversteuerelements für die Kennworteingabe](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) und [Exemplarische Vorgehensweise: Validieren der Benutzereingabe in einer Web Forms-Seite](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).

> [!IMPORTANT]
> Wenn Ihre Anwendung Benutzernamen und Kennwörter überträgt, sollten Sie Ihre Webseite so konfigurieren, dass sie Secure Sockets Layer (SSL) verwendet, um die Übertragung zu verschlüsseln. Weitere Informationen finden Sie unter „Securing Connections with SSL“ („Sichern von Verbindungen mit SSL“) im [IIS Operations Guide (IIS-Benutzerhandbuch)](https://technet.microsoft.com/library/cc732976(v=WS.10).aspx). Es wird außerdem empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Eingabe (Kontrollkästchen)** ![HTML-Webseiten-Toolbox (Kontrollkästchen](../../ide/reference/media/vxcheckbox.gif "vxcheckbox") )

 Fügt ein `input`-Element vom Typ `type="checkbox"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Checkbox1"` für das erste Kontrollkästchen eingefügt, `id="Checkbox2"` für das zweite usw.

 Wenn Sie **Input (Check box)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputCheckBox-Serversteuerelements](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [Übersicht über die CheckBox- und CheckBoxList-Webserversteuerelemente](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> und <xref:System.Web.UI.WebControls.CheckBox>.

 **Eingabe (Radio)** ![VisualStudioHTMLpageRadioButton-Bildschirm](../../ide/reference/media/vxradio.gif "vxradio") Foto

 Fügt ein `input`-Element vom Typ `type="radio"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Radio1"` für das erste Optionsfeld eingefügt, `id="Radio2"` für das zweite usw.

 Wenn Sie **Input (Radio)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Radio1" type="radio" name="Radio1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputRadioButton-Serversteuerelements](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [Übersicht über die RadioButton- und RadioButtonList-Webserversteuerelemente](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> und <xref:System.Web.UI.WebControls.RadioButton>.

 Ausgeblendetes ![HTML-Seitenelement](../../ide/reference/media/vxhidden.gif "vxhidden") **(ausgeblendet)**

 Fügt ein `input`-Element vom Typ `type="hidden"` ein. In der Standardeinstellung wird `id="Hidden1"` für das erste ausgeblendete Feld eingefügt, `id="Hidden2"` für das zweite usw.

 Wenn Sie **Input (Hidden)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputHidden-Serversteuerelements](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) und <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.

 **Textarea** - ![HtmlPage-Symbolleisten-Text Bereich](../../ide/reference/media/vxtextarea.gif "vxtextarea")

 Fügt ein `textarea`-Element ein. Sie können die Größe des Textbereichs ändern oder die Bildlaufleisten verwenden, um Text außerhalb des Anzeigebereichs anzuzeigen. Bearbeiten Sie das `value`-Attribut, um den angezeigten Standardtext zu ändern. In der Standardeinstellung wird `id="textarea1"` für den ersten Textbereich eingefügt, `id=" textarea 2"` für den zweiten usw.

 Wenn Sie **Textarea** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 Weitere Informationen finden Sie unter [deklarative Syntax des HtmlTextArea-Server Steuer](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87)Elements, <xref:System.Web.UI.HtmlControls.HtmlTextArea> und <xref:System.Web.UI.WebControls.TextBox> .

> [!IMPORTANT]
> Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Tabelle** ![htmlpagetoolbartable-Bildschirm](../../ide/reference/media/vxtable.gif "vxtable") Foto

 Fügt ein `table`-Element ein.

 Wenn Sie **Table** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 Weitere Informationen finden Sie unter [Deklarative Syntax des HtmlTable-Serversteuerelements](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Übersicht über die Table-, TableRow- und TableCell-Webserversteuerelemente](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> und <xref:System.Web.UI.WebControls.Table>.

 Bildelement **Bild** - ![HTML-Seite](../../ide/reference/media/vximage.gif "vximage")

 Fügt ein `img`-Element ein. Bearbeiten Sie dieses Element, und geben Sie dessen `src` und `alt`-Text an.

 Wenn Sie **Image** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<img alt="" src="">
```

 Weitere Informationen finden Sie unter [deklarative Syntax des HtmlImage-Server Steuer](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6)Elements, [Übersicht über das Bild Webserver-Steuer](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9)Element, <xref:System.Web.UI.HtmlControls.HtmlImage> , <xref:System.Web.UI.HtmlControls.HtmlInputImage> und <xref:System.Web.UI.WebControls.Image> .

 **Select** ![Dropdown für HTML-Seiten-Toolbox](../../ide/reference/media/vxdropdown.gif "vxdropdown") auswählen

 Fügt ein Dropdown-`select`-Element ein (ohne `size`-Attribut). In der Standardeinstellung wird `id="select1"` für das erste Listenfeld eingefügt, `id="select2"` für das zweite usw.

 Wenn Sie **Select** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<select id="select1" name="select1"><option selected></option></select>
```

 Sie können ein mehrzeiliges `select`-Element erstellen, indem Sie den Wert der size-Eigenschaft erhöhen.

 Weitere Informationen finden Sie unter [Deklarative Syntax des HtmlSelect-Serversteuerelements](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: Vorgehensweise: Erstellen von Skripts und Bearbeiten von Ereignishandlern](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Übersicht über das DropDownList-Webserversteuerelement](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Übersicht über das ListBox-Webserversteuerelement](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect> und <xref:System.Web.UI.WebControls.DropDownList>.

 Horizontales Regel Element der **horizontalen Regel** - ![HTML-Seite](../../ide/reference/media/vxhorizontal.gif "vxhorizontal")

 Fügt ein `hr`-Element ein. Um die Stärke der Linie zu erhöhen, bearbeiten Sie das `size`-Attribut.

 Wenn Sie **Horizontal Rule** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<hr width="100%" size=1>
```

 Weitere Informationen finden Sie unter [Horizontal Rule-Steuerelement (HTML)](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).

 **Div** - ![HTML-Seiten Bezeichnung](../../ide/reference/media/vxlabel.gif "vxlabel")

 Fügt ein `div`-Element ein, das ein `ms_positioning="FlowLayout"`-Attribut enthält. Mit Ausnahme der Breite und Höhe ist dieses Element mit einem Flow Layout Panel identisch. Fügen Sie dem Starttag ein `class="stylename"`-Attribut hinzu, um den Text zu formatieren, der im `div`-Element enthalten ist.

 Wenn Sie **Div** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 Weitere Informationen finden Sie unter [Div-Steuerelement (HTML)](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Übersicht über das Label-Webserversteuerelement](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) und <xref:System.Web.UI.WebControls.Label>.

## <a name="see-also"></a>Weitere Informationen
 [Toolbox](../../ide/reference/toolbox.md) [Standard Registerkarte, Toolbox](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870) -HTML-Steuer [Elemente](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
