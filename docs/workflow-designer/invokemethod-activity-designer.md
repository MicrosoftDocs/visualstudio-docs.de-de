---
title: Workflow-Designer-InvokeMethod-Aktivitäts Designer
description: Erfahren Sie mehr über die InvokeMethod-Aktivität und wie Sie den InvokeMethod-Aktivitäts Designer zum Erstellen und Konfigurieren einer InvokeMethod-Aktivität verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55162def18d2295e0767a3999ffde75d71e1233d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437735"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod-Aktivitätsdesigner

Der **InvokeMethod** -Designer wird verwendet, um eine Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.InvokeMethod> .

## <a name="the-invokemethod-activity"></a>Die InvokeMethod-Aktivität

Die <xref:System.Activities.Statements.InvokeMethod>-Aktivität ruft eine öffentliche Methode eines angegebenen Objekts oder Typs auf.

### <a name="use-the-invokemethod-activity-designer"></a>Verwenden des InvokeMethod-Aktivitäts Designers

Greifen Sie in der Kategorie **Primitives** der **Toolbox** auf den **InvokeMethod** -Aktivitäts Designer zu. Der **InvokeMethod** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b <xref:System.Activities.Statements.Sequence> . in einer. Beim Löschen des Aktivitäts Designers wird eine- <xref:System.Activities.Statements.InvokeMethod> Aktivität mit dem-Standardwert " <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod" erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **InvokeMethod** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-invokemethod-properties"></a>InvokeMethod-Eigenschaften

In der folgenden Tabelle sind die Eigenschaften aufgeführt, <xref:System.Activities.Statements.InvokeMethod> und es wird beschrieben, wie Sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|FALSE|Der Anzeigename der <xref:System.Activities.Statements.InvokeMethod>-Aktivität. Der Standardwert lautet InvokeMethod.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen zu verwenden.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Wahr|Der Name der Methode, die bei Ausführung der Aktivität aufgerufen werden soll. Die aufgerufene Methode muss als **öffentlich** deklariert werden. Diese Eigenschaft kann auf der Designer Oberfläche bearbeitet werden und ist obligatorisch.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|FALSE|Die Parameterauflistung der aufgerufenen Methode. Die Parameter müssen der Auflistung in derselben Reihenfolge wie in der Methodensignatur hinzugefügt werden. Um das Dialogfeld " **Parameter** " anzuzeigen, in dem Sie diese Eigenschaft festlegen können, klicken Sie im Eigenschaften Raster **auf die Schalt** Fläche mit den Auslassungs Punkten. Klicken Sie auf die Schaltfläche **Argument erstellen** , um die Parameter hinzuzufügen.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|FALSE|Der Rückgabewert des Methodenaufrufs.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Wahr|Gibt an, ob die Methode asynchron aufgerufen wird. Der Standardwert ist **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|FALSE|Das Objekt, das die aufzurufende Methode enthält. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.<br /><br /> Es muss entweder das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Objekt oder der <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>-Typ festgelegt werden.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|FALSE|Der <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Typ. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Diese Eigenschaft muss nur festgelegt werden, wenn die aufgerufene Methode statisch ist.|

Verwenden Sie zum Übergeben von Parametern als c#- **out** -Parameter (z. b. `Method1(out myParam))` **OutArgument** anstelle von **InOutArgument** ).

Methoden mit Argumenten, die als **TargetObject** oder **Result** bezeichnet werden, können nicht mithilfe der-Aktivität aufgerufen werden <xref:System.Activities.Statements.InvokeMethod> . Der Grund dafür ist, dass die <xref:System.Activities.Statements.InvokeMethod>-Aktivität <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> und <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A> registriert.

Der Algorithmus zum Registrieren der Parameter in <xref:System.Activities.Activity.CacheMetadata%2A> wird in der folgenden Liste dargestellt:

1. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>-Argument.

2. Registrieren Sie das <xref:System.Activities.Statements.InvokeMethod.Result%2A>-Argument.

3. Durchlaufen Sie die <xref:System.Activities.Statements.InvokeMethod.Parameters%2A>-Auflistung, und registrieren Sie jedes Argument.

Die resultierende Ausnahme hat den Typ <xref:System.Activities.InvalidWorkflowException> mit der folgenden Meldung: 'InvokeMethod': Eine Variable, RuntimeArgument oder ein DelegateArgument ist bereits mit dem Namen 'TargetObject' vorhanden. Namen müssen innerhalb einer Umgebung eindeutig sein.

Diese Einschränkung gilt nicht für <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> und <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . Dabei handelt es sich nicht um Workflow Argumente, die daher nicht in der-Auflistung <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> der- <xref:System.Activities.Statements.InvokeMethod> Aktivität in der-Methode registriert sind <xref:System.Activities.Activity.CacheMetadata%2A> .

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Verzögern](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
