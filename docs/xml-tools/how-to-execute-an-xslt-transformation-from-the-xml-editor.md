---
title: Ausführen einer XSLT-Transformation
description: In diesem Artikel erfahren Sie, wie Sie den XML-Editor verwenden, um ein XSLT-Stylesheet mit einem XML-Dokument zu verknüpfen, eine XSLT-Transformation durchzuführen und die Ausgabe anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1c7165f301c82dfaf5aa066a3e15bd7ab244089
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399481"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Vorgehensweise: Ausführen einer XSLT-Transformation im XML-Editor

Mit dem XML-Editor können Sie einem XML-Dokument ein XSLT-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

Die **Output**-Eigenschaft gibt den Dateinamen für die Ausgabe an. Wenn die **Output**-Eigenschaft leer ist, wird der Dateiname in einem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf dem `xsl:output`-Element in Ihrem Stylesheet und kann *XML*, *TXT* oder *HTM* sein.

Wenn in der **Output**-Eigenschaft ein Dateiname mit einer *HTM*- oder *HTML*-Erweiterung angegeben ist, wird eine Vorschau der XSLT-Ausgabe mit einem Webbrowser angezeigt. Bei allen anderen Dateierweiterungen wird der von Visual Studio ausgewählte Standard-Editor verwendet. Bei Dateien mit der Erweiterung *XML* wird beispielsweise von Visual Studio der XML-Editor verwendet.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Ausführen einer XSLT-Transformation aus einer XML-Datei

1. Öffnen Sie ein XML-Dokument im XML-Editor.

2. Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.

    - Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Fügen Sie z. B. dem Dokumentprolog folgende Zeile hinzu: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`.

       - oder -

    - Fügen Sie mithilfe des Fenster **Eigenschaften** das XSLT-Stylesheet hinzu. Klicken Sie bei im Editor geöffneter XML-Datei mit der rechten Maustaste auf eine beliebige Stelle im Editor, und wählen Sie **Eigenschaften** aus. Klicken Sie im Fenster **Eigenschaften** auf das Feld **Stylesheet**, und wählen Sie die Schaltfläche zum Durchsuchen (...) aus. Wählen Sie das XSLT-Stylesheet aus, und wählen Sie dann **Öffnen** aus.

3. Wählen Sie auf der Menüleiste **XML** > **XSLT ohne Debuggen starten** aus. Oder drücken Sie auf **STRG**+**ALT**+**F5**.

   Die Ausgabe der XSLT-Transformation wird in einem neuen Dokumentfenster angezeigt.

   > [!NOTE]
   > Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Ausführen einer XSLT-Transformation aus einem XSLT-Stylesheet

1. Öffnen Sie ein XSLT-Stylesheet im XML-Editor.

2. Geben Sie im Fenster **Eigenschaften** des Dokuments im Feld **Eingabe** ein XML-Dokument an.

   > [!NOTE]
   > Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn beim Starten der XSLT-Transformation kein Dokument angegeben wurde, wird das Dialogfeld **Datei öffnen** angezeigt, und Sie können nun ein Dokument angeben.

3. Wählen Sie auf der Menüleiste **XML** > **XSLT ohne Debuggen starten** aus. Oder drücken Sie auf **STRG**+**ALT**+**F5**.

   Die Ausgabe der XSLT-Transformation wird in einem neuen Dokumentfenster angezeigt.

## <a name="specify-an-output-file-name"></a>Angeben eines Ausgabedateinamens

Sie können sowohl für XML- als auch für XSL-Dateien einen Ausgabedateinamen angeben. Öffnen Sie das Fenster **Eigenschaften**, und geben Sie im Feld **Ausgabe** einen Dateinamen an.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
