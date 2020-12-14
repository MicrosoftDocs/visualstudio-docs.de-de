---
title: Registerkarte „Allgemein“, Dialogfeld „Prozesseigenschaften“ | Microsoft-Dokumentation
description: Sehen Sie sich die Registerkarte „Allgemein“ an, um Informationen zu einem Prozess zu erhalten, einschließlich des Modulnamens, der Prozess-ID, der Basispriorität, der Threadanzahl, der CPU-Zeit, der Benutzerzeit und der verstrichenen Zeit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4980437c63348050db1a007e8f541e9af9e186cc
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862736"
---
# <a name="general-tab-process-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Prozesseigenschaften"
Verwenden Sie die Registerkarte **Allgemein**, um mehr über einen bestimmten Prozess zu erfahren. Verschieben Sie den Fokus der Ansicht auf das Fenster [Prozessansicht](../debugger/processes-view.md), um das [Dialogfeld „Prozesseigenschaften“](../debugger/process-properties-dialog-box.md) anzuzeigen. Wählen Sie einen beliebigen Prozessknoten in der Struktur aus, und wählend Sie anschließend im Menü **Ansicht** die Option **Eigenschaften** aus.

 Auf der Registerkarte **Allgemein** sind folgende Einstellungen verfügbar:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Modulname**|Der Name des Moduls.|
|**Prozess-ID**|Die eindeutige ID dieses Prozesses. Die Nummern von Prozess-IDs werden wiederverwendet und identifizieren einen Prozess nur während dessen Lebensdauer. Der Prozessobjekttyp wird erstellt, wenn ein Programm ausgeführt wird. Alle Threads in einem Prozess teilen sich den gleichen Adressraum und haben Zugriff auf die gleichen Daten.|
|**Basispriorität**|Die aktuelle Basispriorität dieses Prozesses. Threads innerhalb eines Prozesses können ihre eigene Basispriorität in Relation zur Basispriorität des Prozesses erhöhen und verringern.|
|**Threads**|Die Anzahl der Threads, die aktuell in diesem Prozess aktiv sind|
|**CPU-Zeit**|Die gesamte CPU-Zeit, die für diesen Prozess und die zugehörigen Threads aufgewendet wurde. Diese entspricht der Summe aus Benutzerzeit und privilegierter Zeit.|
|**Benutzerzeit**|Diese Option gibt die kumulierte verstrichene Zeit an, die die nicht im Leerlauf befindlichen Threads dieses Prozesses für die Ausführung von Code im Benutzermodus benötigt haben. Anwendungen werden im Benutzermodus ausgeführt. Das gilt auch für Subsysteme wie den Fenster-Manager und die Grafik-Engine.|
|**Privilegierte Zeit**|Diese Option gibt die insgesamt verstrichene Zeit an, die dieser Prozess im privilegierten Modus in nicht im Leerlauf befindlichen Threads ausgeführt wurde. Die Dienstebene, die Executive-Routinen und der Kernel werden im privilegierten Modus ausgeführt. Die Gerätetreiber für die meisten Geräte (mit Ausnahme von Grafikadaptern und Druckern) werden ebenfalls im privilegierten Modus ausgeführt. Einige Tasks, die Windows für Ihre Anwendung ausführt, werden möglicherweise zusätzlich zur privilegierten Zeit in anderen Subsystemprozessen angezeigt.|
|**Verstrichene Zeit**|Die insgesamt verstrichene Zeit für diesen Vorgang|