---
title: Ausführen eines Einzelschritts in WCF-Diensten | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Einzelschritte in WCF-Diensten (Windows Communication Foundation) durchführen. Wenn der WCF-Dienst sich in derselben Visual Studio-Projektmappe wie der Client befindet, können Sie Breakpoints im WCF-Dienst erreichen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f3a884698586cdd9a89ff62a090f02af3953a91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896632"
---
# <a name="how-to-step-into-wcf-services"></a>Vorgehensweise: Ausführen eines Einzelschritts in WCF-Diensten
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie einen Einzelschritt in einen WCF-Dienst ausführen. Wenn sich der WCF-Dienst in derselben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe wie der Client befindet, erreichen Sie Haltepunkte innerhalb des WCF-Dienstes.

 Damit dies funktioniert, müssen Sie das Debuggen in der Datei app.config oder Web.config aktivieren. Weitere Informationen zum Aktivieren des Debuggens sowie zu Einschränkungen beim Ausführen von Einzelschritten in WCF-Dienste finden Sie unter [Einschränkungen beim WCF-Debuggen](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>So führen Sie einen Einzelschritt in einen WCF-Dienst aus

1. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, die sowohl den WCF-Client als auch WCF-Dienstprojekte enthält.

2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das WCF-Clientprojekt, und klicken Sie dann auf **Als Startprojekt festlegen**.

3. Aktivieren Sie das Debuggen in der Datei app.config oder web.config. Weitere Informationen finden Sie unter [Einschränkungen beim WCF-Debuggen](../debugger/limitations-on-wcf-debugging.md).

4. Setzen Sie an der Stelle im Clientprojekt, an der Sie die schrittweise Ausführung beginnen möchten, einen Haltepunkt. Üblicherweise wird dies vor dem Aufruf des WCF-Diensts sein.

5. Ausführen bis zum Haltepunkt, dann Beginnen der schrittweisen Ausführung. Der Debugger führt die schrittweise Ausführung des Diensts automatisch durch.

## <a name="see-also"></a>Siehe auch
- [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)
- [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md)
- [How to: Debuggen eines lokal gehosteten WCF-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)