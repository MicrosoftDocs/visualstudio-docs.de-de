---
title: RemoveFromCollection &lt; T- &gt; Aktivitäts Designer
description: In Workflow-Designer erfahren Sie, wie Sie den RemoveFromCollection <T> -Aktivitäts Designer verwenden, um eine RemoveFromCollection-Aktivität zu erstellen und zu konfigurieren <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdaf7172c00d80e5e7615bfcadcc1fb6233c257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847361"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T>-Aktivitätsdesigner

Der **RemoveFromCollection \<T>** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.RemoveFromCollection%601> .

## <a name="the-removefromcollectiontactivity"></a>Die RemoveFromCollection- \<T> Aktivität

Die <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität entfernt ein angegebenes Element aus der angegebenen Auflistung.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Verwenden des RemoveFromCollection- \<T> Aktivitäts Designers

Greifen Sie auf den **RemoveFromCollection \<T>** -Aktivitäts Designer in der Kategorie **Sammlung** der **Toolbox** zu.
Der **RemoveFromCollection \<T>** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine- <xref:System.Activities.Statements.RemoveFromCollection%601> Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection-<Int32 erstellt \> . Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **RemoveFromCollection-<\> T** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection-<T- \> Eigenschaften

In der folgenden Tabelle <xref:System.Activities.Statements.RemoveFromCollection%601> werden die Eigenschaften und die Verwendung im Designer beschrieben:

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.Activities.Statements.RemoveFromCollection%601>-Aktivität. Der Standardwert ist der RemoveFromCollection-<Int32 \> .<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Richtig|Das Element **, das aus der \<T> Auflistung** entfernt werden soll. Dieses Element ist vom Typ *T*, der vom Typ *TypeArgument* ist. Geben Sie im Eigenschaftenraster einen Visual Basic-Ausdruck ein, um das Element anzugeben.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Richtig|Die Auflistung, aus der das Element entfernt werden soll. Diese Auflistung weist den Typ **ICollection<TypeArgument auf \> .** Geben Sie im Eigenschaften Raster einen Visual Basic Ausdruck ein, um die Sammlung anzugeben.|
|*TypeArgument*|Richtig|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente. Standardmäßig ist dieser *TypeArgument* -Typ auf **Int32** festgelegt. Ändern Sie den Wert von *TypeArgument* im Kombinations Feld des Eigenschaften Rasters, um den Typ zu ändern.|
|<xref:System.Activities.Activity%601.Result%2A>|Falsch|Ein Wert, der angibt, ob das angegebene Element aus der Auflistung entfernt wurde. Um eine Variable anzugeben, die an das Ergebnis gebunden werden soll, geben Sie im Eigenschaftenraster eine Variable ein.|

## <a name="see-also"></a>Weitere Informationen

- [Sammlung](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)