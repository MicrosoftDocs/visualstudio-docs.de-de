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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c594e613d1160794e8310695d61bcc97902caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876458"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; T- &gt; Aktivitäts Designer

Die <xref:System.Activities.Statements.ForEach%601>-Aktivität führt die in ihrem <xref:System.Activities.Statements.ForEach%601.Body%2A> enthaltene Aktivität für jedes Element einer angegebenen <xref:System.Activities.Statements.ForEach%601.Values%2A>-Auflistung aus.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Foreach-<T- \> Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.ForEach%601>-Aktivität. Der Standardwert ist foreach<Int32 \> . Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Richtig|Die Auflistung, deren Elemente durchlaufen werden. Um den festzulegen <xref:System.Activities.Statements.ForEach%601.Values%2A> , geben Sie im Feld **Werte** des **foreach-<T \>** -Aktivitäts Designers oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|
|*TypeArgument*|Richtig|Der Typ der Elemente in der Auflistung, die <xref:System.Activities.Statements.ForEach%601.Values%2A> durch den generischen Parameter *T* angegeben werden. Standardmäßig ist *TypeArgument* auf **Int32** festgelegt. Ändern Sie den Wert des Kombinations Felds *TypeArgument* im Eigenschaften Raster, um den Typ zu ändern.|

Standardmäßig wird als Schleifen Iterator " **Item**" bezeichnet. Sie können den Namen der Iteratorvariablen im <xref:System.Activities.Statements.ForEach%601>-Aktivitätsdesigner ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Weitere Informationen

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
