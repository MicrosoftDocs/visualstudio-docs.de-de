---
title: Untersuchen einer Ausnahme
titleSuffix: ''
description: Hier erfahren Sie mehr über die Informationen, die Visual Studio bereitstellt, um Sie beim Debuggen von Ausnahmen zu unterstützen, sowie darüber, wie Sie das Unterbrechen bei Ausnahmen selektiv deaktivieren.
ms.custom: SEO-VS-2020
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ddc57d28510fe2e2cd5dbbb3aeea993813546715
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862814"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Untersuchen einer Ausnahme mit der Ausnahmen-Hilfe 

Der Umgang mit Ausnahmen ist unabhängig davon, welche Technologie Sie nutzen oder welchen Wissenstand Sie haben, ein häufiges Problem. Die Ermittlung des Grunds, warum Ausnahmen in Ihrem Code zu Problemen führen, kann ein frustrierender Prozess sein. Beim Debuggen einer Ausnahme in Visual Studio möchten wir Ihnen in diesen frustrierenden Situationen helfen, indem wir Sie mit relevanten Informationen zu Ausnahmen versorgen, damit Sie Ihr Problem schneller debuggen können.

![Ausnahmen-Hilfe](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Anhalten bei einer Ausnahme
Wenn der Debugger den Vorgang beim Auftreten einer Ausnahme unterbricht, wird rechts von der entsprechenden Codezeile ein Symbol für eine Ausnahme angezeigt. Neben dem Symbol für die Ausnahme wird eine nicht modale Ausnahmen-Hilfe angezeigt.

![Ausnahmen-Hilfe neben einer Codezeile](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Untersuchen der Informationen zur Ausnahme
Sie können den Typ und die Meldung zur Ausnahme in der Ausnahmen-Hilfe sofort ablesen, und es ist auch angegeben, ob es sich um eine ausgelöste Ausnahme oder einen Ausnahmefehler handelt. Sie können die Eigenschaften des Ausnahmeobjekts untersuchen und anzeigen, indem Sie auf den Link **Details anzeigen** klicken.

## <a name="analyze-null-references"></a>Analysieren von Nullverweisen
Ab Visual Studio 2017 gilt sowohl für .NET- als auch für C/C++-Code Folgendes: Beim Auftreten von `NullReferenceException` oder `AccessViolation` werden in der Ausnahmen-Hilfe Null-Analyseinformationen angezeigt. Die Analyse wird als Text unterhalb der Ausnahmemeldung angegeben. In der Abbildung unten werden die Informationen als „**s** war NULL“ angezeigt.

![Ausnahmen-Hilfe: Null-Analyse](media/debugger-exception-helper-default.png)


> [!NOTE]
> Für die NULL-Referenzanalyse in verwaltetem Code ist .NET-Version 4.6.2 erforderlich. Die Null-Analyse wird für die Universelle Windows-Plattform (UWP) und andere .NET Core-Anwendungen derzeit nicht unterstützt. Sie ist nur beim Debuggen von Code verfügbar, für den keine JIT-Codeoptimierungen (Just-In-Time) vorhanden sind.

## <a name="configure-exception-settings"></a>Konfigurieren von Einstellungen für Ausnahmen 
Sie können den Debugger so konfigurieren, dass der Vorgang unterbrochen wird, wenn eine Ausnahme des aktuellen Typs auftritt. Verwenden Sie hierfür in der Ausnahmen-Hilfe den Abschnitt mit den **Ausnahmeeinstellungen**. Wenn der Debugger bei Auslösung einer Ausnahme angehalten wird, können Sie das Anhalten über das Kontrollkästchen für den Ausnahmetyp deaktivieren, um das Verhalten bei zukünftigen Fällen entsprechend zu ändern. Gehen Sie wie folgt vor, wenn der Vorgang bei Auslösung dieser Ausnahme im aktuellen Modul nicht angehalten werden soll: Aktivieren Sie im Fenster **Ausnahmeeinstellungen** das Kontrollkästchen neben dem Modulnamen unter **Ausgenommen, wenn ausgelöst von:** . 

## <a name="inspect-inner-exceptions"></a>Untersuchen von inneren Ausnahmen 
Falls die Ausnahme über innere Ausnahmen verfügt ([InnerException](/dotnet/api/system.exception.innerexception)), können Sie diese in der Ausnahmen-Hilfe anzeigen. Wenn mehrere Ausnahmen vorhanden sind, können Sie dazwischen wechseln, indem Sie oberhalb der Aufrufliste den Pfeil nach links bzw. rechts verwenden.

![Ausnahmen-Hilfe mit innerer Ausnahme](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Untersuchen von erneut ausgelösten Ausnahmen
Falls eine Ausnahme ausgelöst wurde (`thrown`), wird in der Ausnahmen-Hilfe die Aufrufliste der ersten Ausnahmenauslösung angezeigt. Wenn die Ausnahme mehrmals ausgelöst wurde, wird nur die Aufrufliste der ursprünglichen Ausnahme angezeigt.

![Ausnahmen-Hilfe mit erneut ausgelösten Ausnahmen](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Freigeben einer Debugsitzung mit Live Share
Über die Ausnahmen-Hilfe können Sie eine [Live Share](/visualstudio/liveshare/)-Sitzung starten, indem Sie den Link **Live Share-Sitzung starten...** verwenden. Alle Benutzer, die der Live Share-Sitzung beitreten, können die Ausnahmen-Hilfe und alle anderen Debuginformationen anzeigen.