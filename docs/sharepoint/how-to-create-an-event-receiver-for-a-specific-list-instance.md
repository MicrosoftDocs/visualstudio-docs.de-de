---
title: 'Vorgehensweise: Erstellen eines Ereignis Empfängers für eine bestimmte Listen Instanz | Microsoft-Dokumentation'
titleSuffix: ''
description: Erstellen Sie einen Ereignis Empfänger für eine bestimmte Listen Instanz. Ein List instance-Ereignis Empfänger antwortet auf Ereignisse, die in einer beliebigen Instanz einer Listen Definition auftreten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 664a7ac4e763b2378cf30603c417aacde27c2e47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925492"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Gewusst wie: Erstellen eines Ereignis Empfängers für eine bestimmte Listen Instanz
  Ein List instance-Ereignis Empfänger antwortet auf Ereignisse, die in einer beliebigen Instanz einer Listen Definition auftreten. Obwohl die Ereignis Empfänger Vorlage nicht das Ziel einer bestimmten Listen Instanz ermöglicht, können Sie einen Ereignis Empfänger ändern, der auf eine Listen Definition festgelegt ist, um auf Ereignisse in einer bestimmten Listen Instanz zu reagieren.

 Um eine bestimmte Listen Instanz als Ziel zu erhalten, ersetzen Sie im *Elements.xml* für den Ereignis Empfänger `ListTemplateId` durch, `ListUrl` und fügen Sie die URL der Listen Instanz hinzu.

## <a name="create-a-list-instance-event-receiver"></a>Erstellen eines Listen Instanz-Ereignis Empfängers
 In den folgenden Schritten wird gezeigt, wie ein Listenelement-Ereignis Empfänger so geändert wird, dass er nur auf Ereignisse antwortet, die in einer benutzerdefinierten Ankündigungs Listen Instanz auftreten.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>So ändern Sie einen Ereignis Empfänger so, dass er auf eine bestimmte Listen Instanz antwortet

1. Öffnen Sie die SharePoint-Website in einem Browser.

2. **Listen** Sie im Navigationsbereich den Link auf.

3. Wählen Sie auf der Seite **alle Website Inhalte** den Link **Erstellen** aus.

4. Wählen Sie im Dialogfeld **Erstellen** den Typ **Ankündigungen** aus, benennen Sie die Ankündigung **testannouncements**, und wählen Sie dann die Schaltfläche **Erstellen** aus.

5. Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Ereignis Empfänger Projekt.

6. Wählen Sie in der Liste **welche Art von Ereignis Empfänger möchten Sie verwenden?** die Option **Listenelement Ereignisse** aus.

    > [!NOTE]
    > Sie können auch eine beliebige andere Art von Ereignis Empfänger für eine Listen Definition auswählen, z. b. **e-Mail-Ereignisse auflisten** oder **Workflow Ereignisse auflisten**.

7. Wählen Sie in der Liste **welches Element soll die Ereignis Quelle sein? die** Option **Ankündigungen** aus.

8. Wählen Sie in der Liste **folgende Ereignisse behandeln** das Kontrollkästchen **ein Element wird hinzugefügt werden** aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

9. Öffnen Sie in **Projektmappen-Explorer** unter EventReceiver1 den *Elements.xml*.

     Der Ereignis Empfänger verweist derzeit mithilfe der folgenden Zeile auf die Definition der Ankündigungsliste:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Ändern Sie diese Zeile in den folgenden Text:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Dadurch wird der Ereignis Empfänger aufgefordert, nur auf Ereignisse zu reagieren, die in der neuen Liste der von Ihnen soeben erstellten **testannouncements** -Ankündigungen auftreten. Sie können das- `ListURL` Attribut so ändern, dass es auf eine beliebige Listen Instanz auf dem SharePoint-Server verweist.

10. Öffnen Sie die Codedatei für den Ereignis Empfänger, und platzieren Sie einen Haltepunkt in der ItemAdding-Methode.

11. Drücken Sie die Taste **F5** , um die Projekt Mappe zu erstellen und auszuführen.

12. Wählen Sie in SharePoint den Link **testannounzemente** im Navigationsbereich aus.

13. Wählen Sie den Link **neue Ankündigung hinzufügen** aus.

14. Geben Sie einen Titel für die Ankündigung ein, und klicken Sie dann auf die Schaltfläche **Speichern** .

     Beachten Sie, dass der Breakpoint gedrückt wird, wenn das neue Element der Liste benutzerdefinierter Ankündigungen hinzugefügt wird.

15. Drücken Sie die Taste **F5** , um fortzufahren.

16. Wählen Sie im Navigationsbereich den Link **Listen** aus, und wählen Sie dann den Link **Ankündigungen** aus.

17. Fügen Sie eine neue Ankündigung hinzu.

     Beachten Sie, dass der Ereignis Empfänger in der neuen Ankündigung nicht auslöst, da der Empfänger so konfiguriert ist, dass er nur auf Ereignisse in der benutzerdefinierten Ankündigungs Listen Instanz ( **testannouncements**) antwortet.

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
