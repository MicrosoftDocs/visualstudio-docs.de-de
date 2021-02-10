---
title: Registerkarte „Auslagerungsdatei“ und Dialogfeld „Prozesseigenschaften“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie die Registerkarte „Auslagerungsdatei“ der Prozesseigenschaften verwenden, um die Auslagerungsdatei eines Prozesses zu untersuchen. Außerdem werden die verfügbaren Einstellungen beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b762fc95d510d5b99a2d4f8f939ef1801b5e70cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891565"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
Verwenden Sie die Registerkarte **Auslagerungsdatei**, um die Auslagerungsdatei eines Prozesses zu untersuchen. Verschieben Sie den Fokus der Ansicht auf das Fenster [Prozessansicht](../debugger/processes-view.md), um das [Dialogfeld „Prozesseigenschaften“](../debugger/process-properties-dialog-box.md) anzuzeigen. Klicken Sie zunächst auf einen beliebigen Prozessknoten in der Struktur und anschließend im Menü **Ansicht** auf **Eigenschaften**.

 Auf der Registerkarte **Auslagerungsdatei** sind folgende Einstellungen verfügbar:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Bytes für Auslagerungsdatei**|Dies ist die aktuelle Anzahl der Seiten, die von diesem Prozess in der Auslagerungsdatei verwendet werden. In der Auslagerungsdatei werden Datenseiten gespeichert, die vom Prozess verwendet werden, aber nicht in anderen Dateien enthalten sind. Die Auslagerungsdatei wird von allen Prozessen verwendet, und der Mangel an Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|
|**Max. Bytes für Auslagerungsdatei**|Dies ist die maximale Anzahl der Seiten, die von diesem Prozess in der Auslagerungsdatei verwendet wurden.|
|**Seitenfehler**|Dies ist die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn von einem Thread auf eine virtuelle Speicherseite verwiesen wird, die nicht auf dessen Arbeitsseite im Hauptspeicher enthalten ist. Die Seite wird daher nicht vom Datenträger abgerufen, wenn sie sich auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie von einem anderen Prozess verwendet wird, für den die Seite freigegeben ist.|