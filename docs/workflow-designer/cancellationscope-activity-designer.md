---
title: Cancellationscope-Aktivitäts Designer
description: Erfahren Sie, wie Sie den cancellationscope-Aktivitäts Designer in Workflow-Designer verwenden können, um eine cancellationscope-Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef415763a67232f79b269650abecfe6bcabe6bd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937198"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope-Aktivitätsdesigner

Der **cancellationscope** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.CancellationScope> .

## <a name="the-cancellationscope-activity"></a>Die CancellationScope-Aktivität

Mit der <xref:System.Activities.Statements.CancellationScope>-Aktivität können Sie für eine Aktivität für die Ausführungs- und Abbruchlogik dieser Aktivität angeben.

### <a name="using-the-cancellationscope-activity-designer"></a>Verwenden des CancellationScope-Aktivitätsdesigners

Der **cancellationscope** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**. Um die **Toolbox** zu öffnen, wählen Sie die Registerkarte **Toolbox** der Workflow-Designer aus. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** + **alt** + **X** drücken.

Der **cancellationscope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Wenn der **cancellationscope** -Aktivitäts Designer gelöscht wird, wird eine- <xref:System.Activities.Statements.CancellationScope> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> cancellationscope erstellt. Bearbeiten Sie den <xref:System.Activities.Activity.DisplayName%2A> Wert im Header des **cancellationscope** -Aktivitäts Designers. Sie können Sie auch im Feld **Display Name** des Eigenschaften Rasters bearbeiten.

### <a name="the-cancellationscope-properties"></a>Die CancellationScope-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die- <xref:System.Activities.Activity.DisplayName%2A> Eigenschaft kann im Eigenschaften Raster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf Workflow-Designer-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.Activities.Statements.CancellationScope>-Aktivität. Der Standardwert lautet CancellationScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Richtig|Gibt die Aktivität an, für die Abbruchlogik bereitgestellt wird. Um die- <xref:System.Activities.Statements.CancellationScope.Body%2A> Aktivität hinzuzufügen, löschen Sie eine Aktivität aus der **Toolbox** im Feld **Body** des **cancellationscope** -Aktivitäts Designers. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Richtig|Gibt die Aktivität an, die ausgeführt wird, wenn ein Abbruch vorliegt. Um die- <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Aktivität hinzuzufügen, löschen Sie eine Aktivität aus der **Toolbox** im Feld **cancellationhandler** des **cancellationscope** -Aktivitäts Designers. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|

## <a name="see-also"></a>Weitere Informationen

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
