---
title: Addchancollection &lt; T- &gt; Aktivitäts Designer
description: Erfahren Sie, wie der AddTo Collection <T> -Aktivitäts Designer verwendet wird, um eine AddTo Collection- <T> Aktivität in Workflow-Designer zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18811199cce88c5d57332ced99763b4f6233da8d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920195"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T>-Aktivitätsdesigner

Der **AddTo Collection \<T>** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.AddToCollection%601> .

## <a name="the-addtocollectiont-activity"></a>Die AddTo Collection- \<T> Aktivität

Die <xref:System.Activities.Statements.AddToCollection%601>-Aktivität fügt einer Auflistung ein Element hinzu.

### <a name="using-the-addtocollectiont-activity-designer"></a>Verwenden des AddTo Collection- \<T> Aktivitäts Designers

Der **addescollection \<T>** -Aktivitäts Designer befindet sich in der Kategorie **Sammlung** der **Toolbox**, auf die Sie zugreifen können, indem Sie im Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **addescollection \<T>** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Wenn Sie den **AddTo \<T> Collection** -Aktivitäts Designer löschen, wird eine- <xref:System.Activities.Statements.AddToCollection%601> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> addoncollection<Int32 erstellt \> . (Standardmäßig ist das *TypeArgument* **Int32**. TypeArgument kann im Eigenschaften Raster geändert werden.) Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **addchancollection-<\> T** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-addtocollectiont-properties"></a>Die AddTo Collection- \<T> Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.AddToCollection%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.AddToCollection%601>-Aktivität. Der Standardwert ist AddTo Collection<Int32 \> . Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Richtig|Das Element, das der Auflistung hinzugefügt werden soll \<T> . Dieses Element ist vom Typ *T*, der vom Typ *TypeArgument* ist. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Richtig|Die Auflistung, zu der das Element hinzugefügt werden soll. Diese Auflistung weist den Typ **ICollection<TypeArgument \>** auf. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|Richtig|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32** festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|

## <a name="see-also"></a>Weitere Informationen

- [Sammlung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T> Aktivitätsdesigner](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
