---
title: Codemetrikfenster
ms.date: 12/12/2017
description: Erfahren Sie, wie Sie die Analysedaten von Visual Studio-Codemetriken anzeigen, Filtern, neu anordnen und exportieren. Weitere Informationen finden Sie unter Erstellen von Arbeitsaufgaben basierend auf Code metrikergebnissen.
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c02f5a3b5175be4517a51a6dc477d6e59b38a762
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859566"
---
# <a name="use-the-code-metrics-results-window"></a>Verwenden des Fensters "Code Metrikergebnisse"

Im Fenster **Code Metrikergebnisse** werden die Daten angezeigt, die von der Codemetrikanalyse generiert werden. Weitere Informationen zu den Datenwerten von Codemetriken finden Sie unter [codemetrikwerte](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Anzeigen von Codemetrikergebnissen

Das Fenster **Code Metrikergebnisse** wird automatisch angezeigt, wenn Sie Code Metrikergebnisse generieren. Sie können das Fenster auch jederzeit anzeigen.

Sie können das Fenster Code Metrikergebnisse mithilfe einer der folgenden Menü Sequenzen anzeigen:

- Wählen Sie im Menü **analysieren** die Option **Windows**-  >  **Codemetrikergebnisse** aus.

- Wählen Sie im Menü **Ansicht** die Option **andere** Ergebnisse der Windows-  >  **Codemetriken** aus.

Das Fenster **Code Metrikergebnisse** wird geöffnet, auch wenn es keine Ergebnisse enthält.

### <a name="to-view-code-metrics-details"></a>So zeigen Sie Code metrikdetails an

Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.

## <a name="filter-code-metrics-results"></a>Filtern von Codemetrikergebnissen

Sie können die Ergebnisse filtern, die im Fenster **Code Metrikergebnisse** angezeigt werden, indem Sie die Symbolleiste oben verwenden. Beispielsweise möchten Sie möglicherweise nur die Ergebnisse sehen, die einen verwaltbarkeitsindex unter 65 aufweisen.

Das Dropdown Feld **Filter** enthält die Namen der Ergebnis Spalten. Wenn ein Filter definiert ist, wird er am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten 10 Filter enthalten, die definiert wurden.

### <a name="to-filter-the-code-metrics-results"></a>So filtern Sie die Codemetrikergebnisse

1. Wählen Sie in der Liste **Filter** den Spaltennamen aus.

2. Geben Sie in **Min** den minimalen Wert ein, der angezeigt werden soll.

3. Geben Sie in **Max** den Maximalwert ein, der angezeigt werden soll.

4. Klicken Sie auf die Schaltfläche **Filter anwenden** .

5. Um die Ergebnis Details anzuzeigen, erweitern Sie die Hierarchiestruktur.

## <a name="add-remove-and-rearrange-data-columns"></a>Hinzufügen, entfernen und Neuanordnen von Datenspalten

Sie können Ergebnis Spalten im Fenster **Code Metrikergebnisse** hinzufügen oder entfernen. Außerdem können Sie Ergebnis Spalten neu anordnen, sodass Sie in der gewünschten Reihenfolge angezeigt werden.

### <a name="add-or-remove-a-column"></a>Hinzufügen oder Entfernen einer Spalte

1. Klicken Sie auf die Schaltfläche **Spalten hinzufügen/entfernen** , oder klicken Sie mit der rechten Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten**

1. Aktivieren bzw. deaktivieren Sie im Dialogfeld **Spalten hinzufügen/entfernen** das Kontrollkästchen für die Spalte, die Sie hinzufügen oder entfernen möchten, und wählen Sie dann **OK** aus.

### <a name="rearrange-columns"></a>Spalten neu anordnen

1. Klicken Sie auf die Schaltfläche **Spalten hinzufügen/entfernen** .

1. Wählen Sie im Dialogfeld **Spalten hinzufügen/entfernen** die Spalte aus, die Sie verschieben möchten, und wählen Sie dann entweder den Pfeil nach oben oder den Pfeil nach unten aus.

1. Wenn die Spalte an der gewünschten Position positioniert ist, wählen Sie **OK** aus.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Kopieren von Daten in die Zwischenablage oder Excel

Sie können eine ausgewählte Zeile mit Codemetrikdaten auswählen und als Text Zeichenfolge in die Zwischenablage kopieren, die eine Zeile für den Namen und den Wert jeder Datenspalte enthält. Sie können auch auf **Auswahl in Microsoft Excel öffnen** klicken, um alle Code Metrikergebnisse in eine Excel-Kalkulations Tabelle zu exportieren.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Erstellen eines Arbeits Elements basierend auf Code metrikergebnissen

Sie können ein [Azure Boards](/azure/devops/boards/index?view=vsts&preserve-view=true) Arbeits Element erstellen, das auf Ergebnissen im Fenster " **Code Metrikergebnisse** " basiert. Wenn das Arbeits Element erstellt wird, gibt Visual Studio automatisch einen Titel in das **Titelfeld** ein und codiert Metrikdaten auf der Registerkarte **Verlauf** .

Weitere Informationen zu Azure Boards Arbeitsaufgaben finden Sie unter [Arbeitselemente](/azure/devops/boards/work-items/index?view=vsts&preserve-view=true).

### <a name="to-create-a-work-item-based-on-a-result"></a>So erstellen Sie ein Arbeits Element basierend auf einem Ergebnis

1. Klicken Sie mit der rechten Maustaste auf das Ergebnis.

2. Zeigen Sie auf **Arbeits Element erstellen**, und klicken Sie dann auf den Typ des Arbeits Elements, das Sie erstellen möchten (**Fehler**, **Aufgabe** usw.).

3. Vervollständigen Sie das Arbeits Element Formular, indem Sie alle erforderlichen Felder ausfüllen.

4. Klicken Sie im Menü **Datei** auf **Alle speichern** , um das Arbeits Element zu speichern.

### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler basierend auf einem Ergebnis

1. Klicken Sie auf das Ergebnis, um es auszuwählen.

2. Klicken Sie auf die Schaltfläche **Arbeitsaufgabe erstellen** .

3. Vervollständigen Sie das Arbeits Element Formular, indem Sie alle erforderlichen Felder ausfüllen.

4. Klicken Sie im Menü **Datei** auf **Alle speichern** , um das Arbeits Element zu speichern.

## <a name="see-also"></a>Weitere Informationen

- [Codemetrikwerte](../code-quality/code-metrics-values.md)
- [Gewusst wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
