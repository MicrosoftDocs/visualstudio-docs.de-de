---
title: Automatisches Inkrement der ClickOnce-Veröffentlichungs Version
description: Erfahren Sie, wie Sie die automatische Inkrementierung der Revisionsnummer für Ihre ClickOnce-Anwendung mit Visual Studio deaktivieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947774"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion

Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung bewirkt das Ändern der- `Publish Version` Eigenschaft, dass die Anwendung als Update veröffentlicht wird. Standardmäßig erhöht Visual Studio automatisch die `Revision` Anzahl von, wenn `Publish Version` Sie die Anwendung veröffentlichen.

Sie können dieses Verhalten auf der Seite **veröffentlichen** des Projekt- **Designers** deaktivieren.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>So deaktivieren Sie die automatische Inkrementierung der Veröffentlichungs Version

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer** im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Deaktivieren Sie im Abschnitt Veröffentlichungs **Version** das Kontrollkästchen **Automatische Schritt weite Revision mit jeder Version** .

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Festlegen der ClickOnce-Veröffentlichungs Version](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)