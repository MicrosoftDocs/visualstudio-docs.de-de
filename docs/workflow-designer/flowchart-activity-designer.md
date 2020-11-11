---
title: Workflow-Designer-Flussdiagramm-Aktivitäts Designer
description: Erfahren Sie, wie Sie die Flowchart-Aktivität verwenden können, um Workflows zu erstellen, die komplexe Fluss Steuerungen definieren und verwalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08c7957d79d51cab93e45adf8f74899ecc59b76d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438008"
---
# <a name="flowchart-activity-designer"></a>Flussdiagramm-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Flowchart>-Aktivität wird verwendet, um Workflows zu erstellen, die komplexe Flusssteuerungen definieren und verwalten. Ein <xref:System.Activities.Statements.Flowchart> kann entweder im Code oder mithilfe von Workflow-Designer erstellt werden. In diesem Thema wird die Workflow-Designer-Darstellung dokumentiert. Der Workflow-Designer Workflow-Aktivitäts Designer ermöglicht es Entwicklern, Workflows auf natürliche Weise zu verfassen.

## <a name="the-flowchart-activity"></a>Die Flowchart-Aktivität

Die <xref:System.Activities.Statements.Flowchart>-Aktivität gibt einen eindeutigen <xref:System.Activities.Statements.Flowchart.StartNode%2A> an, der ausgeführt wird, wenn der Workflow startet und ein Netzwerk miteinander verknüpfter <xref:System.Activities.Statements.Flowchart.Nodes%2A> verwendet, um beliebige Schleifen zu erstellen oder zu einem bestimmten Zeitpunkt den Ausführungsfluss anderswohin im Workflow umzuleiten.

### <a name="using-the-flowchart-activity-designer"></a>Verwenden des Flussdiagramm-Aktivitätsdesigners

Der **Flussdiagramm** -Aktivitäts Designer befindet sich in der Kategorie **Flussdiagramm** der **Toolbox** , auf die Sie zugreifen können, indem Sie im Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **Flussdiagramm** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, entweder als Stamm Aktivität oder als untergeordnetes Element einer anderen Ablauf Steuerungs Aktivität. Wenn der **Flussdiagramm** -Aktivitäts Designer auf einer leeren Workflow-Designer Oberfläche abgelegt wird, erstellt er eine- <xref:System.Activities.Statements.Flowchart> Aktivität, die sich standardmäßig in einer erweiterten Ansicht präsentiert, in der der Startknoten, der die Ausführung initiiert, als grüne Kugel dargestellt wird. Wenn der **Flussdiagramm** -Aktivitäts Designer in einer anderen Ablauf Steuerungs Aktivität abgelegt wird, stellt er sich in einer minimierten Ansicht vor, die durch Doppelklicken auf den **Flussdiagramm** -Aktivitäts Designer erweitert werden kann. Alle Aktivitäten in der **Toolbox** können direkt auf den **Flussdiagramm** -Aktivitäts Designer, einschließlich anderer Ablauf Steuerungsaktivitäten, gezogen werden.

Nachdem verschiedene Aktivitäts Designer auf die Workflow-Designer Canvas gezogen wurden, <xref:System.Activities.Activity> können die Objekte, die Sie darstellen, miteinander verknüpft werden, um die Ausführungsreihenfolge anzugeben. Sie erstellen einen Link zwischen einer Quellaktivität und einer Zielaktivität, indem Sie die Maus über den Designer der Quellaktivität bewegen, an dessen beiden Seiten dann quadratische Ziehpunkte angezeigt werden. Klicken Sie auf einen der quadratischen Ziehpunkte, und ziehen Sie ihn bei gedrückter Maustaste auf einen der Ziehpunkte, die um die Zielaktivität angezeigt werden, sobald Sie die Maus über diese Aktivität bewegen. Lassen Sie die Maustaste los, und zwischen beiden Aktivitäten wird ein Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.

### <a name="flowchart-activity-properties"></a>Flussdiagrammaktivitätseigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Flowchart>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|FALSE|Gibt den Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert lautet Flussdiagramm. Der Wert kann im **Eigenschaften** Fenster oder direkt im Header des Aktivitäts Designers bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|FALSE|Die Auflistung der innerhalb dieses <xref:System.Activities.Statements.Flowchart> gültigen Variablen, mittels derer der Zustand gemeinsam mit seinen untergeordneten Aktivitäten verwendet wird.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|FALSE|Der <xref:System.Activities.Statements.FlowNode>, der ausgeführt wird, wenn <xref:System.Activities.Statements.Flowchart> startet.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|FALSE|Enthält die Auflistung der <xref:System.Activities.Statements.FlowNode>-Objekte im <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Siehe auch

- [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
