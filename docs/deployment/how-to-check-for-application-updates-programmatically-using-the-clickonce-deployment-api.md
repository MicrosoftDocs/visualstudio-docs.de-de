---
title: Automatische APP-Updates mit ClickOnce-Bereitstellungs-API
description: Erfahren Sie, wie Sie Code in ClickOnce schreiben, der die ApplicationDeployment-Klasse verwendet, um basierend auf einem Ereignis, z. b. einer Benutzer Anforderung, nach Updates zu suchen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e7168b78303f93ccf89fad324992dd580481ac2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888445"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Vorgehensweise: Programmgesteuertes Suchen nach Anwendungsupdates mit der API für die ClickOnce-Bereitstellung
ClickOnce bietet zwei Möglichkeiten, eine Anwendung zu aktualisieren, nachdem Sie bereitgestellt wurde. In der ersten Methode können Sie die ClickOnce-Bereitstellung so konfigurieren, dass Sie in bestimmten Intervallen automatisch nach Updates sucht. In der zweiten Methode können Sie Code schreiben, der die- <xref:System.Deployment.Application.ApplicationDeployment> Klasse verwendet, um anhand eines Ereignisses, z. b. einer Benutzer Anforderung, nach Updates zu suchen.

 Die folgenden Prozeduren zeigen Code zum Ausführen eines programmgesteuerten Updates und beschreiben auch, wie Sie Ihre ClickOnce-Bereitstellung konfigurieren, um programmgesteuerte Update Überprüfungen zu aktivieren.

 Um eine ClickOnce-Anwendung Programm gesteuert zu aktualisieren, müssen Sie einen Speicherort für Updates angeben. Dies wird manchmal als Bereitstellungs Anbieter bezeichnet. Weitere Informationen zum Festlegen dieser Eigenschaft finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Sie können auch die unten beschriebene Vorgehensweise verwenden, um die Anwendung von einem Speicherort aus bereitzustellen, aber von einer anderen zu aktualisieren. Weitere Informationen finden Sie unter Gewusst [wie: Angeben eines alternativen Speicher Orts für Bereitstellungs Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>So suchen Sie Programm gesteuert nach Updates

1. Erstellen Sie eine neue Windows Forms Anwendung mit Ihren bevorzugten Befehlszeilen Tools oder visuellen Tools.

2. Erstellen Sie beliebige Schaltflächen, Menü Elemente oder andere Elemente der Benutzeroberfläche, die von den Benutzern für die Suche nach Updates ausgewählt werden sollen. Mit dem-Ereignishandler dieses Elements können Sie die folgende Methode zum Suchen und Installieren von Updates abrufen.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Kompilieren Sie die Anwendung.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden Sie Mage.exe, um eine Anwendung bereitzustellen, die Programm gesteuert nach Updates sucht.

- Befolgen Sie die Anweisungen zum Bereitstellen der Anwendung mithilfe Mage.exe, wie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)erläutert. Wenn Sie Mage.exe aufrufen, um das Bereitstellungs Manifest zu generieren, stellen Sie sicher, dass Sie den Befehls Zeilenschalter verwenden `providerUrl` , und geben Sie die URL an, unter der ClickOnce nach Updates suchen soll. Wenn die Anwendung beispielsweise von aktualisiert wird, `http://www.adatum.com/MyApp` könnte der Befehl zum Generieren des Bereitstellungs Manifests wie folgt aussehen:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Verwenden von MageUI.exe zum Bereitstellen einer Anwendung, die Programm gesteuert nach Updates sucht

- Befolgen Sie die Anweisungen zum Bereitstellen der Anwendung mithilfe Mage.exe, wie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)erläutert. Legen Sie auf der Registerkarte **Bereitstellungs Optionen** das Feld **Start Speicherort** auf das Anwendungs Manifest fest, und suchen Sie nach Updates. Deaktivieren Sie auf der Registerkarte **Update Optionen** das Kontrollkästchen **diese Anwendung sollte nach Updates suchen** .

## <a name="net-framework-security"></a>.NET Framework-Sicherheit
 Die Anwendung muss über voll vertrauenswürdige Berechtigungen für die Verwendung Programm gesteuerter Updates verfügen.

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Angeben eines alternativen Speicher Orts für Bereitstellungs Aktualisierungen](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)