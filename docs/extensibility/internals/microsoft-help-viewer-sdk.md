---
title: Microsoft Help Viewer SDK | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 901a5a5eea7835720ab9d5963f0ab1be36df3685
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668858"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Dieser Artikel enthält die folgenden Aufgaben für Visual Studio Help Viewer-Integratoren:

- Erstellen eines Themas (F1-Unterstützung)

- Erstellen eines Help Viewer-Inhalts-Branding-Pakets

- Bereitstellen von Artikeln

- Hinzufügen von Hilfe zur Visual Studio Shell (integriert oder isoliert)

- Weitere Ressourcen

## <a name="create-a-topic-f1-support"></a>Erstellen eines Themas (F1-Unterstützung)

Dieser Abschnitt enthält eine Übersicht über die Komponenten eines dargestellten Themas, Thema Anforderungen, eine kurze Beschreibung der Vorgehensweise zum Erstellen eines Themas (einschließlich F1-Supportanforderungen) und schließlich ein Beispiel Thema mit dem gerenderten Ergebnis.

**Übersicht über das Help Viewer-Thema**

Wenn ein Thema zum Rendern aufgerufen wird, ruft der Help Viewer die Branding-Paket Elemente, die dem Thema zum Zeitpunkt der Installation oder dem letzten Update zugeordnet sind, zusammen mit dem Thema XHTML ab und kombiniert die beiden mit der dargestellten Inhaltsansicht (Branding Data + Topic Data).  Das Branding-Paket enthält Logos, Unterstützung für Inhalts Verhalten und Brandingtext (Copyright usw.).  Weitere Informationen zu den Branding-Paket Elementen finden Sie unten im Abschnitt "Erstellen von Branding-Paketen".  Wenn dem Thema kein Branding-Paket zugeordnet ist, verwendet Help Viewer das Fall Back-Branding-Paket, das sich im Stammverzeichnis der Help Viewer-Anwendung befindet (Branding_en-US. mshc).

**Hilfe Viewer-Themen Anforderungen**

Um in Help Viewer korrekt gerendert zu werden, muss der Inhalt des unformatierten Themas "W3C Basic 1,1 XHTML" lauten.

Ein Thema enthält in der Regel zwei Abschnitte:

- Metadaten (siehe Inhalts Metadaten-Referenz): Daten zum Thema, z. b. das Thema eindeutige ID, den Schlüsselwort Wert, die TOC-ID des Themas, die ID des übergeordneten Knotens usw.

- Body Content: kompatibel mit W3C Basic 1,1 XHTML, das unterstützte Inhalts Verhalten (redusible Area, Code Ausschnitt usw.) umfasst. Unten ist eine vollständige Liste aufgeführt.)

Von Visual Studio-Branding-Paketen unterstützte Steuerelemente:

- Links

- CodeSnippet

- Redusiblearea

- Vererbte Member

- Languagespecifictext

