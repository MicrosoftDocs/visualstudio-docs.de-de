---
title: Konfigurieren von Projekten für mehrere Zielplattformen
description: Visual Studio ermöglicht es, dass eine Projektmappe mehrere verschiedene CPU-Architekturen oder Plattformen auf einmal ansteuert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4dfbf2808071d47e1f84eef660d936181227f3
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136705"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Vorgehensweise: Konfigurieren von Projekten für mehrere Zielplattformen

Visual Studio ermöglicht es, dass eine Projektmappe mehrere verschiedene CPU-Architekturen oder Plattformen auf einmal ansteuert. Auf die Eigenschaften, die für das Festlegen erforderlich sind, kann über das Dialogfeld **Konfigurations-Manager** zugegriffen werden.

## <a name="target-a-platform"></a>Ausrichten auf eine Plattform

Mit dem Dialogfeld **Konfigurations-Manager** können Sie Konfigurationen und Plattformen auf Projektmappen- und Projektebene erstellen und festlegen. Jeder Kombination von Konfigurationen und Zielen auf Projektmappenebene können eindeutige Eigenschaften zugeordnet sein. Dadurch können Sie beispielsweise einfach zwischen einer Releasekonfiguration für eine [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]-Plattform, einer Releasekonfiguration für eine x86-Plattform und einer Debugkonfiguration für eine x86-Plattform wechseln.

1. Klicken Sie im Menü **Erstellen** auf **Konfigurations-Manager** .

2. Wählen Sie im Feld **Aktive Projektmappenplattform** die Plattform aus, die Ihre Projektmappe ansteuern soll, oder klicken Sie auf **\<New>** , um eine neue Plattform zu erstellen. Visual Studio kompiliert Ihre Plattform, damit diese die Plattform ansteuert, die als aktive Plattform im Dialogfeld **Konfigurations-Manager** festgelegt ist.

## <a name="remove-a-platform"></a>Entfernen einer Plattform

Wenn Sie feststellen, dass Sie keine Plattform benötigen, können Sie diese mithilfe des Dialogfelds **Konfigurations-Manager** entfernen. Dadurch werden alle Projektmappen- und Projekteinstellungen entfernt, die Sie für diese Kombination von Konfiguration und Ziel konfiguriert haben.

1. Klicken Sie im Menü **Erstellen** auf **Konfigurations-Manager** .

2. Klicken Sie im Feld **Aktive Projektmappenplattform** auf **\<Edit>** . Das Dialogfeld **Projektmappenplattformen bearbeiten** wird geöffnet.

3. Klicken Sie auf die Plattform, die Sie entfernen möchten, und dann auf **Entfernen** .

## <a name="target-multiple-platforms-with-one-solution"></a>Ausrichten auf mehrere Plattformen mit einer Projektmappe

Da Sie die Einstellungen basierend auf der Kombination von Konfigurations- und Plattformeinstellungen ändern können, können Sie eine Projektmappe einrichten, die mehr als eine Plattform ansteuern kann.

### <a name="to-target-multiple-platforms"></a>Ansteuern mehrerer Plattformen

1. Verwenden Sie den **Konfigurations-Manager** , um mindestens zwei Zielplattformen für die Projektmappe hinzuzufügen.

2. Wählen Sie die Plattform, die Sie ansteuern möchten, aus der Liste **Aktive Projektmappenplattform** aus.

3. Erstellen Sie die Projektmappe.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Gleichzeitiges Erstellen von mehreren Projektmappenkonfigurationen

1. Verwenden Sie den **Konfigurations-Manager** , um mindestens zwei Zielplattformen für die Projektmappe hinzuzufügen.

2. Verwenden Sie das Fenster **Batch erstellen** , um mehrere Projektmappenkonfigurationen gleichzeitig zu erstellen.

   Es ist möglich, dass eine Plattform auf Projektebene vorhanden ist, die z.B. auf [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] festgelegt ist, aber keine Projekte innerhalb dieser Projektmappe vorhanden sind, die die gleiche Plattform ansteuern. Es ist ebenfalls möglich, dass mehrere Projekte in Ihrer Projektmappe vorhanden sind, die jeweils unterschiedliche Plattformen ansteuern. Es wird empfohlen, in einer dieser Situationen eine neue Konfiguration mit einem aussagekräftigen Namen zu erstellen, um Verwechselungen zu vermeiden.

## <a name="see-also"></a>Siehe auch

- [How to: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
