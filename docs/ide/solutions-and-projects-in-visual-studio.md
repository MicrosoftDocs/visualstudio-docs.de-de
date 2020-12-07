---
title: Projektmappen und Projekte
description: Hier erfahren Sie mehr über Visual Studio-Projekte und -Projektmappen und darüber, wie Sie mit dem Projektmappen-Explorer ein neues Projekt erstellen.
ms.custom: SEO-VS-2020
ms.date: 06/26/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 949da02ac074e9740038fef7917655ca552a12f6
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480706"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Projektmappen und Projekte in Visual Studio

In diesem Artikel wird das Konzept eines *Projekts* und einer *Projektmappe* in Visual Studio erläutert. Darüber hinaus werden das Toolfenster „Projektmappen-Explorer“ und das Erstellen eines neuen Projekts kurz beschrieben.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Projekte und Projektmappen in Visual Studio für Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekte

Wenn Sie eine App oder eine Website in Visual Studio erstellen, beginnen Sie mit einem *Projekt*. Ein Projekt enthält alle Dateien, die zu einer ausführbare Datei, Bibliothek oder Website kompiliert werden. Diese Dateien können beispielsweise Quellcode, Symbole, Bilder und Datendateien enthalten. Ein Projekt enthält außerdem die Compilereinstellungen und andere Konfigurationsdateien, die möglicherweise von verschiedenen Diensten und Komponenten benötigt werden, mit denen Ihr Programm kommuniziert.

### <a name="project-file"></a>Projektdatei

Visual Studio verwendet [MSBuild](../msbuild/msbuild.md), um ein Projekt in einer Projektmappe zu erstellen. Jedes Projekt enthält eine MSBuild-Projektdatei. Die Dateierweiterung zeigt den Projekttyp an, wobei z. B. C#- (.csproj), Visual Basic- (.vbproj) oder Datenbankprojekte (.dbproj) verfügbar sind. Die Projektdatei ist ein XML-Dokument, das alle Informationen und Anweisungen enthält, die MSBuild zur Erstellung des Projekts benötigt. Dazu zählen der Inhalt, Plattformanforderungen, Versionsinformationen, Einstellungen für den Web- oder Datenbankserver und die Aufgaben, die ausgeführt werden sollen.

Projektdateien basieren auf dem [MSBuild-XML-Schema](../msbuild/msbuild-project-file-schema-reference.md). Klicken Sie in Visual Studio im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten und anschließend auf **\<projectname\> bearbeiten**, um sich den Inhalt neuer [Projektdateien im SDK-Format](../msbuild/how-to-use-project-sdk.md) anzeigen zu lassen. Wenn Sie sich den Inhalt von .NET Framework-Projekten und anderen Projekten in diesem Format anzeigen lassen möchten, müssen Sie zuerst das Projekt entladen. Klicken Sie dazu im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten und anschließend auf **Projekt entladen**. Klicken Sie dann mit der rechten Maustaste auf das Projekt und auf **\<projectname\>bearbeiten**.

> [!NOTE]
> Der Code muss in Visual Studio nicht mithilfe von Projektmappen oder Projekten bearbeitet, erstellt und debuggt werden. Zum Debuggen öffnen Sie einfach in Visual Studio den Ordner, der die Quelldateien enthält, und beginnen mit dem Bearbeiten. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Projektmappen

Projekte befinden sich in *Projektmappen*. Trotz der englischen Bezeichnung „Solution“ ist eine Projektmappe keine „Lösung“. Eine Projektmappe ist lediglich ein Container für ein oder mehrere zusammengehörige Projekte sowie Buildinformationen, Visual Studio-Fenstereinstellungen und jegliche weitere Dateien, die zu keinem bestimmten Projekt gehören. Eine Projektmappe wird von einer Textdatei (mit der Erweiterung *SLN*) in einem individuellen Format beschrieben. Dieses sollte nicht manuell bearbeitet werden.

Visual Studio speichert die Einstellungen von Projektmappen in zwei Dateitypen (*SLN* und *SUO*):

