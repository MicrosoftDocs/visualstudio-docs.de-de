---
title: Workflow-Designer-DoWhile-Aktivitäts Designer
description: Erfahren Sie, wie die DoWhile-Aktivität die im Text enthaltene Aktivität mindestens einmal ausführt, bis eine angegebene Bedingung zu "false" ausgewertet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385fe376f56738d76e066dc172e7b6b516f9a08
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438060"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner

Die- <xref:System.Activities.Statements.DoWhile> Aktivität führt die in der enthaltenen Aktivität mindestens <xref:System.Activities.Statements.DoWhile.Body%2A> einmal aus, bis eine angegebene Bedingung als **false** ausgewertet wird. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten <xref:System.Activities.Statements.DoWhile> Aktivitäts Eigenschaften angezeigt, und es wird beschrieben, wie Sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|FALSE|Die Aktivität, die ausgeführt werden soll, während die Bedingung **true** ist. Um die-Aktivität hinzuzufügen, legen Sie <xref:System.Activities.Statements.DoWhile.Body%2A> eine Aktivität aus der Toolbox in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **DoWhile** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Wahr|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Um die festzulegen <xref:System.Activities.Statements.DoWhile.Condition%2A> , geben Sie im Feld **Bedingung** im **DoWhile** -Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|

## <a name="see-also"></a>Siehe auch

- [While](../workflow-designer/while-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)