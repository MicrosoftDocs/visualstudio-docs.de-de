---
title: Festlegen von Haltepunkten in Workflows
description: Erfahren Sie, wie Sie die Workflow-Designer verwenden können, um Haltepunkte für Ihre grafischen Workflows wie in Visual Basic oder c#-Code festzulegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88516a4160c5236a5a4ef9f01d7f15620aee5cc3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993301"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Vorgehensweise: Festlegen von Breakpoints in Workflows

Wenn Sie Workflow-Designer verwenden, können Sie Haltepunkte in ihren grafischen Workflows wie in Visual Basic oder c#-Code festlegen. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

Ein Haltepunkt hat drei Zustände: " *Pending*", " *Bound*" und " *Error*". Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein rot ausgefülltes Symbol dargestellt. Wenn die Laufzeit den Workflowtyp geladen hat, wechselt der Haltepunktstatus zu "Gebunden". Haben Sie ein falsches Format für den Haltepunkt angegeben, etwa einen ungültigen Aktivitätsnamen, dann erscheint eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

> [!NOTE]
> Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.

> [!NOTE]
> Vergewissern Sie sich vor dem Debuggen, dass Sie im Menü Extras Optionen Debuggen die Option **nur eigenen Code aktivieren (nur verwaltet) aktivieren**  >    >   . Wenn die Option nicht ausgewählt ist und zwei Sequenzen in einer anderen Sequenz geschachtelt sind und Sie einen Haltepunkt für die erste innere Sequenz festgelegt haben, wird durch Drücken von **F11** nicht in die zweite innere Sequenz debuggt.

> [!NOTE]
> Haltepunkte in einem Workflow werden nicht getroffen, wenn der vollständige Pfad zur XAML-Datei Eigenschaft nicht korrekt ist. Der vollständige Pfad zur XAML-Datei ist nicht korrekt, nachdem das Projekt oder die Projekt Mappe in einen anderen Ordner oder auf einen anderen Computer verschoben wurde. Drücken Sie **STRG** + **S** , um die Eigenschaft vollständiger Pfad zu speichern und zu aktualisieren.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>So legen Sie einen Haltepunkt für eine Aktivität in der Entwurfsansicht fest

1. Wählen Sie die Aktivität aus, bei der der Debugger unterbrechen soll.

2. Klicken Sie im Menü **Debuggen** auf halte **Punkt umschalten**. Ein rotes Symbol wird am oberen linken Rand der Aktivität angezeigt.

   Sie können auch **F9** drücken, nachdem Sie die Aktivität ausgewählt haben, oder Sie können mit der rechten Maustaste auf die Aktivität klicken und im Kontextmenü **Haltepunkt**  >  **Einfügen Breakpoint** auswählen.

## <a name="see-also"></a>Weitere Informationen

- [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
