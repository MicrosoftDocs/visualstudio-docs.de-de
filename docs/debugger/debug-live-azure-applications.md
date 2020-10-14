---
title: Debuggen von aktiven ASP.NET Azure-Apps
titleSuffix: Visual Studio Enterprise
description: Erfahren Sie, wie Sie Andockpunkte festlegen und Momentaufnahmen mit dem Momentaufnahmedebugger anzeigen.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 526f7b7cc1af3dd5a370c74baa09cbab50b3d866
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91879085"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debuggen von aktiven ASP.NET Azure-Apps mit dem Momentaufnahmedebugger

Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie relevant ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Andockpunkte und Protokollpunkte ähneln Haltepunkten, aber im Gegensatz zu Haltepunkten halten Andockpunkte die Anwendung nicht an, wenn sie erreicht werden. In der Regel dauert das Erfassen einer Momentaufnahme an einem Andockpunkt 10 bis 20 Millisekunden.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Momentaufnahmedebuggers
> * Festlegen eines Andockpunkts und Anzeigen einer Momentaufnahme
> * Festlegen eines Protokollpunkts

## <a name="prerequisites"></a>Voraussetzungen

* Der Momentaufnahmedebugger ist nur für Visual Studio 2017 Enterprise Version 15.5 oder höher mit der **Azure-Entwicklungsworkload** verfügbar. (Auf der Registerkarte **Einzelne Komponenten** finden Sie ihn unter **Debuggen und Testen** > **Momentaufnahmedebugger**.)

   ::: moniker range=">=vs-2019"
   Sofern noch nicht installiert, installieren Sie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Wenn Sie von einer früheren Visual Studio-Installation aus aktualisieren, führen Sie den Visual Studio-Installer aus, und überprüfen Sie die Momentaufnahmedebugger-Komponente in der **ASP.NET- und Webentwicklungsworkload**.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Falls noch nicht installiert, installieren Sie [Visual Studio 2017 Enterprise Version 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) oder höher. Wenn Sie von einer früheren Visual Studio 2017-Installation aus aktualisieren, führen Sie den Visual Studio-Installer aus, und überprüfen Sie die Momentaufnahmedebugger-Komponente in der **ASP.NET- und Webentwicklungsworkload**.
   ::: moniker-end

* Azure App Service-Plan Basic oder höher.

* Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:
  * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Öffnen Ihres Projekts und Starten des Momentaufnahmedebuggers

1. Öffnen Sie das Projekt, das Sie mit einer Momentaufnahme debuggen möchten.

   > [!IMPORTANT]
   > Zum Debuggen mit einer Momentaufnahme müssen Sie *dieselbe Version des Quellcodes* öffnen, die für Ihren Azure App Service veröffentlicht wird.

::: moniker range="<=vs-2017"

