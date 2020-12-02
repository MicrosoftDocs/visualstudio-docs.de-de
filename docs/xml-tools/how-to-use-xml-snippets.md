---
title: Verwenden von XML-Ausschnitten
description: In diesem Artikel erfahren Sie, wie Sie Befehle im XML-Editor verwenden, um XML-Ausschnitte einzufügen oder ausgewählten Text mit einem XML-Ausschnitt zu umschließen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bebca3a27d11015388e45ff6839f446506e716c
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970611"
---
# <a name="how-to-use-xml-snippets"></a>Vorgehensweise: Verwenden von XML-Ausschnitten

Mithilfe der folgenden zwei Befehle im Kontextmenü des XML-Editors können Sie XML-Ausschnitte aufrufen. Mit dem Befehl **Codeausschnitt einfügen** wird der XML-Ausschnitt an der Cursorposition eingefügt. Der Befehl **Umschließen mit** veranlasst, dass der XML-Ausschnitt als Wrapper für den ausgewählten Text fungiert. Jeder XML-Ausschnitt verfügt über definierte Ausschnitttypen. Die Ausschnitttypen bestimmen, ob der Ausschnitt mit dem Befehl **Codeausschnitt einfügen**, mit dem Befehl **Umschließen mit** oder mit beiden Befehlen verfügbar ist.

Nachdem dem Editor der XML-Ausschnitt hinzugefügt wurde, werden alle editierbaren Felder in den Ausschnitten in gelber Farbe hervorgehoben, und der Cursor wird auf dem ersten editierbaren Feld platziert.

## <a name="insert-snippet"></a>Ausschnitt einfügen

In den folgenden Prozeduren wird beschrieben, wie auf den Befehl **Codeausschnitt einfügen** zugegriffen wird.

> [!NOTE]
> Der Befehl **Codeausschnitt einfügen** ist auch über die Tastenkombination (**STRG**+**K**, dann **STRG**+**X**) verfügbar.

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>So fügen Sie Ausschnitte über das Kontextmenü ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Klicken Sie mit der rechten Maustaste, und wählen Sie **Codeausschnitt einfügen** aus.

   Es wird eine Liste der verfügbaren XML-Ausschnitte angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **TAB-TASTE** oder die **EINGABETASTE**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>So fügen Sie Ausschnitte über das IntelliSense-Menü ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Zeigen Sie im Menü **Bearbeiten** auf **IntelliSense**, und klicken Sie dann auf **Codeausschnitt einfügen**.

   Es wird eine Liste der verfügbaren XML-Ausschnitte angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie **TAB** oder die **EINGABETASTE**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>So fügen Sie Ausschnitte über die „Wort vervollständigen“-Liste von IntelliSense ein:

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Beginnen Sie mit dem Eingeben des XML-Ausschnitts, der der Datei hinzugefügt werden soll. Wenn die automatische Vervollständigung aktiviert ist, wird die Wort vervollständigen-Liste von IntelliSense angezeigt. Wenn sie nicht angezeigt wird, drücken Sie **STRG**+**Leertaste**, um die Funktion zu aktivieren.

3. Wählen Sie den XML-Ausschnitt aus der Wort vervollständigen-Liste aus.

4. Drücken Sie **TAB** zweimal, um den XML-Ausschnitt aufzurufen.

> [!NOTE]
> Möglicherweise können XML-Ausschnitte in einigen Fällen nicht aufgerufen werden. Wenn Sie z. B. versuchen, ein `xs:complexType`-Element innerhalb eines `xs:element`-Knotens einzufügen, generiert der Editor keinen XML-Ausschnitt. Wenn ein `xs:complexType`-Element innerhalb eines `xs:element`-Knotens verwendet wird, sind die erforderlichen Attribute oder Unterelemente nicht vorhanden, sodass der Editor über keine Daten zum Einfügen verfügt.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>So fügen Sie Ausschnitte mithilfe von Abkürzungsnamen ein

1. Platzieren Sie den Cursor an der Stelle, an der der XML-Ausschnitt eingefügt werden soll.

