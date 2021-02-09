---
title: Workflow-Designer-FlowSwitch &lt; T- &gt; Aktivitäts Designer
description: Erfahren Sie, wie die FlowSwitch- <T> Aktivität ein bedingter Knoten ist, der Verzweigungen für die Ablauf Steuerung basierend auf dem Übereinstimmungs Kriterium bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f61dd3f14ba527e9f5be0e009825902e683fb1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876562"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T>-Aktivitätsdesigner

Die <xref:System.Activities.Statements.FlowSwitch%601>-Aktivität ist ein bedingter Knoten, der einen Branch auf der Grundlage von Übereinstimmungskriterien für den Steuerungsverlauf bereitstellt, wenn mehr als zwei alternative Branches erforderlich sind. Wenn der Steuerungsverlauf nur zwei Pfade erfordert, verwenden Sie stattdessen die <xref:System.Activities.Statements.FlowDecision>-Aktivität.

## <a name="the-flowswitcht-activity"></a>Die FlowSwitch- \<T> Aktivität

Die- <xref:System.Activities.Statements.FlowSwitch%601> Aktivität enthält eine <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , die einen Wert vom Typ *T* zurückgibt (angegeben durch den generischen-Parameter), wenn Sie ausgewertet wird. Die Aktivität enthält auch einen Satz von <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fällen, der eine eindeutige Zuordnung von möglichen Ergebnissen dieser Auswertung zu einem Satz von <xref:System.Activities.Statements.FlowNode>-Objekten angibt. Das <xref:System.Activities.Statements.FlowNode> ausgeführte ist das, dessen Objekt vom Typ *T* mit dem Wert des ausgewerteten übereinstimmt <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Ein <xref:System.Activities.Statements.FlowSwitch%601.Default%2A>-Fall kann (optional) für den Fall bereitgestellt werden, in dem keine Übereinstimmung gefunden wird.

### <a name="using-the-flowswitcht-activity-designer"></a>Verwenden des FlowSwitch- \<T> Aktivitäts Designers

Der **FlowSwitch \<T>** -Aktivitäts Designer befindet sich in der Kategorie **Flussdiagramm** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **FlowSwitch \<T>** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche innerhalb eines **Flowchart** -Aktivitäts Designers abgelegt werden. Verwenden Sie das Fenster **Typen auswählen** , das angezeigt wird, um den Typ (der durch den generischen Parameter des Codes verknüpft ist) anzugeben, der <xref:System.Activities.Statements.FlowSwitch%601> aus der Auswertung von abgerufen wurde <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Diese Prozedur erstellt eine- <xref:System.Activities.Statements.FlowSwitch%601> Aktivität mit der Bezeichnung **Switch** innerhalb der- <xref:System.Activities.Statements.Flowchart> Aktivität. Der-Wert <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> kann im Feld **Ausdruck** des Fensters **Eigenschaften** eingegeben werden, indem Sie auf die Stelle klicken, an der der Hinweis Text "VB-Ausdruck eingeben" lautet.

Bewegen Sie den Mauszeiger über den **FlowSwitch \<T>** -Aktivitäts Designer, damit die quadratischen Handles, die für die Verknüpfung verwendet werden, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> um Ihre Ränder herum angezeigt werden. Nachdem der **FlowSwitch-<T \>** -Aktivitäts Designer und andere Aktivitäts Designer auf das **Flussdiagramm** gezogen wurden, können die Objekte, die <xref:System.Activities.Activity> Sie darstellen, miteinander verknüpft werden, um die Ausführungsreihenfolge anzugeben. Um eine der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> zugeordneten zu erstellen <xref:System.Activities.Statements.FlowSwitch%601> , klicken Sie auf einen der quadratischen Case-Handles auf dem Umkreis des **FlowSwitch-<\> T** , und ziehen Sie ihn (durchhalten der Maustaste) auf einen der Handles, die auf ähnliche Weise um die Ziel Aktivität angezeigt werden, wenn der Mauszeiger über den Designer bewegt wird. Lassen Sie die Maustaste los, und es wird ein Pfeil vom **FlowSwitch<T \>** zum Ziel-Designer angezeigt, der diesen Fall darstellt. Der Standardwert für diesen Fall wird auf dem Pfeil angezeigt und kann im Feld **Fall** des Fensters **Eigenschaften** bearbeitet werden.

### <a name="the-flowswitcht-properties"></a>FlowSwitch- \<T> Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowSwitch%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Richtig|Gibt den Ausdruck an, der ausgewertet wird, um zu bestimmen, zu welchem der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fälle im Ausführungspfad gewechselt werden soll.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Falsch|Gibt eine eindeutige Zuordnung von möglichen Ergebnissen an, die durch die Auswertung von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> für einen Satz von <xref:System.Activities.Statements.FlowNode>-Objekten ermittelt wurden.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Richtig|Gibt die Zuordnung an, wenn das Auswertungsergebnis von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> mit keinem der Werte übereinstimmt, die im <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Objekt enthalten sind.|

## <a name="see-also"></a>Weitere Informationen

- [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)
- [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
