---
title: Workflow-Designer-CorrelationScope-Aktivitäts Designer
description: Erfahren Sie, wie Sie den CorrelationScope-Aktivitäts Designer verwenden können, um eine CorrelationScope-Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9edd755465cf812c1572c62f1c6335fc5295281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955519"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope-Aktivitätsdesigner

Der **CorrelationScope** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.ServiceModel.Activities.CorrelationScope> , die die implizite Verwaltung von untergeordneten Messaging Aktivitäten mithilfe eines- <xref:System.ServiceModel.Activities.CorrelationHandle> Objekts ermöglicht.

## <a name="the-correlationscope-activity"></a>Die CorrelationScope-Aktivität

Die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>-Eigenschaft gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird. Die <xref:System.ServiceModel.Activities.Send>-Aktivität und die <xref:System.ServiceModel.Activities.Receive>-Aktivität, die im <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>-Objekt enthalten sind, werden so konfiguriert, dass sie die <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>-Eigenschaft der übergeordneten <xref:System.ServiceModel.Activities.CorrelationScope>-Aktivität verwenden, um die Korrelation auszuführen.

### <a name="use-the-correlationscope-activity-designer"></a>Verwenden des CorrelationScope-Aktivitäts Designers

Der **CorrelationScope** -Aktivitäts Designer befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **CorrelationScope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden. Dadurch wird eine- <xref:System.ServiceModel.Activities.CorrelationScope> Aktivität mit dem **Display Name** -Standardwert von CorrelationScope erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **CorrelationScope** -Aktivitäts Designers oder im Feld **Display Name** des **Eigenschaften** Fensters bearbeitet werden.

Um die von untergeordneten <xref:System.ServiceModel.Activities.CorrelationHandle> Messaging Aktivitäten verwendete anzugeben, wählen Sie im **Eigenschaften** Fenster neben dem Feld **correlateswith** die Schaltfläche mit den Auslassungs Zeichen aus, um das Dialogfeld **Ausdrucks-Editor** anzuzeigen. Diese Eigenschaft kann auch in der Aktivitätsdesigneroberfläche festgelegt werden.

Die innerhalb der Korrelation enthaltenen Aktivitäten werden durch Löschen Ihrer Designer innerhalb des Felds **Body** innerhalb des **CorrelationScope** -Designers angegeben.

### <a name="the-correlationscope-properties"></a>Die CorrelationScope-Eigenschaften

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.CorrelationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können entweder im **Eigenschaften** Fenster oder auf der Workflow-Designer Oberfläche und häufig in beiden geändert werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Falsch|Gibt das <xref:System.ServiceModel.Activities.CorrelationHandle>-Handle an, das zum Verwalten der untergeordneten Messagingaktivitäten verwendet wird. Wenn Sie diese Eigenschaft nicht festlegen, erstellt <xref:System.ServiceModel.Activities.CorrelationScope> automatisch einen impliziten <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Falsch|Gibt die Aktivitäten im Bereich der Korrelation an.|

## <a name="see-also"></a>Weitere Informationen

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Medizinisch](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Senden](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)