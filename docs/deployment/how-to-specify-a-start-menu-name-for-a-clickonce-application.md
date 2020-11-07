---
title: Angeben des Start Menü namens für eine ClickOnce-App
description: Erfahren Sie, wie Sie den anzeigen Amen für Ihre ClickOnce-Anwendung ändern, indem Sie im Dialogfeld Veröffentlichungs Optionen den Product Name festlegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a6ebce0ff3bb7c3040765c1a82f876d0055c4d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349671"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Vorgehensweise: Angeben eines Namens im Startmenü für eine ClickOnce-Anwendung
Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung für die Online-und Offline Verwendung installiert wird, wird dem **Startmenü** und der Liste Software **Add or Remove Programs** ein Eintrag hinzugefügt. Standardmäßig ist der Anzeige Name mit dem Namen der Anwendungsassembly identisch, aber Sie können den anzeigen Amen ändern, indem Sie im Dialogfeld **Veröffentlichungs Optionen** den **Product Name** festlegen.

 Der **Produktname** wird auf der Seite " *publish.htm* " angezeigt. bei einer installierten offline Anwendung handelt es sich um den Namen des Eintrags im **Startmenü** . Außerdem handelt es **sich dabei um** den Namen, der in "Software" angezeigt wird.

 Der **Herausgeber Name** wird auf der *publish.htm* Seite oberhalb des **Produkt namens** angezeigt, und für eine installierte offline Anwendung ist dies auch der Name des Ordners, der das Anwendungssymbol im **Startmenü** enthält.

 Die Start Menü Verknüpfung oder die APP-Referenz wird in *%AppData%\Microsoft\Windows\Start menu\programme \\<Herausgeber Name \>* erstellt. Die Verknüpfung oder der APP-Verweis hat denselben Namen wie der Produktname.

 Sie können die Eigenschaften **Produktname** und **Herausgeber Name** im Dialogfeld **Veröffentlichungs Optionen** festlegen, das auf der Seite **veröffentlichen** des **Projekt-Designers** verfügbar ist.

### <a name="to-specify-a-start-menu-name"></a>So geben Sie einen Startmenü Namen an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.

4. Klicken Sie auf **Beschreibung**.

5. Geben Sie im Dialogfeld **Veröffentlichungs Optionen** den Namen ein, der unter **Produktname** angezeigt werden soll.

6. Optional können Sie einen Herausgeber Namen in den **Herausgeber Namen** eingeben.

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)