---
title: 'Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an | Microsoft-Dokumentation'
ms.date: 1/15/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44f7df253951d90a29c459bf28e6ff1c2279ee54
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533367"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an

Diese Sicherheitswarnung wird direkt vor dem Anhängen an einen Prozess angezeigt, der nicht voll vertrauenswürdigen Code enthält oder der im Besitz eines nicht vertrauenswürdigen Benutzers ist. Ein nicht vertrauenswürdiger Prozess, der bösartigen Code enthält, kann unter Umständen den das Debuggen ausführenden Computer beschädigen. Wenn Sie Grund dazu haben, dem Prozess zu misstrauen, sollten Sie das Debuggen durch Klicken auf **Abbrechen** verhindern.

In IIS-Szenarios wird diese Warnung möglicherweise angezeigt, wenn Sie einen benutzerdefinierten Anwendungspool verwenden, der nicht vertrauenswürdig ist.

So unterdrücken Sie diese Warnung beim Debuggen eines legitimen Szenarios:

1. Schließen Sie Visual Studio.

1. Legen Sie den Wert des `DisableAttachSecurityWarning`-Registrierungsschlüssels auf 1 fest.

   Suchen oder erstellen Sie den Schlüssel unter `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger`, und legen Sie ihn auf 1 fest.

   Ab Visual Studio 2017 müssen Sie die private Registrierungsstruktur laden, wenn Sie die Registrierungseinstellungen vollständig anzeigen möchten. Weitere Informationen finden Sie unter [Untersuchen der Visual Studio 2017-Registrierung](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md). Stellen Sie sicher, dass Sie die private Registrierungsstruktur entladen, bevor Sie Visual Studio starten.

1. Starten Sie Visual Studio neu.

1. Nachdem das Debuggen des Szenarios beendet ist, setzten Sie den Wert auf 0 zurück und starten Visual Studio neu.

Zu den "vertrauenswürdigen Benutzern" zählen Sie selbst und noch eine Reihe weiterer Standardbenutzern, die üblicherweise auf Computern definiert sind, auf denen .NET Framework installiert ist (z. B. `aspnet`, `localsystem`, `networkservice` und `localservice`).

## <a name="uielement-list"></a>UIElement-Liste

 Name: Name der zu debuggenden Assembly

 Benutzer: Aktueller Benutzer

 Anfügen: Klicken Sie auf diese Schaltfläche, um das Debuggen durch Anfügen fortzusetzen

 Nicht an den Prozess anfügen: Nicht an den Prozess anfügen

## <a name="see-also"></a>Siehe auch
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
