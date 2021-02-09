---
title: Workflow-Designer Assign-Aktivitäts Designer
description: Erfahren Sie, wie Sie den Assign-Aktivitäts Designer verwenden können, um eine Assign-Aktivität zu erstellen und zu konfigurieren, und wie die Assign-Aktivität einer Variablen oder einem Argument einen Wert zuweist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe6f649543cee66a1050e5724a9317b7b8806534
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888640"
---
# <a name="assign-activity-designer"></a>Assign-Aktivitätsdesigner

Der **assign** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Assign> .

## <a name="the-assign-activity"></a>Die Assign-Aktivität

Die <xref:System.Activities.Statements.Assign>-Aktivität weist einer Variablen oder einem Argument einen Wert zu.

### <a name="using-the-assign-activity-designer"></a>Verwenden des Assign-Aktivitätsdesigners

Der **assign** -Aktivitäts Designer befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG + ALT + X drücken).

Der **assign** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, auf der Aktivitäten platziert werden, z. b <xref:System.Activities.Statements.Sequence> . innerhalb eines. Beim Löschen des **assign** -Aktivitäts Designers wird eine <xref:System.Activities.Statements.Assign> Aktivität mit dem **Display Name** -Standardwert Assign erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **assign** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-assign-properties"></a>Die Assign-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Assign>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige von Ihnen können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.Assign>-Aktivität. Der Standardwert lautet Assign. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Assign.To%2A>|Richtig|Die Variable oder das Argument, dem der <xref:System.Activities.Statements.Assign.Value%2A> zugewiesen wird. Der Wert muss ein gültiger Visual Basic Bezeichner sein. Um die-Eigenschaft festzulegen, geben Sie im **assign** -Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic-Ausdruck in das Feld **an** ein.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Richtig|Der der Variablen zugewiesene Wert. Um die festzulegen <xref:System.Activities.Statements.Assign.Value%2A> , geben Sie im Feld **Wert** des **assign** -Aktivitäts Designers oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|

## <a name="see-also"></a>Weitere Informationen

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Verzögern](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)