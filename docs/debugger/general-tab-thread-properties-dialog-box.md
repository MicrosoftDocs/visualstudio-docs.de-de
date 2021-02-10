---
title: Registerkarte „Allgemein“, Dialogfeld „Threadeigenschaften“ | Microsoft-Dokumentation
description: Sehen Sie sich das Dialogfeld „Threadeigenschaften“ an, um Informationen zu einem Thread zu erhalten, einschließlich des Modulnamens, der Thread-ID, der Prozess-ID, des Threadstatus, der Warteursache und der CPU-Zeit.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02ba7d14dad8e4755170ffca7853aa9cc6c85a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870544"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Threadeigenschaften"
Verwenden Sie dieses Dialogfeld, um mehr über einen bestimmten Thread zu erfahren. Verschieben zum Öffnen dieses Dialogfelds den Fokus auf ein [Threadansichtsfenster](../debugger/threads-view.md), oder öffnen Sie die [Meldungsansicht](../debugger/messages-view.md), und erweitern Sie eine Meldung. Wählen Sie in der Struktur einen beliebigen Threadknoten und anschließend im Menü **Ansicht** die Option **Eigenschaften** aus.

 Das Dialogfeld **Threadeigenschaften** enthält einen einzelnen Bereich: die Registerkarte **Allgemein**. Die folgenden Einstellungen sind verfügbar:

|Eintrag|Beschreibung|
|-----------|-----------------|
|**Modulname**|Der Name des Moduls.|
|**Thread-ID**|Die eindeutige ID dieses Threads. Hinweis: Die Nummern von Thread-IDs werden wiederverwendet und identifizieren einen Thread nur während dessen Lebensdauer.|
|**Prozess-ID**|Die eindeutige ID dieses Prozesses. Die Nummern von Prozess-IDs werden wiederverwendet und identifizieren einen Prozess nur während dessen Lebensdauer. Der Prozessobjekttyp wird erstellt, wenn ein Programm ausgeführt wird. Alle Threads in einem Prozess teilen sich den gleichen Adressraum und haben Zugriff auf die gleichen Daten. Wählen Sie diesen Wert aus, um die Eigenschaften der Prozess-ID anzuzeigen.|
|**Threadzustand**|Der aktuelle Zustand des Threads. Ein ausgeführter Thread verwendet einen Prozessor. Ein Standbythread steht kurz davor, einen Prozessor zu verwenden. Ein bereiter Thread wartet auf die Verwendung eines Prozessors, da gerade keiner frei ist. Ein Thread im Übergangszustand wartet auf die Ausführung einer Ressource, also beispielsweise darauf, dass der zugehörige Ausführungsstapel vom Datenträger aus eingebunden wird. Von einem wartenden Thread wird der Prozessor nicht benötigt, da er darauf wartet, dass ein Peripherievorgang abgeschlossen oder eine Ressource frei wird.|
|**Warteursache**|Nur relevant, wenn sich der Thread im Wartezustand befindet. Für die Kommunikation mit geschützten Subsystemen werden Ereignispaare verwendet.|
|**CPU-Zeit**|Die gesamte CPU-Zeit, die für diesen Prozess und die zugehörigen Threads aufgewendet wurde. Entspricht der Summe aus Benutzerzeit und privilegierter Zeit.|
|**Benutzerzeit**|Die insgesamt verstrichene Zeit, während der von diesem Thread Code im Benutzermodus ausgeführt wurde. Anwendungen werden im Benutzermodus ausgeführt. Gleiches gilt für Subsysteme wie den Fenster-Manager und die Grafik-Engine.|
|**Privilegierte Zeit**|Die insgesamt verstrichene Zeit, während der von diesem Thread Code im privilegierten Modus ausgeführt wurde. Wenn ein Windows-Systemdienst aufgerufen wird, wird dieser häufig im privilegierten Modus ausgeführt, um auf private Systemdaten zugreifen zu können. Solche Daten sind vor dem Zugriff durch Threads im Benutzermodus geschützt. Systemaufrufe können explizit aber auch implizit sein, etwa im Falle eines Seitenfehlers oder eines Interrupts.|
|**Verstrichene Zeit**|Die gesamte verstrichene Zeit (in Sekunden), während der dieser Thread ausgeführt wurde.|
|**Aktuelle Priorität**|Die aktuelle dynamische Priorität dieses Threads. Threads innerhalb eines Prozesses können ihre eigene Basispriorität in Relation zur Basispriorität des Prozesses erhöhen und verringern.|
|**Basispriorität**|Die aktuelle Basispriorität dieses Threads.|
|**Startadresse**|Die virtuelle Startadresse für diesen Thread.|
|**Benutzer-PC**|Der Benutzerprogrammzähler für den Thread.|
|**Kontextwechsel**|Die Anzahl von Wechseln zwischen Threads. Threadwechsel können innerhalb eines einzelnen Prozesses oder prozessübergreifend auftreten. Ein Threadwechsel kann ausgelöst werden, wenn ein Thread Informationen von einem anderen Thread anfordert oder wenn ein Thread mit einer höheren Priorität ausführungsbereit und dem ursprünglichen Thread vorweggenommen wird.|