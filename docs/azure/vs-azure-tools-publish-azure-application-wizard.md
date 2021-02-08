---
title: Veröffentlichen eines Azure-Clouddiensts
description: Erfahren Sie, wie die verschiedenen Einstellungen im Visual Studio-Assistenten zum Veröffentlichen von Azure-Anwendungen konfiguriert werden
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: f965d8e7f71ba34be9901d77fa4f0af881805bb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844059"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Verwenden des Visual Studio-Assistenten zum Veröffentlichen von Azure-Anwendungen

Nachdem Sie eine Webanwendung in Visual Studio entwickelt haben, können Sie diese Anwendung mit dem **Assistenten zum Veröffentlichen einer Azure-Anwendung** in einem Azure-Clouddienst veröffentlichen.

> [!Note]
> In diesem Artikel wird die Bereitstellung in Clouddiensten und nicht auf Websites behandelt. Weitere Informationen zum Bereitstellen von Websites finden Sie unter [Bereitstellen einer Azure-Website](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Zugriff auf den Assistenten zum Veröffentlichen von Azure-Anwendungen

Je nach Art des von Ihnen verwendeten Visual Studio-Projekts können Sie auf eine von zwei Arten auf den Assistenten zum Veröffentlichen von Azure-Anwendungen zugreifen.

**Wenn Sie ein Azure-Clouddienstprojekt verwenden:**

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü die Option **Veröffentlichen** aus.

**Wenn Sie ein Webanwendungsprojekt verwenden, das nicht für Azure aktiviert ist:**

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü **Konvertieren** > **In Azure-Clouddienstprojekt konvertieren** aus.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das neu erstellte Azure-Projekt, und wählen Sie im Kontextmenü die Option **Veröffentlichen** aus.

## <a name="sign-in-page"></a>Anmeldeseite

![Anmeldeseite](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Konto**: Wählen Sie ein Konto aus, oder wählen Sie in der Konto-Dropdownliste **Konto hinzufügen** aus.

**Abonnement wählen**: Wählen Sie das Abonnement aus, das Sie für Ihre Bereitstellung verwenden möchten.

## <a name="settings-page---common-settings-tab"></a>Seite „Einstellungen“ – Registerkarte „Allgemeine Einstellungen“

![Allgemeine Einstellungen](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Clouddienst** : Wählen Sie in der Dropdown Liste einen vorhandenen clouddienst aus, oder wählen Sie **&lt; neue>erstellen** aus, und erstellen Sie einen clouddienst. Das Datencenter wird für jeden Clouddienst in Klammern angezeigt. Es wird empfohlen, für den Clouddienst den gleichen Datencenter-Speicherort wie für das Speicherkonto zu verwenden (Erweiterte Einstellungen).

**Umgebung**: Wählen Sie entweder **Produktion** oder **Staging** aus. Wählen Sie die Stagingumgebung, wenn Sie die Anwendung in einer Testumgebung bereitstellen möchten.

**Buildkonfiguration**: Wählen Sie entweder **Debuggen** oder **Release** aus.

**Dienstkonfiguration**: Wählen Sie entweder **Cloud** oder **Lokal** aus.

**Remotedesktop für alle Rollen aktivieren**: Aktivieren Sie diese Option, wenn Sie eine Remoteverbindung mit dem Dienst herstellen möchten. Diese Option wird in erster Linie für die Problembehandlung verwendet. Weitere Informationen finden Sie unter [Aktivieren einer Remotedesktopverbindung für eine Rolle in Azure Cloud Services mit Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Web Deploy für alle Webrollen aktivieren**: Aktivieren Sie diese Option, um die Webbereitstellung für den Dienst zu aktivieren. Sie müssen außerdem die Option **Remotedesktop für alle Rollen aktivieren** auswählen, um dieses Feature zu verwenden. Weitere Informationen finden Sie unter [Veröffentlichen eines Clouddiensts mit Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Seite „Einstellungen“ – Registerkarte „Erweiterte Einstellungen“

![Erweiterte Einstellungen](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Bereitstellungsbezeichnung**: Akzeptieren Sie den Standardnamen, oder geben Sie einen Namen Ihrer Wahl ein. Um der Bereitstellungsbezeichnung das Datum anzufügen, lassen Sie das Kontrollkästchen aktiviert.

**Speicherkonto**: Wählen Sie das für diese Bereitstellung zu verwendende Speicherkonto aus oder **&lt;Neu erstellen&gt;, um ein Speicherkonto zu erstellen. Das Datencenter wird für jedes Speicherkonto in Klammern angezeigt. Es wird empfohlen, für das Speicherkonto den gleichen Rechenzentrumsstandort wie für den Clouddienst zu verwenden (Erweiterte Einstellungen).

Das Azure-Speicherkonto speichert das Paket für die Bereitstellung der Anwendung. Nach der Bereitstellung der Anwendung wird das Paket aus dem Speicherkonto entfernt.

**Bereitstellung bei Fehler löschen**: Aktivieren Sie diese Option, um die Bereitstellung löschen zu lassen, wenn während der Veröffentlichung Fehler auftreten. Die Option sollte deaktiviert werden, wenn Sie für Ihren Clouddienst eine gleichbleibende virtuelle IP-Adresse verwenden möchten.

**Bereitstellungsaktualisierung**: Aktivieren Sie diese Option, wenn Sie nur aktualisierte Komponenten bereitstellen möchten. Diese Art der Bereitstellung kann schneller als eine vollständige Bereitstellung erfolgen. Die Option sollte aktiviert werden, wenn Sie für Ihren Clouddienst eine gleichbleibende virtuelle IP-Adresse verwenden möchten.

**Bereitstellungsaktualisierung – Einstellungen**: Dieses Dialogfeld wird verwendet, um weitere Optionen für die Aktualisierung der Rollen festzulegen. Bei Auswahl von **Inkrementelle Aktualisierung** werden die Instanzen der Anwendung nacheinander aktualisiert. Die Verfügbarkeit der Anwendung wird also nicht unterbrochen. Wenn Sie **Gleichzeitige Aktualisierung** auswählen, werden alle Instanzen der Anwendung gleichzeitig aktualisiert. Gleichzeitige Updates sind schneller, der Dienst ist während der Aktualisierung jedoch möglicherweise nicht verfügbar.

![Bereitstellungseinstellungen](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace aktivieren**: Geben Sie an, ob Sie IntelliTrace aktivieren möchten. Mit IntelliTrace können Sie umfangreiche Debuginformationen für eine Rolleninstanz protokollieren, wenn sie in Azure ausgeführt wird. Wenn Sie die Ursache eines Problems finden möchten, können Sie mithilfe der IntelliTrace-Protokolle den Code aus Visual Studio schrittweise so durchlaufen, als ob er in Azure ausgeführt würde. Weitere Informationen über IntelliTrace finden Sie unter [Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Profilerstellung aktivieren**: Geben Sie an, ob Sie die Erstellung von Leistungsprofilen aktivieren möchten. Der Visual Studio-Profiler ermöglicht Ihnen, eine detaillierte Analyse der Computingaspekte der Ausführung Ihres Clouddiensts zu erhalten. Weitere Informationen zur Verwendung des Visual Studio-Profilers finden Sie unter [Testen der Leistung eines Azure-Clouddiensts](./vs-azure-tools-performance-profiling-cloud-services.md).

**Remotedebugger für alle Rollen aktivieren**: Geben Sie an, ob Sie Remotedebuggen aktivieren möchten. Weitere Informationen zum Debuggen von Clouddiensten mithilfe von Visual Studio finden Sie unter [Debuggen eines Azure-Clouddiensts oder virtuellen Computers in Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Seite „Diagnoseeinstellungen“

![Diagnoseeinstellungen](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Mithilfe von Diagnose können Sie Problembehebung für einen Azure-Clouddienst (oder einen virtuellen Azure-Computer) ausführen. Informationen zur Diagnose finden Sie unter [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) . Weitere Informationen zu Application Insights finden Sie unter [Was ist Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Seite „Zusammenfassung“

![Seite „Zusammenfassung“](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Zielprofil**: Sie können sich entscheiden, ein Veröffentlichungsprofil auf der Grundlage der von Ihnen ausgewählten Einstellungen zu erstellen. Sie können beispielsweise ein Profil für eine Testumgebung und ein weiteres für die Produktion verwenden. Um dieses Profil zu speichern, wählen Sie das Symbol **Speichern**. Der Assistent erstellt das Profil und speichert es im Visual Studio-Projekt. Um den Profilnamen zu ändern, öffnen Sie die Liste **Ziel Profil** , und wählen Sie dann **&lt; Verwalten &gt; ...** aus.

   > [!Note]
   > Das Veröffentlichungsprofil wird im Projektmappen-Explorer in Visual Studio angezeigt. Die Profileinstellungen werden in eine Datei mit der Erweiterung ".azurePubxml" geschrieben. Einstellungen werden als Attribute der XML-Tags gespeichert.

## <a name="publishing-your-application"></a>Veröffentlichen der Anwendung

Nachdem Sie alle Einstellungen für die Bereitstellung Ihres Projekts konfiguriert haben, wählen Sie unten im Dialogfeld **Veröffentlichen** aus. Sie können den Prozessstatus im Bereich **Ausgabe** in Visual Studio überwachen.

## <a name="next-steps"></a>Nächste Schritte

- [Migrieren und Veröffentlichen einer Webanwendung in einem Azure-Clouddienst aus Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Erfahren Sie, wie Sie Visual Studio zum Veröffentlichen eines Clouddiensts verwenden](./vs-azure-tools-publishing-a-cloud-service.md)

- [Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testen der Leistung eines Azure-Clouddiensts](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)

- [Was ist Application Insights?](/azure/application-insights/app-insights-overview)