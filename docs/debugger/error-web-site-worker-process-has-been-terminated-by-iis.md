---
title: Websiteworkerprozess wurde von IIS beendet | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5991bf0b14cf4952303dba599ad47e4c8fd27a9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852412"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Fehler: Websiteworkerprozess wurde von IIS beendet
Der Debugger hat die Codeausführung auf der Website beendet. Dadurch gehen die Internetinformationsdienste (IIS) davon aus, dass der Arbeitsprozess nicht mehr reagiert. Folglich wurde der Arbeitsprozess von IIS beendet.

 Um das Debuggen fortzusetzen, müssen Sie IIS so konfigurieren, dass der Arbeitsprozess fortgesetzt wird. Diese Fehlermeldung wird erst ab IIS 7 angezeigt.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>So konfigurieren Sie IIS 7 für die Fortsetzung des Arbeitsprozesses

1. Öffnen Sie das Fenster **Verwaltung**.

   1. Klicken Sie auf das Menü **Start**, und wählen Sie anschließend **Systemsteuerung** aus.

   2. Wählen Sie in der **Systemsteuerung** ggf. die Option **Zur klassischen Ansicht wechseln**, und doppelklicken Sie auf **Verwaltung**.

2. Doppelklicken Sie im Fenster **Verwaltung** auf **Internetinformationsdienste-Manager**.

    Der IIS-Manager wird geöffnet.

3. Erweitern Sie im Bereich **Verbindungen** ggf. den Knoten \<computer name>.

4. Klicken Sie unter dem Knoten \<computer name> auf **Anwendungspools**.

5. Klicken Sie in der Liste **Anwendungspools** mit der rechten Maustaste auf den Namen des Pools, in dem Ihre Anwendung ausgeführt wird, und klicken Sie dann auf **Erweiterte Einstellungen**.

6. Suchen Sie im Dialogfeld **Erweiterte Einstellungen** den Bereich **Prozessmodell**, und führen Sie eine der folgenden Aktionen aus:

   - Legen Sie **Ping aktiviert** auf **False** fest.

   - Legen Sie **Maximale Ping-Antwortzeit** auf einen Wert größer als 90 Sekunden fest.

     Wenn Sie **Ping aktiviert** auf **False** festlegen, überprüft IIS nicht mehr, ob der Arbeitsprozess ausgeführt wird. Der Arbeitsprozess bleibt bis zum Ende des Debugprozesses aktiv. Wenn Sie **Maximale Ping-Antwortzeit** auf einen hohen Wert festlegen, setzt IIS die Überwachung des Arbeitsprozesses fort.

7. Klicken Sie auf **OK**, um das Dialogfeld **Erweiterte Einstellungen** zu schließen.

8. Schließen Sie den IIS-Manager und das Fenster **Verwaltung**.

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)