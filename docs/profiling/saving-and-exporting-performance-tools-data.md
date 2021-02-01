---
title: Speichern und Exportieren von Daten aus Leistungstools | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie gefilterte oder ungefilterte Ansichten der Profilerstellungs-Datendateien (.vsp) als Dateien mit analysierten Berichten (.vsps) speichern können.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b340abd81cef7183c2ba25af58ae432d8c80e6a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720151"
---
# <a name="save-and-export-performance-tools-data"></a>Speichern und Exportieren von Daten aus Leistungstools
In diesem Artikel wird das Speichern und Exportieren von Leistungsdatendateien beschrieben.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Vorgehensweise: Speichern von Leistungsdatendateien als analysierte Berichtsdateien
 Sie können gefilterte oder ungefilterte Ansichten der Profilerstellungs-Datendateien (*VSP*) als analysierte Berichtsdateien (*VSPS*) speichern. Eine analysierte Berichtsdatei kann im Berichtsansichtsfenster angezeigt werden und ist erheblich kleiner als die ursprüngliche *VSP*-Datei. Sie können jedoch keine Filter auf die Daten einer *VSPS*-Datei anwenden. Sie können über den Leistungs-Explorer eine analysierte Berichtsdatei erstellen, ohne die Datei in der integrierten Entwicklungsumgebung (IDE) öffnen zu müssen, oder Sie öffnen und filtern die *VSP*-Datei und speichern anschließend die Ergebnisse.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Speichern eines analysierten Leistungsberichts über den Leistungs-Explorer

1. Klicken Sie unter **Berichte** mit der rechten Maustaste auf die Profilerstellungs-Datendatei, die Sie analysieren möchten, und klicken Sie anschließend auf **Analysierte Daten speichern**.

2. Legen Sie im Dialogfeld **Analysierte Daten speichern** das Verzeichnis fest und geben Sie den Dateinamen ein.

3. Klicken Sie auf **Speichern**.

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Speichern eines analysierten Leistungsberichts über das Fenster „Berichtsansicht“

1. Öffnen Sie die Profilerstellungs-Datendatei (*VSP*) im Berichtsansichtsfenster.

2. (Optional) Wenden Sie einen Filter auf die Daten an. Weitere Informationen finden Sie unter [Filter für die Leistungsberichtsansicht](../profiling/performance-report-view-filter.md).

3. Klicken Sie auf der Symbolleiste der Berichtsanzeige auf **Analysierte Daten speichern** .

4. Legen Sie im Dialogfeld **Analysierte Daten speichern** das Verzeichnis fest und geben Sie den Dateinamen ein.

5. Klicken Sie auf **Speichern**.

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Vorgehensweise: Exportieren von Berichten der Profilerstellungstools in eine XML- oder CSV-Datei
 Sie können eine oder mehrere Berichtsansichten aus einer *VSP*-Datei oder einer *VSPS*-Profilerstellungs-Datendatei als eine durch Trennzeichen getrennte Datei oder als XML-Datei exportieren. Sie können die Daten im Fenster „Berichtsansicht“ filtern, bevor Sie exportieren, oder Sie können Berichtsansichten der gesamten Datendatei aus dem Fenster **Leistungs-Explorer** exportieren.

> [!NOTE]
> Sie können auch ausgewählte Zeilen aus dem Fenster „Berichtsanzeige“ als durch Tabstopps getrennte Werte kopieren und einfügen.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Exportieren von Leistungsberichten aus dem Fenster „Leistungs-Explorer“

1. Wählen Sie im **Leistungs-Explorer** den Bericht aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Exportieren** aus.

     Das Dialogfeld **Bericht exportieren** wird angezeigt.

2. Wählen Sie die Berichtsansichten aus, die Sie exportieren möchten.

3. Geben Sie unter **Prefix report with**(Präfixreport mit) das Präfix an, dass Sie dem Berichtsnamen hinzufügen möchten.

4. Geben Sie unter **Speicherort des exportierten Berichts** das Verzeichnis an.

5. Wählen Sie unter **Format des exportierten Berichts**(durch Trennzeichen getrennt) (\*.csv\)) oder XML-Daten (\*.xml\)) aus.

6. Klicken Sie auf **Exportieren**.

     Jede Berichtsansicht wird in einer separaten Datei mit dem Namen \<prefix>_\<report view name>.\<csv&#124;xml> gespeichert.

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>So exportieren Sie Leistungsberichte aus dem Fenster „Berichtsansicht“

1. Öffnen Sie die *VSP*-Datei im Berichtsansichtsfenster.

2. (Optional) Wenden Sie einen Filter auf die Daten an. Weitere Informationen finden Sie unter [Filter für die Leistungsberichtsansicht](../profiling/performance-report-view-filter.md).

3. Klicken Sie auf der Symbolleiste der Berichtsanzeige auf **Bericht exportieren** .

4. Wählen Sie die Berichtsansichten aus, die Sie exportieren möchten.

5. Geben Sie unter **Prefix report with**(Präfixreport mit) das Präfix an, dass Sie dem Berichtsnamen hinzufügen möchten.

6. Geben Sie unter **Speicherort des exportierten Berichts** das Verzeichnis an.

7. Wählen Sie unter **Format des exportierten Berichts** (durch Trennzeichen getrennt) (\*.csv) oder XML-Daten (\*.xml) aus.

8. Klicken Sie auf **Exportieren**.

     Jede Berichtsansicht wird in einer separaten Datei mit dem Namen \<prefix>_\<report view name>.\<csv&#124;xml> gespeichert.

## <a name="see-also"></a>Weitere Informationen
- [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md)
- [Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)
- [Vergleichen von Leistungsdatendateien](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
