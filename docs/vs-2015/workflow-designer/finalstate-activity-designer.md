---
title: FinalState-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dff9793becc3e0619d42b642609273f328c6aa73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656722"
---
# <a name="finalstate-activity-designer"></a>FinalState-Aktivitäts-Designer
Der <xref:System.Activities.Core.Presentation.FinalState>-Designer wird verwendet, um einen <xref:System.Activities.Statements.State> zu erstellen, der eine Instanz des Zustandsautomaten beendet.

## <a name="using-the-finalstate-activity-designer"></a>Verwenden des FinalState-Aktivitäts-Designers
 Der **FinalState** -Designer wird verwendet, um einen zu erstellen, der als Beendigungs <xref:System.Activities.Statements.State> Zustand in einem Zustands Automaten vorkonfiguriert ist. Eine <xref:System.Activities.Statements.State> , die mit dem <xref:System.Activities.Core.Presentation.FinalState> Aktivitäts Designer erstellt wird <xref:System.Activities.Statements.State.IsFinal%2A> , ist für die-Eigenschaft auf **true**festgelegt, es sind keine <xref:System.Activities.Statements.State.Exit%2A> Aktivitäten und keine Übergänge aus der-Eigenschaft. Wenn Sie mit dem <xref:System.Activities.Core.Presentation.FinalState> Aktivitäts Designer eine-Aktivität hinzufügen möchten <xref:System.Activities.Statements.State> , die in einem Zustands Automat als Beendigungs Zustand vorkonfiguriert ist, ziehen Sie den **FinalState** -Aktivitäts Designer aus dem Abschnitt **Zustands Automat** der **Toolbox** , und legen Sie ihn auf dem Workflow-Designer ab. Der <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts-Designer kann auf einem <xref:System.Activities.Statements.StateMachine> abgelegt werden, und es können später Übergänge hinzugefügt werden, oder es kann ein Übergang erstellt werden, wenn der <xref:System.Activities.Core.Presentation.FinalState>-Aktivitäts-Designer abgelegt wird. Weitere Informationen zum Erstellen von Übergängen finden Sie unter [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Zustandsaktivitätseigenschaften im Workflow-Designer
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die mithilfe des <xref:System.Activities.Core.Presentation.FinalState>-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden. Einige dieser Eigenschaften können im Eigenschaftenraster und einige auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.State>Aktivität im Header an. Der Standardwert ist **State**. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden. <xref:System.Activities.Statements.State.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Statements.State.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falsch|Gibt die Aktion an, die eintritt, wenn ein Übergang in diesen Zustand stattfindet. Dieser Wert kann festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und auf dem <xref:System.Activities.Statements.State.Entry%2A> Abschnitt des Zustands ablegen.|

## <a name="see-also"></a>Weitere Informationen
 [StateMachine](../workflow-designer/statemachine-activity-designer.md) - [Zustands](../workflow-designer/state-activity-designer.md) [Übergang](../workflow-designer/transition-activity-designer.md)