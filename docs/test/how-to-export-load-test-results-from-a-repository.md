---
title: Exportieren von Auslastungstestergebnissen
description: Lernen Sie, Informationen mit dem Dialogfeld „Auslastungstestergebnisse öffnen und verwalten“ in das Ergebnisrepository für Auslastungstests zu exportieren.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a0e7d00949686cd7d52400c2d71123b86d28625b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961507"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Vorgehensweise: Exportieren von Auslastungstestergebnissen aus einem Repository

Alle Informationen, die während eines Auslastungstests erfasst werden, werden im Ergebnisrepository für Auslastungstests gespeichert. Das Ergebnisrepository für Auslastungstests enthält Leistungsindikatordaten und Informationen zu Fehlern. Weitere Informationen finden Sie unter [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Sie können Auslastungstestergebnisse aus dem Auslastungstest-Editor im Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** verwalten. Sie können Auslastungstestergebnisse öffnen, importieren, exportieren und entfernen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>So exportieren Sie Ergebnisse aus einem Repository

1. Öffnen Sie in einem Webleistungs- und Auslastungstestprojekt einen Auslastungstest.

2. Klicken Sie auf der eingebetteten Symbolleiste auf **Ergebnisse öffnen und verwalten**.

     Das Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** wird angezeigt.

3. Wählen Sie unter **Enter a controller name to find load test results** (Controllernamen für die Suche nach Auslastungstestergebnissen eingeben) einen Controller aus. Wählen Sie **\<Local - No controller>** aus, um auf lokal gespeicherte Ergebnisse zuzugreifen.

4. Wählen Sie unter **Show results for the following load test** (Ergebnisse für den folgenden Auslastungstest anzeigen) den Auslastungstest aus, dessen Ergebnisse angezeigt werden sollen. Wählen Sie **\<Show results for all tests>** aus, um alle Ergebnisse für alle Tests anzuzeigen.

     Wenn Auslastungstestergebnisse verfügbar sind, werden diese in der Liste **Auslastungstestergebnisse** angezeigt. Die Spalten lauten **Time**, **Duration**, **User**, **Outcome**, **Test**, and **Description** (Zeit, Dauer, Benutzer, Ergebnis, Test und Beschreibung). **Test** ist der Name des Tests und unter **Beschreibung** wird die optionale Beschreibung angegeben, die vor der Ausführung des Tests hinzugefügt wurde. In der Spalte **Beschreibung** werden die kurzen Beschreibungen angezeigt, die in den **Analysekommentaren** für dieses Testergebnis eingegeben wurden.

5. Klicken Sie in der Liste **Auslastungstestergebnisse** auf ein Ergebnis. Sie können die **UMSCHALTTASTE**, die **STRG**-Taste oder beide Tasten verwenden, um mehr als ein Ergebnis auszuwählen und in eine einzelne Datei zu exportieren.

6. Klicken Sie auf **Exportieren**.

     Das Dialogfeld **Auslastungstestergebnisse exportieren** wird angezeigt.

7. Geben Sie im Feld **Dateiname** einen Namen ein, und klicken Sie dann auf **Speichern**.

     Die Ergebnisse werden in eine Archivdatei exportiert.

    > [!NOTE]
    > Das Dialogfeld **Auslastungstestergebnisse öffnen und verwalten** bleibt geöffnet, nachdem die Ergebnisse angezeigt wurden.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [How to: Löschen von Auslastungstestergebnissen aus einem Repository](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [How to: Importieren von Auslastungstestergebnissen in ein Repository](../test/how-to-import-load-test-results-into-a-repository.md)
