---
title: Formular Unterstützung in Workflows | Microsoft-Dokumentation
description: 'Informieren Sie sich über die Formular Unterstützung in SharePoint-Workflows. In einem Workflow können vier Arten von Formularen verwendet werden: Association, Initiierung, Aufgabe und Änderung.'
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52939fe00dcbca1cfd633c81d4b0a00ea6b517b9
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915504"
---
# <a name="form-support-in-workflows"></a>Formular Unterstützung in Workflows
  In einem Workflow können vier Arten von Formularen verwendet werden: Association, Initiierung, Aufgabe und Änderung. Diese Formular Typen können entweder auf einem ASPX-Formular oder auf einem InfoPath-Formular basieren. Die Unterstützungs Ebene, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] für ein bestimmtes Formular bereitstellt, hängt von verschiedenen Faktoren ab, die in den folgenden Tabellen beschrieben werden. Weitere Informationen zu Workflow Formular Typen finden Sie unter [Übersicht über Workflow Formulare](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>XML-Umgestaltung
 Wenn Sie ein aspx-Zuordnungs-oder-Initiierungs Formular zu einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflow Projekt Element hinzufügen, wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] der XML-Code in der *Elements.xml* -Datei des Workflows automatisch neu erstellt, damit das Attribut, das auf das Zuordnungs-oder Initiierungs Formular verweist, immer dann synchronisiert wird, wenn der Formular Name oder der Bereitstellungs Pfad aktualisiert oder Wenn Sie jedoch andere Formular Typen in einem Workflow verwenden, z. b. eine Aufgabe oder ein Änderungs Formular, wird die *Elements.xml* Datei nicht umgestaltet.

## <a name="form-support-in-new-visual-studio-workflows"></a>Formular Unterstützung in neuen Visual Studio-Workflows
 In der folgenden Tabelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird die Unterstützung für verschiedene Formular Typen in aspx-oder InfoPath-Formularen in Workflows aufgelistet, die in erstellt werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Formtyp|In Visual Studio erstelltes Workflow mit einem ASPX-Formular|In Visual Studio erstellter Workflow mithilfe eines InfoPath-Formulars|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Zuordnung|-Ein aspx-Zuordnungs Formular kann dem Workflow hinzugefügt werden, indem die **Workflow Association-Formular** Element Vorlage verwendet wird.<br />-Die *Elements.xml* Datei des Workflows wird umgestaltet, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird oder wenn der Bereitstellungs Pfad geändert wird.<br />-Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Es ist keine InfoPath-Zuordnungs Formular Vorlage in vorhanden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer vorhanden.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.|
|Initiierung|-Ein aspx-Initiierungs Formular kann dem Workflow hinzugefügt werden, indem die **Workflow Initiierungs Formular** -Element Vorlage verwendet wird.<br />-Die *Elements.xml* Datei des Workflows wird umgestaltet, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird oder wenn der Bereitstellungs Pfad geändert wird.<br />-Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Es ist keine InfoPath-Zuordnungs Formular Vorlage in vorhanden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer vorhanden.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.|
|Aufgabe|-Es ist keine aspx-Task Formular Vorlage in verfügbar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sie müssen eine Anwendungsseite erstellen und Ihr Code hinzufügen.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.<br />Weitere Informationen finden Sie unter [Workflow-Aufgaben Formulare (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) .|-Es ist keine InfoPath-Aufgaben Formular Vorlage in vorhanden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer vorhanden.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.|
|Modifikation (Modification)|-Es ist keine aspx-Änderungs Formular Vorlage in verfügbar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Wenn Sie ein Änderungs Formular hinzufügen möchten, müssen Sie eine Anwendungsseite erstellen und Ihr Code hinzufügen.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet. Sie müssen ihn nach Bedarf manuell bearbeiten.<br />Weitere Informationen finden Sie unter [Workflow Änderungs Formulare (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) .|-Es ist keine Formular Vorlage für InfoPath-Änderungen in vorhanden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer vorhanden.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Formular Unterstützung in importierten, wiederverwendbaren Workflows in SharePoint
 In der folgenden Tabelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird die Unterstützung für verschiedene Formular Typen in aspx-oder InfoPath-Formularen in wiederverwendbaren SharePoint-Workflows aufgelistet, die in importiert werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Formtyp|Wiederverwendbarer Workflow, bei dem ein ASPX-Formular aus SharePoint Designer importiert wurde|Wiederverwendbarer Workflow, bei dem ein InfoPath-Formular aus SharePoint Designer importiert wurde|
|---------------|-------------------------------------------------------------------------------| - |
|Zuordnung|-Auf das Formular wird in der *Elements.xml* -Datei des Workflows verwiesen.<br />-Die *Elements.xml* Datei des Workflows wird umgestaltet, wenn das Formular umbenannt oder gelöscht wird, oder wenn der Bereitstellungs Pfad geändert wird.|-Das Formular wird importiert, aber nicht im *Elements.xml* des Workflows referenziert.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.|
|Initiierung|-Das Formular wird vom Workflow in der *Elements.xml* -Datei des Workflows referenziert.<br />-Die *Elements.xml* Datei des Workflows wird umgestaltet, wenn das Formular umbenannt oder gelöscht wird, oder wenn der Bereitstellungs Pfad geändert wird.|-Das Formular wird importiert, aber nicht im *Elements.xml* des Workflows referenziert.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet. **Hinweis:**  Regeln und Eigenschaften müssen hinzugefügt und geändert werden, damit dieses Szenario funktioniert.|
|Aufgabe|-Auf das Formular wird in der *Elements.xml* -Datei des Workflows verwiesen.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet.|-Das Formular wird importiert, aber nicht im *Elements.xml* des Workflows referenziert.<br />-Die *Elements.xml* Datei des Workflows wird nicht umgestaltet. **Hinweis:**  Regeln und Eigenschaften müssen hinzugefügt und geändert werden, damit dieses Szenario funktioniert.|
|Modifikation (Modification)|Nicht zutreffend Aspx-Änderungs Formulare können nicht in SharePoint Designer erstellt werden.|Nicht zutreffend InfoPath-Änderungs Formulare können nicht in SharePoint Designer erstellt werden, mit Ausnahme des integrierten SharePoint-Server Workflows, der beim Exportieren des Workflows nicht in der wsp-Datei enthalten ist.|

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
