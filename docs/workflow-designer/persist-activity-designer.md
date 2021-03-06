---
title: Workflow-Designer-persistenzdesigner
description: Erfahren Sie mehr über die Persistenz-Aktivität und wie Sie den persistenzaktivitäts-Designer zum Erstellen und Konfigurieren einer persistenten Aktivität verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 988c080b7b6c89baa4151858fcaf4e3320582e09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968722"
---
# <a name="persist-activity-designer"></a>Persist-Aktivitätsdesigners

Der  persistente Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Persist> .

## <a name="the-persist-activity"></a>Die Persist-Aktivität

Wenn möglich, speichert die <xref:System.Activities.Statements.Persist>-Aktivität einen Workflow auf dem Datenträger. Die <xref:System.Activities.Statements.Persist>-Aktivität kann nicht in einem Bereich ohne Persistenz ausgeführt werden, z. B. innerhalb einer <xref:System.Activities.Statements.TransactionScope>-Aktivität. Wenn Sie eine- <xref:System.Activities.Statements.Persist> Aktivität in einem Bereich ohne Persistenz verwenden, wird zur Laufzeit eine Ausnahme ausgelöst.

### <a name="using-the-persist-activity-designer"></a>Verwenden des Persist-Aktivitätsdesigners

Der  persistenzaktivitätsdesigner befindet sich in der Kategorie **Laufzeit** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG + ALT + X drücken).

Der  persistenzaktivitätsdesigner kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine- <xref:System.Activities.Statements.Persist> Aktivität mit dem **Display Name** -Standardwert persistent erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann in der Kopfzeile des persistenten  Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-persist-properties"></a>Die Persist-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Persist>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige von Ihnen können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.Persist>-Aktivität. Der Standardwert lautet Persist. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Weitere Informationen

- [Laufzeit](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
