---
title: Dialog Feld "Workflow-Designer-korrelateson-Definition"
description: Erfahren Sie, wie Sie das Dialogfeld CorrelatesOn in Workflow-Designer verwenden können, um die CorrelatesOn-Eigenschaft einer Receive-Aktivität zu bearbeiten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2be38ba9521762c38c629c2817a7c8e8ca5a709a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438125"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn-Definition (Dialogfeld)

Das Dialogfeld **CorrelatesOn** wird in Workflow-Designer verwendet, um die- <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft einer-Aktivität zu bearbeiten <xref:System.ServiceModel.Activities.Receive> . Weitere Informationen finden Sie unter [Receive-Aktivitäts Designer](../workflow-designer/receive-activity-designer.md).

Die Korrelation zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten gibt an, in welcher Beziehung verschiedene Dienstvorgänge in einem Workflow miteinander stehen.

In der folgenden Tabelle werden die Elemente der Benutzeroberfläche (UI) des Dialog Felds **CorrelatesOn** beschrieben.

|Benutzeroberflächenelement|BESCHREIBUNG|
|-|-----------------|
|**CorrelatesWith**|Die <xref:System.ServiceModel.Activities.CorrelationHandle>-Instanz, die verwendet wird, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden Nachrichten extrahiert werden. Dieser Wert entspricht der- <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft. Die XPath-Abfragen sind in einem <xref:System.ServiceModel.MessageQuerySet>-Objekt enthalten.|

## <a name="to-launch-the-correlateson-dialog-box"></a>So öffnen Sie das Dialogfeld CorrelatesOn

Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, wo Aktivitäten normalerweise platziert werden. Beim Löschen des Aktivitäts Designers wird eine- <xref:System.ServiceModel.Activities.Receive> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Um das Dialogfeld **CorrelatesOn-Definition** zu öffnen, wählen Sie den **Receive** -Aktivitäts Designer aus, und wählen Sie dann im Eigenschaften Raster die Schaltfläche mit den Auslassungs Zeichen neben dem Sammlungs Text für die **CorrelatesOn** -Eigenschaft aus.

## <a name="see-also"></a>Siehe auch

- <xref:System.ServiceModel.Activities.Receive>
- [CorrelationInitializers hinzufügen (Dialogfeld)](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)