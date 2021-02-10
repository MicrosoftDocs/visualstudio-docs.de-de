---
title: Workflow-Designer-Kompensierungs Aktivitäts Designer
description: Erfahren Sie mehr über den Kompensierungs Aktivitäts Designer und wie Sie den Kompensierungs Aktivitäts Designer verwenden können, um eine Kompensierungs Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36ab20854adb952d098f71904cdd3cb092e27ac9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955683"
---
# <a name="compensate-activity-designer"></a>Compensate-Aktivitätsdesigner

Der **Kompensierungs** Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Compensate> .

## <a name="the-compensate-activity"></a>Die Compensate-Aktivität

Die <xref:System.Activities.Statements.Compensate>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Compensate>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Compensate.Target%2A>-Eigenschaft angeben.

Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-compensate-activity-designer"></a>Verwenden des Compensate-Aktivitätsdesigners

Der **Kompensierungs** Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**. Um die **Toolbox** zu öffnen, wählen Sie die Registerkarte **Toolbox** auf der linken Seite des Workflow-Designer aus. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **Kompensierungs** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Beim Löschen des Aktivitäts Designers wird eine- <xref:System.Activities.Statements.Compensate> Aktivität mit dem Standardwert "kompensieren" erstellt <xref:System.Activities.Activity.DisplayName%2A> . Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **Kompensierungs** Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-compensate-properties"></a>Die Compensate-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die- <xref:System.Activities.Activity.DisplayName%2A> Eigenschaft kann im Eigenschaften Raster oder auf Workflow-Designer-Oberfläche bearbeitet werden. Bearbeiten Sie die- <xref:System.Activities.Statements.Compensate.Target%2A> Eigenschaft im Eigenschaften Raster.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Compensate>-Aktivität an. Der Standardwert lautet Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Richtig|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Compensate>-Aktivität enthält.|

## <a name="see-also"></a>Weitere Informationen

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate-Aktivitätsdesigner](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)