2. Klicken Sie im Cloud-Explorer (**Ansicht > Cloud-Explorer**) mit der rechten Maustaste auf den Azure App Service, für den Ihr Projekt bereitgestellt ist, und wählen Sie **Momentaufnahmedebugger anfügen** aus.

   ![Starten des Momentaufnahmedebuggers](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Wählen Sie **Debuggen > Momentaufnahmedebugger anfügen** aus. Wählen Sie den Azure App Service aus, für den Ihr Projekt bereitgestellt wird, und ein Azure Storage-Konto, und klicken Sie dann auf **Anfügen**. Der Momentaufnahmedebugger unterstützt auch [Azure Container Service](debug-live-azure-kubernetes.md) und [Azure Virtual Machines (VM) sowie Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md).

   ![Starten des Momentaufnahmedebuggers im Menü „Debuggen“](../debugger/media/snapshot-debug-menu-attach.png)

   ![Auswählen der Azure-Ressource](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > Wenn Sie zum ersten Mal **Momentaufnahmedebugger anfügen** auswählen, werden Sie aufgefordert, die Momentaufnahmedebugger-Websiteerweiterung in Ihrem Azure App Service zu installieren. Diese Installation erfordert einen Neustart des Azure App Service.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Die Application Insights-Websiteerweiterung unterstützt auch das Debuggen von Momentaufnahmen. Wenn Sie eine „Websiteerweiterung veraltet“-Fehlermeldung erhalten, finden Sie unter [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) weitere Informationen zum Aktualisieren.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 Version 16.2 und höher) Der Momentaufnahmedebugger hat die Azure-Cloudunterstützung aktiviert. Stellen Sie sicher, dass sich sowohl die von Ihnen ausgewählte Azure-Ressource als auch das Azure Storage-Konto in derselben Cloud befinden. Wenden Sie sich an Ihren Azure-Administrator, wenn Sie Fragen zu Ihren [Azure-Compliancekonfigurationen](https://azure.microsoft.com/overview/trusted-cloud/) Ihres Unternehmens haben.
   ::: moniker-end

   Visual Studio ist jetzt im Modus des Debuggens von Momentaufnahmen.
   ![Modus des Debuggens von Momentaufnahmen](../debugger/media/snapshot-message.png)

   Im Fenster **Module** sehen Sie, ob alle Module für den Azure App Service geladen wurden (wählen Sie **Debuggen > Fenster > Module** zum Öffnen des Fensters aus).

   ![Überprüfen des Fensters „Module“](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Festlegen eines Andockpunkts

1. Klicken Sie im Code-Editor neben einer Codezeile, die Sie interessiert, auf den linken Bundsteg, um einen Andockpunkt festzulegen. Stellen Sie sicher, dass es sich um Code handelt, von dem Sie wissen, dass er ausgeführt wird.

   ![Festlegen eines Andockpunkts](../debugger/media/snapshot-set-snappoint.png)

2. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

   ![Aktivieren des Andockpunkts](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > Sie können nicht schrittweise vorgehen, wenn Sie eine Momentaufnahme anzeigen, aber Sie können mehrere Andockpunkte im Code platzieren, um die Ausführung auf verschiedenen Codezeilen zu verfolgen. Wenn Ihr Code mehrere Andockpunkte enthält, stellt der Momentaufnahmedebugger sicher, dass die zugehörigen Momentaufnahmen aus der gleichen Endbenutzersitzung stammen. Der Momentaufnahmedebugger leistet dies auch dann, wenn viele Benutzer Ihre App aufrufen.

## <a name="take-a-snapshot"></a>Momentaufnahme erstellen

Nachdem ein Andockpunkt festgelegt wurde, können Sie entweder manuell eine Momentaufnahme über die Browseransicht Ihrer Website generieren, indem Sie die markierte Codezeile ausführen, oder Sie warten, bis Ihre Benutzer eine aus ihrer Website generiert haben.

## <a name="inspect-snapshot-data"></a>Überprüfen von Momentaufnahmedaten

1. Wenn der Andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster „Diagnosetools“ angezeigt. Um dieses Fenster zu öffnen, wählen Sie **Debuggen > Fenster > Diagnosetools anzeigen** aus.

   ![Öffnen eines Andockpunkts](../debugger/media/snapshot-diagsession-window.png)

1. Doppelklicken Sie auf den Andockpunkt, um die Momentaufnahme im Code-Editor zu öffnen.

   ![Überprüfen von Momentaufnahmedaten](../debugger/media/snapshot-inspect-data.png)

   In dieser Ansicht können Sie den Cursor über Variablen platzieren, um DataTips anzuzeigen, die Fenster **Lokal**, **Überwachungen** und **Aufrufliste** verwenden und auch Ausdrücke auswerten.

   Die Website selbst ist noch aktiv, und Endbenutzer sind nicht betroffen. Standardmäßig wird pro Andockpunkt nur eine einzige Momentaufnahme erfasst: Nachdem eine Momentaufnahme erfasst wurde, wird der Andockpunkt deaktiviert. Wenn Sie eine andere Momentaufnahme an dem Andockpunkt erfassen möchten, können Sie den Andockpunkt durch Klicken auf **Sammlung aktualisieren** wieder aktivieren.

Sie können Ihrer App auch weitere Andockpunkte hinzufügen und sie mit der Schaltfläche **Sammlung aktualisieren** aktivieren.

**Benötigen Sie Hilfe?** Lesen Sie die Seiten [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) und [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Festlegen eines bedingten Andockpunkts

Wenn es schwierig ist, einen bestimmten Status in Ihrer App neu herzustellen, erwägen Sie die Verwendung eines bedingten Andockpunkts. Bedingte Andockpunkte helfen Ihnen, zu steuern, wann eine Momentaufnahme erstellt werden soll, wenn z. B. eine Variable einen bestimmten Wert aufweist, den Sie untersuchen möchten. Sie können Bedingungen mithilfe von Ausdrücken, Filtern oder Trefferanzahl festlegen.

#### <a name="to-create-a-conditional-snappoint"></a>So erstellen Sie einen bedingten Andockpunkt

1. Klicken Sie mit der rechten Maustaste auf ein Andockpunktsymbol (die hohle Kugel), und wählen Sie **Einstellungen** aus.

   ![Einstellung auswählen](../debugger/media/snapshot-snappoint-settings.png)

1. Geben Sie im Fenster für Andockpunkteinstellungen einen Ausdruck ein.

   ![Eingeben eines Ausdrucks](../debugger/media/snapshot-snappoint-conditions.png)

   In der vorherigen Abbildung wird die Momentaufnahme nur dann für den Andockpunkt erstellt, wenn `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Festlegen eines Protokollpunkts

Zusätzlich zum Erstellen einer Momentaufnahme, wenn ein Andockpunkt erreicht wird, können Sie auch einen Andockpunkt zum Protokollieren einer Meldung konfigurieren (d.h. einen Protokollpunkt erstellen). Sie können Protokollpunkte festlegen, ohne Ihre App erneut bereitstellen zu müssen. Protokollpunkte werden virtuell ausgeführt und verursachen weder direkte Auswirkungen auf Ihre ausgeführte Anwendung noch Nebeneffekte.

#### <a name="to-create-a-logpoint"></a>So erstellen Sie einen Protokollpunkt

1. Klicken Sie mit der rechten Maustaste auf ein Andockpunktsymbol (das blaue Sechseck), und wählen Sie **Einstellungen** aus.

1. Wählen Sie im Fenster für Andockpunkteinstellungen **Aktionen** aus.

   ![Erstellen eines Protokollpunkts](../debugger/media/snapshot-logpoint.png)

1. Im Feld **Meldung** können Sie die neue Protokollmeldung eingeben, die Sie protokollieren möchten. Sie können auch Variablen in der Protokollmeldung auswerten, indem Sie sie in geschweiften Klammern platzieren.

   Wenn Sie **An Ausgabefenster senden** auswählen, wenn der Protokollpunkt erreicht wird, wird die Meldung im Fenster „Diagnosetools“ angezeigt.

   ![Protokollpunktdaten im Fenster „Diagnosetools“](../debugger/media/snapshot-logpoint-output.png)

   Wenn Sie **An Anwendungsprotokoll senden** auswählen, wenn der Protokollpunkt erreicht wird, wird die Meldung an einer beliebigen Stelle angezeigt, wo Meldungen von `System.Diagnostics.Trace` (oder `ILogger` in .NET Core) angezeigt werden können, wie z.B. [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erfahren, wie Sie den Momentaufnahmedebugger für App Services verwenden. Vielleicht wünschen Sie weitere Informationen zu diesem Feature.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)