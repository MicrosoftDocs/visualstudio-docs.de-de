---
title: Debuggen von ClickOnce-apps, die System. Deployment. Application verwenden
description: Erfahren Sie, wie Sie erweiterte ClickOnce-Bereitstellungs Features verwenden und anpassen, indem Sie auf das von System. Deployment. Application bereitgestellte Bereitstellungs Objektmodell zugreifen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e79b6a64eff9eab92a05624f6ca71ae7a242ad2
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382987"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Debuggen von ClickOnce-Anwendungen, die System.Deployment.Application verwenden
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] können Sie mit der Bereitstellung konfigurieren, wie eine Anwendung aktualisiert wird. Wenn Sie jedoch erweiterte Bereitstellungs Features verwenden und anpassen müssen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , müssen Sie auf das von bereitgestellte Bereitstellungs Objektmodell zugreifen <xref:System.Deployment.Application> . Sie können die <xref:System.Deployment.Application> APIs für erweiterte Aufgaben verwenden, wie z. b.:

- Erstellen einer "Jetzt aktualisieren"-Option in der Anwendung

- Bedingte, Bedarfs gesteuerte Downloads verschiedener Anwendungskomponenten

- Direkt in die Anwendung integrierte Updates

- Sicherstellung, dass die Client Anwendung immer auf dem neuesten Stand ist

  Da die <xref:System.Deployment.Application> APIs nur funktionieren, wenn eine Anwendung mit einer Technologie bereitgestellt wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , ist die einzige Möglichkeit, Sie zu debuggen, die Bereitstellung der Anwendung mithilfe von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , das Anfügen an Sie und die anschließende gen Es kann schwierig sein, den Debugger früh genug anzufügen, da dieser Code häufig ausgeführt wird, wenn die Anwendung gestartet und ausgeführt wird, bevor Sie den Debugger anfügen können. Eine Lösung besteht darin, Unterbrechungen (oder Stopps für Visual Basic Projekte) vor dem Update-Prüfcode oder on-Demand-Code zu platzieren.

  Die empfohlene debugtechnik lautet wie folgt:

1. Bevor Sie beginnen, stellen Sie sicher, dass die Symbol Dateien (PDB) und Quelldateien archiviert werden.

2. Stellen Sie Version 1 der Anwendung bereit.

3. Erstellen Sie eine neue leere Projekt Mappe. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**. Öffnen Sie im Dialogfeld **Neues Projekt** den Knoten **andere Projekttypen** , und wählen Sie dann den Ordner **Visual Studio** -Projektmappen aus. Wählen Sie im Bereich **Vorlagen** die Option **leere** Projekt Mappe aus.

4. Fügen Sie den archivierten Quell Speicherort den Eigenschaften für diese neue Projekt Mappe hinzu. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten Projekt Mappe, und klicken Sie dann auf **Eigenschaften** Wählen Sie im Dialogfeld **Eigenschaften Seiten** die Option **Quelldateien debuggen** aus, und fügen Sie dann das Verzeichnis des archivierten Quellcodes hinzu. Andernfalls findet der Debugger die veralteten Quelldateien, da die Quelldatei Pfade in der PDB-Datei aufgezeichnet werden. Wenn der Debugger veraltete Quelldateien verwendet, wird eine Meldung angezeigt, die besagt, dass die Quelle nicht stimmt.

5. Stellen Sie sicher, dass der Debugger die *PDB* -Dateien finden kann. Wenn Sie diese mit der Anwendung bereitgestellt haben, findet der Debugger diese automatisch. Sie sucht immer zuerst neben der fraglichen Assembly. Andernfalls müssen Sie den Archivpfad zu den **Symbol Datei Standorten (. pdb)** hinzufügen (um auf diese Option zuzugreifen, klicken Sie im **Menü Extras** auf **Optionen** , öffnen Sie den Knoten **Debuggen** , und klicken Sie auf **Symbole** ).

6. Debuggen Sie, was zwischen den `CheckForUpdate` `Download` / `Update` Methoden aufrufen und passiert.

    Der Aktualisierungs Code könnte z. b. wie folgt lauten:

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. Stellen Sie Version 2 bereit.

8. Versuchen Sie, den Debugger an die Anwendung Version 1 anzufügen, während ein Update für Version 2 heruntergeladen wird. Alternativ können Sie die- `System.Diagnostics.Debugger.Break` Methode oder einfach `Stop` in Visual Basic verwenden. Natürlich sollten Sie diese Methodenaufrufe nicht im Produktionscode belassen.

    Nehmen Sie beispielsweise an, Sie entwickeln eine Windows Forms Anwendung, und Sie verfügen über einen Ereignishandler für diese Methode mit der Update Logik. Um dies zu debuggen, fügen Sie einfach an, bevor die Schaltfläche gedrückt wird. Legen Sie dann einen Haltepunkt fest (stellen Sie sicher, dass Sie die entsprechende archivierte Datei öffnen und den Haltepunkt dort festlegen)

   Verwenden Sie die- <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> Eigenschaft, um die APIs nur aufzurufen, <xref:System.Deployment.Application> Wenn die Anwendung bereitgestellt wird. die APIs sollten beim Debuggen in nicht aufgerufen werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Siehe auch
- <xref:System.Deployment.Application>