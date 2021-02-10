---
title: ExistsInCollection &lt; T- &gt; Aktivitäts Designer
description: Erfahren Sie, wie Sie den ExistsInCollection <T> -Aktivitäts Designer in Workflow-Designer verwenden können, um eine ExistsInCollection-Aktivität zu erstellen und zu konfigurieren <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 971d6bd028315ae4a8b6f3a88164c97c6f95712b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961325"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T>-Aktivitätsdesigner

Der **ExistsInCollection \<T>** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.ExistsInCollection%601> .

## <a name="the-existsincollectiont-activity"></a>Die ExistsInCollection- \<T> Aktivität

Mit der <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität wird bestimmt, ob ein angegebenes Element in einer bestimmten Auflistung vorhanden ist.

### <a name="using-the-existsincollectiont-activity-designer"></a>Verwenden des ExistsInCollection- \<T> Aktivitäts Designers

Der **ExistsInCollection \<T>** -Aktivitäts Designer befindet sich in der **Kategorie Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **ExistsInCollection \<T>** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine- <xref:System.Activities.Statements.ExistsInCollection%601> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection<Int32 erstellt \> . (Standardmäßig ist das *TypeArgument* **Int32**. Der Wert kann im Eigenschaften Raster geändert werden.)  Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **ExistsInCollection-<T \>** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-existsincollectiont-properties"></a>Die ExistsInCollection- \<T> Eigenschaften

In der folgenden Tabelle <xref:System.Activities.Statements.ExistsInCollection%601> werden die Eigenschaften und die Verwendung im Designer beschrieben:

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.ExistsInCollection%601>-Aktivität. Der Standardwert ist ExistsInCollection<Int32 \> . Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Richtig|Das Element, das in der Auflistung gesucht werden soll \<T> . Dieses Element ist vom Typ *T*, der vom Typ *TypeArgument* ist. Zum Angeben des Elements geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Richtig|Die Auflistung, in der überprüft werden soll, ob das Element vorhanden ist. Diese Auflistung weist den Typ **ICollection<TypeArgument auf \> .** Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um die Auflistung anzugeben.|
|*TypeArgument*|Richtig|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32** festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|
|<xref:System.Activities.Activity%601.Result%2A>|Falsch|Ein Wert, der angibt, ob das angegebene Element in der Auflistung vorhanden ist. Um eine Variable anzugeben, die an das Ergebnis gebunden wird, geben Sie im Eigenschaftenraster eine Visual Basic-Variable ein.|

## <a name="see-also"></a>Weitere Informationen

- [Sammlung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)