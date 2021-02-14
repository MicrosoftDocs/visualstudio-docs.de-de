---
title: Ausführen von Komponententests mit dem Test-Explorer
description: Erfahren Sie, wie Sie mit dem Test-Explorer in Visual Studio Tests ausführen. In diesem Artikel wird beschrieben, wie Sie automatische Testläufe nach der Erstellung durchführen, die Testergebnisse anzeigen, die Testliste gruppieren und filtern, Wiedergabelisten erstellen und Tastenkombinationen für Tests verwenden.
ms.date: 07/14/2020
ms.topic: how-to
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05a850b0c88a39366805ff892fb698f637b3bbe1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836331"
---
# <a name="run-unit-tests-with-test-explorer"></a>Ausführen von Komponententests mit dem Test-Explorer

Verwenden Sie den Test-Explorer zum Ausführen von Komponententests von Visual Studio oder Komponententestprojekten von Drittanbietern. Sie können den Test-Explorer auch dazu verwenden, Tests in Kategorien zu gruppieren, die Testliste zu filtern und Ausführungslisten zu erstellen, zu speichern und auszuführen. Sie können auch die Code Coverage analysieren und [Komponententests debuggen](../test/debug-unit-tests-with-test-explorer.md).

Im **Test-Explorer** können Tests aus mehreren Testprojekten in einer Projektmappe und aus Testklassen ausgeführt werden, die Teil der Produktionscodeprojekte sind. Für Testprojekte können verschiedene Komponententest-Frameworks verwendet werden. Wenn der zu testende Code für .NET geschrieben wird, kann das Testprojekt in jeder Sprache geschrieben werden, die ebenfalls auf .NET abzielt, unabhängig von der Sprache des Zielcodes. Systemeigene C/C++-Codeprojekte müssen mithilfe eines Komponententest-Frameworks für C++ getestet werden.

## <a name="build-your-test-project"></a>Erstellen des Testprojekts

Wenn Sie noch kein Testprojekt in der Visual Studio-Projektmappe eingerichtet haben, müssen Sie zunächst ein Testprojekt erstellen und kompilieren.

- [Erste Schritte mit Unittests (.NET)](../test/getting-started-with-unit-testing.md)
- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)

Visual Studio enthält die Komponententest-Frameworks von Microsoft für sowohl verwalteten als auch systemeigenen Code. Im Test-Explorer kann jedoch auch jedes Komponententest-Framework mit implementiertem Test-Explorer-Adapter ausgeführt werden. Weitere Informationen zum Installieren von Komponententest-Frameworks von Drittanbietern finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md).

## <a name="run-tests-in-test-explorer"></a>Ausführen von Tests im Test-Explorer

Wenn Sie das Testprojekt erstellen, werden die Tests im Test-Explorer angezeigt. Falls der Test-Explorer nicht geöffnet ist, wählen Sie im Visual Studio-Menü **Test** zuerst **Fenster** und dann **Test-Explorer** aus, oder drücken Sie **STRG** + **E**, **T**.

