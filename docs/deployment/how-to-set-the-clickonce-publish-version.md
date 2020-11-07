---
title: Festlegen der ClickOnce-Veröffentlichungs Version | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Eigenschaft "ClickOnce-Veröffentlichungs Version" festlegen, die bestimmt, ob die Anwendung ein Update ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 100c3cd12a3011d35445ac885333802e28b4a92f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349788"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion
Die- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Eigenschaft bestimmt, ob die Anwendung, die Sie veröffentlichen, als Update behandelt wird. Jedes Mal, wenn die Version erhöht wird, wird die Anwendung als Update veröffentlicht.

 Die- `Publish Version` Eigenschaft kann auf der Seite **veröffentlichen** des Projekt- **Designers** festgelegt werden.

> [!NOTE]
> Es gibt eine Projekt Option, mit der die `Publish Version` Eigenschaft bei jeder Veröffentlichung der Anwendung automatisch erhöht wird. diese Option ist standardmäßig aktiviert. Weitere Informationen finden Sie unter Gewusst [wie: Automatisches erhöhen der ClickOnce-Veröffentlichungs Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>So ändern Sie die Veröffentlichungs Version

1. Wenn ein Projekt in **Projektmappen-Explorer** ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Erhöhen Sie im Feld **Veröffentlichungs Version** die Versionsnummern **Major** , **Minor** , **Build** oder **Revision** .

    > [!NOTE]
    > Sie sollten nie eine Versionsnummer Dekrement. Dies kann zu unvorhersehbarem Update Verhalten führen.

## <a name="see-also"></a>Weitere Informationen
- [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)
- [Gewusst wie: Automatisches erhöhen der ClickOnce-Veröffentlichungs Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)