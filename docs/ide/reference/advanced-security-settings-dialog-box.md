---
title: Erweiterte Sicherheitseinstellungen (Dialogfeld)
description: Mithilfe des Dialogfelds „Erweiterte Sicherheitseinstellungen“ können Sie Sicherheitseinstellungen bezüglich des Debuggens in einer Zone festlegen.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffbf2bb5a8a73ba577489af825969c3bdc23f15e
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351504"
---
# <a name="advanced-security-settings-dialog-box"></a>Erweiterte Sicherheitseinstellungen (Dialogfeld)

Mit diesem Dialogfeld können Sie Sicherheitseinstellungen bezüglich des Debuggens in einer Zone angeben.

![Erweiterte Sicherheitseinstellungen (Dialogfeld) in Visual Studio](../media/advanced-security-settings.png)

Wählen Sie zum Aufrufen des Dialogfelds im **Projektmappen-Explorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit**. Wählen Sie auf der Seite **Sicherheit** die Option **ClickOnce-Sicherheitseinstellungen aktivieren** aus, klicken Sie auf **Teilweise vertrauenswürdige Anwendung**, und klicken Sie dann auf **Erweitert**.

## <a name="uielement-list"></a>UIElement-Liste

**Der Anwendung Zugriff auf die Ursprungssite gewähren**

Wenn Sie dieses Kontrollkästchen aktivieren, kann die Anwendung auf die Website oder die Serverfreigabe, auf der sie veröffentlicht wird, zugreifen. Diese Option ist standardmäßig ausgewählt.

**Diese Anwendung debuggen, als ob sie von folgender URL heruntergeladen würde:**

Wenn Sie der Anwendung erlauben müssen, auf die Website oder die Serverfreigabe entsprechend der **Installations-URL** zuzugreifen, die Sie auf der Seite **Veröffentlichen** angegeben haben, geben Sie die URL hier ein. Diese Option ist nur verfügbar, wenn **Der Anwendung Zugriff auf die Ursprungssite gewähren** ausgewählt ist.

## <a name="see-also"></a>Siehe auch

- [Seite "Sicherheit", Projekt-Designer](../../ide/reference/security-page-project-designer.md)
