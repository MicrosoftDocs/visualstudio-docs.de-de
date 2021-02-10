---
title: Erstellen von Leistungsberichten für Auslastungstests mit Microsoft Word
description: Lernen Sie, Microsoft Word-Auslastungstestberichte manuell zu erstellen, indem Sie Daten aus der Ansicht der Zusammenfassung der Auslastungstestergebnisse und der Diagrammansicht kopieren und einfügen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a7b5246e75b226c04f7dfa2e0e649bcdb85afe8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971881"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Vorgehensweise: Manuelles Erstellen von Leistungsberichten für Auslastungstests mit Microsoft Word

Sie können Microsoft Word-Auslastungstestberichte manuell erstellen, indem Sie Daten aus der Ansicht der Zusammenfassung der Auslastungstestergebnisse und der Diagrammansicht kopieren und einfügen. Die in der Zusammenfassungsansicht und Diagrammansicht dargestellten Daten werden beim Kopieren im HTML-Format eingefügt.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Sie können Nur-Text aus der Tabellenansicht und aus Screenshots aus der Detailansicht in Microsoft Word kopieren. Dann wird jedoch kein HTML-Format angewendet, und zusätzliches Formatieren und Bearbeiten ist erforderlich.

> [!TIP]
> Sie können auch automatisch organisierte Microsoft Excel-Berichte generieren. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Leistungsberichten für Auslastungstests mit Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopieren von Daten aus der Zusammenfassungsansicht

1. Wenn die Zusammenfassungsansicht derzeit nicht angezeigt wird, klicken Sie in den **Auslastungstestergebnissen** auf der Symbolleiste auf **Zusammenfassung**.

2. Klicken Sie in der Zusammenfassungsansicht mit der rechten Maustaste, und wählen Sie **Alles markieren** aus.

3. Klicken Sie in der Zusammenfassungsansicht mit der rechten Maustaste, und wählen Sie **Kopieren** aus. Dadurch werden die Daten aus der Zusammenfassungsansicht im HTML-Format in die Zwischenablage gespeichert.

4. Fügen Sie in Microsoft Word die Zusammenfassungsansichtsdaten an der gewünschten Stelle ein.

5. Sie können nun Teile des kopierten Inhalts entsprechend Ihren Berichtsanforderungen ändern, formatieren und löschen.

## <a name="copy-graph-view-data"></a>Diagrammansichtsdaten kopieren

1. Wenn die Diagrammansicht derzeit nicht angezeigt wird, klicken Sie in den **Auslastungstestergebnissen** auf der Symbolleiste auf **Diagramme**.

2. (Optional) Vergrößern Sie das bestimmte Diagramm, das Sie in Ihr Microsoft Word-Dokument kopieren möchten, wie in der folgenden Abbildung dargestellt. Weitere Informationen finden Sie unter [Vorgehensweise: Vergrößern eines Diagrammbereichs](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Zoomsteuerelement der Diagrammansicht](../test/media/ltest_zoomcontrol.png)

3. Klicken Sie im Diagramm, das Sie in Ihr Microsoft Word-Dokument kopieren möchten, mit der rechten Maustaste, und wählen Sie **Kopieren** aus.

4. Fügen Sie das Diagramm und zugeordnete Tabellendaten in Microsoft Word an der gewünschten Position ein.

    > [!WARNING]
    > Sie können das Diagramm nicht von einem Remotedesktop kopieren und auf einem anderen Computer einfügen, da nur die dem Diagramm zugeordneten Tabelleninformationen und nicht das Diagrammbild kopiert werden. Das Diagrammbild wird im temporären Verzeichnis auf dem Computer gespeichert, von dem es kopiert wurde. Der zweite Computer kann dieses Verzeichnis nicht dereferenzieren.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von Berichten zu Auslastungstestergebnissen für Testvergleiche oder die Trendanalyse](../test/compare-load-test-results.md)
- [Vorgehensweise: Erstellen von Leistungsberichten für Auslastungstests mit Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
