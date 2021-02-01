---
title: Filter für die Leistungsberichtansicht | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Profilerberichtsansicht. Diese befindet sich oben im Leistungsberichtsfenster.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 79fb4b7cf7a5df4b2077a2145172d24acdbf86cb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722736"
---
# <a name="performance-report-view-filter"></a>Filter für die Leistungsberichtansicht
Das Fenster für den **Filter für die Profilerstellungsberichtsansicht** befindet sich am oberen Rand des **Leistungsberichtsfensters**. Wenn es nicht angezeigt wird, klicken Sie auf die Schaltfläche **Filter anzeigen**.

 Sie können jede Filterklausel ändern, um Ihre Suchergebnisse zu verfeinern. Die folgenden Spalten sind im Filtergenerator verfügbar.

|Element filtern|Beschreibung|
|-----------------|-----------------|
|Und/Oder|Wählen Sie **Und** aus, wenn diese Klausel und die nächste Klausel beide wahr sein müssen, um zu einer Übereinstimmung zu führen. Wählen Sie **Oder** aus, wenn diese Klausel oder die nächste Klausel wahr sein kann, um zu einer Übereinstimmung zu führen.|
|Feld|Wählen Sie das zu verwendende Feld in der Filterklausel aus der Liste der Datenfelder aus, die in der aktuellen Berichtsdatei verfügbar sind.|
|Operator|Wählen Sie den Operator aus, der die Beziehung angibt, die Sie zwischen dem Feld und dem Wert herstellen möchten.<br /><br /> = Gleich<br /><br /> <> Ungleich<br /><br /> < Kleiner als<br /><br /> > Größer als<br /><br /> <= Kleiner als oder gleich<br /><br /> >= Größer als oder gleich|
|Wert|Wählen Sie den Wert aus, nach dem gesucht werden soll, oder geben Sie den Wert ein. In einigen Feldern werden die verfügbaren Werte für das Feld aufgeführt.|

 Sie können Filterklauseln hinzufügen, bis Sie glauben, dass Sie durch den Filter die besten Ergebnisse erhalten. Klicken Sie auf **Filter ausführen**, um den Filter auf die Datendatei anzuwenden.

 Aus der Berichtsansicht **Markierungen** können Sie Filterklauseln generieren, um die Daten in den Berichtsansichten auf die Daten zu begrenzen, die zwischen zwei Markierungen gesammelt werden. Wählen Sie die Eingaben, die Sie zum Beginn und Ende der Berichtsdaten verwenden möchten, klicken Sie dann mit der rechten Maustaste und wählen Sie entweder **Filter für Markierungen hinzufügen** oder **Filter für Timestamps hinzufügen**. Beide Filter beschränken die Daten in der aktuellen Datendatei auf denselben Zeitraum. **Filter für Markierungen hinzufügen** kann auf andere VSP-Dateien angewendet werden.

 Klicken Sie zum Speichern des Filters auf **Filter exportieren** in der Symbolleiste **Leistungsbericht**, und geben Sie dann einen Speicherort und einen Namen für die *VSPF*-Datei an. Um einen zuvor gespeicherten Filter zu laden, klicken Sie auf **Filter importieren**, und suchen Sie die gespeicherte Filterdatei. Filterdateien können auch verwendet werden, um Datendateien auf Computern zu filtern, auf denen eigenständigen Profilerstellungstools installiert sind. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Siehe auch
- [Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
