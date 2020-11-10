---
title: Workflow-Designer-Rethrow-Aktivitäts Designer
description: Erfahren Sie mehr über die Rethrow-Aktivität und die Verwendung des Rethrow-Aktivitäts Designers, um eine Rethrow-Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9195fc95ac905213b048aa16882ea6584adacd33
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434115"
---
# <a name="rethrow-activity-designer"></a>Rethrow-Aktivitätsdesigner

Der **Rethrow** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Rethrow> .

## <a name="the-rethrow-activity"></a>Die Rethrow-Aktivität

Die <xref:System.Activities.Statements.Rethrow>-Aktivität löst eine zuvor ausgelöste Ausnahme aus. Diese Aktivität kann nur in einem <xref:System.Activities.Statements.Catch>-Handler in der <xref:System.Activities.Statements.TryCatch> -Aktivität verwendet werden.

### <a name="use-the-rethrow-activity-designer"></a>Verwenden des Rethrow-Aktivitäts Designers

Greifen Sie in der Kategorie **Fehlerbehandlung** der **Toolbox** auf den **Rethrow** -Aktivitäts Designer zu. Der **Rethrow** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Beim Löschen des Aktivitäts Designers wird eine- <xref:System.Activities.Statements.Rethrow> Aktivität mit dem **Display Name** -Standardwert Throw erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **Rethrow** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-rethrow-properties"></a>Die Rethrow-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Rethrow> Eigenschaften angezeigt, und es wird beschrieben, wie Sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|FALSE|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Rethrow>-Aktivität an. Der Standardwert lautet Rethrow.|

## <a name="see-also"></a>Siehe auch

- [Sammlung](../workflow-designer/collection-activity-designers.md)
- [Schale](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
