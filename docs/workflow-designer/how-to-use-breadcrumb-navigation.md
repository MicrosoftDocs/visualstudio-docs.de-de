---
title: 'Workflow-Designer: Gewusst wie: Verwenden der Breadcrumb-Navigation'
description: Erfahren Sie, wie Sie die Breadcrumb-Navigation verwenden, um auf eine untergeordnete Aktivität zuzugreifen, zu einer Vorgänger Aktivität zu navigieren oder um Aktivitäten direkt zu erweitern oder zu reduzieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a15f44b33e7109b126b091dcbf7102aa86a649a9
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437891"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Vorgehensweise: Verwenden der Brotkrümelnavigation

Es gibt drei Hauptmöglichkeiten, den Satz von Aktivitäten zu ändern, die in Workflow-Designer angezeigt werden:

1. Doppelklicken Sie, um in zu einer untergeordneten Aktivität zu wechseln.

2. Klicken Sie auf eine Schaltfläche auf der Breadcrumb-Leiste, um zu einer Vorgängeraktivität zu navigieren.

3. Erweitern oder reduzieren Sie Aktivitäten.

## <a name="using-breadcrumb-navigation"></a>Verwenden der Brotkrümelnavigation

1. Doppelklicken Sie auf eine Aktivität Workflow-Designer, um die Stamm Aktivität in die Aktivität zu ändern, auf die geklickt wurde. Die angeklickte Aktivität wird dann im Stamm vollständig erweitert, und die zugehörigen Vorgänger werden in der Breadcrumb-Leiste angezeigt. Gelegentlich wird dies auch Durchführen von Drillout bzw. Drillinto bei einer Aktivität genannt.

2. Um zu einem Vorgänger der aktuellen Stammaktivität zu navigieren, klicken Sie auf die Aktivität in der Breadcrumb-Leiste.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Erweitern oder Reduzieren einer Aktivität an Ort und Stelle

1. Wenn Sie auf die Chevrons neben einer Aktivität klicken, wird die betreffende Aktivität an Ort und Stelle erweitert bzw. reduziert.

2. Wenn der Erweiterungszustand durch Klicken auf die Schaltfläche geändert wird, dann wird der neue Erweiterungszustand in XAML gespeichert.

    > [!WARNING]
    > Nicht alle Aktivitäten können an Ort und Stelle erweitert werden. Es gibt zwei Fälle, in denen eine Aktivität nicht an Ort und Stelle erweitert werden kann: wenn das übergeordnete Element der Aktivität es nicht zulässt, dass seine untergeordneten Elementen an Ort und Stelle erweitert werden, (Aktivitäten in einem Flussdiagramm können z. B. nicht an Ort und Stelle erweitert werden), und wenn der Aktivitätsdesigner nicht an Ort und Stelle erweitert werden kann. Obwohl keiner der Aktivitäts Designer, der in Workflow-Designer enthalten ist, das letztere Verhalten hat, können einige benutzerdefinierte Aktivitäten dieses Verhalten aufweisen.

## <a name="expanding-all-or-collapsing-all-activities"></a>Erweitern oder Reduzieren aller Aktivitäten

1. Verwenden Sie die Schaltflächen **Alle erweitern** und **alle** reduzieren der Benutzeroberfläche, um alle Aktivitäten unter dem aktuellen Breadcrumb-Stamm zu erweitern oder zu reduzieren. Beachten Sie, dass es sich bei "Alle erweitern" und "Alle reduzieren" um globale Zustände handelt. Dies bedeutet Folgendes: Wenn Sie die Stamm Aktivität mithilfe der Breadcrumb-Navigation ändern, bleibt der Zustand "Alle erweitern" oder "Alle reduzieren" erhalten, bis Sie auf **Wiederherstellen** klicken

2. Nachdem Sie den Zustand "Alle erweitern" oder "Alle reduzieren" angewendet haben, können Sie auf die Schaltfläche **Wiederherstellen** klicken, um den zuvor auf die jeweilige Aktivität angewendeten Zustand zurückzusehen.

    > [!WARNING]
    > Wenn eine Aktivität, z. b. <xref:System.Activities.Statements.Flowchart> , nicht mehr direkt erweitert ist, wird die der Schaltfläche **Alle erweitern** und **alle** reduzieren zugeordnete Funktionalität im **Flussdiagramm** -Designer deaktiviert. Weitere Informationen zum **Flussdiagramm** -Designer finden Sie im Abschnitt [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > "Alle erweitern" wirkt sich auch auf die **Switch** -und **trycatch** -Aktivitäts Designer aus. Wenn Sie auf **Alle erweitern** klicken, werden alle switchfälle und alle try/catch/schließlich-Blöcke angezeigt. Wenn Sie auf " **Wiederherstellen** **" oder "** reduzieren" klicken, werden diese Designer auf ihren Standardzustand zurückversetzt, in dem Sie auf einen einzelnen Fall/Block klicken können, um den Inhalt
