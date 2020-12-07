---
title: Analysieren der Speicherauslastung für .NET-Objekte | Microsoft-Dokumentation
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 563531b6dfbf59e33b63dcb4561612d86cd39acc
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970223"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Analysieren der Speicherauslastung mithilfe des .NET-Tools für die Objektzuordnung

Mithilfe des .NET-Tools für die Objektzuordnung können Sie anzeigen, wie viel Arbeitsspeicher Ihre App insgesamt belegt und für welche Codepfade der Bedarf am höchsten ist.

Nach der Ausführung des Tools können Sie die Pfad zur Funktionsausführung sehen, in denen Objekte zugewiesen werden. Anschließend können Sie durch eine Rückverfolgung bis zum Stamm die Aufrufstruktur ermitteln, die den meisten Arbeitsspeicher belegt.

## <a name="setup"></a>Setup

1. Öffnen Sie über **ALT+F2** den Leistungs-Profiler in Visual Studio.

1. Aktivieren Sie das Kontrollkästchen **Nachverfolgung der .NET-Objektzuordnung**.

   ![Aktivierte Option „Nachverfolgung der .NET-Objektzuordnung“](../profiling/media/dotnetalloctoolselected.png "Aktivierte Option „Nachverfolgung der .NET-Objektzuordnung“")

1. Klicken Sie auf die Schaltfläche **Start**, um das Tool auszuführen.

1. Gehen Sie nach dem Start des Tools das Szenario durch, für das Sie in Ihrer App ein Profil erstellen möchten. Klicken Sie dann auf **Sammlung beenden**, oder schließen Sie Ihre App, um die Daten anzuzeigen.

   ![Fenster mit angezeigter Option „Sammlung beenden“](../profiling/media/stopcollectionlighttheme.png "Fenster mit angezeigter Option „Sammlung beenden“")

1. Wählen Sie die Registerkarte **Zuordnung** aus. Die angezeigten Fensterinhalte sollten denen im folgenden Screenshot ähneln.

   ![Registerkarte „Zuordnung“](../profiling/media/allocationview.png "Registerkarte „Zuordnung“")

Sie können jetzt die Speicherbelegung der Objekte analysieren.

Während der Sammlung kann das Überwachungstool die App verlangsamen, für die das Profil erstellt wird. Falls die Leistung des Tools oder der App herabgesetzt wird und Sie nicht jedes Objekt nachverfolgen müssen, können Sie die Stichprobenhäufigkeit anpassen. Klicken Sie hierzu auf der Seite mit der Profilerzusammenfassung auf das Zahnradsymbol neben dem Überwachungstool.

![Einstellungen für das .NET-Zuordnungstool](../profiling/media/dotnetallocsettings.png "Einstellungen für das .NET-Zuordnungstool")

Passen Sie die Stichprobenhäufigkeit wie gewünscht an. Diese Änderung verbessert die Leistung Ihrer App während der Datensammlung und Analyse.

![Angepasste Stichprobenhäufigkeit](../profiling/media/adjustedsamplingratedotnetalloctool.png "Angepasste Stichprobenhäufigkeit")

