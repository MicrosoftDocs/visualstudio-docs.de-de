---
description: Der Visual Studio-Momentaufnahmedebugger ist nun mit dem Dienst verbunden, und Sie können mit dem Erfassen von Momentaufnahmen beginnen, um das Debuggen zu unterstützen.
title: Startseite für den Momentaufnahmedebugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96e0c6196d99b8a2b7ac9b4187dbd1397111abbd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160341"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Erste Schritte mit dem Momentaufnahmedebugger

Der Visual Studio-Momentaufnahmedebugger ist nun mit dem Dienst verbunden, und Sie können mit dem Erfassen von Momentaufnahmen beginnen, um das Debuggen zu unterstützen.

Legen Sie zum Verwenden des Momentaufnahmedebuggers einige Andockpunkte im Code fest, klicken Sie auf die Schaltfläche, um mit dem Erfassen von Momentaufnahmen zu beginnen, und führen Sie dann das Szenario aus. Wenn Code ausgeführt wird, in dem Sie einen Andockpunkt festgelegt haben, wird eine Momentaufnahme der Anwendung erstellt. Öffnen Sie dann die Momentaufnahme, indem Sie in Visual Studio im Fenster „Diagnosetools“ auf sie klicken. Nun können Sie die Momentaufnahme des Dienstes wie eine lokale Momentaufnahme debuggen. Ausführliche Anweisungen hierzu finden Sie weiter unten.

## <a name="collect-and-view-snapshots"></a>Erfassen und Anzeigen von Momentaufnahmen

Der Momentaufnahmedebugger erfasst Momentaufnahmen Ihrer Anwendung. Momentaufnahmen sind wie Bilder Ihrer Anwendung, die zu einem bestimmten Zeitpunkt aufgenommen wurden. Sie weisen Visual Studio an, wann und wo eine Momentaufnahme erfasst werden soll, indem Sie einen Andockpunkt im Code festlegen. Im Andockpunkt legen Sie alle nötigen Bedingungen fest, um sicherzustellen, dass Sie eine Momentaufnahme des untersuchten Problems erhalten.

### <a name="set-a-snappoint"></a>Festlegen eines Andockpunkts

1. Klicken Sie im Code-Editor neben einer Codezeile, die Sie interessiert, auf den linken Bundsteg, um einen Andockpunkt festzulegen. Stellen Sie sicher, dass es sich um Code handelt, von dem Sie wissen, dass er ausgeführt wird.

    ![Festlegen eines Andockpunkts im Editor](../media/snapshot-startpage-set-snappoint.png)

    An der Stelle auf der linken Seite, auf die Sie klicken, erscheint ein violettes Sechseck.

2. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

### <a name="open-a-snapshot"></a>Öffnen einer Momentaufnahme

1. Wenn der Andockpunkt erreicht wird, wird auf der rechten Seite des Fensters „Diagnosetools“ eine Momentaufnahme angezeigt. Wenn sich das Fenster nicht öffnet, können Sie es öffnen, indem Sie **Debuggen** > **Fenster** > **Diagnosetools anzeigen** auswählen.

    ![Momentaufnahme im Fenster „Diagnosetools“](../media/snapshot-startpage-diagsession-window.png)

2. Doppelklicken Sie auf die Momentaufnahme, um sie zu öffnen.

### <a name="inspect-snapshot-data"></a>Überprüfen von Momentaufnahmedaten

In dieser Ansicht können Sie den Cursor über Variablen platzieren, um DataTips anzuzeigen, die Fenster „Lokal“, „Überwachungen“ und „Aufrufliste“ verwenden und auch Ausdrücke auswerten.

Die Website selbst ist noch aktiv, und Endbenutzer sind nicht betroffen. Standardmäßig wird pro Andockpunkt nur eine Momentaufnahme aufgezeichnet. Nach dem Erfassen einer Momentaufnahme wird der Andockpunkt also ausgeschaltet. Wenn Sie eine andere Momentaufnahme an dem Andockpunkt erfassen möchten, können Sie den Andockpunkt durch Klicken auf **Sammlung aktualisieren** wieder aktivieren.

### <a name="set-a-logpoint"></a>Festlegen eines Protokollpunkts

1. Klicken Sie mit der rechten Maustaste auf ein Andockpunktsymbol (das violette Sechseck), und wählen Sie **Einstellungen** aus.

2. Wählen Sie im Fenster **Andockpunkteinstellungen** den Eintrag **Aktionen** aus.

    ![Andockpunktbedingungen](../media/snapshot-startpage-logpoint.png)

3. Geben Sie im Feld **Meldung** eine Protokollmeldung ein, die Sie protokollieren möchten. Sie können auch Variablen in der Protokollmeldung auswerten, indem Sie sie in geschweiften Klammern platzieren.

    Wenn Sie **An Ausgabefenster senden** auswählen, wird die Meldung bei Erreichen des Protokollpunkts im Fenster „Diagnosetools“ angezeigt.

    Wenn Sie **An Anwendungsprotokoll senden** auswählen, wird die Meldung bei Erreichen des Protokollpunkts an einer beliebigen Stelle angezeigt, wo Meldungen von `System.Diagnostics.Trace` (bzw. `ILogger` in .NET Core) angezeigt werden können, z. B. in App Insights.

## <a name="learn-more"></a>Weitere Informationen

Weitere Informationen zum Momentaufnahmedebugger finden Sie auf der [Dokumentationsseite](../debug-live-azure-applications.md). Erfahren Sie mehr über das Festlegen von Bedingungen, um das Auffinden von Fehlern zu vereinfachen.

## <a name="dont-show-me-this-again"></a>Diese Meldung nicht mehr anzeigen

Wenn die Startseite des Momentaufnahmedebuggers nicht wiederholt angezeigt werden soll, wenn Sie eine Verbindung zum Momentaufnahmedebugger herstellen, ändern Sie die Einstellung der Option **Show 'Getting Started' page on session start** (Seite „Erste Schritte“ beim Sitzungsstart anzeigen) unter **Extras** > **Optionen** > **Momentaufnahmedebugger**.

![Tool-Optionsseite des Momentaufnahmedebuggers](../media/snapshot-startpage-tools-options.png)
