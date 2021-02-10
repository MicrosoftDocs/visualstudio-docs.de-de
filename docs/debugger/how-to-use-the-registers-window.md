---
title: Anzeigen von Registerwerten im Debugger | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Registerwerte im Fenster „Register“ von Visual Studio anzeigen. Während des Debuggens ändern sich die Registerwerte, wenn Code in ihrer App ausgeführt wird.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/19/2018
ms.topic: how-to
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ea0275a5186b58c9b9a07934b95351b597a816f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845008"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Anzeigen von Registerwerten im Fenster „Register“ (C#, C++, Visual Basic, F#)

Der Registerinhalt wird während des Debuggens in Visual Studio im Fenster **Register** angezeigt. Eine allgemeine Einführung in Konzepte hinter Register und die **registriert** Fenster finden Sie unter [Grundlagen des Debuggens:  Fenster „Register“](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Registerinformationen sind für Skript- und SQL-Apps nicht verfügbar.

Während des Debuggens ändern sich die Registerwerte, wenn Code in ihrer App ausgeführt wird. Kürzlich geänderte Werte werden im Fenster **Register** rot angezeigt.

Aus Gründen der Übersichtlichkeit werden Register im Fenster **Register** nach Gruppen eingeteilt, die sich je nach Plattform und Prozessortyp unterscheiden. Sie können Registergruppen ein- oder ausblenden. Weitere Informationen finden Sie unter [Vorgehensweise: Display and hide register groups (Anzeigen und Ausblenden von Registergruppen)](../debugger/how-to-display-and-hide-register-groups.md)

Informationen zu den Flags, die im Fenster **Register** angezeigt werden, finden Sie unter [Informationen zum Fenster „Register“](../debugger/debugging-basics-registers-window.md).

Die Registerwerte können bearbeitet werden. Weitere Informationen finden Sie unter [Vorgehensweise: Edit a register value (Bearbeiten eines Registerwerts)](../debugger/how-to-edit-a-register-value.md).

**So öffnen Sie das Fenster „Register“**

1. Aktivieren Sie das Debuggen auf Adressebene, indem Sie **Debuggen auf Adressebene aktivieren** in **Tools** (oder **Debuggen**) > **Optionen** > **Debuggen** auswählen.

1. Wählen Sie während des Debugvorgangs oder bei einem Haltepunkt **Debuggen** > **Fenster** > **Register** aus, oder drücken Sie **ALT**+**5**.

>[!NOTE]
>Die Dialogfelder und Menübefehle können abweichen, je nach Ihrer Visual Studio-Edition bzw. deren Einstellungen. Wählen Sie im Visual Studio-Menü **Tools** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Siehe auch

- [Debuggrundlagen: Registerfenster](../debugger/debugging-basics-registers-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
