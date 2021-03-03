---
title: Analysetoolkonfiguration
ms.date: 09/02/2020
description: Erfahren Sie, wie Sie Roslyn Analyzer-Regeln anpassen. Weitere Informationen finden Sie unter Vorgehensweise beim Anpassen von Analyse Schwergraden, unterdrücken von Verstößen und Festlegen von Dateien als generierter
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 956e63384619a82b7f0abb7dd3771ed2db9cba01
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684382"
---
# <a name="overview"></a>Übersicht

Jede Roslyn Analyzer- *Diagnose* oder Regel weist einen Standard Schweregrad und Unterdrückungs Zustand auf, der überschrieben und für Ihr Projekt angepasst werden kann. In diesem Artikel werden das Festlegen von Schweregraden und das Unterdrücken von Analyzer-Verstößen behandelt

## <a name="configure-severity-levels"></a>Konfigurieren von Schweregraden

::: moniker range=">=vs-2019"

Ab Visual Studio 2019 Version 16,3 können Sie den Schweregrad von Analyse Regeln oder *Diagnosen* in einer [Editor config-Datei](#set-rule-severity-in-an-editorconfig-file), im [Glühbirnen Menü](#set-rule-severity-from-the-light-bulb-menu)und in der Fehlerliste konfigurieren.

::: moniker-end

::: moniker range="vs-2017"

Sie können den Schweregrad der Analyzer-Regeln oder der *Diagnose* konfigurieren, wenn Sie [die-Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren. Sie können den Schweregrad einer Regel [von Projektmappen-Explorer](#set-rule-severity-from-solution-explorer) oder [einer Regel Satz Datei](#set-rule-severity-in-the-rule-set-file)aus ändern.

::: moniker-end

In der folgenden Tabelle werden die verschiedenen Optionen für den Schweregrad angezeigt:

| Schweregrad (Projektmappen-Explorer) | Schweregrad (EditorConfig-Datei) | Verhalten zur Buildzeit | Editor-Verhalten |
|-|-|-|
| Fehler | `error` | Verstöße werden als *Fehler* in der Fehlerliste und in der Befehlszeilen-Buildausgabe angezeigt und bewirken, dass Builds fehlschlagen.| Der betreffende Code wird mit einer roten Wellenlinie unterstrichen und in der Scrollleiste durch ein kleines rotes Feld markiert. |
| Warnung | `warning` | Verstöße werden als *Warnungen* in der Fehlerliste und in der Befehlszeilen-Buildausgabe angezeigt, bewirken aber nicht, dass Builds fehlschlagen. | Der betreffende Code wird mit einer grünen Wellenlinie unterstrichen und in der Scrollleiste durch ein kleines grünes Feld markiert. |
| Info | `suggestion` | Verstöße werden als *Meldungen* in der Fehlerliste angezeigt, in der Befehlszeilen-Buildausgabe hingegen gar nicht. | Der betreffende Code wird mit einer grauen Wellenlinie unterstrichen und in der Scrollleiste durch ein kleines graues Feld markiert. |
| Ausgeblendet | `silent` | Für den Benutzer nicht sichtbar. | Für den Benutzer nicht sichtbar. Die Diagnose wird jedoch der IDE-Diagnose-Engine gemeldet. |
| Keine | `none` | Vollständig unterdrückt. | Vollständig unterdrückt. |
| Standard | `default` | Entspricht dem Standardschweregrad der Regel. Um den Standardwert für eine Regel zu ermitteln, ziehen Sie in der Eigenschaftenfenster zu Rate. | Entspricht dem Standardschweregrad der Regel. |

Wenn ein Analysetool Regelverstöße findet, werden sie im Code-Editor (als *Wellenlinie* unter dem fehlerhaften Code) und im Fenster „Fehlerliste“ angezeigt.

Die in der Fehlerliste gemeldeten vom Analysetool gefundenen Verstöße stimmen mit der [Einstellung für den Schweregrad der Regel](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) überein. Außerdem werden vom Analysetool gemeldete Verstöße auch im Code-Editor als Wellenlinie unter dem fehlerhaften Code angezeigt. In der folgenden Abbildung werden drei Verstöße angezeigt &mdash; ein Fehler (rote Wellenlinie), eine Warnung (grüne Wellenlinie) und ein Vorschlag (drei graue Punkte):

![Wellenlinien im Code-Editor in Visual Studio](media/diagnostics-severity-colors.png)

Der folgende Screenshot zeigt dieselben drei Verstöße, wie Sie im Fehlerliste angezeigt werden:

![Fehler-, Warn-und Informations Verstoß in Fehlerliste](media/diagnostics-severities-in-error-list.png)

Viele Analysetoolregeln oder *-diagnosen* verfügen über mindestens einen *Codefix*, den Sie zur Korrektur von Regelverstößen anwenden können. Codekorrekturen werden zusammen mit anderen [schnellen Aktionen](../ide/quick-actions.md) im Fehlerbehebungsmenü (Glühbirnensymbol) angezeigt. Weitere Informationen zu diesen Codefixen finden Sie unter [Häufige schnelle Aktionen](../ide/quick-actions.md).

![Verstoß im Analysetool und Codefix mithilfe einer schnellen Aktion](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Schweregrad "ausgeblendet" im Vergleich zu "None"

`Hidden` Schweregrade, die standardmäßig aktiviert sind, unterscheiden sich `None` in vielerlei Hinsicht von den Regeln für deaktivierte Regeln oder Schweregrade.

- Wenn eine Code Korrektur für eine `Hidden` Schweregrad Regel registriert wurde, wird die Korrektur in Visual Studio als eine Glühbirne-Refactoring-Aktion für das Codieren angeboten, auch wenn die verborgene Diagnose für den Benutzer nicht sichtbar ist. Dies gilt nicht für deaktivierte `None` Schweregrad Regeln.
- `Hidden` Schweregrad Regeln können per Massen Konfiguration durch Einträge konfiguriert werden, die den [Schweregrad mehrerer Analyse Regeln in einer Editor config-Datei gleichzeitig festlegen](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` Schweregrad Regeln können nicht auf diese Weise konfiguriert werden. Stattdessen müssen Sie über Einträge konfiguriert werden, die den [Schweregrad der Regel in einer Editor config-Datei für jede Regel-ID festlegen](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Festlegen des schwere Grads der Regel in einer Editor config-Datei

(Visual Studio 2019, Version 16,3 und höher)

Sie können den Schweregrad für Compilerwarnungen oder Analyse Regeln in einer editorconfig-Datei mit der folgenden Syntax festlegen:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Das Festlegen des schwere Grads einer Regel in einer Editor config-Datei hat Vorrang vor einem Schweregrad, der in einem Regelsatz oder in Projektmappen-Explorer festgelegt ist. Sie können den Schweregrad [manuell](#manually-configure-rule-severity-in-an-editorconfig-file) in einer Editor config-Datei oder [automatisch](#set-rule-severity-from-the-light-bulb-menu) über die Glühbirne konfigurieren, die neben einem Verstoß angezeigt wird.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Festlegen des Regel schwere Grads mehrerer Analyse Regeln in einer Editor config-Datei

(Visual Studio 2019, Version 16,5 und höher)

Sie können den Schweregrad für eine bestimmte Kategorie von Analyzer-Regeln oder für alle Analyse Regeln mit einem einzigen Eintrag in einer Editor config-Datei festlegen.

- Festlegen des Regel schwere Grads für eine Kategorie von Analyse Regeln:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Festlegen des Regel schwere Grads für alle Analyse Regeln:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Einträge zum gleichzeitigen Konfigurieren mehrerer Analyse Regeln gelten nur für Regeln, die *standardmäßig aktiviert* sind. Analyse Regeln, die im Analyzer-Paket standardmäßig als deaktiviert gekennzeichnet sind, müssen durch explizite `dotnet_diagnostic.<rule ID>.severity = <severity>` Einträge aktiviert werden.

Wenn Sie über mehrere Einträge verfügen, die auf eine bestimmte Regel-ID anwendbar sind, ist Folgendes die Rangfolge, um den entsprechenden Eintrag auszuwählen:

- Der Schweregrad Eintrag für eine einzelne Regel nach ID hat Vorrang vor dem Schweregrad für eine Kategorie.
- Der Schweregrad Eintrag für eine Kategorie hat Vorrang vor dem Schweregrad für alle Analyse Regeln.

Sehen Sie sich das folgende Editor config-Beispiel an, wobei [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) die Kategorie "Performance" hat:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Im vorherigen Beispiel sind alle drei Einträge auf CA1822 anwendbar. Bei Verwendung der angegebenen Rang folgen Regeln gewinnt jedoch der erste Schweregrad der Regel-ID auf die nächsten Einträge. In diesem Beispiel hat CA1822 den effektiven Schweregrad "Fehler". Alle verbleibenden Regeln mit der Kategorie "Leistung" weisen den Schweregrad "Warnung" auf. Alle verbleibenden Analyse Regeln, die nicht die Kategorie "Leistung" aufweisen, haben den Schweregrad "Vorschlag".

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Manuelles Konfigurieren des Regel schwere Grads in einer Editor config-Datei

1. Wenn Sie nicht bereits über eine Editor config-Datei für Ihr Projekt verfügen, [fügen Sie eine hinzu](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Fügen Sie unter der entsprechenden Dateierweiterung einen Eintrag für jede Regel hinzu, die Sie konfigurieren möchten. Um z. b. den Schweregrad für [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) auf `error` für c#-Dateien festzulegen, sieht der Eintrag wie folgt aus:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Bei IDE-Code Analysetools können Sie Sie auch in einer editorconfig-Datei mit einer anderen Syntax konfigurieren, z `dotnet_style_qualification_for_field = false:suggestion` . b.. Wenn Sie jedoch einen Schweregrad mithilfe der `dotnet_diagnostic` Syntax festlegen, hat dies Vorrang. Weitere Informationen finden Sie unter [sprach Konventionen für Editor config](/dotnet/fundamentals/code-analysis/style-rules/language-rules).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Festlegen des schwere Grads der Regel im Glühbirnen Menü

Visual Studio bietet eine bequeme Möglichkeit, den Schweregrad einer Regel im Glühbirnen Menü [schnell Aktionen](../ide/quick-actions.md) zu konfigurieren.

1. Nachdem eine Verletzung aufgetreten ist, bewegen Sie den Mauszeiger über die Verletzungs Wellenlinie im Editor, und öffnen Sie das Glühbirnen Menü. Oder platzieren Sie den Cursor in der Zeile, und drücken Sie die **STRG**-Taste + **.** (Punkt).

2. Klicken Sie im Glühbirnen Menü auf **Probleme** konfigurieren, und konfigurieren Sie den > **\<rule ID> Schweregrad**.

   ![Konfigurieren des schwere Grads von Regeln über das Glühbirnen Menü in Visual Studio](media/configure-rule-severity.png)

3. Wählen Sie von dort eine der Optionen für den Schweregrad aus.

   ![Regel Schweregrad als Vorschlag konfigurieren](media/configure-rule-severity-suggestion.png)

   Visual Studio fügt der Datei Editor config einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren, wie im Feld Vorschau angezeigt.

   > [!TIP]
   > Wenn Sie noch nicht über eine Editor config-Datei im Projekt verfügen, erstellt Visual Studio einen für Sie.

### <a name="set-rule-severity-from-the-error-list-window"></a>Festlegen des schwere Grads der Regel im Fenster "Fehlerliste"

Visual Studio bietet auch eine bequeme Möglichkeit zum Konfigurieren des schwere Grads einer Regel im Kontextmenü "Fehlerliste".

1. Wenn eine Verletzung auftritt, klicken Sie mit der rechten Maustaste auf den diagnoseeintrag in der Fehlerliste.

2. Wählen Sie im Kontextmenü die Option **Schweregrad festlegen** aus.

   ![Konfigurieren des schwere Grads von Regeln in der Fehlerliste in Visual Studio](media/configure-rule-severity-error-list.png)

3. Wählen Sie von dort eine der Optionen für den Schweregrad aus.

   Visual Studio fügt der Datei Editor config einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren.

   > [!TIP]
   > Wenn Sie noch nicht über eine Editor config-Datei im Projekt verfügen, erstellt Visual Studio einen für Sie.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Festlegen des schwere Grads der Regel Projektmappen-Explorer

Sie können einen Großteil der Anpassung der Analyzer-Diagnose von **Projektmappen-Explorer** erledigen. Wenn Sie [Analysen](../code-quality/install-roslyn-analyzers.md) als nuget-Paket installieren, wird in **Projektmappen-Explorer** unter dem Knoten **Verweise** oder **Abhängigkeiten** ein **Analysen** -Knoten angezeigt. Wenn Sie **Analyzers** erweitern und dann eine der Analyzer-Assemblys erweitern, werden alle Diagnosen in der Assembly angezeigt.

![Analyzers-Knoten in Projektmappen-Explorer](media/analyzers-expanded-in-solution-explorer.png)

Im **Eigenschaften** Fenster können Sie die Eigenschaften einer Diagnose einschließlich der Beschreibung und des Standard schwere Grads anzeigen. Um die Eigenschaften anzuzeigen, klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Eigenschaften** aus, oder wählen Sie die Regel aus, und drücken Sie dann **alt** + 

![Diagnose Eigenschaften in Eigenschaftenfenster](media/analyzer-diagnostic-properties.png)

Um die Online Dokumentation für eine Diagnose anzuzeigen, klicken Sie mit der rechten Maustaste auf die Diagnose und wählen **Hilfe anzeigen** aus.

Die Symbole neben den einzelnen Diagnose in **Projektmappen-Explorer** entsprechen den Symbolen, die im Regelsatz angezeigt werden, wenn Sie Sie im Editor öffnen:

- Das "x" in einem Kreis zeigt den [Schweregrad](#configure-severity-levels) " **Fehler** " an.
- "!" in einem Dreieck weist auf den [Schweregrad](#configure-severity-levels) " **Warnung** " hin.
- "i" in einem Kreis zeigt den [Schweregrad](#configure-severity-levels) der **Informationen** an.
- Das "i" in einem Kreis in einem hellfarbigen Hintergrund weist auf den [Schweregrad](#configure-severity-levels) " **ausgeblendet** " hin.
- der nach unten zeigende Pfeil in einem Kreis gibt an, dass die Diagnose unterdrückt wird.

![Diagnose Symbole in Projektmappen-Explorer](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Konvertieren einer vorhandenen RuleSet-Datei in eine Editor config-Datei

Ab Visual Studio 2019 Version 16,5 sind RuleSet-Dateien zugunsten der Editor config-Datei für die Analyse Konfiguration für verwalteten Code veraltet. Die meisten Visual Studio-Tools für die Konfiguration des analyzerregelschwere Grads wurden so aktualisiert, dass Sie auf Editor config-Dateien statt auf RuleSet-Dateien angewendet werden. Mit Editor config-Dateien können Sie sowohl die Schweregrade der Analyzer-Regel als auch die Analyseoptionen konfigurieren, einschließlich der Code Formatoptionen von Visual Studio-IDE. Es wird dringend empfohlen, die vorhandene RuleSet-Datei in eine Editor config-Datei zu konvertieren. Außerdem wird empfohlen, die editorconfig-Datei im Stammverzeichnis Ihres Repository oder im Projektmappenordner zu speichern. Wenn Sie den Stamm Ihres Repository oder Projektmappenordners verwenden, stellen Sie sicher, dass die Schweregrad Einstellungen aus dieser Datei automatisch auf das gesamte Repository bzw. die gesamte Lösung angewendet werden.

Es gibt mehrere Möglichkeiten, eine vorhandene RuleSet-Datei in eine Editor config-Datei zu konvertieren:

- Über den Regelsatz-Editor in Visual Studio (erfordert Visual Studio 2019 16,5 oder höher). Wenn das Projekt bereits eine bestimmte RuleSet-Datei als `CodeAnalysisRuleSet` hat, können Sie es in eine entsprechende editorconfig-Datei aus dem RuleSet-Editor in Visual Studio konvertieren.

    1. Doppelklicken Sie auf die RuleSet-Datei in Projektmappen-Explorer.

       Die RuleSet-Datei sollte im RuleSet-Editor geöffnet werden. Am oberen Rand des Regelsatz-Editors sollte eine Klick Bare **Info Leiste** angezeigt werden.

       ![Konvertieren von RuleSet in die editorconfig-Datei im RuleSet-Editor](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Wählen Sie den Link **Info Leiste** aus.

       Daraufhin sollte das Dialogfeld **Speichern** unter geöffnet werden, in dem Sie das Verzeichnis auswählen können, in dem Sie die Editor config-Datei generieren möchten.

    3. Klicken Sie auf die Schaltfläche **Speichern** , um die Editor config-Datei zu generieren.

       Die generierte editorconfig-Datei sollte im Editor geöffnet werden. Außerdem wird die MSBuild-Eigenschaft `CodeAnalysisRuleSet` in der Projektdatei so aktualisiert, dass Sie nicht mehr auf die ursprüngliche RuleSet-Datei verweist.

- Über die Befehlszeile:

    1. Installieren Sie das nuget-Paket [Microsoft. Code Analysis. rulesetto Editor configconverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Führen `RulesetToEditorconfigConverter.exe` Sie das installierte Paket aus, wobei die Pfade zur RuleSet-Datei und die editorconfig-Datei als Befehlszeilenargumente angegeben werden.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Hier ist ein Beispiel für eine zu konvertierende RuleSet-Datei:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Im folgenden finden Sie die konvertierte Editor config-Datei:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Festlegen des schwere Grads der Regel Projektmappen-Explorer

1. Erweitern Sie in Projektmappen-Explorer **Verweise**-  >  **Analyzers** (oder **Abhängigkeits**  >  **Analyse** Tools für .net Core-Projekte).

2. Erweitern Sie die Assembly, die die Regel enthält, für die Sie den Schweregrad festlegen möchten.

::: moniker range=">=vs-2019"
3. Klicken Sie mit der rechten Maustaste auf die Regel und wählen Sie **Schweregrad festlegen** Wählen Sie im Kontextmenü eine der Optionen für den Schweregrad aus.

   Visual Studio fügt der Datei Editor config einen Eintrag hinzu, um die Regel auf der angeforderten Ebene zu konfigurieren. Wenn das Projekt eine RuleSet-Datei anstelle einer Editor config-Datei verwendet, wird der Eintrag für den Schweregrad der RuleSet-Datei hinzugefügt.

   > [!TIP]
   > Wenn Sie nicht bereits über eine Editor config-Datei oder eine RuleSet-Datei im Projekt verfügen, erstellt Visual Studio eine neue Editor config-Datei.
::: moniker-end

::: moniker range="vs-2017"
3. Klicken Sie mit der rechten Maustaste auf die Regel, und wählen Sie **Regelsatz Schweregrad festlegen** Wählen Sie im Kontextmenü eine der Optionen für den Schweregrad aus.

   Der Schweregrad für die Regel wird in der aktiven Regel Satz Datei gespeichert.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Festlegen des Regel schwere Grads in der Regel Satz Datei

![Regel Satz Datei in Projektmappen-Explorer](media/ruleset-in-solution-explorer.png)

1. Öffnen Sie die aktive Regel Satz Datei mit einer der folgenden Methoden:

- Doppelklicken Sie in **Projektmappen-Explorer** auf die Datei, klicken Sie mit der rechten Maustaste auf **Verweise**-  >  **Analyzers** -Knoten, und wählen Sie **aktiven Regelsatz öffnen** aus.
- Wählen Sie auf der Eigenschaften Seite **Code Analyse** für das Projekt die Option **Öffnen** aus.

  Wenn Sie den Regelsatz zum ersten Mal bearbeiten, erstellt Visual Studio eine Kopie der standardmäßigen Regel Satz Datei, benennt Sie " *\<projectname> . RuleSet*" und fügt Sie dem Projekt hinzu. Dieser benutzerdefinierte Regelsatz wird auch zum aktiven Regelsatz für Ihr Projekt.

   > [!NOTE]
   > .Net Core-und .NET Standard-Projekte unterstützen nicht die Menübefehle für Regelsätze in **Projektmappen-Explorer**, z. b. **Öffnen des aktiven Regelsatzes**. Wenn Sie einen nicht standardmäßigen Regelsatz für ein .net Core-oder .NET Standard-Projekt angeben möchten, [fügen Sie die Eigenschaft " **codeanalysisruleset**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) " manuell zur Projektdatei hinzu. Sie können die Regeln im Regelsatz weiterhin in der Benutzeroberfläche von Visual Studio-Regelsatz-Editor konfigurieren.

1. Navigieren Sie zu der Regel, indem Sie die enthaltende Assembly erweitern.

1. Wählen Sie in der Spalte **Aktion** den Wert aus, um eine Dropdown Liste zu öffnen, und wählen Sie den gewünschten Schweregrad aus der Liste aus.

   ![Regel Satz Datei in Editor öffnen](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Generierten Code konfigurieren

Analyzers werden für alle Quelldateien in einem Projekt ausgeführt und melden Verstöße gegen Sie. Diese Verstöße sind bei generierten Code Dateien, z. b. vom Designer generierte Code Dateien, temporäre Quelldateien, die vom Buildsystem generiert werden, jedoch nicht nützlich. Benutzer können diese Dateien nicht manuell bearbeiten und/oder sich nicht darum kümmern, Verstöße in dieser Art von Tool generierten Dateien zu beheben.

Standardmäßig behandelt der Analyzer-Treiber, der Analysen ausführt, Dateien mit einem bestimmten Namen, einer Dateierweiterung oder einem automatisch generierten Dateiheader als generierte Code Dateien. Beispielsweise wird ein Dateiname, der mit oder endet, `.designer.cs` `.generated.cs` als generierter Code betrachtet. Diese Heuristik kann jedoch möglicherweise nicht alle benutzerdefinierten generierten Code Dateien im Quellcode der Benutzer identifizieren.

Ab Visual Studio 2019 16,5 können Endbenutzer bestimmte Dateien und/oder Ordner so konfigurieren, dass Sie als generierter Code in einer [Editor config-Datei](https://editorconfig.org/)behandelt werden. Führen Sie die folgenden Schritte aus, um eine solche Konfiguration hinzuzufügen:

1. Wenn Sie nicht bereits über eine Editor config-Datei für Ihr Projekt verfügen, [fügen Sie eine hinzu](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Fügen Sie den `generated_code = true | false` Eintrag für bestimmte Dateien und/oder Ordner hinzu. Um z. b. alle Dateien zu behandeln, deren Name mit `.MyGenerated.cs` dem generierten Code endet, sieht der Eintrag wie folgt aus:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Verstöße unterdrücken

Es gibt mehrere Möglichkeiten, Regel Verletzungen zu unterdrücken:

::: moniker range=">=vs-2019"

- In einer **Editor config-Datei**

  Legen Sie den Schweregrad auf fest `none` , z `dotnet_diagnostic.CA1822.severity = none` . b..

- Über das Menü " **analysieren** "

  Wählen Sie  >  in der Menüleiste die Option **Build analysieren und aktive Probleme unterdrücken** , um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

::: moniker-end

::: moniker range="vs-2017"

- Über das Menü " **analysieren** "

  Wählen Sie  >  in der Menüleiste Analyse **Ausführen Code Analyse und unterdrücken aktiver Probleme** aus, um alle aktuellen Verstöße zu unterdrücken. Dies wird manchmal als "Baselining" bezeichnet.

::: moniker-end

- Von **Projektmappen-Explorer**

  Legen Sie den Schweregrad der Regel auf **None** fest.

- Aus dem **Regelsatz-Editor**

  Deaktivieren Sie das Kontrollkästchen neben dem Namen, oder legen Sie die **Aktion** auf **keine** fest.

- Im **Code-Editor**

  Platzieren Sie den Cursor in der Codezeile mit der Verletzung, und drücken Sie die **STRG**- + Taste **(.)** , um das Menü **schnell Aktionen** zu öffnen. Wählen Sie **CAXXXX**  >  **in Quelle/in Unterdrückungs Datei unter** drücken.

  ![Diagnose über das Menü "schnelle Aktionen" unterdrücken](media/suppress-diagnostic-from-editor.png)

- Aus der **Fehlerliste**

  Wählen Sie die zu unterdrückenden Regeln aus, und klicken Sie dann mit der rechten Maustaste, und wählen Sie  >  **in Quelle unterdrücken/in Unterdrückungs Datei**.

  - Wenn Sie **in Quelle** unterdrücken, wird das Dialogfeld **Vorschau der Änderungen** geöffnet, in dem eine Vorschau der c#- [#pragma Warnung](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) oder Visual Basic [#Disable Warning](/dotnet/visual-basic/language-reference/directives/directives) -Direktive angezeigt wird, die dem Quellcode hinzugefügt wird.

    ![Vorschau der Hinzufügung von #pragma Warnung in der Codedatei](media/pragma-warning-preview.png)

  - Wenn Sie **in Unterdrückungs Datei** auswählen, wird das Dialogfeld **Vorschau der Änderungen** geöffnet, und es wird eine Vorschau des Attributs angezeigt, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> das der globalen Unterdrückungs Datei hinzugefügt wird.

    ![Vorschau zum Hinzufügen des SuppressMessage-Attributs zur Unterdrückungs Datei](media/preview-changes-in-suppression-file.png)

  **Wählen Sie** im Dialogfeld **Vorschau der Änderungen** übernehmen aus.

  > [!NOTE]
  > Wenn die Option Menü unter **drücken** in **Projektmappen-Explorer** nicht angezeigt wird, wird die Verletzung wahrscheinlich von Build und nicht von Live-Analyse stammt. In der **Fehlerliste** werden Diagnose-oder Regelverstöße sowohl aus der Live Code Analyse als auch aus dem Build angezeigt. Da die builddiagnose beispielsweise veraltet sein kann, wenn Sie z. b. den Code bearbeitet haben, um den Verstoß zu beheben, aber nicht neu erstellt wurde, können Sie diese Diagnose nicht im **Fehlerliste** unterdrücken. Die Diagnose aus Live Analyse oder IntelliSense sind immer auf dem neuesten Stand mit aktuellen Quellen und können vom **Fehlerliste** unterdrückt werden. Um die *builddiagnose von* Ihrer Auswahl auszuschließen, ändern Sie den **Fehlerliste** Quellen Filter von **Build + IntelliSense** **nur in IntelliSense**. Wählen Sie dann die Diagnose aus, die Sie unterdrücken möchten, und fahren Sie wie zuvor beschrieben fort.
  >
  > ![Fehlerliste Quellen Filter in Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Befehlszeilen Verwendung

Wenn Sie das Projekt in der Befehlszeile erstellen, werden Regelverstöße in der Buildausgabe angezeigt, wenn die folgenden Bedingungen erfüllt sind:

- Die Analysen werden mit dem .NET SDK oder als nuget-Paket installiert, nicht als VSIX-Erweiterung.

  Für Analyzer, die mithilfe des .net SDKs installiert wurden, müssen Sie möglicherweise [die-Analysen aktivieren](../code-quality/install-net-analyzers.md). Bei Code Stilen können Sie auch [Code Stile beim Erstellen erzwingen](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) , indem Sie eine MSBuild-Eigenschaft festlegen.

- Mindestens eine Regel wird im Code des Projekts verletzt.

- Der [Schweregrad](#configure-severity-levels) einer verletzten Regel ist auf " **Warnung**" festgelegt. in diesem Fall bewirken Verstöße nicht, dass der Buildvorgang fehlschlägt oder dass ein **Fehler** auftritt.

Die Ausführlichkeit der Buildausgabe wirkt sich nicht darauf aus, ob Regelverstöße angezeigt werden. Auch mit der **stillen** Ausführlichkeit werden Regel Verletzungen in der Buildausgabe angezeigt.

> [!TIP]
> Wenn Sie daran gewöhnt sind, eine Legacy Analyse von der Befehlszeile aus durchzuführen, entweder mit *FxCopCmd.exe* oder über MSBuild mit dem **RunCodeAnalysis** -Flag, gehen Sie wie folgt vor: Code Analysetools.

Um Analyzer-Verstöße in der Befehlszeile anzuzeigen, wenn Sie das Projekt mithilfe von MSBuild erstellen, führen Sie einen Befehl wie den folgenden aus:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Der folgende Screenshot zeigt die Befehlszeilen-Buildausgabe vom Erstellen eines Projekts an, das einen Regelverstoß des Analysetools enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Abhängige Projekte

Wenn Sie in einem .net Core-Projekt einen Verweis auf ein Projekt hinzufügen, das über nuget-Analysen verfügt, werden diese Analysen dem abhängigen Projekt ebenfalls automatisch hinzugefügt. Um dieses Verhalten zu deaktivieren, z. b. wenn das abhängige Projekt ein Komponenten Testprojekt ist, markieren Sie das nuget-Paket als privat in der *csproj* -oder *vbproj* -Datei des referenzierten Projekts, indem Sie das **privateassets** -Attribut festlegen:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über Code Analysen in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Senden eines Code Analyzer-Fehlers](https://github.com/dotnet/roslyn-analyzers/issues)
- [Verwenden von Regelsätzen](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Code Analyse Warnungen unterdrücken](../code-quality/in-source-suppression-overview.md)
- [Konfigurationsoptionen für die Code Analyse (.net)](/dotnet/fundamentals/code-analysis/configuration-options)
