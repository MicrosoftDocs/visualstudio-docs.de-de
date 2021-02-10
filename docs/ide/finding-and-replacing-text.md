---
title: Suchen und Ersetzen von Text sowie Auswählen mehrerer Caretzeichen
description: Erfahren Sie mehr über das Feature „Suchen und ersetzen“ und seine Verwendung, um Instanzen eines Musters zu suchen und zu ersetzen.
ms.custom: SEO-VS-2020
ms.date: 10/17/2020
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 534d25c97977d058f0b4137955e44e3d544b3878
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932604"
---
# <a name="find-and-replace-text"></a>Suchen und Ersetzen von Text

Sie können Text im Visual Studio-Editor mit [Suchen und Ersetzen](#find-and-replace-control) (**STRG**+**F** oder **STRG**+**H**) oder mit [In Dateien suchen/In Dateien ersetzen](#find-in-files-and-replace-in-files) (**STRG**+**UMSCHALT**+**F** oder **STRG**+**UMSCHALT**+**H**) suchen und ersetzen. Sie können auch nur *bestimmte* Musterinstanzen mithilfe des *[Auswählens mehrerer Caretzeichen](#multi-caret-selection)* suchen und ersetzen.

> [!TIP]
> Wenn Sie Codesymbole wie Variablen und Methoden umbenennen, ist es besser, anstelle von Suchen und Ersetzen eine *[Umgestaltung](../ide/reference/rename.md)* zu verwenden. Die Umgestaltung ist eine intelligente Funktion, die den Projektumfang berücksichtigt, während Suchen und Ersetzen alle Instanzen blind ersetzt.

Die Funktion Suchen und Ersetzen steht im Editor, in bestimmten anderen textbasierten Fenstern wie z.B. in **Suchergebnis**-Fenstern, in Designerfenstern wie z.B. XAML-Designer und Windows Forms-Designer und in Toolfenstern zur Verfügung.

Sie können den Suchbereich auf das aktuelle Dokument, die aktuelle Projektmappe oder auf eine benutzerdefinierten Ordnersatz festlegen. Ebenfalls können Sie einen Satz mit Dateinamenerweiterungen für Mehrdateiensuchen angeben. Die Suchsyntax kann mit [regulären .NET-Ausdrücken](../ide/using-regular-expressions-in-visual-studio.md) angepasst werden.

> [!TIP]
> Das Feld [Find/Command](../ide/find-command-box.md) (Suchen/Befehl) ist weiterhin als Symbolleisten-Steuerelement verfügbar, wird standardmäßig aber nicht angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der **Standard**-Symbolleiste zunächst **Schaltflächen hinzufügen oder entfernen** auswählen und anschließend **Suchen** auswählen.

## <a name="find-and-replace-control"></a>Steuerelement "Suchen und Ersetzen"

- Verwenden Sie die Tastenkombination **STRG**+**F**, um eine Zeichenfolge in der aktuellen Datei zu *suchen*.
- Verwenden Sie die Tastenkombination **STRG**+**H**, um eine Zeichenfolge in der aktuellen Datei zu *suchen und zu ersetzen*.

Das Steuerelement **Suchen und Ersetzen** finden Sie in der rechten oberen Ecke des Code-Editors. Durch dieses wird jedes Vorkommen des angegebenen Suchbegriffs im aktuellen Dokument sofort hervorgehoben. Sie können von einem Vorkommen zum nächsten navigieren, indem Sie auf dem Steuerelement „Suche“ auf **Weitersuchen** oder **Vorheriges suchen** auswählen.

![Suchen und Ersetzen in Visual Studio](media/find-and-replace-box.png)

Über die Schaltfläche neben dem Textfeld **Suchen** können Sie auf die Optionen für das Ersetzen zugreifen. Um Ersetzungen einzeln durchzuführen, klicken Sie neben dem Textfeld **Ersetzen** auf **Nächstes ersetzen**. Klicken Sie auf **Alle ersetzen**, um alle Übereinstimmungen auf einmal zu ersetzen.

Um die Hervorhebungsfarbe für Übereinstimmungen zu ändern, klicken Sie im Menü **Extras** auf **Optionen**, und wählen Sie dann **Umgebung** und **Schriftarten und Farben** aus. Klicken Sie in der Liste **Einstellungen anzeigen für** auf **Text-Editor**, und wählen Sie dann in der Liste **Elemente anzeigen** die Option **Hervorhebung suchen (Erweiterung)** aus.

### <a name="search-tool-windows"></a>Suchen in Toolfenstern

Sie können das Steuerelement **Suchen** in Code- oder Textfenstern wie beispielsweise den Fenstern **Ausgabe** und **Suchergebnisse** verwenden, indem Sie **Bearbeiten** > **Suchen und Ersetzen** auswählen oder **STRG+F** drücken.

Eine Version des Steuerelements **Suchen** ist auch in einigen Toolfenstern verfügbar. Sie können beispielsweise die Liste der Steuerelemente im Fenster **Toolbox** filtern, indem Sie Text in das Suchfeld eingeben. Andere Toolfenster, deren Inhalte Sie durchsuchen können, sind unter anderem der **Projektmappen-Explorer**, das Fenster **Eigenschaften** und der **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>In Dateien suchen und In Dateien ersetzen

- Verwenden Sie die Tastenkombination **STRG**+**UMSCHALT**+**F**, um eine Zeichenfolge in mehreren Dateien zu *suchen*.
- Verwenden Sie die Tastenkombination **STRG**+**UMSCHALT**+**H**, um eine Zeichenfolge in mehreren Dateien zu *suchen und zu ersetzen*.

**In Dateien suchen/In Dateien ersetzen** funktioniert wie das Steuerelement **Suchen und Ersetzen** mit dem Unterschied, dass Sie einen Bereich für die Suche definieren können. Sie können nicht nur die aktuell geöffnete Datei im Editor durchsuchen, sondern auch alle geöffneten Dokumente, die gesamte Projektmappe, das aktuelle Projekt und ausgewählte Ordnersätze. Ebenfalls können Sie nach Dateierweiterungen suchen. Um auf das Dialogfeld **In Dateien suchen/In Dateien ersetzen** zuzugreifen, wählen Sie im Menü **Bearbeiten** die Option **Suchen und Ersetzen** aus, oder drücken Sie **STRG**+**UMSCHALT**+**F**.

![Suchen in Dateien in Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Suchergebnisse

Wenn Sie **Alle suchen** auswählen, erhalten Sie im Fenster **Suchergebnisse** eine Liste der Übereinstimmungen für Ihre Suche. Wenn Sie ein Ergebnis in der Liste auswählen, wird die dazugehörige Datei mit hervorgehobenen Übereinstimmungen angezeigt. Wenn die Datei nicht bereits zur Bearbeitung geöffnet ist, wird sie in einer Vorschauregisterkarte auf der rechten Seite der Registerkartenreihe geöffnet. Sie können das Steuerelement **Suchen** verwenden, um die Liste **Suchergebnisse** zu durchsuchen.

### <a name="create-custom-search-folder-sets"></a>Erstellen benutzerdefinierter Suchordnersätze

Sie können einen Suchbereich definieren, indem Sie die Schaltfläche **Suchordner auswählen** (sie sieht so aus: **…** ) neben dem Feld **Suchen in** auswählen. Im Dialogfeld **Suchordner auswählen** können Sie einen zu durchsuchenden Ordnersatz angeben, und Sie können die Spezifikation zur späteren Wiederverwendung speichern.

> [!TIP]
> Wenn Sie Ihrem lokalen Computer ein Remotecomputer-Laufwerk zugeordnet haben, können Sie Ordner für die Suche auf dem Remotecomputer angeben.

### <a name="create-custom-component-sets"></a>Erstellen benutzerdefinierter Komponentensätze

Sie können Komponentensätze als Suchbereich definieren, indem Sie auf die Schaltfläche **Benutzerdefinierten Komponentensatz bearbeiten** neben dem Feld **Suchen in** klicken. Sie können installierte .NET- oder COM-Komponenten, in der Projektmappe enthaltene Visual Studio-Projekte oder eine beliebige Assembly bzw. Typbibliothek (*DLL*, *TLB*, *OLB*, *EXE* oder *OCX*) angeben. Wählen Sie zur Suche nach Verweisen das Feld **In Verweisen suchen** aus.

## <a name="multi-caret-selection"></a>Auswählen mehrerer Caretzeichen

> [!NOTE]
> Dieser Abschnitt gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Blockauswahl](/visualstudio/mac/block-selection).

**Eingeführt in Visual Studio 2017 Version 15.8**

Durch das *Auswählen mehrerer Caretzeichen* können Sie dieselbe Änderung gleichzeitig an unterschiedlichen Stellen durchführen. Beispielsweise können Sie Text hinzufügen oder vorhandenen Text bearbeiten. Die Änderungen werden gleichzeitig an mehreren Stellen übernommen.

Auf dem folgenden Screenshot wird `-0000` an drei Stellen ausgewählt. Wenn der Benutzer die **ENTF-Taste** drückt, wird die Auswahl mit diesen Stellen gelöscht:

![Auswählen mehrerer Caretzeichen in einer XML-Datei in Visual Studio](media/multi-caret-selection.png)

Gehen Sie folgendermaßen vor, um mehrere Caretzeichen auszuwählen: Wählen Sie den Text zuerst wie gewohnt aus, oder klicken Sie mit der Maus darauf. Drücken Sie anschließend die **ALT-Taste**, während Sie auf eine andere Stelle mit der Maus klicken oder dort einen Text auswählen. Sie können übereinstimmenden Text auch als zusätzliche Auswahl hinzufügen oder aber ein Textfeld auswählen, um in allen Zeilen dieselben Änderungen durchzuführen.

> [!TIP]
> Wenn Sie unter **Extras** > **Optionen** die **ALT-Taste** als Zusatztaste für die Aktion „Zur Definition wechseln“ festlegen, die normalerweise per Mausklick ausgelöst wird, wird das Auswählen mehrerer Caretzeichen deaktiviert.

### <a name="commands"></a>Befehle

Mit den folgenden Tasten und Aktionen werden unterschiedliche Verhalten für das Auswählen mehrerer Caretzeichen ausgelöst:

|Tastenkombination|Aktion|
|-|-|
|**STRG-TASTE**+**ALT-TASTE**+Klick|Ein zweites Caretzeichen wird hinzugefügt.|
|**STRG-TASTE**+**ALT-TASTE**+Doppelklick|Eine zweite Wortauswahl wird hinzugefügt.|
|**STRG-TASTE**+**ALT-TASTE**+Klick+Ziehen|Eine zweite Auswahl wird hinzugefügt.|
|**UMSCHALTTASTE**+**ALT-TASTE**+ **.**|Der nächsten übereinstimmende Text wird als Auswahl hinzugefügt.|
|**UMSCHALT**+**ALT**+ **;**|Alle übereinstimmenden Texte werden als Auswahl hinzugefügt.|
|**UMSCHALTTASTE**+**ALT-TASTE**+ **,**|Das letzte Ereignis wird entfernt.|
|**UMSCHALT**+**ALT**+ **/**|Die nächste Übereinstimmung wird übersprungen.|
|**ALT-TASTE**+Klick|Eine Feldauswahl wird hinzugefügt.|
|**ESC-Taste** oder Klick|Die gesamte Auswahl wird aufgehoben.|

Einige der Befehle sind auch im Menü **Bearbeiten** unter **Multiple Carets** (Mehrere Caretzeichen) verfügbar:

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Screenshot: Flyoutmenü „Mehrere Einfügemarken“ in Visual Studio":::

## <a name="see-also"></a>Siehe auch

- [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactoring von Code in Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Blockauswahl (Visual Studio für Mac)](/visualstudio/mac/block-selection)
