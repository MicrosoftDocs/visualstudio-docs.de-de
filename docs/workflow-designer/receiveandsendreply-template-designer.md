---
title: ReceiveAndSendReply-Vorlagendesigner
description: Erfahren Sie, wie Sie mit der receiveandsendreply-Vorlage in Workflow-Designer ein paar vorkonfigurierter Receive-und SendReply-Aktivitäten erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f11caa831ca3de0684dd49e46a37620eaa6e435
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996213"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply-Vorlagendesigner

Die **receiveandsendreply** -Vorlage wird verwendet, um ein paar vorkonfigurierter-und-Aktivitäten zu erstellen <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . Die Aktivitäten sind Teil einer- <xref:System.Activities.Statements.Sequence> Aktivität und werden als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Server korreliert.

## <a name="the-receiveandsendreply-template"></a>Die receiveandsendreply-Vorlage

Durch das Hinzufügen einer **receiveandsendreply** -Vorlage werden neben dem Erstellen der <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Aktivitäten und mit einer-Aktivität drei Schritte ausgeführt <xref:System.Activities.Statements.Sequence> :

- Konfiguriert die <xref:System.ServiceModel.Activities.Receive.OperationName%2A> -Eigenschaft und die-Eigenschaft der- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> <xref:System.ServiceModel.Activities.Receive> Aktivität.

- Die Eigenschaft <xref:System.ServiceModel.Activities.SendReply.Request%2A> der <xref:System.ServiceModel.Activities.Receive>-Aktivität wird an die <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden.

- Ein <xref:System.ServiceModel.Activities.CorrelationHandle> wird in der übergeordneten Aktivität als Variable erstellt.

### <a name="use-the-receiveandsendreply-template-designer"></a>Verwenden des receiveandsendreply-Vorlagen-Designers

Greifen Sie in der Kategorie **Messaging** der **Toolbox** auf den **receiveandsendreply** -Aktivitäts Designer zu. Der **receiveandsendreply** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Beim Löschen des Aktivitäts Designers <xref:System.ServiceModel.Activities.Receive> wird eine-Aktivität erstellt, die mit dem **Send** -Aktivitäts Designer konfiguriert werden kann, und eine korrelierte-Aktivität, die <xref:System.ServiceModel.Activities.SendReply> mit dem sendreplytor eceive-Designer konfiguriert werden kann.

Weitere Informationen zum Konfigurieren der Aktivität mithilfe des **Empfangs** -Designers <xref:System.ServiceModel.Activities.Receive> finden Sie unter [Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Eigenschaften von SendReply

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.SendReply>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf der Workflow-Designer Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der optionale Anzeigename der <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Der Standardname lautet SendReplyToReceive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für die Benutzerfreundlichkeit <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Verweis auf die dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität zugeordnete <xref:System.ServiceModel.Activities.SendReply>-Aktivität. Diese Eigenschaft darf nicht **null** sein. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>die Aktivitäten und werden auf dem Server zum Modellieren eines Anforderungs-/Antwort-messagingmusters verwendet. Diese Eigenschaft gibt an, welche <xref:System.ServiceModel.Activities.Send>-Aktivität zugeordnet wird. Im Designer können Sie diese Eigenschaft nicht bearbeiten, da Sie automatisch an die Aktivität gebunden ist, <xref:System.ServiceModel.Activities.Send> aus der Sie die <xref:System.ServiceModel.Activities.SendReply> Aktivität erstellt haben. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Feld **Inhalt** im Eigenschaften Raster klicken, oder indem Sie auf der Oberfläche des **Empfangs** Aktivitäts Designers neben der **Inhalts** Bezeichnung auf die Schaltfläche **definieren** klicken. Beide zeigen das Dialogfeld **Inhalts Definition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Inhalts Definition (Dialog Feld](../workflow-designer/content-definition-dialog-box.md) ). |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie im Eigenschaften Raster neben der Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> , um das Dialogfeld **korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialog Feld "correlationinitializers hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) ". |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn Sie nicht explizit festgelegt ist, wird der Wert standardmäßig auf Folgendes festgelegt:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Gibt an, ob die Workflowinstanz beibehalten werden soll, bevor die Antwortnachricht gesendet wird. Der Standardwert ist **false**. |

## <a name="see-also"></a>Weitere Informationen

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)