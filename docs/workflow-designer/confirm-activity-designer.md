---
title: Workflow-Designer-Confirm-Aktivitäts Designer
description: Informieren Sie sich über den Confirm-Aktivitäts Designer und darüber, wie Sie diesen Designer zum Erstellen und Konfigurieren einer Confirm-Aktivität verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0227a300160434d0052e81d7c1ccd107c5a11a01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955657"
---
# <a name="confirm-activity-designer"></a>Confirm-Aktivitätsdesigner

Der **Confirm** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Confirm> .

## <a name="the-confirm-activity"></a>Die Confirm-Aktivität
 Die <xref:System.Activities.Statements.Confirm>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Confirm>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Confirm.Target%2A>-Eigenschaft angeben.

 Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-confirm-activity-designer"></a>Verwenden des Confirm-Aktivitätsdesigners
 Der **Confirm** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der Workflow-Designer auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

 Der **Confirm** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine <xref:System.Activities.Statements.Confirm>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Confirm erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann entweder im Header des **Confirm** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-confirm-properties"></a>Die Confirm-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Confirm>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die- <xref:System.Activities.Activity.DisplayName%2A> Eigenschaft kann im Eigenschaften Raster oder auf Workflow-Designer-Oberfläche bearbeitet werden, aber die- <xref:System.Activities.Statements.Confirm.Target%2A> Eigenschaft muss im Eigenschaften Raster bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.CancellationScope>-Aktivität an. Der Standardwert lautet Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Richtig|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Confirm>-Aktivität enthält.|

## <a name="see-also"></a>Weitere Informationen

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)