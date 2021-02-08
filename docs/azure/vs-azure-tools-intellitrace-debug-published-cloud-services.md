---
title: Mit IntelliTrace veröffentlichten Azure-clouddienst Debuggen
ms.custom: SEO-VS-2020
description: Erfahren Sie, wie Sie einen Clouddienst mit Visual Studio und IntelliTrace debuggen.
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: d419f80dc0319fbcebe053cd063cf668fc278a38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844202"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace
Mit IntelliTrace können Sie umfangreiche Debuginformationen für eine Rolleninstanz protokollieren, wenn sie in Azure ausgeführt wird. Wenn Sie die Ursache eines Problems finden möchten, können Sie mithilfe der IntelliTrace-Protokolle den Code aus Visual Studio schrittweise so durchlaufen, als ob er in Azure ausgeführt würde. Tatsächlich zeichnet IntelliTrace während der Ausführung der Azure-Anwendung als Clouddienst in Azure wichtige Codeausführungs- und Umgebungsdaten auf und ermöglicht die Wiedergabe der aufgezeichneten Daten von Visual Studio aus.

Sie können IntelliTrace verwenden, wenn Visual Studio Enterprise installiert ist und die Azure-Anwendung .NET Framework 4 oder höher als Zielversion verwendet. IntelliTrace sammelt Informationen für Ihre Azure-Rollen. Die virtuellen Computer für diese Rollen führen immer 64-Bit-Betriebssysteme aus.

Als Alternative können Sie das [Remote Debuggen](vs-azure-tools-debugging-cloud-services-overview.md) verwenden, um direkt an einen Cloud-Dienst anzufügen, der in Azure ausgeführt wird.

> [!IMPORTANT]
> IntelliTrace ist nur für Debugszenarien bestimmt und sollte nicht für eine Produktionsbereitstellung verwendet werden.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurieren einer Azure-Anwendung für IntelliTrace
Wenn Sie IntelliTrace für eine Azure-Anwendung aktivieren möchten, müssen Sie die Anwendung in einem Visual Studio Azure-Projekt erstellen und von dort veröffentlichen. Sie müssen IntelliTrace für die Azure-Anwendung konfigurieren, bevor Sie die Anwendung in Azure veröffentlichen. Wenn Sie Ihre Anwendung veröffentlichen, ohne IntelliTrace zu konfigurieren, müssen Sie das Projekt erneut veröffentlichen. Weitere Informationen finden Sie unter [Veröffentlichen eines Azure-Clouddienstprojekts mit Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

1. Wenn Sie bereit sind, die Azure-Anwendung bereitzustellen, überprüfen Sie, ob die Projektbuildziele auf **Debuggen** festgelegt wurden.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü die Option **Veröffentlichen** aus.

1. Wählen Sie im Dialogfeld **Azure-Anwendung veröffentlichen** das Azure-Abonnement und dann **Weiter** aus.

1. Wählen Sie auf der Seite **Einstellungen** die Registerkarte **Erweiterte Einstellungen** aus.

1. Aktivieren Sie die Option **IntelliTrace aktivieren**, um IntelliTrace-Protokolle für die Anwendung bei der Veröffentlichung in der Cloud zu erfassen.

1. Wenn Sie die IntelliTrace-Basiskonfiguration anpassen möchten, wählen Sie **Einstellungen** neben **IntelliTrace aktivieren** aus.

    ![Link für IntelliTrace-Einstellungen](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. Im Dialogfeld **IntelliTrace-Einstellungen** können Sie angeben, welche Ereignisse protokolliert werden sollen, ob Aufrufinformationen erfasst werden sollen, für welche Module und Prozesse Protokolle erfasst werden sollen und wie viel Speicherplatz der Erfassung zugeordnet werden soll. Weitere Informationen zu IntelliTrace finden Sie unter [Debuggen mit IntelliTrace](../debugger/intellitrace.md).

    ![IntelliTrace-Einstellungen](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Das IntelliTrace-Protokoll ist eine zirkuläre Protokolldatei, welche die in den IntelliTrace-Einstellungen angegebene maximale Größe besitzt (die Standardgröße beträgt 250 MB). IntelliTrace-Protokolle werden in einer Datei im Dateisystem des virtuellen Computers gesammelt. Wenn Sie die Protokolle anfordern, wird zu diesem Zeitpunkt eine Momentaufnahme erstellt und auf den lokalen Computer heruntergeladen.

Nachdem der Azure-Clouddienst in Azure veröffentlicht wurde, können Sie über den Azure-Knoten im **Server-Explorer** ermitteln, ob IntelliTrace aktiviert wurde, wie in der folgenden Abbildung gezeigt:

![Server-Explorer – IntelliTrace aktiviert](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Herunterladen von IntelliTrace-Protokollen für eine Rolleninstanz
Mit den folgenden Schritten können Sie in Visual Studio IntelliTrace-Protokolle für eine Rolleninstanz herunterladen:

1. Erweitern Sie im **Server-Explorer** den Knoten **Cloud Services**, und suchen Sie die Rolleninstanz, deren Protokolle heruntergeladen werden sollen.

1. Klicken Sie mit der rechten Maustaste auf die Rolleninstanz, und wählen Sie im Kontextmenü die Option **IntelliTrace-Protokolle anzeigen** aus.

    ![Menüoption „IntelliTrace-Protokolle anzeigen“](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Die IntelliTrace-Protokolle werden in eine Datei in einem Verzeichnis auf dem lokalen Computer heruntergeladen. Bei jeder Anforderung der IntelliTrace-Protokolle wird eine neue Momentaufnahme erstellt. Während die Protokolle heruntergeladen werden, wird in Visual Studio der Status des Vorgangs im Fenster **Azure-Aktivitätsprotokoll** angezeigt. Wie in der folgenden Abbildung gezeigt, können Sie die Zeile des Vorgangs erweitern, um weitere Details anzuzeigen.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Sie können weiterhin in Visual Studio arbeiten, während die IntelliTrace-Protokolle heruntergeladen werden. Wenn das Protokoll vollständig heruntergeladen wurde, wird es in Visual Studio geöffnet.

> [!NOTE]
> Die IntelliTrace-Protokolle enthalten möglicherweise vom Framework generierte und anschließend verarbeitete Ausnahmen. Der interne Frameworkcode generiert diese Ausnahmen ganz normal im Rahmen des Starts einer Rolle, sodass sie gefahrlos ignoriert werden können.
>
>

## <a name="next-steps"></a>Nächste Schritte
- [Optionen zum Debuggen von Azure-Clouddiensten](vs-azure-tools-debugging-cloud-services-overview.md)
- [Veröffentlichen eines Azure-Clouddiensts mit Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)