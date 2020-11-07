---
title: Angeben einer Veröffentlichungs Seite (ClickOnce-APP)
description: Erfahren Sie, wie Sie die Eigenschaft Veröffentlichungs Seite für Ihr Projekt festlegen, mit der Sie eine Webseite für Ihre ClickOnce-Anwendung angeben können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecf70f5ffdd81688943892c06fdf98aae73d6c57
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350958"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung
Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird eine Standard Webseite (publish.htm) generiert und zusammen mit der Anwendung veröffentlicht. Diese Seite enthält den Namen der Anwendung, einen Link zum Installieren der Anwendung und/oder alle Voraussetzungen sowie einen Link zu einem Hilfethema, das beschreibt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Mit der Eigenschaft **Veröffentlichungs Seite** für Ihr Projekt können Sie einen Namen für die Webseite für Ihre Anwendung angeben [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Nachdem die Veröffentlichungs Seite angegeben wurde, wird Sie beim nächsten veröffentlichen an den Veröffentlichungs Speicherort kopiert. Sie wird nicht überschrieben, wenn Sie Sie erneut veröffentlichen. Wenn Sie das Erscheinungsbild der Seite anpassen möchten, können Sie dies tun, ohne sich Gedanken über den Verlust der Änderungen machen zu müssen. Weitere Informationen finden Sie unter Gewusst [wie: Anpassen der ClickOnce-Standard Webseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 Die Eigenschaft **Veröffentlichungs Seite** kann im Dialogfeld **Veröffentlichungs Optionen** festgelegt werden, das über den Bereich **veröffentlichen** des Projekt- **Designers** zugänglich ist.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>So geben Sie eine benutzerdefinierte Webseite für eine ClickOnce-Anwendung an

1. Wenn ein Projekt in **Projektmappen-Explorer** ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Wählen Sie den Bereich **veröffentlichen** aus.

3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.

4. Klicken Sie auf **Bereitstellung**.

5. Stellen Sie im Dialogfeld **Veröffentlichungs Optionen** sicher, dass das Kontrollkästchen **Bereitstellung nach der Veröffentlichung öffnen** aktiviert ist (standardmäßig ausgewählt).

6. Geben Sie im Feld **Bereitstellungs Webseite** den Namen für die Webseite ein, und klicken Sie dann auf **OK**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>So verhindern Sie, dass die Veröffentlichungs Seite jedes Mal gestartet wird, wenn Sie veröffentlichen

1. Wenn ein Projekt in **Projektmappen-Explorer** ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Wählen Sie den Bereich **veröffentlichen** aus.

3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.

4. Klicken Sie auf **Bereitstellung**.

5. Deaktivieren Sie im Dialogfeld **Veröffentlichungs Optionen** das Kontrollkästchen **Bereitstellungs Webseite nach Veröffentlichung öffnen** .

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Gewusst wie: Anpassen der ClickOnce-Standard Webseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)