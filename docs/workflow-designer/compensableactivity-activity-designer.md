---
title: CompensableActivity-Aktivitätsdesigner
description: Erfahren Sie, wie Sie den CompensableActivity-Aktivitäts Designer in Workflow-Designer verwenden können, um eine CompensableActivity-Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9612e1b8e808437122df88ad0bbef3a4cce74c0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955111"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity-Aktivitätsdesigner

Der **CompensableActivity** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.CompensableActivity> .

## <a name="the-compensableactivity-activity"></a>Die CompensableActivity-Aktivität
 Die <xref:System.Activities.Statements.CompensableActivity> definiert eine Arbeitseinheit, die nach erfolgreichem Abschluss bestätigt oder kompensiert werden kann.

### <a name="using-the-compensableactivity-activity-designer"></a>Verwenden des CompensableActivity-Aktivitätsdesigners
 Der **CompensableActivity** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**. Um die **Toolbox** zu öffnen, wählen Sie die Registerkarte **Toolbox** auf der linken Seite des Workflow-Designer aus. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

 Der **CompensableActivity** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden. Sie können den Aktivitäts Designer in einem ablegen <xref:System.Activities.Statements.Sequence> . Beim Löschen des Aktivitäts Designers wird eine- <xref:System.Activities.Statements.CompensableActivity> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity erstellt. Bearbeiten Sie den <xref:System.Activities.Activity.DisplayName%2A> Wert im Header des **CompensableActivity** -Aktivitäts Designers. Sie kann auch im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-compensableactivity-properties"></a>Die CompensableActivity-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CompensableActivity>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A> -Eigenschaft und die- <xref:System.Activities.Activity%601.Result%2A> Eigenschaft können im Eigenschaften Raster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der Workflow-Designer-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.Activities.Statements.CompensableActivity>-Aktivität. Der Standardwert lautet CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Falsch|Gibt den Rückgabewert der <xref:System.Activities.Statements.CompensableActivity> an. Diese Eigenschaft muss im Eigenschaftenraster bearbeitet werden.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Richtig|Gibt die Aktivität an, für die Kompensations-, Abbruch- und Bestätigungslogik bereitgestellt wurde. Um die-Aktivität hinzuzufügen, legen Sie <xref:System.Activities.Statements.CompensableActivity.Body%2A> eine Aktivität aus der **Toolbox** im Feld **Body** des **CompensableActivity** -Aktivitäts Designers ab. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Falsch|Gibt die Aktivität an, die ausgeführt wird, wenn ein Abbruch vorliegt. Um die-Aktivität hinzuzufügen, löschen Sie Ihren Designer aus der **Toolbox** im Feld **cancellationhandler** im **CompensableActivity** -Aktivitäts Designer. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Falsch|Gibt die Aktivität an, die beim Kompensieren der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Compensate>-Aktivität aufgerufen werden.<br /><br /> Um die-Aktivität hinzuzufügen, löschen Sie Ihren Aktivitäts Designer aus der **Toolbox** in das Feld **compensationhandler** im **CompensableActivity** -Aktivitäts Designer. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Falsch|Gibt die Aktivität an, die beim Bestätigen der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Confirm>-Aktivität aufgerufen werden.<br /><br /> Um die-Aktivität hinzuzufügen, löschen Sie Ihren Aktivitäts Designer aus der **Toolbox** in das Feld **confirmationhandler** im **CompensableActivity** -Aktivitäts Designer. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|

## <a name="see-also"></a>Weitere Informationen

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