|Erweiterung|name|Beschreibung|
|---------------|----------|-----------------|
|.sln|Visual Studio-Projektmappe|Organisiert Projekte, Projektelemente und Projektmappenelemente in einer Projektmappe.|
|.suo|Benutzeroptionen bei Projektmappen|Speichert Einstellungen und Anpassungen (z.B. Breakpoints) auf Benutzerebene.|

## <a name="create-new-projects"></a>Neue Projekte erstellen

Ein neues Projekt lässt sich am einfachsten über eine Projektvorlage für einen bestimmten Anwendungs- oder Websitetyp erstellen. Eine Projektvorlage besteht aus mehreren grundlegenden und vorab generierten Codedateien, Konfigurationsdateien, Objekten und Einstellungen. Diese Vorlagen finden Sie in dem Dialogfeld, in dem Sie ein neues Projekt erstellen (**Datei** > **Neu** > **Projekt**). Weitere Informationen finden Sie unter [Erstellen eines neuen Projekts in Visual Studio](create-new-project.md) und [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md).

Wenn Sie Ihre Projekte häufig auf eine bestimmte Weise anpassen, können Sie eine benutzerdefinierte Projektvorlage erstellen, die Sie dann zum Erstellen neuer Projekte verwenden können. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

Wenn Sie ein neues Projekt erstellen, wird es standardmäßig unter *%USERPROFILE%\source\repos* gespeichert. Sie können diesen Speicherort in der Einstellung **Projektspeicherort** unter **Extras** > **Optionen** > **Projekte und Projektmappen** > **Speicherorte** ändern. Weitere Informationen finden Sie auf der Seite [„Projekte und Projektmappen“, Dialogfeld „Optionen“](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Projektmappen-Explorer

Nachdem Sie ein neues Projekt erstellt haben, können Sie mit dem **Projektmappen-Explorer** Projekte und Projektmappen sowie zugehörige Elemente anzeigen und verwalten. Die folgende Abbildung zeigt den **Projektmappen-Explorer** mit einer C#-Projektmappe, die zwei Projekte enthält:

![Projektmappen-Explorer](../ide/media/vs2015_solution_explorer.png)

Viele Menübefehle sind über das Kontextmenü verschiedener Elemente im **Projektmappen-Explorer** verfügbar. Diese Befehle umfassen das Erstellen eines Projekts, das Verwalten von NuGet-Paketen, das Hinzufügen einer Referenz, das Umbenennen einer Datei und das Ausführen von Tests, um nur einige zu nennen. Die Symbolleiste oben im **Projektmappen-Explorer** bietet Schaltflächen, mit denen Sie von einer Projektmappenansicht zu einer Ordneransicht wechseln, ausgeblendete Dateien anzeigen, alle Knoten reduzieren und viele weitere Aktionen ausführen können.

> [!TIP]
> Wenn Sie den Projektmappen-Explorer geschlossen haben und diesen wieder öffnen möchten, klicken Sie in der Menüleiste auf **Fenster** > **Fensterlayout zurücksetzen**.

Bei ASP.NET Core-Projekten können Sie die Schachtelung von Dateien im **Projektmappen-Explorer** anpassen. Weitere Informationen finden Sie unter [Anpassen der Dateischachtelung im Projektmappen-Explorer](file-nesting-solution-explorer.md).

Eine Liste einiger der Symbole, die im Projektmappen-Explorer angezeigt werden, finden Sie unter [Symbole in der Klassenansicht und im Objektkatalog](class-view-and-object-browser-icons.md).

## <a name="see-also"></a>Siehe auch

- [Visual Studio-IDE](../get-started/visual-studio-ide.md)
- [Portieren, Migrieren und Aktualisieren von Projekten](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Projekte und Projektmappen (Visual Studio für Mac)](/visualstudio/mac/projects-and-solutions)
- [Hinzufügen und Entfernen von Projektelementen (Visual Studio für Mac)](/visualstudio/mac/add-and-remove-project-items)
