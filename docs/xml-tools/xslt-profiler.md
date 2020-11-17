---
title: XSLT-Leistung
description: In diesem Artikel erfahren Sie mehr über den XSLT-Profiler in Visual Studio, der ausführliche XSLT-Leistungsberichte erstellt, mit denen Sie die Leistung Ihres XSLT-Codes optimieren können.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4fd10df6a5cd91866633a46e1a512e91da2040
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351413"
---
# <a name="the-xslt-profiler"></a>Der XSLT-Profiler

Der XSLT-Profiler erstellt ausführliche XSLT-Leistungsberichte zur Erfassung, Messung und Bewertung leistungsbezogener Probleme im XSLT-Code. Der XSLT-Profiler enthält nützliche Hinweise zu XSL- und XSLT-Stylesheetoptimierungen. Für XSLT-Anwendungen, bei denen maximale Leistung erforderlich ist, ist dieses Tool unentbehrlich.

Der XSLT-Profiler ist Bestandteil von Visual Studio und im Menü **XML** verfügbar.

![XSLT-Profiler](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Der XSLT-Profiler ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="create-a-performance-report"></a>Erstellen eines Leistungsberichts

1. Öffnen Sie in Visual Studio ein XSLT-Dokument.

2. Wählen Sie auf der Menüleiste **XML** > **XSLT-Profil erstellen** aus.

3. Geben Sie ein Eingabe-XML-Dokument an. Wenn noch kein XML-Dokument geöffnet ist, werden Sie zur Angabe der Datei aufgefordert.

   Die Analyse wird gestartet, und der Status wird im Editor in einer Statusanzeige angezeigt. Die XSLT-Ausgabe ist ebenfalls sichtbar.

4. Nach Ende der Leistungssitzung überprüfen Sie den Leistungsbericht, um die XSLT-Leistung zu analysieren.

## <a name="get-all-available-views"></a>Abrufen aller verfügbaren Ansichten

1. Klicken Sie auf die Dropdownliste **Aktuelle Ansicht**, um alle verfügbaren Ansichten abzurufen.

2. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option für die **Zusammenfassungsansicht** aus. Leistungsberichte werden standardmäßig in der **Zusammenfassungsansicht** angezeigt. Diese Ansicht ist ein Ausgangspunkt für die Ermittlung von Leistungsproblemen in XSLT-Dokumenten. In der **Zusammenfassungsansicht** werden die folgenden Datenpunkte angezeigt:

   - Am häufigsten aufgerufene Funktionen

   - Funktionen mit der meisten individuellen Arbeit

   - Funktionen mit der längsten Ausführungszeit

   Standardmäßig werden für jeden Datenpunkt drei Spalten angezeigt: der Name der Funktion, die Anzahl von Aufrufen als absoluter Wert und ein Prozentwert, der den Anteil der jeweiligen Funktion an der Gesamtanzahl von Funktionsaufrufen darstellt. Von den einzelnen Datenpunkten in der **Zusammenfassungsansicht** können Sie zu detaillierteren Ansichten navigieren, indem Sie mit der rechten Maustaste auf die Funktionsdatenpunkte klicken.

3. Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option für die **Funktionsansicht** aus. In der **Funktionsansicht** werden die während der Profilerstellung aufgerufenen Funktionen aufgeführt. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Die folgenden Spalten werden standardmäßig angezeigt:

    - **Funktionsname**

    - **verstrichene inklusive Zeit**

    - **verstrichene exklusive Zeit**

    - **inklusive Anwendungszeit**

    - **exklusive Anwendungszeit**

    - **Anzahl der Aufrufe**

   Alle Zeitspalten werden in absoluten Werten und Prozentsätzen angezeigt. Der Begriff **Exklusiv** bezieht sich auf die gesamte Ausführungszeit einer Funktion ohne die Ausführungszeit anderer Funktionen, die während der Ausführung dieser Funktion aufgerufen wurden.

   Der Begriff **Inklusiv** bezieht sich auf die gesamte Ausführungszeit einer Funktion einschließlich der Ausführungszeit aller von ihr aufgerufenen Funktionen und anderer von diesen Funktionen aufgerufenen Funktionen.

## <a name="select-callercallee-view"></a>Auswählen der Ansicht "Aufrufer/Aufgerufener"

Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Ansicht **Aufrufer/Aufgerufener** aus. Die Ansicht **Aufrufer/Aufgerufener** besteht aus den folgenden drei Teilen:

- **Funktionen, die aufgerufen haben**: Alle Funktionen, die eine bestimmte Funktion aufgerufen haben, werden im oberen Teil der Ansicht aufgelistet.

- **Aktuelle Funktion**: Die aufgerufene Funktion wird im mittleren Teil der Ansicht angezeigt.

- **Funktionen, die aufgerufen wurden von**: Alle Funktionen, die von der jeweiligen Funktion aufgerufen wurden, werden im unteren Teil der Ansicht aufgelistet.

Wenn eine Funktion mit dem Namen `SyncToNavigator` im mittleren Teil der Ansicht angezeigt wird, werden alle von der `SyncToNavigator`-Funktion aufgerufenen Funktionen im oberen Teil der Ansicht aufgelistet, und alle Funktionen, die von `SyncToNavigator` aufgerufen wurden, werden im unteren Teil der Ansicht aufgeführt.

- Die im mittleren Teil der Ansicht angezeigte Funktion kann per Doppelklick auf eine der Funktionen in den anderen beiden Teilen der Ansicht gewechselt werden. Die Ansicht wird dann automatisch entsprechend den Änderungen aktualisiert.

- Sie können die Daten auch durch Klicken auf die Spaltennamen sortieren.

## <a name="select-call-tree-view"></a>Auswählen der Aufrufstrukturansicht

- Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Ansicht **Aufrufstrukturansicht** aus. Diese Ansicht ist eine Strukturansicht der Programmausführung.

   In der **Aufrufstrukturansicht** wird der Stamm der Struktur als Prozessname angezeigt. Die Funktionen sind die Knoten der Struktur. In dieser Ansicht können Sie einen Drilldown in bestimmte Aufrufablaufverfolgungen ausführen und analysieren, welche Aufrufe die größten Auswirkungen auf die Leistung haben. Die Ansicht ähnelt der beim Debuggen verfügbaren **Aufruflistenansicht**. Neben den Spalten in der **Funktionsansicht** enthält die **Aufrufstrukturansicht** eine weitere Spalte für den **Modulnamen**.

- Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option **Markierungen** aus.

   Im XSLT-Profiler werden Markierungen verwendet, die im Datensammlungsdatenstrom zusammen mit einem Kommentar angezeigt werden. Markierungen sind Stellen im Code, die über Indikatoren verfügen. Wenn Sie den XSLT-Profiler anweisen, XSLT-Leistungsindikatoren zu erfassen, werden die Indikatoren bei jeder Ausführung einer dieser Markierungen gesammelt. Die Daten werden in einer Tabelle mit **Markierungs-ID**, **Markierungsname** (**Programm starten**, **Programm beenden**) und dem **Zeitstempel** angezeigt. Die Markierungen werden nicht aggregiert und in chronologischer Reihenfolge in der **Markierungsansicht** des Leistungsberichts angezeigt.

## <a name="select-modules-in-the-current-view"></a>Auswählen von Modulen in der aktuellen Ansicht

- Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option **Module** aus.

   Die Modulansicht ist eine einfache Liste aller Funktionen zusammengefasst zur Modulebene. Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Standardmäßig werden sowohl absolute Werte als auch Prozentzahlen für **Verstrichene inklusive Zeit**, **Verstrichene exklusive Zeit**, **Inklusive Anwendungszeit**, **Exklusive Anwendungszeit** und **Anzahl der Aufrufe** angezeigt.

- Wählen Sie in der Dropdownliste **Aktuelle Ansicht** die Option **Prozess** aus.

   In der Prozessansicht wird eine Tabelle mit **Prozess-ID**, **Prozessname**, **Anfangszeit** und **Endzeit** angezeigt. Sie können die Daten durch Klicken auf die Spaltennamen sortieren.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie](../xml-tools/walkthrough-using-xslt-hierarchy.md)
