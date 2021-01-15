---
title: Registerkarte „Speicherplatz“, Dialogfeld „Prozesseigenschaften“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Dialogfeld „Prozesseigenschaften“ in Spy++ beim Debuggen verwenden. Außerdem können Sie die in der Registerkarte „Speicherplatz“ verfügbaren Einstellungen überprüfen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe168f34baf65b00eab59e94afb30e07dfe89b50
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149078"
---
# <a name="space-tab-process-properties-dialog-box"></a>Registerkarte "Speicherplatz", Dialogfeld "Prozesseigenschaften"
Verwenden Sie die Registerkarte **Speicherplatz**, um den Adressraum eines Prozesses zu untersuchen. Verschieben Sie den Fokus der Ansicht auf das Fenster [Prozessansicht](../debugger/processes-view.md), um das [Dialogfeld „Prozesseigenschaften“](../debugger/process-properties-dialog-box.md) anzuzeigen. Wählen Sie einen beliebigen Prozessknoten in der Struktur aus, und wählend Sie anschließend im Menü **Ansicht** die Option **Eigenschaften** aus.

 Auf der Registerkarte **Speicherplatz** sind folgende Einstellungen verfügbar:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Anzeigen, wenn markiert als**|Verwenden Sie dieses Listenfeld, um eine Speicherplatzkategorie (Image, zugeordnet, reserviert oder nicht zugewiesen) auszuwählen.|
|**Ausführbare Bytes**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die von diesem Prozess verwendet werden. Der ausführbare Arbeitsspeicher, der von Programmen ausgeführt werden kann, für den jedoch kein Lese- oder Schreibvorgang durchgeführt werden kann.|
|**Ausführb. Bytes (schreibgeschützt)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die mit schreibgeschützten Eigenschaften und von diesem Prozess verwendet werden. Der Arbeitsspeicher „Exec-read-only“ kann ausgeführt und gelesen werden.|
|**Ausführb. Bytes (lesen/schreiben)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die mit den Eigenschaften Lesen/Schreiben und von diesem Prozess verwendet werden. Der Arbeitsspeicher „Exec-read-write“ ist Speicher, der von Programmen ausgeführt und auch gelesen und geändert werden kann.|
|**Ausführb. Bytes (schreiben/kopieren)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die von Programm ausgeführt und auch gelesen und geschrieben werden können. Dieser Schutztyp wird verwendet, wenn Arbeitsspeicher zwischen Prozessen freigegeben werden muss. Wenn die Freigabeprozesse den Speicher nur lesen, verwenden sie alle denselben Speicher. Wenn ein Freigabeprozess Schreibzugriff anfordert, wird für den Prozess eine Kopie dieses Arbeitsspeichers erstellt.|
|**Bytes (kein Zugriff)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die Prozesse daran hindert, diese zu verwenden. Eine Zugriffsverletzung wird generiert, wenn ein Schreib- oder Leseversuch durchgeführt wird.|
|**Bytes (schreibgeschützt)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die sowohl ausgeführt als auch gelesen werden können.|
|**Bytes (lesen/schreiben)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die Lese- und Schreibvorgänge zulassen.|
|**Bytes (schreiben/kopieren)**|Für die ausgewählte Kategorie ist dies die Summe aller Adressräume, die die Speicherfreigabe für Lesevorgänge, aber nicht für Schreibvorgänge zulassen. Wenn Prozesse diesen Arbeitsspeicher lesen, können sie denselben Arbeitsspeicher teilen. Wenn ein Freigabeprozess jedoch über Lese-/Schreibzugriff auf diesen freigegebenen Speicher verfügen möchte, wird für den Schreibzugriff eine Kopie dieses Speichers erstellt.|