---
title: Debuggen von aktiven ASP.NET Azure Kubernetes Services
description: Hier erfahren Sie, wie Sie den Momentaufnahmedebugger in Visual Studio verwenden, um beim Debuggen von aktiven ASP.NET Azure Kubernetes Services Andockpunkte festzulegen und Momentaufnahmen zu erstellen.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 823da6da0a842766739cb50c700bb723a47d0309
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846965"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Debuggen von aktiven ASP.NET Azure Kubernetes Services mit dem Momentaufnahmedebugger

Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie relevant ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Andockpunkte und Protokollpunkte ähneln Haltepunkten, aber im Gegensatz zu Haltepunkten halten Andockpunkte die Anwendung nicht an, wenn sie erreicht werden. In der Regel dauert das Erfassen einer Momentaufnahme an einem Andockpunkt 10 bis 20 Millisekunden.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Momentaufnahmedebuggers
> * Festlegen eines Andockpunkts und Anzeigen einer Momentaufnahme
> * Festlegen eines Protokollpunkts

## <a name="prerequisites"></a>Voraussetzungen

* Der Momentaufnahmedebugger für Azure Kubernetes Services ist nur für Visual Studio 2019 Enterprise oder höher mit der **Azure-Entwicklungsworkload** verfügbar. (Auf der Registerkarte **Einzelne Komponenten** finden Sie ihn unter **Debuggen und Testen** > **Momentaufnahmedebugger**.)

    Installieren Sie [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/), falls dies noch nicht geschehen ist.

* Die Momentaufnahmensammlung ist für folgende Azure Kubernetes Services-Web-Apps verfügbar:
  * ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Debian 9 ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Alpine 3.8 ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Ubuntu 18.04 ausgeführt werden.

    > [!NOTE]
    > Um Ihnen das Aktivieren der Unterstützung für den Momentaufnahmedebugger in AKS zu erleichtern, haben wir ein [Repository mit einem Satz von Dockerfile-Dateien, die das Setup auf Docker-Images veranschaulichen](https://github.com/Microsoft/vssnapshotdebugger-docker), bereitgestellt.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Öffnen Ihres Projekts und Starten des Momentaufnahmedebuggers

1. Öffnen Sie das Projekt, das Sie mit einer Momentaufnahme debuggen möchten.

    > [!IMPORTANT]
    > Zum Debuggen mit einer Momentaufnahme müssen Sie *dieselbe Version des Quellcodes* öffnen, die für Ihren Azure Kubernetes-Dienst veröffentlicht wird.

1. Wählen Sie **Debuggen > Momentaufnahmedebugger anfügen** aus. Wählen Sie die AKS-Ressource aus, für die Ihre Web-App bereitgestellt wird, und ein Azure Storage-Konto, und klicken Sie dann auf **Anfügen**. Der Momentaufnahmedebugger unterstützt auch [Azure App Service](debug-live-azure-applications.md) und [Azure Virtual Machines (VM) sowie Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md).

    ![Starten des Momentaufnahmedebuggers im Menü „Debuggen“](../debugger/media/snapshot-debug-menu-attach.png)

    ![Auswählen der Azure-Ressource](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 Version 16.2 und höher) Der Momentaufnahmedebugger hat die Azure-Cloudunterstützung aktiviert. Stellen Sie sicher, dass sich sowohl die von Ihnen ausgewählte Azure-Ressource als auch das Azure Storage-Konto in derselben Cloud befinden. Wenden Sie sich an Ihren Azure-Administrator, wenn Sie Fragen zu den [Azure-Compliancekonfigurationen](https://azure.microsoft.com/overview/trusted-cloud/) Ihres Unternehmens haben.

Visual Studio ist jetzt im Modus des Debuggens von Momentaufnahmen.

   ![Modus des Debuggens von Momentaufnahmen](../debugger/media/snapshot-message.png)

   Im Fenster **Module** sehen Sie, ob alle Module für den Azure App Service geladen wurden (wählen Sie **Debuggen > Fenster > Module** zum Öffnen des Fensters aus).

   ![Überprüfen des Fensters „Module“](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Festlegen eines Andockpunkts

1. Klicken Sie im Code-Editor neben einer Codezeile, die Sie interessiert, auf den linken Bundsteg, um einen Andockpunkt festzulegen. Stellen Sie sicher, dass es sich um Code handelt, von dem Sie wissen, dass er ausgeführt wird.

   ![Festlegen eines Andockpunkts](../debugger/media/snapshot-set-snappoint.png)

1. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

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

Wenn es schwierig ist, einen bestimmten Zustand in Ihrer App zu reproduzieren, erwägen Sie die Verwendung eines bedingten Andockpunkts. Bedingte Andockpunkte helfen Ihnen, zu steuern, wann eine Momentaufnahme erstellt werden soll, wenn z. B. eine Variable einen bestimmten Wert aufweist, den Sie untersuchen möchten. Sie können Bedingungen mithilfe von Ausdrücken, Filtern oder Trefferanzahl festlegen.

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

In diesem Tutorial haben Sie erfahren, wie Sie den Momentaufnahmedebugger für Azure Kubernetes verwenden. Vielleicht wünschen Sie weitere Informationen zu diesem Feature.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)