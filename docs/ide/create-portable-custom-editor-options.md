---
title: EditorConfig-Einstellungen
description: Erfahren Sie, wie Sie Ihrem Projekt oder der Codebasis eine EditorConfig-Datei hinzufügen können, um einheitliche Codierungsformate für alle Benutzer durchzusetzen, die an der Codebasis arbeiten.
ms.custom: SEO-VS-2020
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: a1f66368972614347df9eebe33af435987ea9cc8
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006496"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Erstellen von portablen, benutzerdefinierten Editor-Einstellungen mit „EditorConfig“

Sie können Ihrem Projekt oder der Codebasis eine EditorConfig-Datei hinzufügen, um einheitliche Codierungsformate für alle Benutzer durchzusetzen, die an der Codebasis arbeiten. EditorConfig Einstellungen haben Vorrang vor den globalen Einstellungen des Visual Studio-Text-Editors. Das bedeutet, dass Sie jede Codebasis für die Verwendung von Text-Editor-Einstellungen anpassen können, die für dieses Projekt spezifisch sind. Ihre persönlichen Einstellungen können Sie im Visual Studio-Dialogfeld **Optionen** festlegen. Diese Einstellungen gelten immer dann, wenn Sie ohne eine *EDITORCONFIG*-Datei an einer Codebasis arbeiten oder wenn die *EDITORCONFIG*-Datei eine bestimmte Einstellung nicht außer Kraft setzt. Ein Beispiel ist das Format von Einzügen, also Tabulatoren oder Leerzeichen.

EditorConfig-Einstellungen werden von zahlreichen Code-Editoren und IDEs einschließlich Visual Studio unterstützt. Außerdem ist es eine portable Komponente, die mit dem Code geliefert wird und Codierungsstile auch außerhalb von Visual Studio erzwingen kann.

::: moniker range=">=vs-2019"

Wenn Sie eine EditorConfig-Datei zu Ihrem Projekt in Visual Studio hinzufügen, werden neue Codezeilen gemäß der EditorConfig-Einstellungen formatiert. Die Formatierung von vorhandenem Code wird nicht geändert, es sei denn, Sie führen einen der folgenden Befehle aus:

 - [Codebereinigung](../ide/code-styles-and-code-cleanup.md) (**STRG**+**K**, **STRG**+**E**): wendet die Leerzeicheneinstellungen, z. B. das Einzugsformat, und ausgewählte Codeformatierungseinstellungen an, z. B. die Sortierung von `using`-Anweisungen.
 - **Bearbeiten** > **Erweitert** > **Dokument formatieren** (oder **STRG**+**K**, **STRG**+**D** im Standardprofil): wendet nur die Leerzeicheneinstellungen an, z. B. das Einzugsformat.

 ::: moniker-end

::: moniker range="=vs-2017"

