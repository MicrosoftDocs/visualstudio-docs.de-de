---
title: Workflow-Designer-transactedreceivescope-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75fb1da392bce7dbd0cd7849d83b3b452521e0c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875929"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope-Aktivitätsdesigner

Der **transactedreceivescope** -Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.ServiceModel.Activities.TransactedReceiveScope> .

## <a name="the-transactedreceivescope-activity"></a>Die TransactedReceiveScope-Aktivität

Die <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Aktivität ermöglicht es Ihnen, eine Transaktion in Servertransaktionen einzubinden, die von einem Workflow oder einem Verteiler erstellt werden.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Verwenden des TransactedReceiveScope-Aktivitätsdesigners

Greifen Sie auf den **transactedreceivescope** -Aktivitäts Designer in der Kategorie **Messaging** der **Toolbox**zu. Der **transactedreceivescope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine- <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivität mit dem **Display Name** -Standardwert von transactedreceivescope erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **transactedreceivescope** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

Der **transactedreceivescope** -Designer enthält **Anforderungs** -und **Text** Felder. Diese werden verwendet, um die <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>-Eigenschaft, die eine <xref:System.ServiceModel.Activities.Receive>-Aktivität angibt, und die <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>-Eigenschaft zu konfigurieren, die eine andere <xref:System.Activities.Activity>-Instanz angibt. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> erstellt eine Transaktion. Die Transaktion wird dann dem Geltungsbereich der <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>-Instanz zugeordnet, damit jede Aktivität in diesem Bereich in dieser Transaktion ausgeführt wird.

### <a name="the-transactedreceivescope-properties"></a>Die TransactedReceiveScope-Eigenschaften

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese <xref:System.Activities.Activity.DisplayName%2A> Eigenschaft kann im Eigenschaften Raster oder auf der Workflow-Designer-Oberfläche bearbeitet werden, die anderen müssen jedoch auf der Entwurfs Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Aktivität. Der Standardwert lautet TransactedReceiveScope.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Name nicht unbedingt erforderlich ist, wird als Best Practice empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Richtig|Löscht eine- <xref:System.ServiceModel.Activities.Receive> Aktivität in den **Anforderungs** Block auf der Aktivitäts Designer Oberfläche.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Falsch|Löscht ein <xref:System.Activities.Activity> in den **Body** -Block auf der Aktivitäts Designer Oberfläche.|

## <a name="see-also"></a>Weitere Informationen

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Medizinisch](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)