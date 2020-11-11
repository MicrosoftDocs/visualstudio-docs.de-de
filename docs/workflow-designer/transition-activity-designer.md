---
title: Workflow-Designer-Übergangs Aktivitäts Designer
description: Erfahren Sie, wie Sie den Übergangs Aktivitäts Designer verwenden können, um einen Übergang zwischen zwei Zuständen zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: cedc9c7b6f402ad3f5f2c40e21c29e2a0d1ad2e6
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433725"
---
# <a name="transition-activity-designer"></a>Übergangsaktivitäts-Designer

Ein <xref:System.Activities.Statements.Transition> stellt den Übergang zwischen zwei Zuständen dar.

## <a name="using-the-transition-activity-designer"></a>Verwenden des Transition-Aktivitäts-Designers

Der Transition-Aktivitäts-Designer ermöglicht es Ihnen, einen Übergang zwischen zwei Zuständen zu konfigurieren.

### <a name="transition-properties-in-the-workflow-designer"></a>Transition-Eigenschaften im Workflow-Designer

In der folgenden Tabelle sind die <xref:System.Activities.Statements.Transition>-Eigenschaften aufgeführt, die mithilfe des Workflow-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|FALSE|Gibt den optionalen Anzeigenamen des <xref:System.Activities.Statements.Transition>-Aktivitätsdesigners an. Der Standardwert ist **T1**. Der Wert kann im Eigenschaftenraster im Header des erweiterten Übergangs-Designers und im Header des Aktionsabschnitts innerhalb des erweiterten Übergangs-Designers bearbeitet werden. <xref:System.Activities.Activity.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|FALSE|Gibt ggf. einen Ausdruck an, der zu **true** ausgewertet werden muss, bevor die Steuerung an den Zielzustand übermittelt wird. Diese Bedingung kann im Eigenschaftenraster und im erweiterten Übergangs-Designer bearbeitet werden. Mehrere Bedingungen in einem gemeinsamen Übergang werden in der Reihenfolge ausgewertet, in der sie im Übergangs-Designer angezeigt werden. **Hinweis:**  Beachten Sie, dass der <xref:System.Activities.Statements.Transition.Condition%2A> Übergang nicht stattfindet und alle Trigger für alle Übergänge aus dem Zustand neu geplant werden, wenn der eines Übergangs zu " **false** " ausgewertet wird (oder alle Bedingungen für den Übergang eines freigegebenen Triggers zu " **false** " ausgewertet werden). In diesem Lernprogramm kann diese Situation aufgrund der Konfigurationsmethode für die Bedingungen (es gibt spezielle Aktionen für richtige oder falsche Schätzungen) nicht auftreten.|
|**Quelle**|Wahr|Gibt den Zustand an, von dem dieser Übergang ausgeht. Indem Sie auf den Namen des Quellzustands klicken, wechselt die Designeransicht in eine erweiterte Ansicht dieses Zustands. Dieser Wert wird festgelegt, wenn der Übergang erstellt wird, und kann nicht geändert werden.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|FALSE|Gibt die Aktivität an, deren Abschluss den Übergang initiiert. Um diese Aktivität festzulegen, ziehen Sie eine Aktivität aus der **Toolbox** , und legen Sie Sie auf dem **triggerabschnitt** des Übergangs ab.|
|<xref:System.Activities.Statements.Transition.Action%2A>|FALSE|Gibt die Aktivität an, die ausgeführt wird, wenn die auslöseraktivität abgeschlossen ist, und <xref:System.Activities.Statements.Transition.Condition%2A> , falls vorhanden, als **true** ausgewertet wird. Diese Aktivität wird ausgeführt, wenn der Übergang in den Zielzustand erfolgt, nachdem die <xref:System.Activities.Statements.State.Exit%2A>-Aktivität für den Quellzustand, falls vorhanden, ausgeführt wurde. Wenn der Übergangs-Designer erweitert wird, kann dieser Wert festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und auf dem Abschnitt **Aktion** des Übergangs ablegen. Ein Übergang kann mehrere Aktionen aufweisen. Die einzelnen Aktionen können erweitert, verkürzt und geordnet werden, indem Sie auf den Pfeil nach oben oder nach unten klicken, der für die Aktion angezeigt wird, wenn mehrere Aktionen in einem Übergang vorhanden sind.|
|**Ziel**|Wahr|Gibt den Zustand an, in den der Zustandsautomat übergeht, nachdem der Übergang abgeschlossen ist. Dies entspricht der <xref:System.Activities.Statements.Transition.To%2A>-Eigenschaft des Übergangs im Objektmodell. Indem Sie auf den Namen des Zielzustands klicken, wechselt die Designeransicht in eine erweiterte Ansicht dieses Zustands. Dieser Wert wird festgelegt, wenn der Übergang erstellt wird, und kann geändert werden, indem Sie im Designer den Pfeil ziehen, der den Übergang mit dem Zielzustand verbindet.|

### <a name="creating-transitions"></a>Erstellen von Übergängen

Übergänge werden erstellt, indem eine Linie von einem Zustand zu einem anderen gezogen wird, oder indem ein Zustand auf den Dreiecken abgelegt wird, die angezeigt werden, wenn ein Zustand über einen anderen Zustand gezogen wird. Um einen Übergang durch Ziehen zu erstellen, zeigen Sie mit der Maus auf den Rand des Quellzustands und ziehen eine Linie vom Quell- zum Zielzustand. Um einen Übergang durch Ablegen zu erstellen, ziehen Sie den Zielzustand auf den Quellzustand und legen ihn auf einem der vier Dreiecke ab, die um den Quellzustand herum angezeigt werden. Der Ziel Status kann entweder ein neuer, aus der **Toolbox** gezogener Zustand oder ein vorhandener Zustand, der aus dem Workflow-Designer gezogen wurde, sein.

> [!NOTE]
> Ein einzelner Zustand eines Zustandsautomaten kann bis zu 76 Übergänge aufweisen, die mithilfe des Workflow-Designers erstellt wurden. Die Anzahl der Zustandsübergänge für Workflows, die außerhalb des Designers erstellt werden, wird nur durch die verfügbaren Systemressourcen beschränkt.

Übergänge mit gemeinsamem Trigger sind Übergänge, die dasselbe Triggerereignis verwenden. Ein gemeinsamer Trigger ermöglicht den bedingten Übergang zu einem Zielzustand auf Grundlage der Auswertung von Ausdrücken, die für mehrere Übergänge konfiguriert wurden, die über ein gemeinsames Triggerereignis verfügen. Um einem Übergang zusätzliche Aktionen hinzuzufügen und einen gemeinsamen Übergang zu erstellen, klicken Sie auf den Kreis, der den Anfang des gewünschten Übergangs angibt, und ziehen Sie ihn auf den gewünschten Zustand. Der neue Übergang verwendet denselben Trigger wie der Anfangsübergang, besitzt jedoch eine eindeutige Bedingung und Aktion. Freigegebene Übergänge können auch aus dem Übergangs-Designer erstellt werden, indem Sie im unteren Bereich des Übergangs-Designers auf frei **gegebenen triggerübergang hinzufügen** klicken und dann den gewünschten Ziel Status aus der Dropdown Liste **Verfügbare Zustände zum Verbinden** auswählen.

## <a name="see-also"></a>Siehe auch

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