Weitere Informationen zur Optimierung des Tools finden Sie unter [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Verstehen Ihrer Daten

![Diagramm für das .NET-Zuordnungstool](../profiling/media/graphdotnetalloc.png "Diagramm für das .NET-Zuordnungstool")

In der grafischen Darstellung oben wird im oberen Bereich die Anzahl von Liveobjekten in Ihrer App angezeigt. Das untere Diagramm **Objektdelta** zeigt die prozentuale Änderung von App-Objekten. Rote Linien kennzeichnen, wann eine Garbage Collection stattgefunden hat.

![Gefiltertes Diagramm der .NET-Zuordnungszeit](../profiling/media/graphdotnetalloctimefiltered.png "Gefiltertes Diagramm der .NET-Zuordnungszeit")

Sie können die tabellarischen Daten filtern, um nur Aktivitäten für einen angegebenen Zeitraum anzuzeigen. Außerdem können Sie einen Bereich des Diagramms vergrößern oder verkleinern.

### <a name="allocation"></a>Zuordnung

![Erweiterte Zuordnungsansicht](../profiling/media/allocationexpandedlight.png "Erweiterte Zuordnungsansicht")

In der Ansicht **Zuordnung** können Sie sehen, welche Objekte wie viel Arbeitsspeicher belegen und wo sich diese Objekte befinden.

- Die Spalte **Typ** enthält eine Liste der Klassen und Strukturen, die Arbeitsspeicher verbrauchen. Doppelklicken Sie auf einen Typ, um die Rückverfolgung als umgekehrte Aufrufstruktur anzuzeigen. Nur in der Ansicht **Zuordnung** können Sie Elemente innerhalb der ausgewählten Kategorie anzeigen, die Arbeitsspeicher beanspruchen.

- Die Spalte **Zuordnungen** zeigt die Anzahl von Objekten an, die innerhalb eines bestimmten Zuordnungstyps oder einer bestimmten Funktion Arbeitsspeicher belegen. Diese Spalte wird nur in den Ansichten **Speicherbelegung**, **Aufrufbaum** und **Funktionen** angezeigt.

- Die Spalten **Byte** und **Average Size (Bytes)** (Durchschnittliche Größe (Byte)) werden standardmäßig nicht angezeigt. Damit sie eingeblendet werden, müssen Sie mit der rechten Maustaste auf die Spalte **Typ** oder **Zuordnungen** klicken und dann die Optionen **Byte** und **Durchschnittliche Größe (Byte)** auswählen, um sie dem Diagramm hinzuzufügen. 

   Die zwei Spalten ähneln **Gesamt (Zuordnungen)** und **Selbst (Zuordnungen)** , zeigen jedoch die Menge des belegten Arbeitsspeichers anstelle der Anzahl von Objekten an, die Arbeitsspeicher verbrauchen. Diese Spalten sind nur in der Ansicht **Zuordnung** enthalten.

- Die Spalte **Modulname** zeigt das Modul an, das die aufrufende Funktion oder den aufrufenden Prozess enthält.

Alle diese Spalten sind sortierbar. Die Elemente in den Spalten **Typ** und **Modulname** können Sie alphabetisch sortieren (in aufsteigender oder absteigender Reihenfolge). Für **Zuordnungen**, **Byte** und **Durchschnittliche Größe (Byte)** können Sie Elemente sortieren, indem Sie den numerischen Wert erhöhen oder verringern.

#### <a name="symbols"></a>Symbole

Die folgenden Symbole erscheinen auf den Registerkarten **Zuordnungen**, **Aufrufstruktur** und **Funktionen**:

- ![Das Symbol für einen Werttyp](../profiling/media/valuetypeicon.png "Das Symbol für einen Werttyp") – Ein Werttyp wie z. B. „Integer“

- ![Das Symbol für eine Werttypsammlung](../profiling/media/valuetypecollectionicon.png "Das Symbol für eine Werttypsammlung") – Eine Werttypsammlung wie beispielsweise ein Array aus Ganzzahlen

- ![Das Symbol für einen Verweistyp](../profiling/media/referencetypeicon.png "Das Symbol für einen Verweistyp") – Ein Verweistyp wie z. B. eine Zeichenfolge

- ![Das Symbol für eine Verweistypsammlung](../profiling/media/referencetypecollectionicon.png "Das Symbol für eine Verweistypsammlung") – Eine Verweistypsammlung wie beispielsweise ein Array aus Zeichenfolgen

### <a name="call-tree"></a>Aufrufstruktur

![Die Ansicht „Aufrufstruktur“](../profiling/media/calltreelight.png "Die Ansicht „Aufrufstruktur“")

Die Ansicht **Aufrufbaum** zeigt die Funktionsausführungspfade an, die Objekte mit einem hohen Arbeitsspeicherverbrauch enthalten.

- Die Spalte **Funktionsname** zeigt den Prozess oder den Namen der Funktion an, die Objekte mit hohem Arbeitsspeicherverbrauch enthält. Die Anzeige basiert auf der Knotenebene, auf der die Untersuchung erfolgt.
- Die Spalten **Gesamt (Zuordnungen)** und **Gesamtgröße (Byte)** zeigen die Anzahl von zugeordneten Objekten und die Menge von Arbeitsspeicher, die von einer Funktion und allen von ihr aufgerufenen Funktionen belegt wird.
- Die Spalten **Selbst (Zuordnungen)** und **Automatische Größe (Bytes)** zeigen die Anzahl von zugeordneten Objekten und die Gesamtmenge an Arbeitsspeicher, die von einer einzelnen ausgewählten Funktion oder dem Zuordnungstyp belegt wird.
- Die Spalte **Durchschnittliche Größe (Bytes)** zeigt die gleichen Informationen wie in der Ansicht **Zuordnungen** an.
- Die Spalte **Modulname** zeigt das Modul an, das die aufrufende Funktion oder den aufrufenden Prozess enthält.

   ![Erweiterter langsamster Pfad](../profiling/media/hotpathlight.png "Erweiterter langsamster Pfad")

- Wenn Sie auf die Schaltfläche **Langsamsten Pfad erweitern** klicken, wird ein Funktionsausführungspfad hervorgehoben, der viele Objekte enthält, die Arbeitsspeicher belegen. Der Algorithmus startet beim ausgewählten Knoten, hebt den Pfad der meisten Zuordnungen hervor und unterstützt Sie bei der Untersuchung.
- Die Schaltfläche **Langsamsten Pfad anzeigen** blendet das Flammensymbol ein oder aus, das zeigt, welche Knoten Teil des langsamsten Pfads sind.

### <a name="functions"></a>Funktionen

![Die Ansicht „Funktionen“](../profiling/media/functionslight.png "Die Ansicht „Funktionen“")

Mit der Ansicht **Funktionen** können Sie sich Prozesse, Module und Funktionen anzeigen lassen, die Arbeitsspeicher belegen.

- In der Spalte **Name** werden Prozesse als Knoten der obersten Ebene angezeigt. Unterhalb der Prozesse befinden sich die Module und darunter die Funktionen.
- Diese Spalten zeigen die gleichen Informationen an wie in den Ansichten **Zuordnung** und **Aufrufstruktur**:

  - **Gesamt (Zuordnungen)**
  - **Selbst (Zuordnungen)**
  - **Gesamtgröße (Bytes)**
  - **Automatische Größe (Bytes)**
  - **Durchschnittliche Größe (Bytes)**

### <a name="collection"></a>Auflistung

![Die Ansicht „Sammlung“](../profiling/media/collectionlight.png "Die Ansicht „Sammlung“")

In der Ansicht **Sammlung** können Sie sehen, wie viele Objekte während der Garbage Collection gesammelt oder beibehalten wurden. Hier finden Sie auch zwei Kreisdiagramme, mit denen die Informationen zu den Objekten nach Typ grafisch dargestellt werden.

- In der Spalte **Collected** (Gesammelt) wird die Anzahl der Objekte angezeigt, die vom Garbage Collector erfasst wurden.
- Die Spalte **Survived** (Verblieben) zeigt, wie viele Objekte nach der Ausführung des Garbage Collectors noch vorhanden waren.

### <a name="filtering-tools"></a>Filtertools

Die Ansichten **Zuordnungen**, **Aufrufstruktur** und **Funktionen** enthalten alle die Optionen **Nur eigenen Code anzeigen** und **Nativen Code anzeigen** und ein Filterfeld.

- **Nur eigenen Code anzeigen**: Damit Sie sich auf den eigenen Code konzentrieren können, werden Systeme, Frameworks und anderer nicht vom Benutzer stammender Code hinter Frames ( **[Externer Code]** ) verborgen. Weitere Informationen finden Sie unter [Funktion „Nur eigenen Code anzeigen“ verwenden, um nur eigenen Code zu debuggen](../debugger/just-my-code.md).
- **Nativen Code anzeigen**: Zeigt nativen Code in der Analyse an, einschließlich Code, der nicht vom Benutzer stammt.
- Mit dem Filterfeld können Sie basierend auf dem angegebenen Wert die Spalten **Name** oder **Funktionsname** filtern. Geben Sie einen Zeichenfolgenwert in das Feld ein. Die Tabelle zeigt anschließend nur Typen an, die diese Zeichenfolge enthalten.
