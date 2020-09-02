---
title: 'Prüfliste: Erstellen neuer Projekttypen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02edc5925109a31eebfd98c90bd116fb86eef276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697230"
---
# <a name="checklist-creating-new-project-types"></a>Prüfliste: Erstellen neuer Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um einen neuen Projekttyp zu erstellen, müssen Sie mehrere Aufgaben ausführen. Die folgende Checkliste enthält eine Anleitung für diese Aufgaben.  
  
1. Entwerfen Sie die Funktionalität für den neuen Projekttyp. Weitere Informationen finden Sie unter [Entwurfsentscheidungen für Projekttyp](../../extensibility/internals/project-type-design-decisions.md).  
  
2. Bestimmen Sie, welche Editoren für Code und andere Projekt Elemente verwendet werden. Sie können die Core-oder Standard-Editoren verwenden, oder Sie können projektspezifische Editoren erstellen und verwenden. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md) und Gewusst [wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).  
  
3. Bestimmen Sie den Grad der Teilnahme, den Ihre Projekt Elemente in der **Klassenansicht** und der **Objektkatalog**haben. Weitere Informationen finden Sie [unter unterstützen von Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md)zum Durchsuchen von Symbolen.  
  
4. Leiten Sie neue Klassen auf der Grundlage von Entwurfsentscheidungen ab, die Sie zuvor für das Projekt und die Projekt Elemente erstellt haben.  
  
5. Schreiben Sie den Code für die folgenden Projekttyp Komponenten:  
  
    - Projektfactory, um das Erstellen neuer Projekte und das Öffnen vorhandener Projekte zu verwalten. Weitere Informationen finden Sie unter [Erstellen von Projekt Instanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    - Projekt Hierarchie und Befehls Verarbeitung. Weitere Informationen finden Sie unter [nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elemente eines Projekt Modells](../../extensibility/internals/elements-of-a-project-model.md), [Projekt Modell Core-Komponenten](../../extensibility/internals/project-model-core-components.md) und [MenuCommands im Vergleich zu olemenucommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    - Verwaltung von Projekt Elementen, einschließlich Hinzufügen des Projekts zum Dialogfeld " **Neues Projekt** ". Weitere Informationen finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md) und [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    - Persistenz des Projekt Zustands und einzelner Elemente. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md). Informationen zur Persistenz von Lösungs Informationen finden Sie unter [Lösungen](../../extensibility/internals/solutions-overview.md).  
  
    - Konfigurations unabhängige Eigenschaften, die in der Eigenschaftenfenster angezeigt werden sollen. Weitere Informationen finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
    - Projekt Konfigurations Eigenschaften, die in Eigenschaften Seiten implementiert sind, um Konfigurations abhängige Eigenschaften anzuzeigen. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).  
  
    - Ausgaben für die Bereitstellung werden aufgezählt. Weitere Informationen finden Sie unter [Projekt Konfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
    - Start Dienste des Projekts. Weitere Informationen finden Sie unter [Elemente von Projekt Modellen](../../extensibility/internals/elements-of-a-project-model.md) und [Projekt Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md).  
  
    - Objekte oder von abgeleitete Klassen `IDispatch` sind für die Automatisierung verfügbar.  
  
    - XML-Befehls Tabellen Dateien (vsct). Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6. Testen, Debuggen und starten Sie den Projekttyp.  
  
7. Zeigen Sie das Projekt im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Projekt** an, indem Sie `VARIANT_TRUE` als Wert für festlegen `VSHPROPID_ShowProjInSolutionPage` . Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8. Erstellen Sie die Microsoft Installer-Datei (MSI-Datei) zum Installieren der VSPackages. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrieren eines Projekt Typs](../../extensibility/internals/registering-a-project-type.md)und [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Wann Projekttypen erstellt werden sollen](../../extensibility/internals/when-to-create-project-types.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
