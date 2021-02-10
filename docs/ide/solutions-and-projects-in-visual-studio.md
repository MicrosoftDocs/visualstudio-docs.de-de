---
title: Informationen zu Projektmappen und Projekten
description: Erfahren Sie mehr über Visual Studio-Projekte und -Projektmappen, das Erstellen neuer Projekte aus einer Vorlage sowie das Anzeigen und Verwalten von Projekten im Projektmappen-Explorer.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 473c3ca0e4a9998d6a320e384bf39b4b5e037085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878499"
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

### <a name="create-new-projects"></a>Neue Projekte erstellen

Die einfachste Methode zum Erstellen eines neuen Projekts besteht darin, eine Projektvorlage für den gewünschten Projekttyp zu verwenden. Eine Projektvorlage enthält mehrere grundlegende und vorab generierte Codedateien, Konfigurationsdateien, Objekte und Einstellungen. Verwenden Sie die Menüoptionen **Datei**  >  **Neu**  >  **Projekt**, um eine Projektvorlage auszuwählen. Weitere Informationen finden Sie unter [Erstellen eines neuen Projekts](create-new-project.md).

Sie können auch eine benutzerdefinierte Projektvorlage erstellen, die Sie zum Erstellen neuer Projekte verwenden können. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

Wenn Sie ein neues Projekt erstellen, speichert Visual Studio dieses am Standardspeicherort unter *%BENUTZERPROFIL%\source\repos*. Sie können diesen Speicherort unter **Extras**  >  **Optionen**  >  **Projekte und Projektmappen**  >  **Speicherorte** ändern. Weitere Informationen finden Sie unter [Dialogfeld „Optionen“: Projekte und Projektmappen > Speicherorte](./reference/projects-solutions-locations-options.md).

## <a name="solutions"></a>Projektmappen

Projekte befinden sich in *Projektmappen*. Trotz der englischen Bezeichnung „Solution“ ist eine Projektmappe keine „Lösung“. Eine Projektmappe ist lediglich ein Container für ein oder mehrere zusammengehörige Projekte sowie Buildinformationen, Visual Studio-Fenstereinstellungen und jegliche weitere Dateien, die zu keinem bestimmten Projekt gehören.

### <a name="solution-file"></a>Projektmappendatei

Visual Studio speichert die Einstellungen von Projektmappen in zwei Dateitypen (*SLN* und *SUO*):

|Erweiterung|name|Beschreibung|
|---------------|----------|-----------------|
|.sln|Visual Studio-Projektmappe|Organisiert Projekte, Projektelemente und Projektmappenelemente in einer Projektmappe.|
|.suo|Benutzeroptionen bei Projektmappen|Speichert Einstellungen und Anpassungen (z.B. Breakpoints) auf Benutzerebene.|

> [!IMPORTANT]
> Eine Projektmappe wird von einer Textdatei (mit der Erweiterung *SLN*) in einem individuellen Format beschrieben. Dieses sollte nicht manuell bearbeitet werden. Dementsprechend handelt es sich bei der *SUO*-Datei um eine versteckte Datei, die bei den Standardeinstellungen des Datei-Explorers nicht angezeigt wird. Aktivieren Sie das Feld **Ausgeblendete Elemente** in der **Menüansicht** des Datei-Explorers, damit ausgeblendete Dateien angezeigt werden.

### <a name="solution-folder"></a>Projektmappenordner

Ein „Projektmappenordner“ ist ein virtueller Ordner, der sich nur im **Projektmappen-Explorer** befindet. In diesem Ordner können Sie Projekte in einer Projektmappe gruppieren. Wenn Sie eine Projektmappendatei auf einem Computer suchen möchten, klicken Sie auf **Extras** > **Optionen** > **Projekte und Projektmappen** > **Speicherorte**. Weitere Informationen finden Sie unter [Dialogfeld „Optionen“: Projekte und Projektmappen > Speicherorte](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Ein Beispiel für die Erstellung eines Projekts und einer Projektmappe von Grund auf mit exemplarischen Anweisungen und Beispielcode finden Sie in der [Einführung in Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md).

## <a name="solution-explorer"></a>Projektmappen-Explorer

Nachdem Sie ein neues Projekt erstellt haben, können Sie mit dem **Projektmappen-Explorer** Projekte und Projektmappen sowie zugehörige Elemente anzeigen und verwalten. Die folgende Abbildung zeigt den **Projektmappen-Explorer** mit einer C#-Projektmappe, die zwei Projekte enthält:

::: moniker range="vs-2017"

![Screenshot: Projektmappen-Explorer mit zwei Projekten](../ide/media/vs2015_solution_explorer.png)

Die Symbolleiste oben im **Projektmappen-Explorer** bietet Schaltflächen, mit denen Sie von einer Projektmappenansicht zu einer Ordneransicht wechseln, ausgeblendete Dateien anzeigen, alle Knoten reduzieren und viele weitere Aktionen ausführen können.

::: moniker-end

::: moniker range="vs-2019"

![Screenshot: Projektmappen-Explorer mit zwei Projekten in Visual Studio 2019](../ide/media/solution-explorer.png)

Die Symbolleiste oben im **Projektmappen-Explorer** enthält Schaltflächen, mit denen Sie von einer Projektmappenansicht zu einer Ordneransicht wechseln, ausstehende Änderungen filtern, alle Dateien anzeigen, alle Knoten reduzieren, [Eigenschaftenseiten](managing-project-and-solution-properties.md) anzeigen, eine Codevorschau im [Code-Editor](writing-code-in-the-code-and-text-editor.md) einsehen und viele weitere Funktionen verwenden können.

::: moniker-end

Viele Menübefehle sind im **Projektmappen-Explorer** über das Kontextmenü verfügbar, das Sie mithilfe eines Rechtsklicks auf verschiedene Elemente aufrufen können. Diese Befehle umfassen das Erstellen eines Projekts, das Verwalten von NuGet-Paketen, das Hinzufügen einer Referenz, das Umbenennen einer Datei und das Ausführen von Tests, um nur einige zu nennen.

Bei ASP.NET Core-Projekten können Sie die Schachtelung von Dateien im **Projektmappen-Explorer** anpassen. Weitere Informationen finden Sie unter [Anpassen der Dateischachtelung im Projektmappen-Explorer](file-nesting-solution-explorer.md).

> [!TIP]
> Wenn Sie den Projektmappen-Explorer geschlossen haben und ihn wieder öffnen möchten, klicken Sie in der Menüleiste auf **Ansicht** > **Projektmappen-Explorer**, oder drücken Sie **STRG**+**ALT**+**L**. Wenn Sie seitliche Registerkarten geschlossen haben und diese an ihren Standardpositionen wiederherstellen möchten, klicken Sie in der Menüleiste auf **Fenster** > **Fensterlayout zurücksetzen**.

> [!NOTE]
> Laden Sie [**Visual Studio Image Library**](https://www.microsoft.com/download/details.aspx?id=35825) herunter, um die Anwendungsbilder und -symbole aus Visual Studio anzuzeigen.

## <a name="see-also"></a>Weitere Informationen

- [Einführung in Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)
- [Gefilterte Projektmappen in Visual Studio](filtered-solutions.md)
- [Portieren, Migrieren und Aktualisieren von Projekten](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Ressourcen für die Problembehandlung bei IDE-Fehlern in Visual Studio](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projekte und Projektmappen (Visual Studio für Mac)](/visualstudio/mac/projects-and-solutions)