Unterstützte sprach Zeichenfolgen (Groß-/Kleinschreibung nicht beachtet

- javascript

- CSharp oder c #

- CPlusPlus oder VisualC + + oder c++

- jscript

- VisualBasic oder VB

- f # oder FSharp oder FS

- Sonstige-eine Zeichenfolge, die einen Sprachen Namen darstellt.

**Erstellen eines Help Viewer-Themas**

Erstellen Sie ein neues XHTML-Dokument mit dem Namen ContosoTopic4.htm, und schließen Sie das Titeltag (unten) ein.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Fügen Sie als nächstes Daten hinzu, um zu definieren, wie das Thema angezeigt werden soll (selbst Branding oder nicht), wie Sie auf dieses Thema für F1 verweisen, wo dieses Thema im Inhaltsverzeichnis, seine ID (für Link Verweis in anderen Themen) usw. vorhanden ist. Eine umfassende Liste der unterstützten Metadaten finden Sie unten in der Tabelle "Content Metadata".

- In diesem Fall verwenden wir unser eigenes Branding-Paket, eine Variante des Visual Studio Help Viewer-Branding-Pakets.

- Fügen Sie den F1-Meta-Namen und-Wert ("Microsoft. Help. F1" Content = "ContosoTopic4") hinzu, der dem angegebenen F1-Wert in der IDE-Eigenschaften Sammlung entspricht. (Weitere Informationen finden Sie im Abschnitt F1-Unterstützung.) Dies ist der Wert, der mit dem F1-Befehl aus der IDE abgeglichen wird, um dieses Thema anzuzeigen, wenn F1 in der IDE ausgewählt wird.

- Fügen Sie die Themen-ID hinzu. Dies ist die Zeichenfolge, die von anderen Themen zum Verknüpfen mit diesem Thema verwendet wird. Dies ist die Help Viewer-ID für dieses Thema.

- Fügen Sie für das Inhaltsverzeichnis den übergeordneten Knoten dieses Themas hinzu, um zu definieren, wo der Inhaltsverzeichnis Knoten angezeigt wird.

- Fügen Sie für das Inhaltsverzeichnis die Knoten Reihenfolge dieses Themas hinzu. Wenn der übergeordnete Knoten über die `n` Anzahl der untergeordneten Knoten verfügt, definieren Sie in der Reihenfolge der untergeordneten Knoten den Speicherort dieses Themas. Dieses Thema ist beispielsweise die Nummer 4 von vier untergeordneten Themen.

Beispiel für einen Metadatenabschnitt:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**Der Themen Text**

Der Text (ohne Kopf-und Fußzeile) des Themas enthält Seiten Verknüpfungen, einen Notiz Abschnitt, einen Reduzierungs Bereich, einen Code Ausschnitt und einen Abschnitt mit sprach spezifischem Text.  Informationen zu den Bereichen des dargestellten Themas finden Sie im Abschnitt Branding.

1. Hinzufügen eines Thementitel Tags:  `<div class="title">Contoso Topic 4</div>`

2. Hinweis Abschnitt hinzufügen: `<div class="alert"> add your table tag and text </div>`

3. Fügen Sie einen redusible-Bereich hinzu:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Fügen Sie einen Code Ausschnitt hinzu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Code sprachspezifischer Text hinzufügen:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` beachten Sie, dass `devLangnu=` es Ihnen ermöglicht, andere Sprachen einzugeben. Zeigt beispielsweise `devLangnu="Fortran"` Fortran an, wenn der Code Ausschnitt Display Language = Fortran

6. Seiten Verknüpfungen hinzufügen: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Hinweis: bei einer nicht unterstützten neuen "Anzeige Sprache" (z. b. F #, COBOL, Fortran) ist die Farbgebung von Code im Code Ausschnitt Monochrom.

**Beispiel für Help Viewer-Thema** Im Code wird veranschaulicht, wie Metadaten, ein Code Ausschnitt, ein redusible Bereich und ein sprachspezifischer Text definiert werden.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1-Unterstützung**

Wenn Sie in Visual Studio F1 auswählen, werden Werte generiert, die von der Platzierung des Cursors innerhalb der IDE bereitgestellt werden, und es wird ein "Eigenschaften Behälter" mit den angegebenen Werten (basierend auf der Cursorposition) aufgefüllt. Wenn sich der Cursor über dem Feature x befindet, ist Feature x aktiv/im Fokus und füllt den Eigenschaften Behälter mit Werten auf.  Wenn F1 ausgewählt wird, wird der Eigenschaften Behälter aufgefüllt, und Visual Studio-F1-Code sucht nach dem anzeigen, ob die Standard Hilfe Quelle der Kunden lokal oder Online ist (Online ist die Standardeinstellung). dann erstellt die entsprechende Zeichenfolge auf der Grundlage der Benutzereinstellung (Online ist die Standardeinstellung)-Shell Execute (Weitere Informationen finden Sie im Hilfe Administrator Handbuch für exe-Startparameter) mit Parametern für das lokale Help Viewer + Schlüsselwort aus dem Eigenschaften Behälter, wenn local Help der Standardwert ist. , oder die MSDN-URL mit dem-Schlüsselwort in der Parameterliste.

Wenn drei Zeichen folgen für F1 zurückgegeben werden, die als mehrwertige Zeichenfolge bezeichnet werden, nehmen Sie zuerst den ersten Begriff vor, suchen Sie nach einem Treffer, und wenn Sie gefunden werden, ist der Vorgang abgeschlossen. Wenn nicht, fahren Sie mit der nächsten Zeichenfolge fort.  Reihenfolge wichtig. Die Darstellung der mehrwertigen Schlüsselwörter sollte die längste Zeichenfolge bis zur kürzesten Zeichenfolge sein.  Um dies im Fall von mehrwertigen Schlüsselwörtern zu überprüfen, sehen Sie sich die F1-Online-URL-Zeichenfolge an, die das ausgewählte Schlüsselwort enthält.

In Visual Studio 2012 haben wir absichtlich eine stärkere Teilung zwischen Online und offline vorgenommen, sodass die F1-Anforderung, wenn die Einstellung des Benutzers Online war, einfach direkt an den Online Abfragedienst auf MSDN weitergeleitet wurde, anstatt über den hilfebibliotheks-Agent weiterzuleiten, den wir in Visual Studio 2010 hatten. Wir verlassen uns dann auf den Status "Hersteller Inhalt installiert = true", um zu bestimmen, ob in diesem Kontext etwas anderes durchzuführen ist. Wenn der Wert true ist, führen wir diese Verarbeitungs-und Routing Logik aus, je nachdem, was Sie für Ihre Kunden unterstützen möchten. Bei "false" wechseln wir einfach zu MSDN. Wenn die Einstellung des Benutzers auf Local festgelegt ist, werden alle Aufrufe an die lokale Hilfe-Engine weitergeleitet.

F1-Flussdiagramm:

![F1-Fluss](../../extensibility/internals/media/f1flow.png "F1flow")

Wenn die Help Viewer-Standard Hilfe Inhaltsquelle auf Online (in Browser starten) festgelegt ist:

- Funktionen von Visual Studio-Partner (VSP) geben einen Wert an den F1-Eigenschaften Behälter (Eigenschaften Behälter Präfix. Schlüsselwort und Online-URL für das in der Registrierung gefundene Präfix): F1 sendet eine VSP-URL + Parameter an den Browser.

- Visual Studio-Funktionen (sprach-Editor, Visual Studio-spezifische Menü Elemente usw.): F1 sendet eine Visual Studio-URL an den Browser.

Wenn die Quelle Help Viewer-Standard Hilfe Inhalt auf lokale Hilfe (in Help Viewer starten) festgelegt ist:

- VSP-Funktionen, bei denen die Schlüsselwort Übereinstimmung zwischen F1-Eigenschaften Behälter und lokalem Speicher Index vorliegt (d. h. das Eigenschaften Behälter Präfix. Schlüsselwort = der im lokalen Speicher Index gefundene Wert): F1 rendert das Thema im Help Viewer.

- Visual Studio-Features (keine Option für den VSP zum Überschreiben des Eigenschaften Behälters, der von Visual Studio-Funktionen ausgegeben wird): F1 rendert ein Visual Studio-Thema im Help Viewer.

Legen Sie die folgenden Registrierungs Werte fest, um den F1-Fallback für den Anbieter Hilfe Inhalt zu aktivieren. Der F1-Fallback bedeutet, dass der Help Viewer auf die Online Suche nach F1-Hilfe Inhalten festgelegt ist und der Hersteller Inhalt lokal auf der Festplatte des Benutzers installiert ist. Der Help Viewer sollte sich die lokale Hilfe für den Inhalt ansehen, auch wenn die Standardeinstellung für die Online Hilfe gilt.

1. Legen Sie den **vendorcontent** -Wert unter dem Registrierungsschlüssel "Help 2,3" fest:

   - Für 32-Bit-Betriebssysteme:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "Vendorcontent" = DWORD: 00000001

   - Für 64-Bit-Betriebssysteme:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "Vendorcontent" = DWORD: 00000001

2. Registrieren Sie den Partner-Namespace unter dem Registrierungsschlüssel Help 2,3:

   - Für 32-Bit-Betriebssysteme:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em> \\<Namespace \> </em>

      "Location" = "Offline"

   - Für 64-Bit-Betriebssysteme:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em> \\<Namespace \> </em>

      "Location" = "Offline"

**Native Native Namespace-Verarbeitung**

Fügen Sie in der Registrierung ein neues DWORD mit dem Namen basenativenamespaces hinzu, und legen Sie seinen Wert auf 1 fest (unter dem Katalog Schlüssel, den Sie unterstützen möchten), um die grundlegende Native Namespace-Verarbeitung zu aktivieren.  Wenn Sie z. b. den Visual Studio-Katalog verwenden möchten, können Sie dem Pfad den Schlüssel hinzufügen:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Beim Auftreten eines F1-Schlüssel Worts im Format Header/der-Methode wird das Zeichen "/" analysiert, was zu folgendem Konstrukt führt:

- Header: ist der Namespace, der zur Registrierung in der Registrierung verwendet werden kann.

- Methode: Dies wird zum Schlüsselwort, das durchlaufen wird.

Wenn z. b. eine benutzerdefinierte Bibliothek mit dem Namen "CustomLibrary" und eine Methode namens "MyTestMethod" angegeben wird, wird die Formatierung als formatiert, wenn eine F1-Anforderung `CustomLibrary/MyTestMethod`

Ein Benutzer kann dann CustomLibrary als Namespace unter der Partnerstruktur registrieren und den gewünschten Speicherort Schlüssel bereitstellen, und das an die Abfrage weiter gegebene Schlüsselwort lautet MyTestMethod.

**Tool zum Debuggen von Hilfe in der IDE aktivieren**

Fügen Sie den folgenden Registrierungsschlüssel und-Wert hinzu:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Wert: Debugausgabe in Einzelhandelsdaten anzeigen: Ja

Wählen Sie in der IDE unter dem Menü Element Hilfe die Option **Debughilfe Kontext** aus.

**Inhalts Metadaten**

In der folgenden Tabelle ist jede Zeichenfolge, die zwischen eckigen Klammern steht, ein Platzhalter, der durch einen anerkannten Wert ersetzt werden muss. In \<meta name="Microsoft.Help.Locale" content="[language code]" /> muss "[Sprachcode]" z. b. durch einen Wert wie "en-US" ersetzt werden.

| Property (HTML-Darstellung) | BESCHREIBUNG |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Legt ein Gebiets Schema für dieses Thema fest. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden, und es muss über alle anderen Microsoft-Hilfe Tags eingefügt werden. Wenn dieses Tag nicht verwendet wird, wird der Textkörper des Themas mithilfe der Wörter Trennung indiziert, die dem Gebiets Schema des Produkts zugeordnet ist, sofern angegeben. Andernfalls wird die Wörter Trennung "en-US" verwendet. Dieses Tag entspricht der ISOC RFC 4646. Um sicherzustellen, dass die Microsoft-Hilfe ordnungsgemäß funktioniert, verwenden Sie diese Eigenschaft anstelle des allgemeinen sprach Attributs. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Legt ein Gebiets Schema für dieses Thema fest, wenn auch andere Gebiets Schemas verwendet werden. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Verwenden Sie dieses Tag, wenn der Katalog Inhalte in mehr als einer Sprache enthält. Mehrere Themen in einem Katalog können dieselbe ID aufweisen, aber jeder muss eine eindeutige topiclocale angeben. Das Thema, das ein topiclocale angibt, das mit dem Gebiets Schema des Katalogs übereinstimmt, ist das Thema, das im Inhaltsverzeichnis angezeigt wird. Allerdings werden alle Sprachversionen des Themas in den Suchergebnissen angezeigt. |
| \< title>Tel\</title> | Gibt den Titel dieses Themas an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Wenn der Hauptteil des Themas keinen Titel \<div> Abschnitt enthält, wird dieser Titel im Thema und im Inhaltsverzeichnis angezeigt. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Gibt den Text eines Links an, der im Index Bereich von Help Viewer angezeigt wird. Wenn auf den Link geklickt wird, wird das Thema angezeigt. Sie können mehrere Index Schlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn Sie nicht möchten, dass Links zu diesem Thema im Index angezeigt werden. "K"-Schlüsselwörter aus früheren Versionen der Hilfe können in diese Eigenschaft konvertiert werden. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Legt den Bezeichner für dieses Thema fest. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Die ID muss in den Themen im Katalog eindeutig sein, die über die gleiche Gebiets Schema Einstellung verfügen. In einem anderen Thema können Sie mithilfe dieser ID einen Link zu diesem Thema erstellen. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Gibt das F1-Schlüsselwort für dieses Thema an. Sie können mehrere F1-Schlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn Sie nicht möchten, dass dieses Thema angezeigt wird, wenn ein Anwendungs Benutzer F1 drückt. In der Regel wird nur ein F1-Schlüsselwort für ein Thema angegeben. F-Schlüsselwörter aus früheren Versionen der Hilfe können in diese Eigenschaft konvertiert werden. |
| \< meta name="Description" content="[topic description]" /> | Enthält eine kurze Zusammenfassung des Inhalts in diesem Thema. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Der Zugriff auf diese Eigenschaft erfolgt direkt über die Abfrage Bibliothek. Er wird nicht in der Indexdatei gespeichert. |
| Meta Name = "Microsoft. Help. decparent" Content = "[parent_Id]"/> | Gibt das übergeordnete Thema dieses Themas im Inhaltsverzeichnis an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist der Microsoft.Help.ID-Wert des übergeordneten Elements. Ein Thema kann nur einen Speicherort im Inhaltsverzeichnis enthalten. "-1" wird als Thema-ID für den TOC-Stamm angesehen. Auf [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] dieser Seite befindet sich die Help Viewer-Startseite. Dies ist der gleiche Grund, den wir speziell zu einigen Themen hinzufügen, um sicherzustellen, dass Sie auf der obersten Ebene angezeigt werden. Die Help Viewer-Startseite ist eine System Seite und somit nicht ersetzbar. Wenn ein VSP versucht, eine Seite mit der ID "-1" hinzuzufügen, wird diese möglicherweise dem Inhalts Satz hinzugefügt, der Help Viewer verwendet jedoch immer die Startseite des System Page-Help Viewers. |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Gibt an, wo im Inhaltsverzeichnis dieses Thema relativ zu seinen Peer Themen erscheint. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist eine ganze Zahl. Ein Thema, das eine ganze Zahl mit niedrigerer Wert angibt, wird oberhalb eines Themas angezeigt, das eine Ganzzahl mit höherem Wert angibt. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Gibt das Produkt an, das in diesem Thema beschrieben wird. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Diese Informationen können auch als Parameter bereitgestellt werden, der an den Hilfe Indexer übergeben wird. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Gibt die Version des Produkts an, das in diesem Thema beschrieben wird. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Diese Informationen können auch als Parameter bereitgestellt werden, der an den Hilfe Indexer übergeben wird. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Wird von Produkten verwendet, um Unterabschnitte von Inhalten zu identifizieren. Sie können mehrere Unterabschnitte für ein Thema identifizieren, oder Sie können dieses Tag weglassen, wenn Sie nicht möchten, dass die Unterabschnitte von Links identifiziert werden. Dieses Tag wird zum Speichern der Attribute für targetos und TargetFrameworkMoniker verwendet, wenn ein Thema aus einer früheren Version der Hilfe konvertiert wird. Das Format des Inhalts lautet AttributeName: AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Gibt diese Version des Themas an, wenn mehrere Versionen in einem Katalog vorhanden sind. Da Microsoft.Help.ID nicht unbedingt eindeutig ist, ist dieses Tag erforderlich, wenn mehr als eine Version eines Themas in einem Katalog vorhanden ist, z. b. Wenn ein Katalog ein Thema für den .NET Framework 3,5 und ein Thema für die .NET Framework 4 und beide denselben Microsoft.Help.ID-Wert enthält. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Gibt an, ob in diesem Thema das Start-Branding-Paket des Hilfe-Bibliotheks-Managers oder ein für das Thema spezifischer brandingpaket verwendet wird. Dieses Tag muss entweder "true" oder "false" lauten. Wenn dies der Fall ist, überschreibt das brandingpaket für das zugehörige Thema das brandingpaket, das beim Starten des hilfebibliotheks-Managers festgelegt wird, damit das Thema auch dann wie vorgesehen gerendert wird, wenn es sich vom Rendering anderer Inhalte unterscheidet. Wenn der Wert false ist, wird das aktuelle Thema entsprechend dem brandingpaket gerendert, das beim Starten des hilfebibliotheks-Managers festgelegt wird. Standardmäßig geht der hilfebibliotheks-Manager davon aus, dass das Self-Branding false ist, es sei denn, die Variable selfbranding ist als true deklariert Daher müssen Sie nicht deklarieren \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Erstellen eines Branding-Pakets

Die Visual Studio-Version umfasst eine Reihe von unterschiedlichen Visual Studio-Produkten, einschließlich isolierter und integrierter Shells für Visual Studio-Partner.  Jedes dieser Produkte erfordert einen gewissen Grad an Themen basiertem Branding-Support, der für das Produkt eindeutig ist.  Beispielsweise müssen die Visual Studio-Themen eine konsistente Markenpräsentation aufweisen, während SQL Studio, das die ISO-Shell umschließt, für jedes Thema ein eigenes Branding von Hilfe Inhalten erfordert.  Ein integrierter shellpartner möchte, dass sich Ihre Hilfe Themen in den übergeordneten Visual Studio-Produkt Hilfe Inhalten befinden, während Sie ein eigenes Themen Branding erhalten.

Brandingpakete werden von dem Produkt installiert, das den Help Viewer enthält.  Für Visual Studio-Produkte:

- Ein Fall Back-brandingpaket (Branding_ \<locale> . mshc) wird 2,3 im Help Viewer-App-Stamm installiert (Beispiel: c:\Programme (x86) \Microsoft Help viewer\v2.3).  Diese Option wird für Fälle verwendet, in denen das Produkt Branding-Paket nicht installiert ist (es wurden keine Inhalte installiert) oder wenn das installierte brandingpaket beschädigt ist.  Die Visual Studio-Elemente (Logo und Feedback) werden bei Verwendung des App-Stamm-Fall Back-Branding-Pakets ignoriert.

- Wenn Visual Studio-Inhalt aus dem Inhalts Paketdienst installiert wird, wird auch ein Branding-Paket installiert (zum ersten Mal ein Inhalts Installationsszenario).  Wenn ein Update für das brandingpaket vorliegt, wird das Update installiert, wenn die nächste Aktion zum Aktualisieren des Inhalts oder einer zusätzlichen Paketinstallation durchgeführt wird.

Der Microsoft Help Viewer unterstützt das Branding von Themen auf der Grundlage von Themen Metadaten.

- Where Topic Metadata definiert selbst Branding = true, gibt das Thema unverändert an, Do Nothing (soweit Branding).

- Wenn Topic-Metadaten selbst Branding = false definieren, verwenden Sie das dem TopicVendor-Metadatenwert zugeordnete Branding-Paket.

- Wenn Topic Metadata Name = "Microsoft. Help. TopicVendor" Content = definiert \< branding package name in vendor MSHA> , verwenden Sie das im Inhalts Wert definierte Branding-Paket.

- Im Visual Studio-Katalog gibt es eine Prioritäts Anwendung von Branding-Paketen.  Zuerst wird das Standard Branding von Visual Studio angewendet. Anschließend wird das Hersteller definierte Branding als außer Kraft Setzung angewendet, wenn es im Thema Metadaten definiert und mit dem zugeordneten Branding-Paket unterstützt wird (wie in der MSHA-Installation definiert).

Brandingelemente werden in der Regel in drei Hauptkategorien unterteilt:

- Header Elemente (Beispiele: Feedback Link, bedingter Ausschluss Text, Logo)

- Inhalts Verhalten (Beispiele hierfür sind Steuerelement Textelemente erweitern/reduzieren und Code Ausschnitt Elemente)

- Footer-Elemente (Beispiel Copyright)

Elemente, die als Markenelemente angesehen werden, sind u.a. (in dieser Spezifikation ausführlich):

- Katalog-/Produktlogo (z. b. Visual Studio)

- Feedback Link und e-Mail-Elemente

- Ausschluss Text

- Copyright Text

Zu den unterstützenden Dateien im Visual Studio Help Viewer-Branding-Paket gehören:

- Grafiken (Logos, Symbole usw.)

- Branding.js-Skriptdateien, die Inhalts Verhalten unterstützen

- Branding.xml Zeichen folgen, die konsistent über Katalog Inhalte hinweg verwendet werden.  Hinweis: Schließen Sie für Visual Studio-Lokalisierungs Textelemente in der branding.xml _locID = "" ein. \<unique value>

- Branding. CSS-Definitionen für die Präsentations Konsistenz

- Drucken von CSS-Definitionen für eine konsistente gedruckte Darstellung

Wie bereits erwähnt, werden Branding-Pakete mit dem Thema verknüpft:

- Wenn selfbranding = false in den Metadaten definiert ist, erbt das Thema das Katalog Branding-Paket.

- Oder wenn selfbranding = false ist und ein eindeutiges brandingpaket im MSHA definiert ist und verfügbar ist, wenn der Inhalt installiert ist.

Für VSPs, die benutzerdefinierte Branding-Pakete (VSP-Inhalt, selfbranding = true) implementieren, besteht die Möglichkeit, mit dem Fall Back-Branding-Paket (installiert mit Help Viewer) zu beginnen und den Namen der Datei nach Bedarf zu ändern.  Bei der Datei "Branding_ \<locale> . mshc" handelt es sich um eine ZIP-Datei, bei der die Dateierweiterung in ". mshc" geändert wurde. ändern Sie also einfach die Erweiterung von ". mshc" in ". zip"  Siehe unten für brandingpaketelemente und ändern nach Bedarf (ändern Sie z. b. das Logo in das VSP-Logo und den Verweis auf das Logo in der Branding.xml-Datei, aktualisieren Sie Branding.xml pro VSP-Details usw.).

Wenn alle Änderungen vorgenommen wurden, erstellen Sie eine ZIP-Datei, die die gewünschten Brandingelemente enthält, und ändern Sie die Erweiterung in. mshc.

Um das benutzerdefinierte brandingpaket zuzuordnen, erstellen Sie das MSHA, das den Verweis auf die mshc-Branding-Datei sowie den Content mshc (enthält die Themen) enthält.  Weitere Informationen zum Erstellen eines einfachen MSHA finden Sie unter "MSHA".

Die Branding.xml Datei enthält eine Liste von Elementen, die für das konsistente Rendering bestimmter Elemente in einem Thema verwendet werden, wenn das Thema enthält \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Die Visual Studio-Liste der Elemente in der Branding.xml-Datei ist unten aufgeführt.  Diese Liste ist für die Verwendung als Vorlage für ISO-shellanwender gedacht, in denen Sie diese Elemente (z. b. Logo, Feedback und Copyright) ändern, um Ihre eigenen produkttbrandinganforderungen zu erfüllen.

Hinweis: die von "{n}" notierten Variablen weisen Code Abhängigkeiten auf. Wenn Sie diese Werte entfernen oder ändern, werden Fehler und möglicherweise Anwendungs Abstürze verursacht. Lokalisierungs Bezeichner (z. b. _locID = "CodeSnippet. n") sind im Visual Studio-Branding-Paket enthalten.

**Branding.xml**

| Element | BESCHREIBUNG |
| - | - |
| Feature: | **Redusiblearea** |
| Verwendung: | Erweitern des Inhalts Steuer Elements "reduziert" |
| **Element** | **Wert** |
| Expandtext | Expand |
| Reduzierungs Text | Reduzieren |
| Feature: | **CodeSnippet** |
| Verwendung: | Code Ausschnitt-Steuerelement Text.  Hinweis: Code Ausschnitt Inhalt mit "nicht unterbrechenden" Speicherplatz wird in "Space" geändert. |
| **Element** | **Wert** |
| Copyum-Zwischenablage | In Zwischenablage kopieren |
| Viewcolorizedtext | Farbige Ansicht |
| Combinedvbtabdisplaylanguage | Visual Basic (Beispiel) |
| Vbdeclaration | Deklaration |
| Vbusage | Verwendung |
| Feature: | **Feedback, Fußzeile und Logo** |
| Verwendung: | Stellen Sie ein Feedback-Steuerelement bereit, mit dem Kundenfeedback zum aktuellen Thema per e-Mail senden können.  Copyright Text für den Inhalt.  Logo Definition. |
| **Element** | **Value (diese Zeichen folgen können so geändert werden, dass Sie die Anforderungen der Inhalts Adoption erfüllen.)** |
| Copyright | © 2013 Microsoft Corporation. Alle Rechte vorbehalten. |
| Sendfeedback | \<a href="{0}" {1}>Senden Sie Feedback \</a> zu diesem Thema an Microsoft. |
| Feedback Link | |
| Logotitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| Dateiname | vs_logo_bk.gif |
| Ablogodatamehc | vs_logo_wh.gif |
| Feature: | **ERS** |
| Verwendung: | Ein Satz von Fall spezifischen Haftungsausschlüsse für maschinell übersetzte Inhalte. |
| **Element** | **Wert** |
| MT_Editable | Dieser Artikel war maschinell übersetzt. Wenn Sie über eine Internet Verbindung verfügen, wählen Sie "dieses Thema Online anzeigen" aus, um diese Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_NonEditable | Dieser Artikel war maschinell übersetzt. Wenn Sie über eine Internet Verbindung verfügen, wählen Sie "dieses Thema Online anzeigen" aus, um diese Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_QualityEditable | Dieser Artikel wurde manuell übersetzt. Wenn Sie über eine Internet Verbindung verfügen, wählen Sie "dieses Thema Online anzeigen" aus, um diese Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_QualityNonEditable | Dieser Artikel wurde manuell übersetzt. Wenn Sie über eine Internet Verbindung verfügen, wählen Sie "dieses Thema Online anzeigen" aus, um diese Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_BetaContents | Dieser Artikel war maschinell übersetzt für eine vorläufige Version. Wenn Sie über eine Internet Verbindung verfügen, wählen Sie "dieses Thema Online anzeigen" aus, um diese Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_BetaRecycledContents | Dieser Artikel wurde manuell für eine vorläufige Version übersetzt. Wenn Sie über eine Internet Verbindung verfügen, wählen Sie "dieses Thema Online anzeigen" aus, um diese Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| Feature: | **LinkTable** |
| Verwendung: | Unterstützung für Online Themen Links |
| **Element** | **Wert** |
| Linktabletitle | Link Tabelle |
| Topicenulinktext | Sehen Sie sich die englische Version \</a> dieses Themas an, die auf Ihrem Computer verfügbar ist. |
| Topiconlinelinktext | Dieses Thema \<a href="{0}" {1}> Online anzeigen\</a> |
| Online Text | Online |
| Feature: | **Videoaudiosteuerelement** |
| Verwendung: | Anzeigen von Elementen und Text für Videoinhalte |
| **Element** | **Wert** |
| Multimedianotsupported | Zur Unterstützung von Inhalten muss Internet Explorer 9 oder höher installiert sein {0} . |
| Videotext | Anzeigen von Videos |
| Audiotext | Streaming-Audiodaten |
| Onlinevideolinktext | \<p>Um das Video anzuzeigen, das diesem Thema zugeordnet ist, klicken Sie {0} \<a href="{1}"> {2} hier \</a> .\</p> |
| Onlineaudiolinktext | \<p>Klicken Sie hier, um die diesem Thema zugeordneten Audiodaten zu überwachen {0} \<a href="{1}"> {2} \</a> .\</p> |
| Feature: | **Steuerelement "Inhalt nicht installiert"** |
| Verwendung: | Text Elemente (Zeichen folgen), die für das Rendering von contentnotinstalled.htm verwendet werden |
| **Element** | **Wert** |
| Contentnotinstalledtitle | Auf Ihrem Computer wurde kein Inhalt gefunden. |
| Contentnotinstalleddownloadcontenttext | \<p>Um Inhalte auf Ihren Computer herunterzuladen, \<a href="{0}" {1}> Klicken Sie auf die Registerkarte verwalten \</a> .\</p> |
| Contentnotinstalledtext | \<p>Auf Ihrem Computer ist kein Inhalt installiert. Informationen zur Installation lokaler Hilfe Inhalte finden Sie unter Administrator.\</p> |
| Feature: | **Steuerelement wurde nicht gefunden.** |
| Verwendung: | Text Elemente (Zeichen folgen), die für das Rendering von topicnotfound.htm verwendet werden |
| **Element** | **Wert** |
| TopicNotFoundTitle | Das angeforderte Thema wurde auf Ihrem Computer nicht gefunden. |
| TopicNotFoundViewOnlineText | \<p>Das von Ihnen angeforderte Thema wurde auf Ihrem Computer nicht gefunden, aber Sie können \<a href="{0}" {1}> das Thema Online anzeigen \</a> .\</p> |
| TopicNotFoundDownloadContentText | \<p>Links zu ähnlichen Themen finden Sie im Navigationsbereich, oder \<a href="{0}" {1}> Klicken Sie auf die Registerkarte verwalten, \</a> um Inhalte auf Ihren Computer herunterzuladen.\</p> |
| TopicNotFoundText | \<p>Das von Ihnen angeforderte Thema wurde auf Ihrem Computer nicht gefunden.\</p> |
| Feature: | **Beschädigtes Steuerelement** |
| Verwendung: | Text Elemente (Zeichen folgen), die für das Rendering von topiccorrupted.htm verwendet werden |
| **Element** | **Wert** |
| TopicCorruptedTitle | Das angeforderte Thema kann nicht angezeigt werden. |
| TopicCorruptedViewOnlineText | \<p>Help Viewer kann das angeforderte Thema nicht anzeigen. Möglicherweise ist ein Fehler im Inhalt des Themas oder eine zugrunde liegende System Abhängigkeit aufgetreten.\</p> |
| Feature: | **Startseiten-Steuerelement** |
| Verwendung: | Text, der die Anzeige des Inhalts der obersten Ebene des Help Viewer-Knotens unterstützt. |
| **Element** | **Wert** |
| HomePageTitle | Help Viewer-Startseite |
| HomePageIntroduction | \<p>Willkommen bei der Microsoft Help Viewer, einer wichtigen Informationsquelle für alle, die Microsoft-Tools,-Produkte,-Technologien und-Dienste verwenden. Der Help Viewer bietet Ihnen Zugriff auf Anleitungen und Referenzinformationen, Beispielcode, technische Artikel und vieles mehr. Um den benötigten Inhalt zu finden, Durchsuchen Sie das Inhaltsverzeichnis, verwenden Sie die Volltextsuche, oder navigieren Sie mithilfe des Schlüsselwort Indexes durch Inhalt.\</p> |
| Homepagecontentinstalltext | \<p>\<br />Verwenden Sie die \<a href="{0}" {1}> \</a> Registerkarte Inhalt verwalten, um Folgendes zu tun: \<ul> \<li> Hinzufügen von Inhalt zu Ihrem Computer. \</li> \<li> Suchen Sie nach Updates für Ihren lokalen Inhalt. \</li> \<li> Entfernen Sie Inhalt von Ihrem Computer.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Installierte Bücher |
| HomePageNoBooksInstalled | Auf Ihrem Computer wurde kein Inhalt gefunden. |
| Homepagehelpsettings | Hilfe Inhaltseinstellungen |
| Homepagehelpsettingstext | \<p>Die aktuelle Einstellung ist die lokale Hilfe. In Help Viewer werden Inhalte angezeigt, die Sie auf Ihrem Computer installiert haben. \<br /> Um die Quelle des Hilfe Inhalts zu ändern, wählen Sie in der Visual Studio-Menüleiste \<span style="{0}"> Hilfe aus, und legen Sie Hilfe Einstellung fest \</span> .\<br />\</p> |
| Megabyte | MB |

**branding.js**

Die branding.js Datei enthält JavaScript, das von den Visual Studio Help Viewer-Branding-Elementen verwendet wird.  Im folgenden finden Sie eine Liste der Brandingelemente und der unterstützenden JavaScript-Funktion.  Alle Zeichen folgen, die für diese Datei lokalisiert werden sollen, werden im Abschnitt "lokalisierbare Zeichen folgen" oben in dieser Datei definiert.  Die ICL-Datei wurde für LOC-Zeichen folgen in der branding.js-Datei erstellt.

|**Brandingfeature**|**JavaScript-Funktion**|**Beschreibung**|
|-|-|-|
|Var...||Definieren von Variablen|
|Benutzercode Sprache|setuserpreferendcelang|ordnet einen Index # der Codesprache zu.|
|Festlegen und erhalten von Cookie-Werten|GetCookie, setcookie||
|Vererbte Member|changemembership-Bezeichnung|Vererbten Member erweitern/reduzieren|
|Wenn selfbranding = false|onLoad|Lesen Sie die Abfrage Zeichenfolge, um zu prüfen, ob Sie eine Druck Anforderung ist.  Legen Sie alle CodeSnippets fest, um die Benutzer bevorzugte Registerkarte zu fokussieren.  Wenn es sich um eine Druck Anforderung handelt, legen Sie isprinterfriendly auf true fest. Überprüfen Sie den Modus für hohe Kontraste.|
|Beispiele|addspecifictextlanguagetagset||
||getindexfromdevlang||
||Changetab||
||setcodesnippetlang||
||setcurrentlang||
||Copyum-Zwischenablage||
|Redusiblearea|addtredusiblecontrolset|Schreiben Sie das gesamte redusible-Steuerelement Objekt in die Liste.|
||CA_Click|definiert basierend auf dem Zustand des Reduzierungs Bereichs, welches Bild und welcher Text vorhanden sein müssen.|
|Kontrast Unterstützung für Logo|isblackbackground ()|Wird aufgerufen, um zu bestimmen, ob background schwarz ist.  Nur im Modus für hohe Kontraste genau.|
||ishighcontrast ()|Verwenden einer farbigen Spanne zum Erkennen des Modus für hohe Kontraste|
||onhighcontrast (schwarz)|Aufruf erfolgt, wenn ein hoher Kontrast erkannt wird.|
|LST-Funktionalität|||
||addtolanspectextidset (ID)||
||updatelst (currentlang)||
||getdevlangfromcodesnippet (lang)||
|Multimedia-Funktionalität|Beschriftung (Anfang, Ende, Text, Format)||
||findallmediacontrols (normalizedid)||
||getactiveplayer (normalizedid)||
||captionsonoff (ID)||
||Minuten (t)||
||getallcomments (Knoten)||
||stylerectify (styleName, stylevalue)||
||showcc (ID)||
||Untertitel (ID)||

**HTM-Dateien**

Das Branding-Paket enthält eine Reihe von htm-Dateien, die Szenarien für die Kommunikation von Schlüsselinformationen zur Unterstützung von Inhalts Benutzern unterstützen, z. b. eine Startseite, die einen Abschnitt enthält, in dem beschrieben wird, welche Inhalts Sätze installiert werden, und Seiten, die dem Benutzer mitteilen, wenn Themen in der lokalen Diese HTM-Dateien können pro Produkt geändert werden.  ISO-Shell-Anbieter können das standardmäßige brandingpaket übernehmen und das Verhalten und den Inhalt dieser Seiten ändern, um Ihre Anforderungen zu erfassen.  Diese Dateien verweisen auf das jeweilige brandingpaket, damit die brandingtags den entsprechenden Inhalt aus der branding.xml Datei erhalten.

|**File**|**Verwenden Sie**|**Quelle der angezeigten Inhalte**|
|-|-|-|
|homepage.htm|Dies ist eine Seite, auf der der aktuell installierte Inhalt und jede andere Meldung angezeigt wird, die dem Benutzer für seinen Inhalt zur Verfügung steht.  Diese Datei enthält das zusätzliche Meta-Daten Attribut "Microsoft.Help.ID" Content = "-1", mit dem dieser Inhalt am oberen Rand des lokalen Inhalts Inhaltsverzeichnis platziert wird.||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml, Tag \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml, Tag \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml, Tag \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Überschriften Abschnitt Branding.xml Tag \<HomePageInstalledBooks> , die von der Anwendung generierten Daten,  \<HomePageNoBooksInstalled> Wenn keine Bücher installiert werden.|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|Überschriften Abschnitt Branding.xml-Tags \<HomePageHelpSettings> , Abschnitts Text \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Wenn ein Thema in der lokalen Gruppe vorhanden ist, kann jedoch aus irgendeinem Grund nicht angezeigt werden (beschädigter Inhalt).||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml, Tag \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml, Tag \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Wenn ein Thema nicht im lokalen Inhalts Satz gefunden wird oder online verfügbar ist||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml, Tag \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml, Tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml, Tag \<TopicNotFoundText>|
|contentnotinstalled.htm|Wenn kein lokaler Inhalt für das Produkt installiert ist.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml, Tag \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml, Tag \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml, Tag \<ContentNotInstalledText>|

**CSS-Dateien**

Das Visual Studio Help Viewer-Branding-Paket enthält zwei CSS-Dateien zur Unterstützung der konsistenten Darstellung von Visual Studio-Hilfe Inhalten:

- Branding. CSS: enthält CSS-Elemente für das Rendering, wenn selfbranding = false

- Printer. CSS: enthält CSS-Elemente für das Rendering, wenn selfbranding = false

Branding. CSS-Dateien enthalten Definitionen für die Visual Studio-Themen Präsentation (Beachten Sie, dass sich das Branding. CSS, das in der Branding_ \<locale> . mshc aus dem Paketdienst enthalten ist, möglicherweise ändert).

**Grafikdateien**

Visual Studio-Inhalt zeigt ein Visual Studio-Logo und andere Grafiken an.  Die komplette Liste der Grafikdateien im Visual Studio Help Viewer-Branding-Paket ist unten dargestellt.

|**File**|**Verwenden Sie**|**Beispiele**|
|-|-|-|
|clear.gif|Wird zum Rendering des redusible-Bereichs verwendet.||
|footer_slice.gif|Footer-Präsentation||
|info_icon.gif|Wird beim Anzeigen von Informationen verwendet.|Haftungsausschluss|
|online_icon.gif|Dieses Symbol muss Online Verknüpfungen zugeordnet werden.||
|tabLeftBD.gif|Wird verwendet, um den Code Ausschnitt Container zu Rendering.||
|tabRightBD.gif|Wird verwendet, um den Code Ausschnitt Container zu Rendering.||
|vs_logo_bk.gif|Wird für normale Kontrast-Logo-Verweise verwendet, wie in Branding.xml Tag definiert \<LogoFileName> .  Für Visual Studio-Produkte wird der logoname vs_logo_bk.gif.||
|vs_logo_wh.gif|Wird für normale High-Logo-Verweise verwendet, wie in Branding.xml Tag definiert \<LogoFileNameHC> .  Für Visual Studio-Produkte wird der logoname vs_logo_wh.gif.||
|ccOff.png|Grafik zum Beschriftungen||
|ccOn.png|Grafik zum Beschriftungen||
|ImageSprite.png|Wird zum Rendering des redusible-Bereichs verwendet.|Grafik zu erweitert oder zuklappen|

## <a name="deploy-a-set-of-topics"></a>Bereitstellen von Themen

Dies ist ein einfaches und kurzes Tutorial zum Erstellen eines Help Viewer-Inhalts Bereitstellungs Satzes, der aus einer MSHA-Datei und der Gruppe von Cabs oder mshcs besteht, die die Themen enthalten. Das MSHA ist eine XML-Datei, die eine Gruppe von Cabs-oder mshc-Dateien beschreibt. Der Help Viewer kann das MSHA lesen, um eine Liste von Inhalten (das zu erhalten. CAB oder. Mshc-Dateien) für die lokale Installation verfügbar.

Dies ist nur eine Einführung, die das grundlegende XML-Schema für den Help Viewer-MSHA beschreibt.  Unter dieser kurzen Übersicht und in der Beispieldatei "helpcontentsetup. MSHA" finden Sie eine Beispiel Implementierung.

Der Name des MSHA ist für diese Einführung "helpcontentsetup. MSHA" (der Name der Datei kann beliebig sein, mit der Erweiterung). MSHA). Helpcontentsetup. MSHA (Beispiel unten) sollte eine Liste der verfügbaren Cabs oder mshcs enthalten.  Der Dateityp muss innerhalb des MSHA konsistent sein (eine Kombination von MSHA-und CAB-Dateitypen wird von nicht unterstützt). Für jede CAB-Datei oder mshc-Datei sollte eine \<div class="package"> ... \</div> (siehe Beispiel unten) vorhanden sein.

Hinweis: im folgenden Implementierungs Beispiel ist das Branding-Paket enthalten. Dies ist wichtig, um die erforderlichen Visual Studio-inhaltsrenderingelemente und das Inhalts Verhalten zu erhalten.

Beispieldatei "helpcontentsetup. MSHA": (ersetzen Sie "Inhalts Satz Name 1" und "Inhalts Satz Name 2" usw. durch ihre Dateinamen.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. Erstellen Sie einen lokalen Ordner, z. b. "c:\samplecontent".

2. In diesem Beispiel werden mshc-Dateien verwendet, um die Themen zu enthalten.  Ein mshc ist eine ZIP-Datei, bei der die Dateierweiterung von zip in geändert wurde. MSHC.

3. Erstellen Sie die folgende Datei "helpcontentsetup. MSHA" als Textdatei (Notepad wurde verwendet, um die Datei zu erstellen), und speichern Sie Sie im oben angegebenen Ordner (siehe Schritt 1).

Die Klasse "Branding" ist vorhanden und eindeutig. Das Branding-mshc ist in dieser Einführung enthalten, sodass der installierte Inhalt das Branding hat und die in den mshcs enthaltenen Inhalts Verhalten die entsprechenden Unterstützungs Elemente enthalten, die im brandingpaket enthalten sind. Ohne diesen Fehler treten Fehler auf, wenn das System nach Unterstützungs Elementen sucht, die nicht Teil des aufgerissen (installierten) Inhalts sind.

Zum Abrufen des Visual Studio-Branding-Pakets kopieren Sie Branding_en-US. mshc-Datei unter "c:\Programme (x86) \Microsoft Help viewer\v2.3 \" in Ihren Arbeitsordner.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**Zusammenfassung**

Wenn Sie die oben beschriebenen Schritte verwenden und erweitern, kann VSPs ihre Inhalts Sätze für den Visual Studio Help Viewer bereitstellen.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Hinzufügen von Hilfe zur Visual Studio Shell (integriert und isoliert)

**Introduction (Einführung)**

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie Hilfe Inhalte in eine Visual Studio Shell-Anwendung integrieren und dann bereitstellen.

**Anforderungen**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 isolierter shellredist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Übersicht**

Die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell ist eine Version der [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE, auf der Sie eine Anwendung aufbauen können. Solche Anwendungen enthalten die isolierte Shell und die von Ihnen erstellten Erweiterungen. Verwenden Sie isolierte shellprojektvorlagen, die im SDK enthalten sind [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] , zum Erstellen von Erweiterungen.

Die grundlegenden Schritte zum Erstellen einer isolierten shellbasierten Anwendung und ihrer Hilfe:

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Rufen Sie die weitervertreibbare ISO Shell-Datei ab (ein Microsoft-Download).

2. Erstellen Sie in Visual Studio eine Hilfe Erweiterung, die auf der isolierten Shell basiert, z. b. der Hilfe Erweiterung von "sutoso", die weiter unten in dieser exemplarischen Vorgehensweise beschrieben wird.

3. Wrappen der Erweiterung und der verteilbaren ISO-Shell in eine Bereitstellungs-MSI (Anwendungs Einrichtung). Diese exemplarische Vorgehensweise enthält keinen Setup Schritt.

Erstellen Sie einen Visual Studio-Inhalts Speicher. Ändern Sie für das integrierte shellszenario Visual Studio12 wie folgt in den Namen des Produktkatalogs:

- Create Folder c:\programdata\microsoft\helplibrary2\catalogs\visualstudio15.

- Erstellen Sie eine Datei mit dem Namen CatalogType.xml, und fügen Sie Sie dem Ordner hinzu. Die Datei sollte die folgenden Codezeilen enthalten:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Hiermit wird der Inhalts Speicher in der Registrierung definiert. Ändern Sie VisualStudio15 für die integrierte Shell in den Namen des Produktkatalogs:

- Hklm\software\wow6432node\microsoft\help\v2.3 \catalogs\visualstudio15

   Key: locationpath Zeichen folgen Wert: c:\programdata\microsoft\helplibrary2\catalogs\visualstudio15\

- Hklm\software\wow6432node\microsoft\help\v2.3 \catalogs\visualstudio15\en-US

   Key: CatalogName Zeichen folgen Wert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation

**Erstellen des Projekts**

So erstellen Sie eine isolierte Shellerweiterung:

1. Wählen Sie in Visual Studio **unter Datei** die Option **Neues Projekt** aus, wählen Sie unter **andere Projekttypen** die Option **Erweiterbarkeit** aus, und wählen Sie dann die Option  **Visual Studio Shell isoliert** aus. Benennen Sie das Projekt `ContosoHelpShell` ), um ein Erweiterbarkeits Projekt zu erstellen, das auf der Vorlage für isolierte Shell von Visual Studio basiert.

2. Öffnen Sie in Projektmappen-Explorer im Projekt contosohelpshellui im Ordner Ressourcen Dateien die Datei "ApplicationCommands. vsct". Stellen Sie sicher, dass diese Zeile auskommentiert ist (suchen Sie nach "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Drücken Sie F5, um das **Debuggen** zu kompilieren und auszuführen. Wählen Sie in der experimentellen Instanz der isolierten Shell-IDE das Menü **Hilfe** aus. Stellen Sie sicher, dass die Befehle Hilfe **anzeigen**, **Hilfe Inhalt hinzufügen und entfernen** und **Hilfe Einstellung festlegen** angezeigt werden.

4. Öffnen Sie in Projektmappen-Explorer im Projekt contoshelpshell im Ordner shellanpassung die Datei contosohelpshell. pkgdef. Fügen Sie die folgenden Zeilen hinzu, um den Hilfe Katalog von "Configuration Manager" zu definieren:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Öffnen Sie in Projektmappen-Explorer im Projekt contoshelpshell im Ordner shellanpassung die Datei contosohelpshell. Application. pkgdef. Fügen Sie die folgenden Zeilen hinzu, um die F1-Hilfe zu aktivieren:

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. Wählen Sie in Projektmappen-Explorer im Kontextmenü der Projekt Mappe condesohelpshell das Menü Element **Eigenschaften** aus. Wählen Sie unter **Konfigurations Eigenschaften** die Option **Configuration Manager** aus. Ändern Sie in der Spalte **Konfiguration** jeden "Debug"-Wert in "Release".

7. Erstellen Sie die Projektmappe. Dadurch wird ein Satz von Dateien in einem releaseordner erstellt, der im nächsten Abschnitt verwendet wird.

So testen Sie dies wie bei Bereitstellung:

1. Installieren Sie auf dem Computer, auf dem Sie "Configuration Manager" bereitstellen, die ISO-Shell (von oben) heruntergeladen.

2. Erstellen Sie einen Ordner in \\ \Programme (x86) \\ , und benennen Sie ihn `Contoso` .

3. Kopieren Sie den Inhalt aus dem Ordner "condesohelpshell" in den \\ Ordner "\Program Files (x86) \condeso\".

4. Starten Sie den Registrierungs-Editor, indem Sie im **Startmenü** **Ausführen** und eingeben `Regedit` . Klicken Sie im Registrierungs-Editor auf **Datei** und dann auf **importieren**. Navigieren Sie zum Projektordner Conto sohelpshell. Wählen Sie im Unterordner conum sohelpshell den Eintrag Conto sohelpshell. reg aus.

5. Erstellen Sie einen Inhalts Speicher:

    Für ISO-Shell: Erstellen Sie einen condeso-Inhalts Speicher "c:\programdata\microsoft\helplibrary2\catalogs\condesodev12".

    Erstellen Sie für die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] integrierte Shell den Ordner c:\programdata\microsoft\helplibrary2\catalogs\visualstudio15.

6. Erstellen Sie CatalogType.xml, und fügen Sie dem Inhalts Speicher (vorheriger Schritt) Folgendes hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Fügen Sie die folgenden Registrierungsschlüssel hinzu:

    Hklm\software\wow6432node\microsoft\help\v2.3 \catalogs\visualstudio15key: locationpath Zeichen folgen Wert:

    Für ISO-Shell:

    C:programdatamikrosofthelplibrary2catalogsvisualstudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrierte Shell:

    C:programdatamikrosofthelplibrary2catalogsvisualstudio15de-US

    Key: CatalogName Zeichen folgen Wert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation. Bei ISO Shell ist dies der Name Ihres Katalogs.

8. Kopieren Sie Ihre Inhalte (Cabs oder mshc und MSHA) in einen lokalen Ordner.

9. Beispiel für eine integrierte Shell-Befehlszeile zum Testen des Inhalts Stores. Ändern Sie für die ISO-Shell die Werte für Catalog und launchingapp entsprechend dem Produkt entsprechend.

     "C:\Programme (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/CatalogName. VisualStudio15/helpQuery Method = "page&ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

10. Starten Sie die Anwendung "appto" (über den Stamm der APP-Stamm Anwendung). Wählen Sie in der ISO-Shell das Menü Element **Hilfe** aus, und ändern Sie die **Einstellung Hilfe Einstellung festlegen** , um **lokale Hilfe zu verwenden**.

11. Wählen Sie in der Shell das Menü Element **Hilfe** aus, und klicken Sie dann **auf Hilfe anzeigen**. Der lokale Help Viewer sollte starten. Wählen Sie die Registerkarte **Inhalt verwalten** aus. Wählen Sie unter **Installationsquelle** das **options** Feld Datenträger aus. Wählen Sie die Schaltfläche **...** aus, und navigieren Sie zum lokalen Ordner, der den Inhalt von "Configuration Manager" enthält (im obigen Schritt in den lokalen Ordner kopiert). Wählen Sie die Datei helpcontentsetup. MSHA aus. "Configuration Manager" sollte nun in der Buchauswahl als Buch angezeigt werden. Wählen Sie **Hinzufügen** aus, und klicken Sie dann auf die Schaltfläche **Aktualisieren** (unten rechts).

12. Wählen Sie in der Configuration Manager-IDE die F1-Taste, um die F1-Funktionalität zu testen.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Informationen zur Laufzeit-API finden Sie unter [Windows-Hilfe-API](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Weitere Informationen zur Verwendung der Hilfe-API finden Sie unter [Help Viewer-Codebeispiele](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Sie können Featurevorschläge an die [Entwickler Community](https://aka.ms/feedback/suggest?space=8)senden.
