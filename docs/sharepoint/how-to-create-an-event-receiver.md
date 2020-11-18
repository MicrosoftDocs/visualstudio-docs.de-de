---
title: 'Vorgehensweise: Erstellen eines Ereignis Empfängers | Microsoft-Dokumentation'
description: Erstellen Sie einen Ereignis Empfänger, damit Sie Antworten können, wenn ein Benutzer mit SharePoint-Elementen (z. b. Listen oder Listenelementen) interagiert.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e94bd1594f94f43c82eed5033d6ec2660905c18
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849882"
---
# <a name="how-to-create-an-event-receiver"></a>Vorgehensweise: Erstellen eines Ereignis Empfängers
  Durch das Erstellen von *Ereignis Empfängern* können Sie Antworten, wenn ein Benutzer mit SharePoint-Elementen, z. b. Listen oder Listenelementen, interagiert. Beispielsweise kann der Code in einem Ereignis Empfänger ausgelöst werden, wenn ein Benutzer den Kalender ändert oder einen Namen aus einer Kontaktliste löscht. In diesem Thema erfahren Sie, wie Sie einen Ereignis Empfänger zu einer Listen Instanz hinzufügen.

 Um diese Schritte ausführen zu können, müssen die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Windows-und SharePoint-Editionen installiert und unterstützt werden. Da für dieses Beispiel ein SharePoint-Projekt erforderlich ist, müssen Sie auch das Verfahren im Thema Exemplarische Vorgehensweise [: Erstellen einer Websites palte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)abgeschlossen haben.

## <a name="adding-an-event-receiver"></a>Hinzufügen eines Ereignis Empfängers
 Das Projekt, das Sie in Exemplarische Vorgehensweise [: Erstellen einer Websites palte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) erstellt haben, enthält benutzerdefinierte Websites Palten, eine benutzerdefinierte Liste und einen Inhaltstyp. Im folgenden Verfahren erweitern Sie dieses Projekt, indem Sie einen einfachen Ereignishandler (einen Ereignis Empfänger) zu einer Listen Instanz hinzufügen, um anzuzeigen, wie Ereignisse behandelt werden, die in SharePoint-Elementen wie z. b. Listen auftreten.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>So fügen Sie der Listen Instanz einen Ereignis Empfänger hinzu

1. Öffnen Sie das Projekt, das Sie in Exemplarische Vorgehensweise [: Erstellen einer Websites palte, eines Inhaltstyps und einer Liste für SharePoint erstellt haben](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. Wählen Sie in **Projektmappen-Explorer** den SharePoint-Projekt Knoten aus, der als " **Clinic**" bezeichnet wird.

3. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

4. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann das Element **2010** aus.

5. Wählen Sie im Bereich **Vorlagen** die Option **Ereignis Empfänger**, benennen Sie Sie **TestEventReceiver1**, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

6. Wählen Sie in der Liste **welche Art von Ereignis Empfänger möchten Sie verwenden?** die Option **Listenelement Ereignisse** aus.

7. Wählen Sie in der Liste **welches Element soll die Ereignis Quelle sein? die** Option **Patienten (clinic\patienten)** aus.

8. Aktivieren Sie in der Liste **folgende Ereignisse behandeln** das Kontrollkästchen neben **einem hinzugefügten Element**, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

     Die Codedatei für den neuen Ereignis Empfänger enthält eine einzelne Methode mit dem Namen `ItemAdded` . Im nächsten Schritt fügen Sie dieser Methode Code hinzu, damit jeder Kontakt standardmäßig mit Scott Brown benannt wird.

9. Ersetzen Sie die vorhandene `ItemAdded` -Methode durch den folgenden Code, und drücken Sie dann die **F5** -Taste:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Der Code wird ausgeführt, und die SharePoint-Website wird im Webbrowser angezeigt.

10. Wählen Sie auf der Schnellstartleiste den Link **Patienten** aus, und wählen Sie dann den Link **Neues Element hinzufügen** aus.

     Das Eingabeformular für neue Elemente wird geöffnet.

11. Geben Sie Daten in die Felder ein, und klicken Sie dann auf die Schaltfläche **Speichern** .

     Nachdem Sie die Schaltfläche **Speichern** ausgewählt haben, wird die Spalte **Patienten Name** automatisch auf den Namen Scott Brown aktualisiert.

## <a name="see-also"></a>Weitere Informationen

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)