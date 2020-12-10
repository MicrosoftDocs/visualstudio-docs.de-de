---
title: SendAndReceiveReply-Vorlagendesigner
description: Erfahren Sie, wie Sie die sendandreceivereply-Vorlage in Workflow-Designer verwenden können, um ein paar vorkonfigurierter Sende-und receivereply-Aktivitäten zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91885371f72c5756ddc026111404f091a2cccf08
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993262"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply-Vorlagendesigner

Die **sendandreceivereply** -Vorlage wird verwendet, um ein paar vorkonfigurierter-und-Aktivitäten zu erstellen <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Die Aktivitäten sind Teil einer- <xref:System.Activities.Statements.Sequence> Aktivität und werden als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Client korreliert.

## <a name="the-sendandreceivereply-template"></a>Die sendandreceivereply-Vorlage

Durch das Hinzufügen der **sendandreceivereply** -Vorlage werden neben dem Erstellen der <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten und innerhalb einer-Aktivität drei Schritte ausgeführt <xref:System.Activities.Statements.Sequence> :

- Konfiguriert die <xref:System.ServiceModel.Activities.Send.OperationName%2A> -Eigenschaft und die-Eigenschaft der- <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> <xref:System.ServiceModel.Activities.Send> Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-sendandreceivereply-template-designer"></a>Verwenden des Vorlagen-Designers sendandreceivereply

Greifen Sie auf den **sendandreceivereply** -Aktivitäts Designer in der Kategorie **Messaging** der **Toolbox** zu. Der **sendandreceivereply** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Beim Löschen des Aktivitäts Designers <xref:System.ServiceModel.Activities.Send> wird eine-Aktivität erstellt, die mit dem **Send** -Aktivitäts Designer konfiguriert werden kann, und eine korrelierte-Aktivität <xref:System.ServiceModel.Activities.ReceiveReply> , die mit dem **receivereplyforsend** -Designer konfiguriert werden kann.

Weitere Informationen zum Konfigurieren der Aktivität mithilfe des **Sende** -Designers <xref:System.ServiceModel.Activities.Send> finden Sie unter [senden](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Eigenschaften von ReceiveReply

In der folgenden Tabelle sind die Eigenschaften aufgeführt, <xref:System.ServiceModel.Activities.ReceiveReply> und es wird beschrieben, wie Sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf der Workflow-Designer Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der optionale Anzeigename der <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Der Standardwert lautet ReceiveReplyForSend.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für die Benutzerfreundlichkeit <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Verweis auf die dieser <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität. Diese Eigenschaft darf nicht **null** sein. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>die Aktivitäten und werden auf dem Client zum Modellieren eines Anforderungs-/Antwort-messagingmusters verwendet. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da Sie automatisch an die Aktivität gebunden ist, <xref:System.ServiceModel.Activities.Send> aus der Sie die <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität erstellt haben. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Feld **Inhalt** im Eigenschaften Raster klicken, oder indem Sie auf der Oberfläche **des Empfangs** Aktivitäts Designers neben der **Inhalts** Bezeichnung auf die Schaltfläche **definieren** klicken. Beide zeigen das Dialogfeld **Inhalts Definition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie unter [Inhalts Definition (Dialog Feld](../workflow-designer/content-definition-dialog-box.md)). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie im Eigenschaften Raster neben der Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> , um das Dialogfeld **korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie unter [Dialog Feld "correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md)". |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn Sie nicht explizit festgelegt ist, wird der Wert standardmäßig auf Folgendes festgelegt:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Weitere Informationen

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)