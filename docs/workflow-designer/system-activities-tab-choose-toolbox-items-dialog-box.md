---
title: System. Activities, Toolbox Elemente auswählen
description: In Workflow-Designer erfahren Sie, wie die Registerkarte System. Activities eine Liste der Windows Workflow Foundation (WF)-Aktivitäten,-Vorlagen und-Elemente anzeigt, die Ihnen zur Verfügung stehen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73027013916d909fd5d9f4c9f00949ce9a863708
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867944"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Registerkarte "System. Activities", Dialogfeld "Toolbox Elemente auswählen"

Auf dieser Registerkarte des Dialog Felds **Toolbox Elemente auswählen** wird eine Liste der Windows Workflow Foundation (WF)-Aktivitäten,-Vorlagen und-Elemente angezeigt, die Ihnen zur Verfügung stehen. Um diese Liste anzuzeigen, wählen Sie **im Menü Extras die Option** **Toolbox Elemente** auswählen aus, oder klicken Sie mit der rechten Maustaste auf die **Toolbox** , und **Wählen Sie Elemente auswählen** aus, um das Dialogfeld **Toolbox Elemente auswählen** anzuzeigen, und wählen Sie dann die Registerkarte **System. Activities** Standardmäßig enthält die Liste Workflow Aktivitäten aus den Assemblys System. Activities, System. Service Model. Activities und System. Activities. Core. Presentation. Allerdings werden nur die vom System bereitgestellten Aktivitäten und Aktivitäten, die über andere in der **Toolbox** angezeigte Assemblys hinzugefügt wurden, standardmäßig aktiviert. Zuletzt hinzugefügte Aktivitäten werden automatisch aktiviert und in der **Toolbox** angezeigt, wenn Sie im Dialogfeld auf **OK** klicken. Außerdem werden diese Elemente in der **Toolbox** unter einer neuen Kategorie angezeigt, die dem Namespace entspricht, in dem sich die Aktivität/das Element/die Vorlage befindet.

> [!WARNING]
> Wenn Sie versuchen, eine Assembly hinzuzufügen, die keine Workflowaktivitäten enthält, wird ein Dialogfeld mit einer Fehlermeldung angezeigt, die besagt, dass die Assembly keine Aktivitäten enthält.

Dieses Dialogfeld ist Projekt agnostisch, sodass die Registerkarte **System. Activities** weiterhin in einem eigenständigen XAML-oder einem nicht-Workflow-Projekttyp angezeigt wird.

Die Filterung erfolgt auf jeder Registerkarte, und es ist nicht möglich, Workflow Aktivitäten über die Registerkarte **.NET-Komponente** hinzuzufügen. Fügen Sie diese über die Registerkarte **System. Activities** selbst hinzu.

Sie können alle Elemente, die nicht in der **Toolbox** angezeigt werden sollen, auf dieser Dialogfeld Registerkarte deaktivieren. Alternativ dazu können Sie auch die Menüoption zum **Löschen** mit der rechten Maustaste in der **Toolbox** verwenden. Wenn Sie auf eine Assembly verweisen, wird das Element nicht aus der **Toolbox** entfernt.

Durch Ziehen und Ablegen im Designer wird die Aktivität instanziiert und die Assembly, die das Element enthält, automatisch der Liste von Assemblys hinzugefügt, auf die verwiesen wird. Außerdem gilt, wenn die Aktivität auf eine Assembly C verweist, wird C nicht der Liste von Assemblys, auf die verwiesen wird, hinzugefügt. Die Assembly C muss sich im GAC oder im selben Verzeichnis wie die Aktivität B befinden. Im eigenständigen Fall muss sich die Assembly im GAC oder in den Überprüfungs Pfaden von vs befinden. Nur dann können Sie die Aktivität auf die Workflow-Designer-Oberfläche ziehen und dort ablegen.

**Toolbox** Einstellungen werden standardmäßig als Benutzeroptionen gespeichert. Wenn Sie die **Toolbox** zum nächsten Mal öffnen, wird Ihre angepasste Liste mit Workflow Aktivitäten angezeigt. Ein Nebeneffekt besteht darin, dass Sie, wenn Sie Ihre spezifischen Domänen Elemente der **Toolbox** über das Dialogfeld **Toolbox Elemente auswählen** hinzugefügt haben, diese Elemente weiterhin anzeigen, wenn Sie auch in einer Workflow Konsolenanwendung arbeiten. Wenn Sie Sie nicht anzeigen möchten, löschen Sie Sie mithilfe des Rechtsklick Menüs, oder deaktivieren Sie Sie wie zuvor im Dialogfeld **Toolbox Elemente auswählen** .

Die Spalten in diesem Dialogfeld enthalten die folgenden Informationen:

Name\
Führt die Namen der Workflowaktivitäten auf, die aktuell auf dem lokalen Computer registriert sind.

Namespace
Zeigt die Hierarchie des .NET-Namespace an, der die Struktur der Aktivität definiert.

AssemblyName \
Zeigt den Namen und die Version der .NET-Assembly an, die die Aktivität enthält.

Befinden
Zeigt den Speicherort der .NET-Assembly an, die die Workflow Aktivitäten enthält. Der Standardspeicherort für alle Assemblys ist der globale Assemblycache.

Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.
