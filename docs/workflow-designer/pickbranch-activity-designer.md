---
title: Workflow-Designer-PickBranch-Aktivitäts Designer
description: Erfahren Sie, wie der PickBranch-Aktivitäts Designer einen ereignisbasierten Ausführungs Pfad innerhalb einer Pick-Aktivität bereitstellt, die von einem eingehenden Ereignis ausgelöst werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bce1cee7fad7ccff57a6911c99a9470a22b9a927
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434232"
---
# <a name="pickbranch-activity-designer"></a>PickBranch-Aktivitätsdesigner

Der <xref:System.Activities.Statements.PickBranch> stellt einen ereignisbasierten Ausführungspfad innerhalb einer <xref:System.Activities.Statements.Pick>-Aktivität bereit, der von einem eingehenden Ereignis ausgelöst werden kann.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch>-Objekte sind in der <xref:System.Activities.Statements.Pick.Branches%2A>-Auflistung einer <xref:System.Activities.Statements.Pick>-Aktivität enthalten. Jede <xref:System.Activities.Statements.PickBranch> ist in einem Branch der <xref:System.Activities.Statements.Pick>-Aktivität enthalten und wird aufgrund eines eingehenden Ereignisses ausgeführt, das als Trigger dient. Auf diese Weise stellt die Workflow-Designer die ereignisbasierte Ablauf Steuerungs Modellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner

Greifen Sie in der Kategorie **Ablauf Steuerung** der **Toolbox** auf den **PickBranch** -Designer zu.

<xref:System.Activities.Statements.PickBranch>Standardmäßig werden zwei leere Objekte mit den anzeigen Amen **Branch1** und **Branch2** als Elemente einer- <xref:System.Activities.Statements.Pick> Aktivität erstellt, wenn der **Pick** -Aktivitäts Designer anfänglich auf dem Workflow-Designer abgelegt wird. Diese entsprechenden <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können im Header des **PickBranch** -Designers oder innerhalb des **Eigenschaften** Fensters für jede Verzweigung bearbeitet werden.

Es gibt zwei Möglichkeiten, <xref:System.Activities.Statements.PickBranch> Objekte zur-Auflistung eines <xref:System.Activities.Statements.Pick> -Objekts hinzuzufügen: ziehen Sie den **PickBranch** -Designer aus der **Toolbox** , oder verwenden Sie das Kontextmenü in der **Pick** -Entwurfs Oberfläche, um Objekte zu erstellen:

- Der **PickBranch** -Designer erstellt eine, <xref:System.Activities.Statements.PickBranch> Wenn Sie aus der **Toolbox** gezogen und in einer der Verzweigungen eines **Pick** -Aktivitäts Designers auf der Workflow-Designer Oberfläche abgelegt wird. Die neuen <xref:System.Activities.Statements.PickBranch>-Objekte können im <xref:System.Activities.Statements.Pick>-Designer auf der linken oder rechten Seite jedes <xref:System.Activities.Statements.PickBranch>-Elements platziert werden, das bereits in der Auflistung enthalten ist. Wenn ein **PickBranch** -Designer mit der Maus auf den **Pick** -Designer gezogen wird, verwendet der **Pick** -Designer ein vertikales blaues grau, um anzugeben, wo der <xref:System.Activities.Statements.PickBranch> für eine bestimmte Maus Platzierung hinzugefügt wird.

- Klicken Sie mit der rechten Maustaste auf **Pick** Activity Designer (jedoch nicht im **PickBranch** -Designer), um ein Kontextmenü abzurufen, und wählen Sie **Branch erstellen** aus, um <xref:System.Activities.Statements.PickBranch> einen neuen hinzuzufügen Beachten Sie, dass das neue- <xref:System.Activities.Statements.PickBranch> Objekt rechts neben den vorhandenen- <xref:System.Activities.Statements.PickBranch> Objekten im **Pick** -Designer hinzugefügt wird.

Der **PickBranch** -Designer kann erweitert werden, um die **Triggerfelder** und **Aktions** Felder anzuzeigen oder durch Klicken auf die doppelten Caretzeichen auf der rechten Seite Ihrer Header reduziert zu werden. Bearbeiten Sie <xref:System.Activities.Statements.PickBranch.Trigger%2A> und <xref:System.Activities.Statements.PickBranch.Action%2A> von jedem, <xref:System.Activities.Statements.PickBranch> indem Sie Aktivitäten in den **Triggern** und den **Aktions** Feldern ihrer Designer ablegen.

Die <xref:System.Activities.Statements.PickBranch> Objekte in der Auflistung <xref:System.Activities.Statements.Pick.Branches%2A> eines- <xref:System.Activities.Statements.Pick> Objekts können neu angeordnet werden, indem Sie per Drag & amp; Drop an einen neuen Speicherort im **Pick** -Designer abgelegt werden. Der **Pick** -Designer gibt mithilfe eines vertikalen blau grauen Bands an, wo der <xref:System.Activities.Statements.PickBranch> für eine bestimmte Maus Platzierung hinzugefügt wird.

Es gibt zwei Möglichkeiten, ein <xref:System.Activities.Statements.PickBranch>-Objekt zu löschen:

- Wählen Sie den **PickBranch** -Designer aus, und löschen Sie ihn.
- Wählen Sie den **PickBranch** -Designer aus, klicken Sie mit der rechten Maustaste auf das Kontextmenü, und wählen Sie **Löschen**.

Achten Sie darauf, den **PickBranch** -Designer auszuwählen. Wenn Sie eine der Aktivitäten in den **Triggern** oder **Aktions** Feldern versehentlich auswählen, wird eine dieser Aktivitäten und nicht das- <xref:System.Activities.Statements.PickBranch> Objekt gelöscht.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>PickBranch-Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten <xref:System.Activities.Statements.PickBranch> Eigenschaften angezeigt, und es wird beschrieben, wie Sie in der Workflow-Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|FALSE|Der Anzeige Name, der im Header des **PickBranch** -Designers angezeigt wird. Der Standardwert lautet Branch.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Wahr|Jedes <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Trigger%2A>-Aktion, die <xref:System.Activities.Statements.PickBranch.Action%2A> aufrufen kann.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|FALSE|Jede <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Action%2A>, die ausgeführt wird, sobald sie ausgelöst wird.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [Auswahlaktivität](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Verwenden der Pick-Aktivität](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)