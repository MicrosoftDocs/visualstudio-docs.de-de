---
title: 'Vorgehensweise: Verwenden der Suche im Workflow-Designer'
description: Erfahren Sie, wie Sie im Workflow-Designer nach Elementen nach Schlüsselwort suchen, um das Erstellen größerer, komplexerer Workflows zu vereinfachen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fb30d4846c24638f87989d2a7a716df06b0523b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894113"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Vorgehensweise: Verwenden der Suche im Workflow-Designer

Um das Erstellen größerer, komplexerer Workflows zu vereinfachen, können Sie im Workflow-Designer nach Elementen nach Schlüsselwort suchen. Beachten Sie, dass Ersetzen vom Designer nicht unterstützt wird.

## <a name="quick-find"></a>Schnellsuche

Die Schnellsuche findet Folgendes im Designer:

- Eigenschaften von <xref:System.Activities.Activity>-Objekten, <xref:System.Activities.Statements.FlowNode>-Objekten, <xref:System.Activities.Statements.State>-Objekten, Übergängen und anderen benutzerdefinierten Flusssteuerungselementen.

- Variablen

- Argumente

- Ausdrücke

### <a name="use-quick-find"></a>Schnellsuche verwenden

1. Wenn der Workflow-Designer geöffnet ist, **drücken Sie** **STRG + F**, oder wählen Sie die Option zum  >  **Suchen und ersetzen** von  >  **Schnellsuche**.

2. Geben Sie den Suchbegriff in **das Textfeld Suchen nach** ein, und klicken Sie auf **weiter** suchen.

3. Der Suchbegriff befindet sich im aktuellen Workflow. In der folgenden Abbildung wird ein Aktivitäts Anzeige Name im Designer angezeigt:

   ![Suchergebnisse im Workflow Designer](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Suchen in Dateien

In Dateien suchen sucht Zeichen folgen in Workflow Dateien, einschließlich XAML-Dateien.

### <a name="use-find-in-files"></a>Verwenden von "in Dateien suchen"

1. Drücken Sie in Visual Studio **STRG** + **UMSCHALT** + **F**, oder wählen Sie in Dateien **Suchen**  >  **und ersetzen**  >  **Suchen aus**.

2. Geben Sie das Suchelement in **das Textfeld Suchen nach** ein, und klicken Sie auf **alle** suchen.

3. Das Suchergebnis wird in der Ansicht " **Ergebnis suchen** " angezeigt. Durch Doppelklicken auf ein Ergebnis Element gelangen Sie zu der Aktivität, die die Entsprechung im Workflow-Designer enthält.