---
title: Lösungen und Projekte
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b1783adadd1bfab32bfbbdcfb5ae28df7c0aae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661195"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Projektmappen und Projekte in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Erstellen einer App, Anwendung, Website, Web App und eines Skripts, Plug-ins usw. in Visual Studio beginnen Sie mit einem *Projekt*. In funktionaler Hinsicht enthält ein Projekt alle Quellcodedateien, Symbole, Bilder, Datendateien und alles andere, was zu einem ausführbaren Programm, einer Website o. Ä. kompiliert werden soll oder für die Kompilierung benötigt wird.  Ein Projekt enthält außerdem alle Compilereinstellungen und andere Konfigurationsdateien, die möglicherweise von verschiedenen Diensten und Komponenten benötigt werden, mit denen Ihr Programm kommuniziert.

 Auf struktureller Ebene handelt es sich bei einem Projekt um eine XML-Datei (*.vbproj, \*.csproj, \*.vcxproj), die eine virtuelle Ordnerhierarchie mit Pfaden zu allen Elementen, die es enthält, und den Buildeinstellungen definiert. In Visual Studio wird die Projektdatei im Projektmappen-Explorer verwendet, um Projektinhalte und Einstellungen anzuzeigen. Wenn Sie das Projekt kompilieren, verwendet die MSBuild-Engine die Projektdatei, um die ausführbare Datei zu erstellen. Sie können Projekts auch so anpassen, dass andere Arten von Ausgaben produziert werden.

 Eine *Projektmappe*enthält in funktionaler Hinsicht und im Dateisystem ein Projekt, das wiederum mindestens ein Projekt sowie Buildinformationen, Visual Studio-Fenstereinstellungen sowie beliebige weitere Dateien, die nicht mit einem bestimmten Projekt verknüpft sind, enthalten kann. Auf struktureller Ebene handelt es sich bei einer Projektmappe um eine Textdatei in einem nativen Format, die normalerweise nicht manuell bearbeitet werden soll.

 Einer Projektmappe ist eine SUO-Datei zugeordnet, die Einstellungen und Konfigurationsinformationen für jeden Benutzer speichert , der am Projekt gearbeitet hat.

 Das folgende Diagramm zeigt die Beziehung zwischen Projekten und Projektmappen und die Elemente, die sie logisch enthalten.

 ![Visual Studio-Projekte und -Projektmappen](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Sie können auch benutzerdefinierte Projekte und Elementvorlagen erstellen. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Erstellen neuer Projekte
 Die einfachste Möglichkeit zum Erstellen eines neuen Projekts ist eine vordefinierte Projektvorlage, die eine Reihe grundlegender vorab generierten Codedateien, Konfigurationsdateien, Assets und Einstellungen für die ersten Schritte mit einer bestimmten Anwendungsart oder Website in einer bestimmten Programmiersprache enthält. Diese Vorlagen finden Sie im Hauptmenü im **Dialogfeld „Neues Projekt“**, wenn Sie **Datei &#124; Neu &#124; Projekt** oder **Datei &#124; Neu &#124; Website** auswählen und dann navigieren. Weitere Informationen finden Sie unter [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md) und [NIB Erstellen von Projekten aus Vorlagen](https://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Verwalten von Projekten im Projektmappen-Explorer
 Nachdem Sie ein neues Projekt erstellt haben, verwenden Sie den **Projektmappen-Explorer** , um Projekte und Projektmappen sowie zugehörige Elemente anzuzeigen und zu verwalten. Die folgende Abbildung zeigt den Server-Explorer mit einer C#-Projektmappe, die zwei Projekte enthält.

 ![Projektmappen-Explorer](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>In diesem Abschnitt

- [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md)

- [Hinzufügen und Entfernen von Projekt Elementen](../ide/adding-and-removing-project-items.md)

- [Verwalten von Projekt- und Projektmappeneigenschaften](../ide/managing-project-and-solution-properties.md)

- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)

- [Anwendungseigenschaften](../ide/application-properties.md)

- [Verwalten der Signierung von Assemblys und Manifesten](../ide/managing-assembly-and-manifest-signing.md)

- [Gewusst wie: Angeben eines Anwendungs Symbols (Visual Basic, c#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

- [Festlegen einer bestimmten .NET-Framework-Version](../ide/targeting-a-specific-dotnet-framework-version.md)

- [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-IDE](../ide/visual-studio-ide.md)
