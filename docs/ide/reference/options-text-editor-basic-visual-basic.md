---
title: Optionen, Text-Editor, Standard (VB), Erweitert
description: Hier erfahren Sie, wie Sie mithilfe der Seite „Erweitert“ im Abschnitt „Basic“ die Standardeinstellungen der Eigenschaften „Analyse“, „Import-Direktiven“ und „Hervorheben“ ändern.
ms.custom: SEO-VS-2020
ms.date: 08/12/2020
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 530fffdf335232a76a54e66551487a89dc50b09a
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040991"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Optionen, Text-Editor, Standard (Visual Basic), Erweitert
Die Eigenschaftenseite **VB-spezifisch** im Ordner **Basic** im Ordner **Text-Editor** des Dialogfelds **Optionen** (Menü **Extras**) umfasst die folgenden Eigenschaften:

## <a name="analysis"></a>Analyse

- Bereich für Livecodeanalyse oder Hintergrundanalyse

   Konfigurieren des Bereichs für die Hintergrundanalyse für verwalteten Code. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren des Bereichs für die Liveanalyse für verwalteten Code](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Using-Direktiven

- System-Direktiven beim Sortieren von Using-Direktiven an erster Stelle platzieren

   Wenn er ausgewählt wurde, sortiert der Befehl **Remove and Sort Usings** (Using-Anweisungen entfernen und sortieren) im Kontextmenü die `using`-Anweisungen und platziert die „System“-Namespaces ganz oben in der Liste.

- Using-Direktivengruppen trennen

   Wenn ausgewählt, trennt der Befehl **Using-Anweisungen entfernen und sortieren** im Kontextmenü die `using`-Anweisungen, indem er eine leere Zeile zwischen Gruppen von Anweisungen einfügt, die den gleichen Stammnamespace aufweisen.

- Using-Direktiven für Typen in Verweisassemblys vorschlagen
- Using-Direktiven für Typen in NuGet-Paketen vorschlagen

   Wenn diese Optionen ausgewählt wurden, ist eine [Schnellaktion](../quick-actions.md) zum Installieren eines NuGet-Pakets und Hinzufügen einer `using`-Anweisung für nicht referenzierte Typen verfügbar.

   ![Schnellaktion zum Installieren eines NuGet-Pakets in Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Markieren

 **Markierung von Verweisen und Schlüsselwörtern aktivieren**

Der Text-Editor kann alle Instanzen eines Symbols oder alle Schlüsselwörter in Klauseln wie `If..Then`, `While...End While` oder `Try...Catch...Finally` hervorheben. Sie können zwischen markierten Verweisen oder Schlüsselwörtern durch Drücken von **STRG** + **UMSCHALT** + **NACH-UNTEN** oder **STRG** + **UMSCHALT** + **NACH-OBEN** navigieren.

## <a name="outlining"></a>Gliedern

**Gliederungsmodus aktivieren**

Wenn Sie eine Datei im Code-Editor öffnen, können Sie das Dokument im Gliederungsmodus anzeigen. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md). Ist diese Option ausgewählt, wird die Gliederungsfunktion beim Öffnen einer Datei aktiviert.

**Zeilentrennzeichen zwischen Prozeduren anzeigen**

Der Text-Editor gibt den visuellen Bereich von Prozeduren an. In den *VB*-Quelldateien des Projekts werden an den in der folgenden Tabelle aufgeführten Positionen Linien gezeichnet:

|Position in der VB-Quelldatei|Beispiel für die Linienposition|
|---------------------------------|------------------------------|
|Nach dem Schließen eines Blockdeklarationskonstrukts|– Am Ende einer Klasse, einer Struktur, eines Moduls, einer Schnittstelle oder einer Enumeration<br />– Hinter einer Eigenschaft, Funktion oder Sub<br />– Nicht zwischen den get- und set-Klauseln in einer Eigenschaft|
|Nach mehreren Einzelzeilenkonstrukten|– Hinter Import-Anweisungen, vor einer Typdefinition in einer Klassendatei<br />– Hinter den in einer Klasse deklarierten Variablen, vor jeglichen Prozeduren|
|Nach Einzelzeilendeklarationen (Deklarationen, die nicht auf Blockebene erfolgen)|– Nach Import-Anweisungen, Inherits-Anweisungen, Variablendeklarationen, Ereignisdeklarationen, Delegatdeklarationen und Declare-Anweisungen für DLLs|

## <a name="block-structure-guides"></a>Führungslinien für Blockstruktur

Wenn diese Option ausgewählt ist, erscheinen im Editor vertikale Linien, die sich mit strukturierten Codeblöcken decken, sodass Sie die einzelnen Codeblöcke leicht identifizieren können. Beispielsweise würden Sie in einer `Sub`-Anweisung eine Linie zwischen `Sub` und `EndSub` sehen.

## <a name="editor-help"></a>Editor-Hilfe

::: moniker range=">=vs-2019"
**Hinweise zu Inlineparameternamen**    
Wenn diese Option ausgewählt ist, werden Hinweise zu Parameternamen für Literale, umgewandelte Literale und Objektinstanziierungen vor jedem Argument in Funktionsaufrufen eingefügt.  

![Hinweise zu Parameternamen für Visual Basic](media/inline-parameter-name-hints-visualbasic.png)
::: moniker-end

**Automatische Strukturierung und Einrückung des Programmcodes:** Der Text-Editor formatiert den Code entsprechend neu. Wenn diese Option aktiviert ist, führt der Code-Editor die folgenden Aufgaben durch:

- Ausrichten des Codes an der richtigen Tabulatorposition

- Ändern der Groß-/Kleinschreibung von Schlüsselwörtern, Variablen und Objekten in die richtige Schreibweise

- Hinzufügen eines fehlenden `Then` zu einer `If...Then`-Anweisung

- Hinzufügen von Klammern zu Funktionsaufrufen

- Hinzufügen fehlender Anführungszeichen am Ende von Zeichenfolgen

- Neuformatieren der exponentiellen Notation

- Neuformatieren von Datumsangaben

**Automatisches Einfügen von End-Konstruktionen**

Wenn Sie z.B. die erste Zeile einer Prozedurdeklaration, `Sub Main`, eingeben und die **EINGABETASTE** drücken, wird im Text-Editor eine entsprechende `End Sub`-Zeile hinzugefügt. Ebenso wird beim Hinzufügen einer [For](/dotnet/visual-basic/language-reference/statements/for-next-statement)-Schleife im Text-Editor eine entsprechende `Next`-Anweisung hinzugefügt. Wenn diese Option ausgewählt ist, wird im Code-Editor automatisch das end-Konstrukt eingefügt.

**Schnittstellen- und MustOverride-Member automatisch einfügen**

Wenn Sie ein Commit für eine `Implements`-Anweisung oder eine `Inherits`-Anweisung für eine Klasse ausführen, fügt der Text-Editor Prototypen für die Member ein, die implementiert bzw. überschrieben werden müssen.

**Vorschläge für Fehlerkorrektur aktivieren**

Der Text-Editor kann Lösungsvorschläge zu allgemeinen Fehlern ausgeben und bietet die Möglichkeit, die geeignete Korrekturmaßnahme auszuwählen, die dann auf den Code angewendet wird.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)
