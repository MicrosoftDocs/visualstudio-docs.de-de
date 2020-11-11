---
title: Workflow-Designer ForEach &lt; T- &gt; Aktivitäts Designer
description: Erfahren Sie, wie die ForEach- <T> Aktivität die im Text enthaltene Aktivität für jedes Element in einer angegebenen Werte Auflistung ausführt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fd81377ca24dfbeaf4a25f2af00fb69f4821d73
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437982"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; T- &gt; Aktivitäts Designer

Die <xref:System.Activities.Statements.ForEach%601>-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>-Auflistung aus.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Foreach-<T- \> Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|FALSE|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>-Aktivität. Der Standardwert ist foreach<Int32 \> . Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Wahr|Die Auflistung, deren Elemente durchlaufen werden. Um den festzulegen <xref:System.Activities.Statements.ForEach%601.Values%2A> , geben Sie im Feld **Werte** des **foreach-<T \>** -Aktivitäts Designers oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|
|*TypeArgument*|Wahr|Der Typ der Elemente in der Auflistung, die <xref:System.Activities.Statements.ForEach%601.Values%2A> durch den generischen Parameter *T* angegeben werden. Standardmäßig ist *TypeArgument* auf **Int32** festgelegt. Ändern Sie den Wert des Kombinations Felds *TypeArgument* im Eigenschaften Raster, um den Typ zu ändern.|

Standardmäßig wird als Schleifen Iterator " **Item** " bezeichnet. Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>-Aktivitätsdesigner ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Siehe auch

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
