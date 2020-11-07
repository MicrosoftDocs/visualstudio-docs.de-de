---
title: Aktivieren von AutoStart für CD-Installationen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Autostart aktivieren, wenn Sie eine ClickOnce-Anwendung mithilfe von Wechselmedien wie CD-ROM oder DVD-ROM bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6ed3df72b98454c4669e7d9bcd21c0612a6fef3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349957"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Vorgehensweise: Aktivieren von AutoStart für CD-Installationen
Beim Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe von Wechselmedien wie CD-ROM oder DVD-ROM können Sie aktivieren, `AutoStart` damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung beim Einfügen des Mediums automatisch gestartet wird.

 `AutoStart` kann auf der Seite **veröffentlichen** des **Projekt-Designers** aktiviert werden.

### <a name="to-enable-autostart"></a>So aktivieren Sie Autostart

1. Wenn ein Projekt in **Projektmappen-Explorer** ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Optionen** .

     Das Dialogfeld **Veröffentlichungs Optionen** wird angezeigt.

4. Klicken Sie auf **Bereitstellung**.

5. Aktivieren Sie das Kontrollkästchen **bei CD-Installationen, beim Einfügen der CD automatisch starten** .

     Wenn die Anwendung veröffentlicht wird, wird eine *Autorun. inf* -Datei an den Speicherort der Veröffentlichung kopiert.

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)