::: moniker range="vs-2017"
![Komponententest-Explorer](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test-Explorer](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Standardgruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** und **Nicht ausgeführte Tests** angezeigt. Sie können die Gruppierung der Tests im Test-Explorer ändern.
::: moniker-end
::: moniker range=">=vs-2019"
Während Sie Ihre Tests ausführen, schreiben und erneut ausführen, zeigt der Test-Explorer die Ergebnisse in einer Standardgruppierung Aus **Projekt**, **Namespace** und **Klasse** an. Sie können die Gruppierung der Tests im Test-Explorer ändern.
::: moniker-end

Sie können über die Symbolleiste **Test-Explorer** die meisten Aktionen zum Suchen, Organisieren und Ausführen von Tests ausführen.

::: moniker range="vs-2017"
![Tests von der Test-Explorer-Symbolleiste ausführen](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Tests von der Test-Explorer-Symbolleiste ausführen](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Tests durchführen

::: moniker range="vs-2017"
Sie können alle Tests in der Projektmappe, alle Tests in einer Gruppe oder einen Satz ausgewählter Tests ausführen. Führen Sie einen der folgenden Schritte aus:

- Wählen Sie **Alle ausführen** aus, oder drücken Sie **STRG**+**R**, **V**, um alle Tests in einer Projektmappe auszuführen.

- Klicken Sie zum Ausführen aller Tests in einer Standardgruppe auf **Ausführen**, und wählen Sie dann im Menü die Gruppe aus.

- Wählen Sie die einzelnen auszuführenden Tests aus, öffnen Sie das Kontextmenü eines ausgewählten Tests, und wählen Sie dann **Ausgewählte Tests ausführen** aus, oder drücken Sie **STRG**+**R**, **T**.

- Wenn einzelne Tests keine Abhängigkeiten haben, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über die ![Screenshot der Umschaltfläche für die parallele Testausführung auf der Visual Studio-Test-Explorer-Symbolleiste. Wenn diese Schaltfläche ausgewählt ist, werden Tests parallel ausgeführt.](../test/media/ute_parallelicon-small.png) -Umschaltfläche auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.

Während der Testausführung wird die oben im Fenster **Test-Explorer** angezeigte Leiste **Erfolgreich/Fehlgeschlagen** animiert. Am Ende des Testlaufs wird die Leiste **Erfolgreich/Fehlgeschlagen** grün, wenn alle Tests erfolgreich verlaufen sind, oder rot, wenn ein Test fehlgeschlagen ist.
::: moniker-end
::: moniker range=">=vs-2019"
Sie können alle Tests in der Projektmappe, alle Tests in einer Gruppe oder einen Satz ausgewählter Tests ausführen. Führen Sie einen der folgenden Schritte aus:

- Wählen Sie das Symbol **Alle ausführen** aus, oder drücken Sie **STRG**+**R**, **V**, um alle Tests in einer Projektmappe auszuführen.

- Klicken Sie zum Ausführen aller Tests in einer Standardgruppe auf das Symbol **Ausführen**, und wählen Sie dann im Menü die Gruppe aus.

- Wählen Sie die einzelnen auszuführenden Tests aus, öffnen Sie das Kontextmenü eines ausgewählten Tests, und wählen Sie dann **Ausgewählte Tests ausführen** aus, oder drücken Sie **STRG**+**R**, **T**.

- Wenn einzelne Tests keine Abhängigkeiten aufweisen, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über das Eigenschaftenmenü auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Ausführen von Tests nach jedem Build
::: moniker range="vs-2017"
|Schaltfläche|Beschreibung|
|-|-|
|![Nach Build ausführen](../test/media/ute_runafterbuild_btn.png)|Klicken Sie zum Ausführen der Komponententests nach jedem lokalen Buildvorgang im Standardmenü auf **Test** und anschließend in der Symbolleiste **Test-Explorer** auf **Nach dem Buildvorgang Tests ausführen**.|

> [!NOTE]
> Zum Ausführen von Komponententests nach jedem Buildvorgang benötigen Sie Visual Studio 2017 Enterprise oder Visual Studio 2019. In Visual Studio-2019 ist die Lösung in Community und Professional sowie Enterprise enthalten.
::: moniker-end
::: moniker range=">=vs-2019"
Klicken Sie zum Ausführen der Komponententests nach jedem lokalen Buildvorgang in der Test-Explorer-Symbolleiste auf das Einstellungssymbol, und wählen Sie **Nach dem Buildvorgang Tests ausführen** aus.
::: moniker-end

## <a name="view-test-results"></a>Testergebnisse anzeigen

Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Gruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** sowie **Nicht ausgeführte Tests** angezeigt. Im Detailbereich unten oder auf der Seite des Test-Explorers wird eine Zusammenfassung des Testlaufs angezeigt.

### <a name="view-test-details"></a>Anzeigen von Testdetails

Zum Anzeigen der Details eines einzelnen Tests wählen Sie den jeweiligen Test aus.

::: moniker range="vs-2017"
![Details zur Testausführung](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Details zur Testausführung](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Im Testdetailbereich werden folgende Informationen angezeigt:

- Quelldateiname und Zeilennummer der Testmethode

- Teststatus

- Ausführungsdauer der Testmethode

Bei einem fehlgeschlagenen Test wird im Detailbereich außerdem Folgendes angezeigt:

- Die vom Komponententest-Framework für den Test zurückgegebene Meldung

- Die Stapelüberwachung zum Zeitpunkt des Testfehlers

### <a name="view-the-source-code-of-a-test-method"></a>Anzeigen des Quellcodes einer Testmethode

Wählen Sie zum Anzeigen des Quellcodes einer Testmethode im Visual Studio-Editor den Test und anschließend im Kontextmenü **Test öffnen** aus, oder drücken Sie **F12**.

## <a name="group-and-filter-the-test-list"></a>Gruppieren und Filtern der Testliste

Im Test-Explorer können Sie Tests in vordefinierte Kategorien gruppieren. In den meisten der im Test-Explorer ausführbaren Komponententest-Frameworks können Sie eigene Kategorien und Kategorie/Wert-Paare zum Gruppieren der Tests definieren. Sie können die Testliste auch durch das Vergleichen von Zeichenfolgen mit Testeigenschaften filtern.

### <a name="group-tests-in-the-test-list"></a>Gruppieren von Tests in der Testliste

::: moniker range="vs-2017"
Klicken Sie zum Ändern der Testunterteilung den neben der Schaltfläche **Gruppieren nach** auf den Pfeil nach unten (![Gruppenschaltfläche „Test-Explorer“](../test/media/ute_groupby_btn.png)), und wählen Sie anschließend neue Gruppierungskriterien aus.

![Tests im Test-Explorer nach Kategorie gruppieren](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Im Test-Explorer können Sie Tests in eine Hierarchie gruppieren. Die Standardhierarchiegruppierung ist **Projekt**, **Namespace** und dann **Klasse**. Klicken Sie zum Ändern der Testunterteilung auf die Schaltfläche **Gruppieren nach**![Gruppenschaltfläche „Test-Explorer“](../test/media/ute_groupby_btn.png), und wählen Sie anschließend neue Gruppierungskriterien aus.

![Tests im Test-Explorer nach Kategorie gruppieren](../test/media/vs-2019/test-explorer-groupby-162.png)

Sie können Ihre eigenen Hierarchie- und Gruppenebenen nach **Zustand** und dann **Klasse** definieren, indem Sie beispielsweise „Gruppieren nach“-Optionen in Ihrer bevorzugten Reihenfolge auswählen.

![Screenshot des Visual Studio-Test-Explorers mit einer Testhierarchie in einem Bereich und dem Menü „Gruppieren nach“ im anderen mit aktivierten Optionen „Klasse“ und „Zustand“.](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test-Explorer-Gruppen

::: moniker range="vs-2017"
|Gruppieren|Beschreibung|
|-|-----------------|
|**Dauer**|Tests werden anhand der Ausführungszeit gruppiert: **Schnell**, **Mittel** und **Langsam**.|
|**Ergebnis**|Tests werden anhand der Ausführungsergebnisse gruppiert: **Fehlgeschlagene Tests**, **übersprungene Tests** und **bestandene Tests**.|
|**Merkmale**|Gruppiert Tests nach von Ihnen definierten Kategorie/Wert-Paaren. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.|
|**Projekt**|Gruppiert Tests nach den Namen der Projekte.|
::: moniker-end
::: moniker range=">=vs-2019"
|Gruppieren|Beschreibung|
|-|-----------------|
|**Dauer**|Gruppiert Tests nach Ausführungszeit: **Schnell**, **Mittel** und **Langsam**.|
|**Zustand**|Tests werden anhand der Ausführungsergebnisse gruppiert: **Fehlgeschlagene Tests**, **Übersprungene Tests**, **Bestandene Tests** und **Nicht ausführen**|
|**Zielframework** | Gruppiert Tests nach dem Framework, das die Projekte als Ziel haben |
|**Namespace**|Gruppiert Tests nach dem enthaltenden Namespace.|
|**Projekt**|Gruppiert Tests nach dem enthaltenden Projekt.|
|**Klasse**|Gruppiert Tests nach der enthaltenden Klasse.|
::: moniker-end

### <a name="traits"></a>Merkmale

In der Regel handelt es sich bei Merkmalen um Kategoriename/Wert-Paare, ein Merkmal kann jedoch auch eine einzelne Kategorie darstellen. Merkmale können Methoden zugewiesen werden, die im Komponententest-Framework als Testmethoden identifiziert sind. In einem Komponententest-Framework können Merkmalskategorien definiert werden. Außerdem können Sie den Merkmalskategorien Werte hinzufügen, um eigene Kategoriename/Wert-Paare zu definieren. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.

**Merkmale im Microsoft-Komponententest-Framework für verwalteten Code**

Im Microsoft-Komponententest-Framework für verwaltete Apps wird ein Merkmalsname/Wert-Paar in einem  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> -Attribut definiert. Das Testframework weist zudem folgende vordefinierte Merkmale auf:

|Merkmal|Beschreibung|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Die Kategorie "Besitzer" wird vom Komponententest-Framework definiert. Sie müssen einen Zeichenfolgenwert für den Besitzer angeben.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Die Kategorie "Priorität" wird vom Komponententest-Framework definiert. Sie müssen einen ganzzahligen Wert für die Priorität angeben.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Das TestCategory-Attribut ermöglicht es Ihnen, die Kategorie eines Komponententests anzugeben.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Mithilfe des TestProperty-Attributs können Sie Merkmalskategorie/Wert-Paare definieren.|


**Merkmale im Microsoft-Komponententest-Framework für C++**

Weitere Informationen finden Sie unter [Verwenden des Microsoft-Komponententest-Frameworks für C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Erstellen benutzerdefinierter Wiedergabelisten

::: moniker range="vs-2017"
Sie können eine Liste mit Tests erstellen und speichern, die als Gruppe ausgeführt oder angezeigt werden sollen. Wenn Sie eine Wiedergabeliste auswählen, werden die Tests in der Liste im Test-Explorer angezeigt. Sie können einen Test zu mehr als einer Wiedergabeliste hinzufügen, und bei Auswahl der Standardwiedergabeliste **Alle Tests** sind alle Tests im Projekt verfügbar.

![Wiedergabeliste auswählen](../test/media/ute_playlist.png)

Wählen Sie zum **Erstellen einer Wiedergabeliste** im Komponententest-Explorer mindestens einen Test aus. Klicken Sie im Kontextmenü auf **Zu Wiedergabeliste hinzufügen** > **Neue Wiedergabeliste**. Speichern Sie die Datei unter dem im Dialogfeld **Neue Wiedergabeliste erstellen** angegebenen Namen und Speicherort.

Wählen Sie zum **Hinzufügen von Tests zu einer Wiedergabeliste** im Komponententest-Explorer mindestens einen Test aus. Wählen Sie im Kontextmenü **Zu Wiedergabeliste hinzufügen** und anschließend die Wiedergabeliste aus, der die Tests hinzugefügt werden sollen.

**Wählen Sie zum Öffnen einer Wiedergabeliste** im Visual Studio-Menü **Test** > **Wiedergabeliste** aus. Anschließend können Sie entweder aus der Liste der zuletzt verwendeten Wiedergabelisten oder die Option **Wiedergabelistendatei öffnen** auswählen, um den Namen und Speicherort der Wiedergabeliste anzugeben.

Wenn einzelne Tests keine Abhängigkeiten haben, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über die ![Screenshot der Umschaltfläche für die parallele Testausführung auf der Visual Studio-Test-Explorer-Symbolleiste.](../test/media/ute_parallelicon-small.png) -Umschaltfläche auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.
::: moniker-end
::: moniker range=">=vs-2019"
Sie können eine Liste mit Tests erstellen und speichern, die als Gruppe ausgeführt oder angezeigt werden sollen. Wenn Sie eine Wiedergabeliste auswählen, werden die Tests in der Liste auf einer neuen Registerkarte im Test-Explorer angezeigt. Sie können einen Test zu mehr als einer Wiedergabeliste hinzufügen.

Wählen Sie zum **Erstellen einer Wiedergabeliste** im Komponententest-Explorer mindestens einen Test aus. Klicken Sie im Kontextmenü auf **Zu Wiedergabeliste hinzufügen** > **Neue Wiedergabeliste**.

![Erstellen einer Wiedergabeliste](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Die Wiedergabeliste wird in einer neuen Registerkarte im Test-Explorer geöffnet. Sie können diese Wiedergabeliste einmal verwenden und dann verwerfen, oder Sie können auf die Schaltfläche **Speichern** in der Symbolleiste des Wiedergabelistenfensters klicken und dann einen Namen und einen Ort zum Speichern der Wiedergabeliste auswählen.

![Die Wiedergabeliste wird in einer separaten Registerkarte im Test-Explorer geöffnet.](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

Wählen Sie zum **Erstellen einer Wiedergabeliste** im Komponententest-Explorer mindestens einen Test aus. Klicken Sie im Kontextmenü auf **Zu Wiedergabeliste hinzufügen** > **Neue Wiedergabeliste**.

**Um eine Wiedergabeliste zu öffnen**, wählen Sie das Wiedergabelistensymbol in der Visual Studio-Symbolleiste, und wählen Sie eine zuvor gespeicherte Wiedergabelistendatei aus dem Menü.

Sie können **eine Wiedergabeliste bearbeiten**, indem Sie mit der rechten Maustaste auf einen beliebigen Test klicken und diesen über die Menüoptionen zu einer Wiedergabeliste hinzufügen oder aus einer entfernen.

Ab Visual Studio 2019 Version 16.7 können Sie in der Symbolleiste auf **Bearbeiten** klicken. Daraufhin werden neben Ihren Tests Kontrollkästchen angezeigt, sodass Sie sehen, welche Tests in die Wiedergabeliste eingeschlossen oder aus dieser ausgeschlossen werden. Bearbeiten Sie Gruppen wie gewünscht.

![Schaltfläche „Wiedergabeliste bearbeiten“](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Sie können die Kontrollkästchen der übergeordneten Gruppen in der Hierarchie auch aktivieren oder deaktivieren. Dadurch wird eine dynamische Wiedergabeliste erstellt, die basierend auf den Tests in der Gruppe immer aktualisiert wird. Wenn Sie beispielsweise ein Kontrollkästchen neben einer Klasse aktivieren, wird jeder Test, den diese Klasse hinzufügt, in die Wiedergabeliste aufgenommen. Wenn Sie einen Test aus dieser Klasse löschen, wird er aus der Wiedergabeliste entfernt. Weitere Informationen zu den Regeln finden Sie, indem Sie die Wiedergabeliste mit der Schaltfläche „Speichern“ auf der Symbolleiste speichern und die *PLAYLIST-Datei* öffnen, die auf dem Datenträger erstellt wird. In dieser Datei werden alle Regeln und die einzelnen Tests aufgelistet, aus denen eine Wiedergabeliste besteht.

![XML-Datei für Wiedergabeliste](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

Wenn Sie eine Wiedergabeliste für Merkmale erstellen möchten, verwenden Sie das folgende Format für MSTest.
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

Verwenden Sie das folgende Format für xUnit. Stellen Sie sicher, dass ein Leerzeichen zwischen Ihrem `TestCategory`-Namen und dem `[Value]` steht.
```xml
<Playlist Version="2.0">
  <Rule Name="Includes" Match="Any">
    <Rule Match="All">
      <Property Name="Solution" />
        <Rule Match="Any">
            <Property Name="Trait" Value="TestCategory [Value]" />
        </Rule>
    </Rule>
  </Rule>
</Playlist>
```

::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Test-Explorer-Spalten

Die [Gruppen](#test-explorer-groups) sind auch als Spalten im Test-Explorer verfügbar, wie „Merkmal“, „Stapelverfolgung“, „Fehlermeldung“ und „Vollständig qualifizierter Name“. Die meisten Spalten sind standardmäßig nicht sichtbar, und Sie können festlegen, welche Spalten Sie sehen und in welcher Reihenfolge sie angezeigt werden.

![Screenshot des Visual Studio-Test-Explorers mit einem Menü mit ausgewählten „Spalten“ und einem Untermenü mit ausgewählten Optionen „Dauer“, „Merkmale“ und „Fehlermeldung“.](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtern, Sortieren und Neuordnen von Testspalten

Spalten können gefiltert, sortiert und neu angeordnet werden.
* Um bestimmte Merkmale zu filtern, klicken Sie oben in der Spalte „Merkmale“ auf das Filtersymbol.

  ![Spaltenfilter](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Um die Reihenfolge der Spalten zu ändern, klicken Sie auf eine Spaltenüberschrift, und ziehen Sie Sie nach links oder rechts.

* Um eine Spalte zu sortieren, klicken Sie auf die Spaltenüberschrift. Es können nicht alle Spalten sortiert werden. Sie können auch nach einer sekundären Spalte sortieren, indem Sie die **UMSCHALTTASTE** gedrückt halten und auf einen zusätzlichen Spaltenheader klicken.

  ![Spaltensortierung](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Durchsuchen und Filtern der Testliste

Sie können die Test-Explorer-Suchfilter auch verwenden, um die Testmethoden einzuschränken, die in Ihren Projekten angezeigt und ausgeführt werden können.

Wenn Sie in das Suchfeld des **Test-Explorers** eine Zeichenfolge eingeben und die **Eingabetaste** drücken, wird die Testliste so gefiltert, dass nur Tests angezeigt werden, deren vollqualifizierte Namen die Zeichenfolge aufweisen.

Filtern nach einem anderen Kriterium:

1. Öffnen Sie die rechts neben dem Suchfeld angezeigte Dropdownliste.

2. Wählen Sie ein neues Kriterium aus.

3. Geben Sie zwischen den Anführungszeichen den Filterwert ein. Wenn Sie nach einer genauen Entsprechung für die Zeichenfolge anstatt einer enthaltenden Entsprechung suchen möchten, verwenden Sie das Gleichheitszeichen (=) anstelle des Doppelpunkts (:).

::: moniker range="vs-2017"
![Tests im Test-Explorer filtern](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Tests im Test-Explorer filtern](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Bei Suchvorgängen wird die Groß-/Kleinschreibung nicht beachtet, und die angegebene Zeichenfolge kann einem die oft ausgegebene Befehlszeilen  Teil des Kriteriumswerts entsprechen.

::: moniker range="vs-2017"
|Qualifizierer|Beschreibung|
|-|-----------------|
|**Merkmal**|Durchsucht sowohl die Merkmalskategorie als auch den Wert nach Übereinstimmungen. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.|
|**Projekt**|Durchsucht die Testprojektnamen nach Übereinstimmungen.|
|**Fehlermeldung**|Durchsucht die von fehlerhaften Asserts zurückgegebenen benutzerdefinierte Fehlermeldungen nach Übereinstimmungen.|
|**Dateipfad**|Durchsucht die vollqualifizierten Dateinamen der Testquelldateien nach Übereinstimmungen.|
|**Vollqualifizierter Name**|Durchsucht die vollqualifizierten Namen von Testnamespaces, Klassen und Methoden nach Übereinstimmungen.|
|**Ausgabe**|Durchsucht die benutzerdefinierten Fehlermeldungen, die als Standardausgabe (stdout) oder Standardfehler (stderr) geschrieben werden. Die Syntax zum Angeben von Ausgabemeldungen wird durch das Komponententest-Framework festgelegt.|
|**Ergebnis**|Sucht in den Kategorienamen des Test-Explorers nach Übereinstimmungen: **Fehlgeschlagene Tests**, **übersprungene Tests** und **bestandene Tests**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Qualifizierer|Beschreibung|
|-|-----------------|
|**Zustand**|Sucht in den Kategorienamen des Test-Explorers nach Übereinstimmungen: **Fehlgeschlagene Tests**, **übersprungene Tests** und **bestandene Tests**.|
|**Merkmale**|Durchsucht sowohl die Merkmalskategorie als auch den Wert nach Übereinstimmungen. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.|
|**Vollqualifizierter Name**|Durchsucht die vollqualifizierten Namen von Testnamespaces, Klassen und Methoden nach Übereinstimmungen.|
|**Projekt**|Durchsucht die Testprojektnamen nach Übereinstimmungen.|
|**Zielframework**|Sucht in den Kategorienamen des Test-Explorers nach Übereinstimmungen: **Fehlgeschlagene Tests**, **übersprungene Tests** und **bestandene Tests**.|
|**Namespace**|Durchsucht die Testnamespaces nach Übereinstimmungen.|
|**Klasse**|Durchsucht die Testklassennamen nach Übereinstimmungen.|
::: moniker-end

Verwenden Sie folgende Syntax, um eine Teilmenge von Filterergebnissen auszuschließen :

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Zum Beispiel gibt `FullName:"MyClass" - FullName:"PerfTest"` alle Tests mit „MyClass“ im Namen zurück, mit Ausnahme der Tests, deren Namen auch „PerfTest“ enthalten.

### <a name="analyze-unit-test-code-coverage"></a>Analysieren der Codeabdeckung für Komponententests

Mithilfe des Codeabdeckungstools von Visual Studio, das in der Visual Studio Enterprise-Edition verfügbar ist, können Sie die Menge des Produktcodes ermitteln, die tatsächlich von den Komponententests getestet wird. Das Codeabdeckungstool kann für ausgewählte oder alle Tests in einer Projektmappe ausgeführt werden.

Ausführen des Codeabdeckungstools für Testmethoden in einer Projektmappe:

::: moniker range="vs-2017"

1. Wählen Sie in der obersten Menüleiste **Tests** und anschließend **Code Coverage analysieren** aus.

2. Wählen Sie in Untermenü einen der folgenden Befehle aus:

    - Mit **Ausgewählte Tests** werden die im Test-Explorer ausgewählten Testmethoden analysiert.

    - Mit **Alle Tests** werden alle Testmethoden in der Projektmappe analysiert.

::: moniker-end

::: moniker range=">=vs-2019"

* Klicken Sie mit der rechten Maustaste in den Test-Explorer, und wählen Sie **Code Coverage für ausgewählte Tests analysieren** aus.

::: moniker-end

Im Fenster **Code Coverage-Ergebnisse** wird der Prozentsatz der durchlaufenen Produktcodeblöcke angezeigt, angeordnet nach Zeile, Funktion, Klasse, Namespace und Modul.

Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Tastenkombinationen für Tests

Sie können Tests im Test-Explorer ausführen, indem Sie mit der rechten Maustaste auf einen Test im Code-Editor klicken und dann **Test ausführen** auswählen oder indem Sie die standardmäßigen [Test-Explorer-Tastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) in Visual Studio verwenden. Manche dieser Tastenkombinationen sind vom Kontext abhängig. Das heißt, dass sie Tests basierend auf der Position Ihres Cursors im Code ausführen oder [debuggen](../test/debug-unit-tests-with-test-explorer.md). Wenn Ihr Cursor sich in einer Testmethode befindet, wird diese Testmethode ausgeführt. Wenn Ihr Cursor sich auf der Klassenebene befindet, werden alle Tests in dieser Klasse ausgeführt. Dies gilt ebenfalls für die Namespaceebene.

|Häufig verwendete Befehle| Tastenkombinationen|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**STRG**+**R**, **STRG**+**T**|
|TestExplorer.RunAllTestsInContext|**STRG**+**R**, **T**|
|TestExplorer.RunAllTests|**STRG**+**R**, **A**|
|TestExplorer.RepeatLastRun|**STRG**+**R**, **L**|

> [!NOTE]
> In einer abstrakten Klasse können Sie keinen Test ausführen, da Tests nur in abstrakten Klassen definiert werden und nicht instanziiert. Zum Ausführen von Tests in abstrakten Klassen müssen Sie eine Klasse erstellen, die von der abstrakten Klasse abgeleitet ist.

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Testen des Audiohinweises
Der Test-Explorer kann Sounds wiedergeben, wenn ein Testlauf abgeschlossen ist. Es gibt zwei Sounds: ein Sound, mit dem angegeben wird, dass der Testlauf mit allen durchlaufenen Tests erfolgreich war, und ein zweiter Sound, der angibt, dass der Testlauf mit mindestens einem fehlerhaften Test abgeschlossen wurde. Sie können diese Sounds im Windows 10-Standarddialogmenü „Sound“ einrichten. Dieses Feature ist ab Visual Studio 2019 Update 16.9 Preview 3 verfügbar.

1. Öffnen Sie das Windows 10-Standardmenü „Sound“.
2. Navigieren Sie zur Registerkarte **Sound**.
3. Suchen Sie die **Microsoft Visual Studio**-Kategorie. Wählen Sie die Sounds **Test Run Succeeded** (Testlauf erfolgreich) oder **Test Run Failed** (Testlauf fehlgeschlagen), um die vordefinierten Sounds auszuwählen, oder navigieren Sie zu Ihrer eigenen Audiodatei.  
![Windows 10-Sounddialogmenü](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Debuggen von Komponententests mit dem Test-Explorer](../test/debug-unit-tests-with-test-explorer.md)
- [Ausführen eines Komponententest als 64-Bit-Prozess](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Häufig gestellte Fragen zum Test-Explorer](test-explorer-faq.md)
