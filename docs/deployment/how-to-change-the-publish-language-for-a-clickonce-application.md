---
title: Ändern der Veröffentlichungs Sprache für die ClickOnce-Anwendung
description: Erfahren Sie, wie Sie eine Sprache/Kultur für eine lokalisieren-Anwendung in ClickOnce angeben, anstatt die Sprache bzw. Kultur Ihres Entwicklungs Computers zu verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0d9c3d49dde0bdef41e89ee71139fb1ab621297
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851464"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Vorgehensweise: Ändern der Sprache für die Veröffentlichung einer ClickOnce-Anwendung

Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird die Benutzeroberfläche, die während der Installation angezeigt wird, standardmäßig auf die Sprache und Kultur Ihres Entwicklungs Computers angewendet. Wenn Sie eine lokalisierte Anwendung veröffentlichen, müssen Sie eine Sprache und eine Kultur angeben, die mit der lokalisierten Version verglichen werden soll. Dies wird durch die- `Publish language` Eigenschaft für Ihr Projekt festgelegt.

Die- `Publish language` Eigenschaft kann im Dialogfeld **Veröffentlichungs Optionen** festgelegt werden, das über die Seite **veröffentlichen** des **Projekt-Designers** zugänglich ist.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>So ändern Sie die Veröffentlichungs Sprache

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.

4. Klicken Sie auf **Beschreibung**.

5. Wählen Sie im Dialogfeld **Veröffentlichungs Optionen** in der Dropdown Liste **Veröffentlichungs Sprache** eine Sprache und Kultur aus, und klicken Sie dann auf **OK**.

## <a name="see-also"></a>Weitere Informationen

- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)