Wenn Sie eine EditorConfig-Datei zu Ihrem Projekt in Visual Studio hinzufügen, werden neue Codezeilen gemäß der EditorConfig-Einstellungen formatiert. Die Formatierung von vorhandenem Code wird nicht geändert, es sei denn, Sie formatieren das Dokument (**Bearbeiten** > **Erweitert** > **Dokument formatieren** oder **STRG**+**K**, **STRG**+**D** im Standardprofil). Das Formatieren des Dokuments wirkt sich nur auf die Leerzeicheneinstellungen (z. B. auf das Einzugsformat) aus, es sei denn, Sie haben „Dokument formatieren“ zur [Durchführung zusätzlicher Codebereinigung](../ide/code-styles-and-code-cleanup.md#apply-code-styles) konfiguriert.

 ::: moniker-end

::: moniker range="vs-2017"

Sie können festlegen, welche EditorConfig-Einstellungen von **Dokument formatieren** auf die [**Seite Formatierungsoptionen**](reference/options-text-editor-csharp-formatting.md#format-document-settings) angewendet werden sollen.

::: moniker-end

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [EditorConfig in Visual Studio für Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Codekonsistenz

Durch die Einstellungen in EDITORCONFIG-Dateien können Sie einen einheitlichen Programmierstil und einheitliche Programmiereinstellungen in einer Codebasis erzielen. Dies betrifft beispielsweise die Einzugsgröße, die Tabulatorbreite, Zeilenendzeichen, die Codierung usw. und ist unabhängig vom verwendeten Editor oder der verwendeten IDE. Wenn Sie beispielsweise in C# programmieren und für Ihre Codebasis eine Konvention gilt, dass Einzüge immer aus fünf Leerzeichen bestehen, für Dokumente UTF-8-Codierung verwendet wird und jede Zeile mit CR/LF endet, können Sie eine *EDITORCONFIG*-Datei entsprechend konfigurieren.

Programmierkonventionen, die Sie für Ihre eigenen Projekte verwenden, unterscheiden sich möglicherweise von denen, die für Ihre Teamprojekte verwendet werden. Z.B. kann es sein, dass Sie es vorziehen, dass beim Programmieren bei einem Einzug ein Tabstoppzeichen hinzugefügt wird. Ihrem Team ist es aber möglicherweise lieber, dass bei einem Einzug vier Leerzeichen anstelle eines Tabstoppzeichens hinzugefügt werden. EditorConfig-Dateien lösen dieses Problem, indem sie Ihnen ermöglichen, für jedes Szenario eine Konfiguration zu verwenden.

Da sich die Einstellungen in einer Datei innerhalb der Codebasis befinden, bilden sie eine Transporteinheit mit der Codebasis. Sofern Sie die Codedatei in einem mit EditorConfig kompatiblen Editor öffnen, werden die Text-Editor-Einstellungen implementiert. Weitere Informationen zu EditorConfig-Dateien finden Sie auf der Website von [EditorConfig.org](https://editorconfig.org/).

> [!NOTE]
> Konventionen, die in einer EditorConfig-Datei festgelegt sind, können zurzeit in einer CI/CD-Pipeline nicht als Buildfehler oder Warnungen erzwungen werden. Alle Stilabweichungen werden nur im Visual Studio-Editor und in der **Fehlerliste** angezeigt.

## <a name="supported-settings"></a>Unterstützte Einstellungen

Der Editor in Visual Studio unterstützt die gebräuchlichsten [EditorConfig-Eigenschaften](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- root

Die Einstellungen des EDITORCONFIG-Editors werden in allen von Visual Studio unterstützten Sprachen mit Ausnahme von XML unterstützt. Zusätzlich unterstützt EditorConfig Konventionen für [Codeformate](/dotnet/fundamentals/code-analysis/code-style-rule-options) wie z.B. Konventionen für [Sprache](/dotnet/fundamentals/code-analysis/style-rules/language-rules), [Formatierung](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules) und [Benennung](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) für C# und Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Hinzufügen und Entfernen von EditorConfig-Dateien

Wenn Sie eine EditorConfig-Datei zu Ihrem Projekt oder Ihrer Codebasis hinzufügen, werden alle neuen Zeilen, die Sie schreiben, gemäß der EditorConfig-Datei formatiert. Durch das Hinzufügen einer EditorConfig-Datei werden vorhandene Formate jedoch erst dann in die neuen konvertiert, wenn Sie das Dokument formatieren oder eine [Codebereinigung](../ide/code-styles-and-code-cleanup.md) ausführen. Wenn in Ihrer Datei beispielsweise Einzüge vorhanden sind, die mit Tabstopps formatiert sind, und Sie eine EditorConfig-Datei hinzufügen, bei der die Einzüge mit Leerzeichen formatiert sind, werden die Einzugszeichen nicht automatisch in Leerzeichen konvertiert. Beim Formatieren des Dokuments (**Bearbeiten** > **Erweitert** > **Dokument formatieren** oder **STRG**+**K**, **STRG**+**D**) werden die Leerzeicheneinstellungen in der EditorConfig-Datei auf vorhandene Codezeilen angewendet.

Wenn Sie eine EditorConfig-Datei aus Ihrem Projekt oder Ihrer Codebasis entfernen und neue Codezeilen gemäß den globalen Editor-Einstellungen formatiert werden sollen, müssen Sie alle geöffneten Codedateien schließen und erneut öffnen.

### <a name="add-an-editorconfig-file-to-a-project"></a>Hinzufügen einer EditorConfig-Datei zu einem Projekt

1. Öffnen Sie ein Projekt oder eine Projektmappe in Visual Studio. Wählen Sie den Knoten „Projekt“ oder „Projektmappe“ aus, je nachdem, ob Ihre Einstellungen für die *EDITORCONFIG*-Datei für alle Projekte in der Projektmappe oder nur für ein Projekt gelten sollen. Sie können ebenfalls einen Ordner in Ihrem Projekt oder in Ihrer Projektmappe auswählen, zu dem die *EDITORCONFIG*-Datei hinzugefügt werden soll.

1. Klicken Sie in der Menüleiste auf **Projekt** > **Neues Element hinzufügen**, oder drücken Sie **STRG**+**UMSCHALTTASTE**+**A**.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Suchen Sie im Suchfeld nach **editorconfig**.

   In den Suchergebnissen werden zwei Elementvorlagen für die **EditorConfig-Datei** angezeigt.

   ![Elementvorlagen für EditorConfig-Datei in Visual Studio](media/editorconfig-item-templates.png)

1. Wählen Sie die Vorlage **editorconfig-Datei (Standard)** aus, um eine EditorConfig-Datei hinzuzufügen, die vorab mit zwei grundlegenden EditorConfig-Optionen für Einzugsformat und Größe aufgefüllt ist. Alternativ dazu können Sie auch die Vorlage **editorconfig-Datei (.NET)** auswählen, um eine EditorConfig-Datei hinzuzufügen, die vorab mit standardmäßigen [Konventionen für .NET-Codeformat, Formatierung und Benennung](/dotnet/fundamentals/code-analysis/code-style-rule-options) aufgefüllt ist.

   Anschließend wird eine *EDITORCONFIG*-Datei in Projektmappen-Explorer angezeigt und im Editor geöffnet.

   ![EDITORCONFIG-Datei in Projektmappen-Explorer und Editor](media/editorconfig-dotnet.png)

1. Bearbeiten Sie die Datei wie gewünscht.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Weitere Möglichkeiten zum Hinzufügen einer EditorConfig-Datei

Es gibt mehrere Möglichkeiten, wie Sie Ihrem Projekt eine EditorConfig-Datei hinzufügen können:

- Das [Coderückschluss-Feature](/visualstudio/intellicode/code-style-inference) von IntelliCode für Visual Studio leitet Codeformate aus vorhandenem Code ab. Dann erstellt das Feature eine nicht leere EditorConfig-Datei, in der Ihre bevorzugten Codeformate bereits definiert sind.

- Ab Visual Studio 2019 können Sie in **Extras** > **Optionen**[eine EditorConfig-Datei basierend auf Ihren Codeformateinstellungen generieren](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files).

## <a name="file-hierarchy-and-precedence"></a>Dateihierarchie und Rangfolge

Wenn Sie einem Ordner in Ihrer Dateihierarchie eine *EDITORCONFIG*-Datei hinzufügen, gelten deren Einstellungen für alle geeigneten Dateien auf der betreffenden Ebene und den Ebenen darunter. Sie können die EditorConfig-Einstellungen ebenfalls für ein bestimmtes Projekt, eine bestimmte Codebasis oder für einen Teil einer Codebasis außer Kraft setzen, sodass dieser andere Konventionen als die anderen Teile der Codebasis verwendet. Dies kann nützlich sein, wenn Sie Code von einer anderen Stelle integrieren und dessen Konventionen nicht ändern möchten.

Fügen Sie zur Außerkraftsetzung einiger oder aller EditorConfig-Einstellungen eine *EDITORCONFIG*-Datei zu der Ebene der Dateihierarchie hinzu, für die die Einstellungen außer Kraft gesetzt werden sollen. Die neuen EDITORCONFIG-Dateieinstellungen gelten für alle Dateien auf der gleichen Ebene sowie für alle Dateien in Unterverzeichnissen.

![EditorConfig-Hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

Wenn einige, aber nicht alle Einstellungen außer Kraft gesetzt werden sollen, geben Sie nur diese Einstellungen in der *EDITORCONFIG*-Datei an. Nur die Eigenschaften, die Sie explizit in der Datei auf der niedrigsten Ebene auflisten, werden außer Kraft gesetzt. Andere Einstellungen aus *EDITORCONFIG*-Dateien auf höheren Ebenen werden weiterhin angewendet. Wenn Sie sicherstellen möchten, dass die _Nein_-Einstellungen von _beliebigen_*EDITORCONFIG*-Dateien auf höheren Ebenen auf diesen Teil der Codebasis angewendet werden, fügen Sie die ```root=true```-Eigenschaft zu der *EDITORCONFIG*-Datei auf niedrigerer Ebene hinzu:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig-Dateien werden von oben nach unten gelesen. Wenn es mehrere Regeleigenschaften mit dem gleichen Namen gibt, hat die zuletzt gefundene Eigenschaft mit diesem Namen Vorrang.

## <a name="edit-editorconfig-files"></a>Bearbeiten von EditorConfig-Dateien

Mit Visual Studio können Sie *EDITORCONFIG*-Dateien bearbeiten, indem Sie IntelliSense-Vervollständigungslisten bereitstellen.

![IntelliSense in einer EDITORCONFIG-Datei](media/editorconfig-intellisense-no-extension.png)

Nachdem Sie Ihre EDITORCONFIG-Datei bearbeitet haben, müssen Sie Ihre Codedateien erneut laden, damit die neuen Einstellungen wirksam werden.

Wenn Sie mehrere *EDITORCONFIG*-Dateien bearbeiten, kann die Erweiterung [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) nützlich sein. Zu den Features dieser Erweiterung zählen die Syntaxhervorhebung sowie eine Verbesserung der Überprüfung, Codeformatierung und von IntelliSense.

![IntelliSense in der Erweiterung „EditorConfig Language Service“](media/editorconfig-intellisense.png)

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Einzüge eines C#-Codeausschnitts vor und nach dem Hinzufügen einer *EDITORCONFIG*-Datei zum Projekt gezeigt. Die Einstellung **Tabstopps** im Dialogfeld **Optionen** für den Visual Studio-Text-Editor ist auf das Einfügen von Leerräumen festgelegt, wenn Sie die **TAB**-TASTE drücken.

![Text-Editor-Tabstoppeinstellung](../ide/media/vside_editorconfig_tabsetting.png)

Wie erwartet erfolgt der Einzug beim Drücken der **TAB-TASTE** in der nächsten Zeile durch Hinzufügen von vier zusätzlichen Leerzeichen.

![Code vor der Verwendung von EditorConfig](../ide/media/vside_editorconfig_before.png)

Fügen Sie dem Projekt eine neue Datei mit dem Namen *EDITORCONFIG* mit folgenden Inhalten hinzu. Die Einstellung `[*.cs]` bewirkt, dass sich diese Änderung nur auf C#-Codedateien in diesem Projekt auswirkt.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Wenn Sie jetzt die **TAB-TASTE** drücken, werden Tabstoppzeichen anstelle von Leerzeichen eingefügt.

![Die TAB-TASTE fügt Tabstoppzeichen hinzu](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Behandeln von Problemen mit den EditorConfig-Einstellungen

Wenn irgendwo in der Verzeichnisstruktur entweder am Speicherort Ihres Projekts oder darüber eine EditorConfig-Datei vorhanden ist, wendet Visual Studio die Editoreinstellungen in dieser Datei auf Ihren Editor an. In diesem Fall wird Ihnen die folgende Meldung in der Statusleiste angezeigt:

   **User preferences for this file type are overridden by this project's coding conventions** („Benutzereinstellungen für diesen Dateityp werden durch die Codekonventionen dieses Projekts außer Kraft gesetzt“).

Das bedeutet, dass die Konventionen der EDITORCONFIG-Dateien die Einstellungen in **Optionen** überschreiben, wenn Editor-Einstellungen (z.B. Einzugsgröße und Stil, Tabstoppgröße oder Codierungskonventionen) in **Extras** > **Optionen** > **Text-Editor** in einer EDITORCONFIG-Datei auf Projektebene oder höher in der Verzeichnisstruktur festgelegt sind. Dieses Verhalten können Sie steuern, indem Sie die Option **Codierungskonventionen des Projekts befolgen** unter **Extras** > **Optionen** > **Text-Editor** verändern. Wenn Sie diese Option deaktivieren, wird auch die EditorConfig-Unterstützung für Visual Studio deaktiviert.

![Tooloptionen: Codierungskonventionen des Projekts befolgen](media/coding_conventions_option.png)

Sie können *EDITORCONFIG*-Dateien in übergeordneten Verzeichnissen finden, indem Sie eine Eingabeaufforderung öffnen und den folgenden Befehl vom Stamm des Datenträgers ausführen, der Ihr Projekt enthält:

```Shell
dir .editorconfig /s
```

Sie können den Bereich Ihrer EDITORCONFIG-Konventionen steuern, indem Sie die ```root=true```-Eigenschaft in *EDITORCONFIG*-Dateien am Stamm Ihres Repositorys oder an dem Verzeichnis, in dem sich Ihr Projekt befindet, festlegen. Visual Studio sucht in dem Verzeichnis der geöffneten Datei oder in allen übergeordneten Verzeichnissen nach einer Datei mit der Dateiendung *EDITORCONFIG*. Die Suche wird beendet, wenn es den Stammdateipfad erreicht oder wenn eine *EDITORCONFIG*-Datei mit ```root=true``` gefunden wird.

## <a name="see-also"></a>Siehe auch

- [.NET-Codeformatkonventionen](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Supporting EditorConfig for a language service (Unterstützen von EditorConfig für einen Sprachdienst)](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Features des Code-Editors](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio für Mac)](/visualstudio/mac/editorconfig)
