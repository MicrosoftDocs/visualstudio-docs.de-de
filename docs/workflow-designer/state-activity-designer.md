---
title: Workflow-Designer-Status-Aktivitäts Designer
description: Erfahren Sie mehr über die StateMachine-Aktivität und wie Sie den Zustands Aktivitäts Designer verwenden können, um einem Workflow einen Zustand hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: abf4e81ecd258668c93b674410f029e6be0f5bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873514"
---
# <a name="state-activity-designer"></a>Zustandsaktivitäts-Designer

<xref:System.Activities.Statements.State> stellt einen Zustand dar, in dem sich ein Zustandsautomat befinden kann.

## <a name="using-the-state-activity-designer"></a>Verwenden des Zustandsaktivitäts-Designers

Wenn Sie einen einem Workflow hinzufügen möchten <xref:System.Activities.Statements.State> , ziehen Sie den **Zustands** Aktivitäts Designer aus dem Abschnitt **Zustands Automat** der **Toolbox** , und legen Sie ihn auf <xref:System.Activities.Statements.StateMachine> der Workflow-Designer-Oberfläche auf einer-Aktivität ab. Eine <xref:System.Activities.Statements.State>-Aktivität kann auf einem <xref:System.Activities.Statements.StateMachine> abgelegt werden, und es können später Übergänge hinzugefügt werden, oder es kann ein Übergang erstellt werden, wenn die <xref:System.Activities.Statements.State>-Aktivität abgelegt wird. Um eine <xref:System.Activities.Statements.State> -Aktivität hinzuzufügen und einen Übergang in einem Schritt zu erstellen, ziehen Sie eine **State** -Aktivität aus dem Abschnitt **Zustands Automat** der **Toolbox** , und bewegen Sie den Mauszeiger über einen anderen Zustand im Workflow-Designer. Sobald sich der gezogene <xref:System.Activities.Statements.State> über einem anderen <xref:System.Activities.Statements.State> befindet, werden vier Dreiecke um den anderen <xref:System.Activities.Statements.State> herum eingeblendet. Wenn <xref:System.Activities.Statements.State> auf einem der vier Dreiecke abgelegt wird, wird er dem Zustandsautomaten hinzugefügt, und es wird ein Übergang vom Quell-<xref:System.Activities.Statements.State> zum abgelegten Ziel-<xref:System.Activities.Statements.State> erstellt. Weitere Informationen finden Sie unter [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Zustandsaktivitätseigenschaften im Workflow-Designer

In der folgenden Tabelle sind die <xref:System.Activities.Statements.State>-Eigenschaften aufgeführt, die mithilfe des Workflow-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Einige dieser Eigenschaften können im Eigenschaftenraster und einige auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.State>Aktivität im Header an. Der Standardwert ist **State**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Statements.State.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Statements.State.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falsch|Gibt die Aktion an, die eintritt, wenn ein Übergang in diesen Zustand stattfindet. Wenn die <xref:System.Activities.Statements.State> Aktivität erweitert wird, kann dieser Wert festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und auf dem **Eintrags** Abschnitt des Zustands ablegen.|
|<xref:System.Activities.Statements.State.Exit%2A>|Falsch|Gibt die Aktion an, die eintritt, wenn ein Übergang aus diesem Zustand stattfindet. Wenn die <xref:System.Activities.Statements.State> Aktivität erweitert wird, kann dieser Wert festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und auf  dem Beendigungs Bereich des Zustands ablegen.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Falsch|Listet die möglichen Übergänge auf, die von <xref:System.Activities.Statements.State> ausgehen. Jedes Element in der Liste weist einen Link zum verknüpften <xref:System.Activities.Statements.Transition> und zum Ziel-<xref:System.Activities.Statements.State> auf. Indem Sie auf den Link klicken, wechselt der Designer zur erweiterten Ansicht von <xref:System.Activities.Statements.Transition> oder <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Weitere Informationen

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Umstellung](../workflow-designer/transition-activity-designer.md)
