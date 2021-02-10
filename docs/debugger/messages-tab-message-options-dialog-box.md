---
title: Meldungen-Registerkarte und Meldungsoptionen-Dialogfeld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c0a97a5b42e27c6db770e0c74a64e214561cea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891604"
---
# <a name="messages-tab-message-options-dialog-box"></a>Registerkarte "Meldungen", Dialogfeld "Meldungsoptionen"
Verwenden Sie die Registerkarte **Meldungen**, um auszuwählen, welche Meldungstypen in der [Meldungsansicht](../debugger/messages-view.md) angezeigt werden sollen, und um Suchkriterien für Meldungen anzugeben. Um das [Dialogfeld „Meldungsoptionen](../debugger/message-options-dialog-box.md) anzuzeigen, wählen Sie im Menü **Spy** die Option **Meldungen protokollieren** aus.

 In der Regel wählen Sie zunächst **Meldungsgruppen** aus und optimieren dann die Auswahl, indem Sie einzelne **anzuzeigende Meldungen** auswählen. Mit der Schaltfläche **Alle** können Sie alle Meldungstypen auswählen und mit der Schaltfläche **Keine** werden alle Typen gelöscht.

 Auf der Registerkarte **Meldungen** sind folgende Einstellungen verfügbar:

 **Anzuzeigende Meldungen:** Hier wählen Sie spezifische Meldungen aus, die angezeigt werden sollen. Wenn Sie ein neues Meldungsfenster erstellen, können alle Meldungen angezeigt werden. Wenn Sie Meldungen über die Registerkarte **Meldungen** filtern, gilt dieser Filter nur für neue Meldungen und nicht für Meldungen, die bereits in der Fensteransicht angezeigt wurden.

 **Meldungsgruppen:** Hier wählen Sie Meldungsgruppen aus, die angezeigt werden sollen. Zu den verfügbaren Gruppen gehören:

- WM_USER: Meldungen mit einem Code größer als oder gleich WM_USER

- Registered (Registriert): Meldungen die mit dem Aufruf **RegisterWindowMessage** registriert wurden

- Unknown (Unbekannt): Unbekannte Meldungen im Bereich 0 (null) bis (WM_USER - 1)

  Beachten Sie, dass diese **Meldungsgruppen** nicht bestimmten Einträgen unter **Anzuzeigende Meldungen** zugeordnet werden. Wenn Sie eine Gruppe auswählen, wird diese Auswahl direkt auf den Meldungsdatenstrom angewendet.

  Ein ausgegrautes Kontrollkästchen in **Meldungsgruppen** gibt an, dass das Listenfeld **Anzuzeigende Meldungen** für Meldungen in dieser Gruppe geändert wurde. Nicht alle Meldungstypen in dieser Gruppe wurden ausgewählt.

  **Als Voreinstellung speichern:** Hiermit können Sie die aktuellen Einstellungen zur späteren Verwendung als Optionen für die Suche nach Meldungen speichern. Diese Einstellungen werden ebenfalls beim Beenden von Spy++ gespeichert.