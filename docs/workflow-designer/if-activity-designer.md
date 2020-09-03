---
title: Workflow-Designer-if-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 099be38c5585fe19c00b31c00ac3a7ddcd3d7fe2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "76111462"
---
# <a name="if-activity-designer"></a>If-Aktivitätsdesigner

Die <xref:System.Activities.Statements.If>-Aktivität wertet eine Bedingung aus und führt eine Aktivität aus, die von den Ergebnissen dieser Auswertung abhängig ist. Bei Verwendung eines Programmierstils nach Art der Verfahrensmodellierung ist diese Aktivität höchst nützlich. Eine <xref:System.Activities.Statements.If>-Aktivität kann in eine <xref:System.Activities.Statements.Sequence>-Aktivität oder beispielsweise eine <xref:System.Activities.Statements.Parallel>-Aktivität geschachtelt werden. Wenn Sie eine <xref:System.Activities.Statements.Flowchart>-Aktivität verwenden, sollten Sie in Erwägung ziehen, stattdessen eine <xref:System.Activities.Statements.FlowDecision>-Aktivität zu verwenden.

## <a name="if-properties-in-the-workflow-designer"></a>If- Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.If>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Richtig|Die Bedingung, die die auszuführende untergeordnete Aktivität bestimmt. Um das festzulegen <xref:System.Activities.Statements.If.Condition%2A> , geben Sie im **if** -Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic Ausdruck im Feld **Bedingung** ein.|
|<xref:System.Activities.Statements.If.Else%2A>|Falsch|Die Aktivität, die ausgeführt werden soll, wenn <xref:System.Activities.Statements.If.Condition%2A> **false**ist. Um eine Aktivität hinzuzufügen, die von der <xref:System.Activities.Statements.If.Else%2A> Verzweigung ausgeführt wird, legen Sie eine Aktivität aus der **Toolbox** im **if** -Aktivitäts Designer auf dem Feld **else** mit dem Hinweis Text "Aktivität hier ablegen" ab.|
|<xref:System.Activities.Statements.If.Then%2A>|Falsch|Die Aktivität, die ausgeführt werden soll, wenn <xref:System.Activities.Statements.If.Condition%2A> **true**ist. Um eine Aktivität hinzuzufügen, die von der <xref:System.Activities.Statements.If.Then%2A> Verzweigung ausgeführt wird, legen Sie eine Aktivität aus der **Toolbox** im **if** -Aktivitäts Designer auf dem Feld **Then** mit dem Hinweis Text "Aktivität hier ablegen" ab.|

## <a name="see-also"></a>Weitere Informationen

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
