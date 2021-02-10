---
title: Dialog Feld ' Korrelation Workflow-Designer initialisieren '
description: Erfahren Sie, wie Sie das Dialogfeld Korrelation initialisieren im Workflow-Designer verwenden können, um die correlationdata-Eigenschaft einer InitializeCorrelation-Aktivität zu bearbeiten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a41511f9bfb381eeb422cc9cf7ec015d55ceff70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931512"
---
# <a name="initialize-correlation-dialog-box"></a>Korrelation initialisieren (Dialogfeld)

Das Dialogfeld **Korrelation initialisieren** wird in Workflow-Designer verwendet, um die-Eigenschaft einer-Aktivität zu bearbeiten <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> <xref:System.ServiceModel.Activities.InitializeCorrelation> . Weitere Informationen finden Sie unter [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds " **Korrelation initialisieren** " beschrieben:

|Benutzeroberflächenelement|BESCHREIBUNG|
|-|-----------------|
|**Korrelation**|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt der zu initialisierenden Korrelation.|
|**Initialisieren mit**|Ein Schlüssel-Wert-Paar, das die Daten zum Initialisieren enthält. Dieser Wert entspricht der- <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft. Ein Beispiel für ein gültiges Schlüssel-Wert-Paar ist ein Schlüssel mit dem Namen "OrderID", der mit einer Variablen namens OrderID gekoppelt ist.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>So starten Sie das Dialogfeld "Korrelation initialisieren"

Klicken Sie im **InitializeCorrelation** -Aktivitäts Designer auf **Ansicht** , oder wählen Sie <xref:System.ServiceModel.Activities.InitializeCorrelation> in Workflow-Designer eine Aktivität aus. Klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten neben der- <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Eigenschaft im Eigenschaften Raster.

## <a name="see-also"></a>Weitere Informationen

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
