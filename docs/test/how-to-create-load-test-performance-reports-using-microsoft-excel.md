---
title: Erstellen von Leistungsberichten für Auslastungstests mit Excel
description: Lernen Sie, Microsoft Excel-Auslastungstestberichte zu generieren, die auf mindestens zwei Testergebnissen basieren. Sie können Ausführungsvergleichs- und Trendberichte erstellen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a89818630258aab42535fb4256fa3e844b0c6878
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442429"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Vorgehensweise: Erstellen von Leistungsberichten für Auslastungstests mit Microsoft Excel

Sie können Microsoft Excel-Auslastungstestberichte generieren, die auf zwei oder mehr Testergebnissen basieren.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Zwei Typen von Auslastungstestberichten sind verfügbar:

- **Vergleich ausführen;** Mit diesem Befehl wird eine Reihe von Berichten erstellt, in denen die Daten von zwei Auslastungstestergebnissen mithilfe von Tabellen und Säulendiagrammen verglichen werden.

- **Trend:** Eine Trendanalyse kann für zwei oder mehr Auslastungstestergebnisse generiert werden. Die Ergebnisse werden mit Liniendiagrammen angezeigt, doch die Daten sind in PivotTables enthalten.

> [!TIP]
> Sie können auch manuell Microsoft Word-Berichte erstellen, indem Sie Daten aus der Zusammenfassungsansicht, Diagrammansicht und Tabellenansicht kopieren und einfügen. Weitere Informationen finden Sie unter [Vorgehensweise: Manuelles Erstellen von Leistungsberichten für Auslastungstests mit Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Beide Berichte können verwendet werden, um Leistungsdaten für Projektbeteiligte freizugeben, und liefern Informationen dazu, ob die Gesamtleistung und Integrität des Systems besser oder schlechter wird.

Berichtsdefinitionen werden in der Auslastungstestdatenbank gespeichert. Wenn ein Bericht gespeichert wird, wird die Definition für den Bericht in der Datenbank gespeichert und kann später wieder verwendet werden.

Zudem kann die Excel-Arbeitsmappe für Projektbeteiligte freigegeben werden, damit diese zum Anzeigen des Berichts keine Verbindung mit der Datenbank herstellen müssen.

> [!NOTE]
> Sie können die Excel-Arbeitsmappe freigeben, aber nur Benutzer, die Visual Studio auf ihrem Computer installieren haben, können Arbeitsblätter ändern. Für andere Benutzer wird die Option **Auslastungstestbericht** im **Office**-Menüband nicht angezeigt. Sie haben jedoch die Möglichkeit, die Arbeitsmappe anzuzeigen.

Die folgende Abbildung zeigt ein Beispiel für einen Bericht, in dem ein Zusammenhang zwischen einer Abnahme der Transaktionsgeschwindigkeit (Einkaufskorb aktualisieren) und der rückläufigen Entwicklung des Indikators "% Prozessor" dargestellt wird. Dies weist auf ein potenzielles Problem im Anwendungscode hin (nicht in der Datenbank oder im Netzwerk) und eignet sich für die Diagnose mit dem ASP.NET-Profiler.

![Mögliches Problem im Anwendungscode](../test/media/lt_excel.png)

Excel-Berichte können entweder im **Auslastungstest-Analyzer** durch Klicken auf die Schaltfläche **Excel-Bericht erstellen** in der Symbolleiste oder in Excel über die Option **Auslastungstestbericht** auf der Registerkarte **Auslastungstest** des **Office**-Menübands generiert werden.

> [!NOTE]
> Wenn Sie einem Auslastungstest Kommentare hinzufügen, werden sie im Excel-Bericht angezeigt.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>So generieren Sie mit Excel Vergleichsberichte für Auslastungstests

1. Bevor Sie einen Bericht generieren, müssen Sie zuerst einen Auslastungstest ausführen.

2. Für die Erstellung von Excel-Auslastungstestberichten stehen Ihnen zwei Möglichkeiten zur Verfügung:

   - Nachdem Sie einen Auslastungstest abgeschlossen haben, klicken Sie auf der Seite **Auslastungstestergebnisse** auf der Symbolleiste auf die Schaltfläche **Excel-Bericht erstellen**.

      > [!NOTE]
      > Wenn die Schaltfläche **Excel-Bericht erstellen** auf der Symbolleiste des **Webleistungstest-Ergebnisviewers** deaktiviert ist, müssen Sie ggf. Microsoft Excel einmal ausführen, damit eine Aktivierung erfolgt. Wenn Visual Studio Enterprise installiert wird, wird das Visual Studio Enterprise-Auslastungstest-Add-In auf den Computer für Microsoft Excel kopiert. Microsoft Excel muss jedoch ausgeführt werden, um den Installationsvorgang für das Add-In abzuschließen.

      Microsoft Excel wird geöffnet, und der **Assistent zum Generieren eines Auslastungstestberichts** wird angezeigt.

   **OR**

   1. Öffnen Sie Microsoft Excel, wählen Sie die Registerkarte **Auslastungstest** im **Office**-Menüband aus, und klicken Sie anschließend auf **Auslastungstestbericht**.

       Der **Assistent zum Generieren eines Auslastungstestberichts** wird angezeigt.

   2. Geben Sie auf der Seite **Datenbank auswählen, die Auslastungstests enthält** unter **Servername** den Namen des Servers ein, der die Auslastungstestergebnisse enthält.

   3. Wählen Sie in der Dropdownliste **Datenbankname** die Datenbank aus, die die Auslastungstestergebnisse enthält.

3. Vergewissern Sie sich, dass auf der Seite **Wie soll der Bericht generiert werden** die Option **Bericht erstellen** ausgewählt ist, und klicken Sie auf **Weiter**.

4. Vergewissern Sie sich, dass auf der Seite **Welchen Berichttyp möchten Sie generieren** die Option **Vergleich ausführen** ausgewählt ist, und klicken Sie auf **Weiter**.

5. Geben Sie auf der Seite **Auslastungstestbericht-Details eingeben** einen Namen für den Bericht in das Feld **Berichtsname** ein.

6. Wählen Sie den Auslastungstest aus, für den Sie den Bericht generieren möchten, und klicken Sie auf **Weiter**.

7. Wählen Sie auf der Seite **Wählen Sie die Läufe für den Bericht aus** unter **Mindestens einen Lauf auswählen, der dem Bericht hinzugefügt wird** zwei Auslastungstestergebnisse aus, die Sie im Bericht vergleichen möchten, und klicken Sie auf **Weiter**.

   > [!NOTE]
   > Ein Vergleichsbericht kann nur für zwei Auslastungstestberichte generiert werden. Wenn Sie entweder ein Auslastungstestergebnis oder mehr als zwei Auslastungstestergebnisse auswählen, wird eine Warnmeldung angezeigt.

8. Auf der Seite **Indikatoren für den Bericht auswählen** steht Ihnen unter **Mindestens einen Indikator auswählen, der dem Bericht hinzugefügt wird** eine erweiterbare Liste von Indikatoren zur Verfügung, mit der der Bericht angepasst werden kann. Wählen Sie die Indikatoren aus, die Sie für die zwei ausgewählten Testläufe im Bericht vergleichen möchten, und klicken Sie auf **Fertig stellen**.

9. Der Excel-Arbeitsmappenbericht wird mit den folgenden Arbeitsblattregisterkarten generiert:

   - **Inhaltsverzeichnis:** Zeigt den Namen des Auslastungstestberichts an und enthält ein Inhaltsverzeichnis mit Links zu den verschiedenen Registerkarten im Bericht.

   - **Läufe:** Enthält Details zu den zwei Testläufen, die im Bericht verglichen werden.

   - **Testvergleich:** Stellt in einem Balkendiagramm Details zu Leistungsabnahmen und -verbesserungen zwischen den zwei verglichenen Testläufen bereit.

   - **Seitenvergleich:** Stellt in einem Balkendiagramm und als Prozentzahlen Leistungsvergleichsdaten zu den verschiedenen Seiten in den zwei Testläufen bereit.

   - **Computervergleich:** Stellt Vergleichsdaten auf Grundlage der verwendeten Computer für die zwei Testläufe bereit.

   - **Fehlervergleich:** Vergleicht die bei den zwei Testläufen gefundenen Fehlertypen und die Anzahl von Vorkommen.

     > [!TIP]
     > Für Auslastungstests und Webleistungstests sind verschiedene Eigenschaften verfügbar, mit denen detailliertere Berichte erstellt werden können. Für die Seitenanforderung werden zwei Eigenschaften in den Berichten dargestellt: "Ziel" und "Berichtsname". Seitenantwortzeiten werden für das Ziel angezeigt, und der Berichtsname wird in den Berichten anstelle der URL verwendet. In den Testlaufeinstellungen eines Auslastungstests wird unter "Indikatorensätze verwalten" die Eigenschaft "Computertags" in den Berichtscomputernamen dargestellt. Dies ist hilfreich, um die Rolle eines bestimmten Computers im Bericht zu beschreiben.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>So generieren Sie mit Excel Trendberichte für Auslastungstests

1. Bevor Sie einen Bericht generieren, müssen Sie einen Auslastungstest ausführen.

2. Für die Erstellung von Excel-Auslastungstestberichten stehen Ihnen zwei Möglichkeiten zur Verfügung:

   - Nachdem Sie einen Auslastungstest abgeschlossen haben, klicken Sie auf der Seite **Auslastungstestergebnisse** auf der Symbolleiste auf die Schaltfläche **Excel-Bericht erstellen**.

      > [!NOTE]
      > Wenn die Schaltfläche **Excel-Bericht erstellen** auf der Symbolleiste des **Webleistungstest-Ergebnisviewers** deaktiviert ist, müssen Sie ggf. Microsoft Excel einmal ausführen, damit eine Aktivierung erfolgt. Wenn Visual Studio Enterprise installiert wird, wird das Visual Studio Enterprise-Auslastungstest-Add-In auf den Computer für Microsoft Excel kopiert. Microsoft Excel muss jedoch ausgeführt werden, um den Installationsvorgang für das Add-In abzuschließen.

      Microsoft Excel wird geöffnet, und der **Assistent zum Generieren eines Auslastungstestberichts** wird angezeigt.

   **OR**

   1. Öffnen Sie Microsoft Excel, wählen Sie die Registerkarte **Auslastungstest** im **Office**-Menüband aus, und klicken Sie anschließend auf **Auslastungstestbericht**.

       Der **Assistent zum Generieren eines Auslastungstestberichts** wird angezeigt.

   2. Geben Sie auf der Seite **Datenbank auswählen, die Auslastungstests enthält** unter **Servername** den Namen des Servers ein, der die Auslastungstestergebnisse enthält.

   3. Wählen Sie in der Dropdownliste **Datenbankname** die Datenbank aus, die die Auslastungstestergebnisse enthält.

3. Vergewissern Sie sich, dass auf der Seite **Wie soll der Bericht generiert werden** die Option **Bericht erstellen** ausgewählt ist, und klicken Sie auf **Weiter**.

4. Vergewissern Sie sich, dass auf der Seite **Welchen Berichttyp möchten Sie generieren** die Option **Trend** ausgewählt ist, und klicken Sie auf **Weiter**.

5. Geben Sie auf der Seite **Auslastungstestbericht-Details eingeben** einen Namen für den Bericht in das Feld **Berichtsname** ein.

6. Wählen Sie den Auslastungstest aus, für den Sie den Bericht generieren möchten, und klicken Sie auf **Weiter**.

7. Wählen Sie auf der Seite **Wählen Sie die Läufe für den Bericht aus** unter **Mindestens einen Lauf auswählen, der dem Bericht hinzugefügt wird** die Auslastungstestergebnisse aus, die Sie im Bericht vergleichen möchten, und klicken Sie auf **Weiter**.

8. Auf der Seite **Indikatoren für den Bericht auswählen** steht Ihnen unter **Mindestens einen Indikator auswählen, der dem Bericht hinzugefügt wird** eine erweiterbare Liste von Indikatoren zur Verfügung, mit der der Bericht angepasst werden kann. Wählen Sie die Indikatoren aus, die Sie für die Trendanalyse vergleichen möchten, und klicken Sie auf **Fertig stellen**.

9. Der Bericht wird mit einem Inhaltsverzeichnis generiert, das Links zu den verschiedenen Excel-Arbeitsmappenregisterkarten im Bericht enthält. Die Links basieren auf den für den Trendbericht ausgewählten Indikatoren. Wenn Sie in Schritt 7 z. B. die Standardindikatoren übernommen haben, werden Daten für jeden der in Schritt 7 aufgeführten Indikatoren generiert und auf separaten Registerkarten in Excel dargestellt. Die für die einzelnen Indikatoren generierten Daten werden in Trenddiagrammen dargestellt.

   > [!TIP]
   > Für Auslastungstests und Webleistungstests sind verschiedene Eigenschaften verfügbar, mit denen detailliertere Berichte erstellt werden können. Für die Seitenanforderung werden zwei Eigenschaften in den Berichten dargestellt: "Ziel" und "Berichtsname". Seitenantwortzeiten werden für das Ziel angezeigt, und der Berichtsname wird in den Berichten anstelle der URL verwendet. In den Testlaufeinstellungen eines Auslastungstests wird unter "Indikatorensätze verwalten" die Eigenschaft "Computertags" in den Berichtscomputernamen dargestellt. Dies ist hilfreich, um die Rolle eines bestimmten Computers im Bericht zu beschreiben.

## <a name="net-security"></a>.NET-Sicherheit

Auslastungstestergebnisse und -berichte enthalten potenziell sicherheitsrelevante Informationen, die für einen Angriff auf Ihren Computer oder Ihr Netzwerk verwendet werden können. Auslastungstestergebnisse und -berichte enthalten Computernamen und Verbindungszeichenfolgen. Seien Sie sich dessen bewusst, wenn Sie Auslastungstestberichte für andere freigeben.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von Berichten zu Auslastungstestergebnissen für Testvergleiche oder die Trendanalyse](../test/compare-load-test-results.md)
