---
title: Richtlinien zum Importieren von wiederverwendbaren Workflows | Microsoft-Dokumentation
description: Lesen Sie die Richtlinien für den Import wiederverwendbarer Workflows, die in SharePoint Designer in Visual Studio erstellt wurden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aab3d3b73fac086c4ff5aee8b5319a76e9aaea15
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915517"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Richtlinien für das Importieren von wiederverwendbaren Workflows
  Um wiederverwendbare Workflows zu importieren, die in SharePoint Designer erstellt wurden, verwenden Sie die wiederverwendbare SharePoint 2010-Workflow Projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vorlage in Mit dieser Vorlage wird ein *deklarativer* *Workflow* importiert ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] nur) und in einen *Code Workflow* konvertiert. dabei handelt es sich um einen Workflow, den Sie entweder mit oder mit Code erweitern können [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)]Exemplarische Vorgehensweise [: Importieren eines wiederverwendbaren Workflows in SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)

 Mit der wiederverwendbaren SharePoint 2010-Workflow Vorlage importieren können jedoch nur Farm Lösungen importiert werden. Wenn Sie den Workflow als Sandkasten Lösung bereitstellen möchten, importieren Sie ihn mit der Vorlage "SharePoint 2010-Lösungspaket importieren". Auf diese Weise können Sie Sie jedoch nicht in den Code Workflow konvertieren und können Sie daher nicht ändern.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importieren wiederverwendbarer Workflows mithilfe der Vorlage zum Importieren von wiederverwendbaren Workflows
 Wenn Sie einen wiederverwendbaren Workflow mithilfe der wiederverwendbaren SharePoint 2010-Workflow Vorlage importieren importieren, können Sie die Projekt Mappe genauso wie jede andere SharePoint-Lösung ausführen oder ändern [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aber Sie müssen möglicherweise einige Elemente manuell beheben.

### <a name="import-task-forms"></a>Importieren von Task Formularen
 Mit der wiederverwendbaren SharePoint 2010-Workflow-Projektvorlage importieren werden alle Initiierungs-und Zuordnungs Formulare importiert, aber nur ein Aufgaben Formular importiert, weil das Code Workflow Schema nur ein Aufgaben Formular zulässt. Alle zusätzlichen Aufgaben Formulare aus der ursprünglichen Workflow Projekt Mappe werden in **Projektmappen-Explorer** in den Ordner " **importierte Dateien** " eingefügt.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importieren von wiederverwendbaren Workflows mithilfe der Vorlage "SharePoint 2010-Lösungspaket importieren"
 Wenn Sie einen wiederverwendbaren Workflow mithilfe der Vorlage SharePoint 2010-Lösungspaket importieren importieren, müssen Sie die folgenden Punkte beachten:

- Nachdem Sie den Workflow importiert haben, können Sie ihn sofort bereitstellen und ausführen, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] indem Sie die **F5** -Taste drücken. Wenn Sie jedoch etwas im Workflow in der importierten Projekt Mappe ändern, müssen Sie die Elemente im Projekt möglicherweise manuell korrigieren, bevor Sie den Workflow bereitstellen und ausführen können.

- Da der Workflow deklarativ ist, kann ihm kein Code hinzugefügt werden. Wenn Sie den Workflow in einen Code Workflow konvertieren möchten, müssen Sie ihn [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der wiederverwendbaren SharePoint 2010-Workflow Vorlage importieren in importieren.

- Sie können zwar die Workflow-Designer-Datei (. xoml) in Designansicht bearbeiten, es wird jedoch empfohlen, dass Sie Sie in der Quell Ansicht bearbeiten, da der Workflow-Designer falsche Fehler anzeigt.

- Das Debuggen im Workflow funktioniert nicht bei deklarativem Inhalt. Breakpoints, die in festgelegt [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] sind, werden nicht getroffen.

## <a name="import-globally-reusable-workflow-solutions"></a>Importieren Global wiederverwendbarer Workflow Lösungen
 Global wiederverwendbare Workflows können nicht mithilfe der wiederverwendbaren SharePoint 2010-Workflow Vorlage importieren importiert werden. Wenn Sie einen Global wiederverwendbaren Workflow importieren möchten, müssen Sie ihn in einen nicht global wiederverwendbaren Workflow konvertieren, oder Sie müssen die Vorlage SharePoint 2010-Lösungspaket importieren verwenden.

 Um den Workflow zu konvertieren, erstellen Sie eine Kopie des Global wiederverwendbaren Workflows in SharePoint Designer (indem Sie das Kontextmenü für den Workflow öffnen und dann **als Kopie speichern** auswählen). Importieren Sie dann den neuen wiederverwendbaren Workflow mit der wiederverwendbaren SharePoint 2010-Workflow Vorlage in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Verwenden Sie die Vorlage SharePoint 2010-Lösungspaket importieren, um den Global wiederverwendbaren Workflow zu importieren, ohne ihn zu ändern. Wenn Sie diese Methode verwenden, wird der Workflow nicht in einen Code Workflow konvertiert und bleibt ein deklarativer Workflow.

## <a name="see-also"></a>Weitere Informationen
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio 2010](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
