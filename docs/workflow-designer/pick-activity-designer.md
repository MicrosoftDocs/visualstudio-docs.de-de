---
title: Workflow-Designer-Pick-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01ebd0dbfa8274b370a7e84b1033465e2be0b4a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876033"
---
# <a name="pick-activity-designer"></a>Pick-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Pick>-Aktivität stellt eine ereignisbasierte Ablaufsteuerung bereit. Die Aktivität führt einen von mehreren Branches als Reaktion auf die Auslösung eines Ereignisses aus.

## <a name="the-pick-activity"></a>Die Pick-Aktivität

Eine <xref:System.Activities.Statements.Pick>-Aktivität enthält eine Auflistung von <xref:System.Activities.Statements.PickBranch>-Objekten, von denen die <xref:System.Activities.Statements.Pick>-Aktivität eines ausführen kann, wenn sie ein Ereignis empfängt, das als Trigger dient. Auf diese Weise Workflow-Designer die ereignisbasierte Ablauf Steuerungs Modellierung bereitstellt. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>. Zu Beginn der Ausführung einer <xref:System.Activities.Statements.Pick> Aktivität werden alle triggeraktivitäten der <xref:System.Activities.Statements.PickBranch> Elemente geplant. Wenn die erste Aktivität abgeschlossen wird, wird die entsprechende Aktionsaktivität geplant, und alle anderen Triggeraktivitäten werden abgebrochen.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner

Greifen Sie in der Kategorie **Ablauf Steuerung** der **Toolbox**auf den **Pick** -Aktivitäts Designer zu. Der **Pick** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, z. b. innerhalb eines **Sequence** -Aktivitäts Designers. Nach dem Ablegen in Workflow-Designer wird eine- <xref:System.Activities.Statements.Pick> Aktivität erstellt, die standardmäßig zwei leere <xref:System.Activities.Statements.PickBranch> Aktivitäten als Elemente mit den anzeigen Amen Branch1 und Branch2 enthält. Diese entsprechenden <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können im Header des **PickBranch** -Aktivitäts Designers oder innerhalb des **Eigenschaften** Fensters für jede Verzweigung bearbeitet werden.

Es gibt zwei Möglichkeiten, <xref:System.Activities.Statements.PickBranch> Aktivitäten zur-Auflistung eines <xref:System.Activities.Statements.Pick> -Objekts hinzuzufügen: ziehen Sie den **PickBranch** -Designer aus der **Toolbox** , oder verwenden Sie das Kontextmenü in der **Pick** -Entwurfs Oberfläche, um Aktivitäten hinzuzufügen. Weitere Informationen finden Sie im Thema [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Beachten Sie, dass das einzige Element, das in einem **Pick** -Aktivitäts Designer platziert werden kann, ein **PickBranch** -Aktivitäts Designer ist.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Eigenschaften für Pick-Aktivitäten im Workflow-Designer

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Pick>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Pick>Aktivität im Header an. Der Standardwert lautet Pick. Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Weitere Informationen

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [Auswahlaktivität](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Verwenden der Pick-Aktivität](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)