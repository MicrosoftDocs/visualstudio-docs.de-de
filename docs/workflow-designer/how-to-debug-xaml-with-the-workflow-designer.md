---
title: 'Workflow-Designer: XAML Debuggen'
description: Erfahren Sie, wie Workflows in Bezug auf XAML definiert werden und wie Sie XAML mit dem Workflow-Designer Debuggen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 24540a6e7a2f99f35edf6018355583b5f9230e1a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437930"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer

Workflows werden in XAML definiert. In der Benutzeroberfläche werden Workflows in Form einer XAML-Struktur dargestellt, die den Workflow definiert. Die debuggingdarstellung ähnelt dem Debuggen von Workflows in der Workflow-Designer. Beim Debuggen von XAML funktionieren beispielsweise die Fenster "lokal", "überwachen" und "Threads" genauso wie bei der Workflow-Designer Debuggen. Zusätzlich ist während des XAML-Debuggens die Aufruflistenansicht als zeilenbasierte hierarchische Ansicht des Ausführungsflusses für den Workflow verfügbar.

> [!NOTE]
> Wenn sich das XAML für einen Workflow in derselben Assembly wie die Aktivitäten befindet, wird der Assemblyteil der Klassennamen nicht eingeschlossen. Ohne diesen Teil der Klassennamen (Activity) kann der XAML-Code zur Laufzeit nicht geladen werden. Es wird davon abgeraten, Aktivitäten in demselben Namespace wie das Hauptprojekt zu definieren; andernfalls muss das XAML manuell bearbeitet werden, nachdem es im Designer bearbeitet wurde.

## <a name="to-debug-workflow-xaml"></a>So debuggen Sie Workflow-XAML

1. Öffnen Sie in Visual Studio ein Workflow-oder Aktivitäts Projekt.

2. Legen Sie einen Haltepunkt für die Aktivität oder die Aktivitäten fest, die Sie debuggen möchten, wie unter Gewusst [wie: Festlegen von Breakpoints in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)beschrieben.

3. Klicken Sie mit der rechten Maustaste auf die XAML-Datei, die die Workflow Definition enthält, und wählen Sie **Code anzeigen** aus. Der Haltepunkt wird in der gleichen Zeile wie die XAML-Elementdeklaration der Aktivität angezeigt, für die Sie den Haltepunkt in der Entwurfsansicht festgelegt haben.

4. Rufen Sie den Debugger auf, wie in [Debug-Workflows](debugging-workflows-with-the-workflow-designer.md)beschrieben.

5. Wenn die Codeausführung einen der Haltepunkte erreicht, wird das diesem Haltepunkt zugeordnete XAML-Element hervorgehoben dargestellt. Verwenden Sie die Taste **F10** oder **F11** , um zum nächsten Haltepunkt zu gelangen.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debuggen von Workflows](debugging-workflows-with-the-workflow-designer.md)