2. Geben Sie im Editorbereich `<` ein.

3. Drücken Sie die **ESC-TASTE**, um die „Wort vervollständigen“-Liste von IntelliSense zu schließen.

4. Geben Sie den Verknüpfungsnamen des Ausschnitts ein, und drücken Sie **TAB**, um den XML-Ausschnitt aufzurufen.

## <a name="surround-with"></a>Umgeben mit

In den folgenden Prozeduren wird beschrieben, wie auf den Befehl **Umschließen mit** zugegriffen wird.

> [!NOTE]
> Der Befehl **Umschließen mit** ist auch über die Tastenkombination (**STRG**+**K**, anschließend **STRG**+**S**) verfügbar.

### <a name="to-use-surround-with-from-the-context-menu"></a>So verwenden Sie „Umschließen mit“ über das Kontextmenü:

1. Wählen Sie den Text aus, der im XML-Editor umschlossen werden soll.

2. Klicken Sie mit der rechten Maustaste, und wählen Sie **Umschließen mit** aus.

   Eine Liste der verfügbaren Umgeben mit-XML-Ausschnitte wird angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **TAB-TASTE** oder die **EINGABETASTE**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>So verwenden Sie „Umschließen mit“ über das IntelliSense-Menü:

1. Wählen Sie den Text aus, der im XML-Editor umschlossen werden soll.

2. Zeigen Sie im Menü **Bearbeiten** auf **IntelliSense**, und klicken Sie dann auf **Umschließen mit**.

   Eine Liste der verfügbaren Umgeben mit-XML-Ausschnitte wird angezeigt.

3. Wählen Sie mit der Maus einen Ausschnitt aus der Liste aus, oder geben Sie den Namen des Ausschnitts ein, und drücken Sie die **TAB-TASTE** oder die **EINGABETASTE**.

## <a name="use-xml-snippets"></a>Verwenden von XML-Ausschnitten

Wenn Sie einen XML-Ausschnitt ausgewählt haben, wird der Text des Codeausschnitts automatisch an der Cursorposition eingefügt. Alle editierbaren Felder im Ausschnitt sind hervorgehoben, und das erste editierbare Feld wird automatisch markiert. Das aktuell markierte Feld ist geschachtelt.

Wenn ein Feld markiert ist, können Sie einen neuen Wert in das Feld eingeben. Durch Drücken von **TAB** können Sie mit dem Cursor alle bearbeitbaren Felder des Ausschnitts durchlaufen. Wenn Sie **UMSCHALT**+**TAB** drücken, durchläuft der Cursor die Felder in umgekehrter Reihenfolge. Durch Klicken auf ein Feld wird der Cursor in diesem Feld platziert. Mit einem Doppelklick auf ein Feld wird dieses markiert. Wenn ein Feld hervorgehoben ist, kann eine QuickInfo angezeigt werden, die eine Beschreibung des Felds liefert.

Nur die erste Instanz des jeweiligen Feldes ist editierbar. Wenn dieses Feld hervorgehoben ist, sind die anderen Instanzen des Feldes mit einem Rahmen versehen. Wenn Sie den Wert eines editierbaren Feldes ändern, wird das Feld an allen Stellen im Ausschnitt geändert, an denen es verwendet wird.

Durch Drücken der **EINGABETASTE** oder **ESC** wird die Feldbearbeitung beendet, und der Editor kehrt in den Normalzustand zurück.

Die Standardfarben für bearbeitbare Codeausschnittsfelder können geändert werden, indem im Dialogfeld **Optionen** im Bereich **Schriftarten und Farben** die Einstellung **Codeausschnittfeld** geändert wird. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern der im Editor in Visual Studio 2017 verwendeten Schriftarten und Farben](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Siehe auch

- [XML-Ausschnitte](../xml-tools/xml-snippets.md)
- [How to: Generieren eines XML-Ausschnitts aus einem XML-Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [How to: Erstellen von XML-Ausschnitten](../xml-tools/how-to-create-xml-snippets.md).
