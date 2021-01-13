---
title: Deaktivieren des Just-In-Time-Debuggers | Microsoft-Dokumentation
description: Das Dialogfeld „Just-In-Time Debugger“ öffnet sich möglicherweise, wenn in einer App ein Fehler auftritt. Erfahren Sie, was Sie tun können, wenn dies geschieht, und Möglichkeiten, um dies zu verhindern.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7904b4bbf56c0a547d9f7b1e94bb46af8dd48d98
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903895"
---
# <a name="disable-the-just-in-time-debugger"></a>Deaktivieren des Just-In-Time-Debuggers

Das Dialogfeld „Just-In-Time Debugger“ öffnet sich möglicherweise, wenn bei einer ausgeführten App ein Fehler auftritt, der ein Fortsetzen der Ausführung verhindert.

Der Just-In-Time-Debugger bietet Ihnen die Möglichkeit, Visual Studio zu starten, um den Fehler zu beheben. Damit Sie ausführliche Fehlerinformationen anzeigen oder den Fehler beheben können, muss Visual Studio oder ein anderer ausgewählter Debugger installiert sein.

Wenn Sie bereits Visual Studio verwenden und den Fehler beheben möchten, sehen Sie sich [Debuggen mit dem Just-In-Time-Debugger in Visual Studio](../debugger/debug-using-the-just-in-time-debugger.md) an. Wenn Sie den Fehler nicht beheben können oder das Öffnen des Just-In-Time-Debuggers verhindern möchten, können Sie das [Just-In-Time-Debuggen in Visual Studio deaktivieren](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Wenn Visual Studio deinstalliert wurde, müssen Sie möglicherweise das [Just-In-Time-Debuggen über die Windows-Registrierung deaktivieren](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Wenn Visual Studio nicht installiert ist, können Sie das Just-In-Time-Debuggen verhindern, indem Sie das Skriptdebugging oder das serverseitige Debuggen deaktivieren.

- Wenn Sie versuchen, eine Web-App auszuführen, deaktivieren Sie das Skriptdebugging:

  Klicken Sie unter Windows in der **Systemsteuerung** auf **Netzwerk und Internet** > **Internetoptionen**, und aktivieren Sie **Skriptdebugging deaktivieren (Internet Explorer)** und **Skriptdebugging deaktivieren (Andere)** . Die genauen Schritte und Einstellungen hängen von Ihrer Windows-Version und Ihrem Browser ab.

  ![JIT-Internetoptionen](../debugger/media/jitinternetoptions.png "JIT-Internetoptionen")

- Wenn Sie eine ASP.NET-Web-App in den IIS hosten, deaktivieren Sie das serverseitige Debuggen:

  1. Doppelklicken Sie im IIS-Manager in der **Ansicht „Features“** im Abschnitt **ASP.NET** auf **.NET-Kompilierung**, oder klicken Sie einmal darauf und dann im Bereich **Aktionen** auf **Feature öffnen**.
  1. Klicken Sie unter **Verhalten** > **Debuggen** auf **False**. Die Schritte unterscheiden sich bei älteren Versionen der IIS.

Nachdem Sie das Just-In-Time-Debuggen deaktiviert haben, kann die App den Fehler möglicherweise behandeln und ordnungsgemäß ausgeführt werden.

Wenn bei der App weiterhin ein unbehandelter Fehler auftritt, wird möglicherweise eine Fehlermeldung angezeigt, oder die App stürzt ab oder reagiert nicht. Die App wird erst normal dann ausgeführt, wenn der Fehler behoben wurde. Sie können sich an den Besitzer der App wenden und ihn bitten, den Fehler zu beheben.
