---
title: Arbeiten mit Projektmappen und Projekten
description: Erfahren Sie mehr über den Unterschied zwischen Projektmappen und Projekten und wie sie in Visual Studio verwendet werden können.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f702908c60b08ac1eaae5aa1f941a2f56eaf8fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956801"
---
# <a name="work-with-solutions-and-projects"></a>Arbeiten mit Projektmappen und Projekten

*Projekte* enthalten die Elemente, die zum Erstellen Ihrer App in Visual Studio erforderlich sind. Dabei handelt es sich z. B. um Quellcodedateien, Bitmaps, Symbole sowie Verweise auf Komponenten und Dienste. Wenn Sie ein neues Projekt erstellen, erstellt Visual Studio dafür eine *Projektmappe*. Danach können Sie der Projektmappe nach Bedarf weitere neue oder vorhandene Projekte hinzufügen. Projektmappen können außerdem Dateien enthalten, die zu keinem bestimmten Projekt gehören.

![Diagramm: Projektmappe und Projekthierarchie](./media/vside-proj-soln.png)

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Erstellen von Projekten in Visual Studio für Mac](/visualstudio/mac/create-new-projects).

Sie können Ihre Projektmappen und Projekte in dem Toolfenster **Projektmappen-Explorer** abrufen. Im untenstehenden Screenshot wird ein Beispiel für eine Projektmappe im **Projektmappen-Explorer** (**BikeSharing.Xamarin-UWP**) angezeigt, die zwei Projekte enthält: **BikeSharing.Clients.Core** und **BikeSharing.Clients.Windows**. In jedem Projekt sind mehrere Dateien, Ordner und Verweise enthalten. Der Name des *Startprojekts* – also das Projekt, das gestartet wird, wenn Sie die App ausführen – ist fett gedruckt. Sie können das Startprojekt selbst festlegen.

![Screenshot: Projektmappen-Explorer mit zwei Projekten](./media/vside-solution-explorer-projects.png)

Visual Studio bietet eine Auswahl von Projektvorlagen, die Sie beim Starten unterstützen sollen. Sie können Projekte aber auch selbst gestalten, indem Sie alle notwendigen Dateien hinzufügen. Wenn Sie ein neues Projekt aus einer Vorlage erstellen, entsteht ein Projekt, dass alle für den Projekttyp benötigten Bestandteile enthält. Außerdem können Sie die Dateien umbenennen und nach Bedarf neuen oder vorhandenen Code sowie andere Ressourcen hinzufügen.

An dieser Stelle sollte erwähnt werden, dass Projektmappen und Projekte nicht unbedingt zum Entwickeln von Apps in Visual Studio benötigt werden. Sie können auch einfach nur den Code öffnen, den Sie aus Git geklont oder an anderer Stelle heruntergeladen haben. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Erstellen eines Projekts aus einer Projektvorlage

Informationen zum Auswählen einer Vorlage zum Erstellen eines neuen Projekts finden Sie unter [Erstellen eines neuen Projekts in Visual Studio](create-new-project.md). Ein Beispiel für die Erstellung eines Projekts und einer Projektmappe von Grund auf mit exemplarischen Anweisungen und Beispielcode finden Sie in der [Einführung in Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md).

## <a name="create-a-project-from-existing-code-files"></a>Erstellen eines Projekts aus vorhandenen Codedateien

Auflistungen von Quellcodedateien können Sie dem Projekt bei Bedarf hinzufügen.

1. Klicken Sie im Menü auf **Datei**  >  **Neu**  >  **Project From Existing Code** (Projekt aus vorhandenem Code).

1. Wählen Sie im Assistenten **Create Project from Existing Code Files** („Projekt aus vorhandenen Codedateien erstellen“) den gewünschten Projekttyp im Dropdown-Listenfeld **Ein Projekt welchen Typs möchten Sie erstellen?** aus, und klicken Sie dann auf **Weiter**.

1. Wechseln Sie im Assistenten zum Speicherort der Dateien, und geben Sie dann einen Namen für das neue Projekt in das Feld **Name** ein. Klicken Sie auf **Fertigstellen**, wenn Sie fertig sind.

> [!NOTE]
> Diese Option funktioniert am besten für relativ einfache Sammlungen von Dateien. Derzeit werden nur die Projekttypen C++, Apache Cordova, Visual Basic und C# unterstützt.

## <a name="add-files-to-a-solution"></a>Hinzufügen von Dateien zu einer Projektmappe

Dateien, die für mehrere Projekt gelten, wie Infodateien zur Projektmappe oder andere Dateien, die eher auf Projektmappenebene als auf Projektebene abgelegt werden sollten, können Sie zur Projektmappe hinzufügen. Öffnen Sie das Kontextmenü des Projektmappenknotens im **Projektmappen-Explorer** mit einem Rechtsklick, und wählen Sie **Hinzufügen**  >  **Neues Element** oder **Hinzufügen**  >  **Vorhandenes Element** aus, um der Projektmappe ein Element hinzuzufügen.

> [!TIP]
> Eine Projektmappendatei ist eine Struktur zum Organisieren von Projekten in Visual Studio. Sie enthält den Zustand dieser Informationen in zwei Dateien: eine *SLN*-Datei (eine textbasierte, freigegebene Datei) und eine *SUO*-Datei (binäre, versteckte und benutzerspezifische Projektmappenoptionen). Daher sollte eine Projektmappe nicht kopiert und umbenannt werden. Stattdessen empfiehlt es sich, eine neue Projektmappe zu erstellen, und vorhandene Elemente zu dieser hinzuzufügen.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Erstellen eines .NET-Projekts, das für eine bestimmte Version von .NET Framework vorgesehen ist

Bei der Erstellung eines .NET Framework-Projekts können Sie angeben, welche Version von .NET Framework Sie verwenden möchten. (Wenn Sie ein .NET Core-Projekt erstellen, geben Sie keine Frameworkversion an.)

::: moniker range="vs-2017"

Klicken Sie im Dialogfeld **Neues Projekt** auf das Dropdownmenü **Framework**, um eine .NET Framework-Version festzulegen.

![Screenshot: Dropdownmenü „Framework“ im Dialogfeld „Neues Projekt“](./media/vside-newproject-framework.png)

> [!NOTE]
> Sie müssen auf dem System .NET Framework 3.5 installiert haben, um auf frühere Frameworkversionen als .NET Framework 4 zugreifen zu können.

::: moniker-end

::: moniker range=">=vs-2019"

Klicken Sie auf der Seite **Neues Projekt erstellen** auf das Dropdownmenü **Framework**, um eine .NET Framework-Version festzulegen.

![Screenshot: Frameworkauswahl im Dialogfeld „Neues Projekt konfigurieren“](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Erstellen von leeren Projektmappen

Sie können auch leere Projektmappen ohne Projekt erstellen. Dies erweist sich unter Umständen als nützlich, wenn Sie die Projektmappe und Projekte von Grund auf neu erstellen möchten.

### <a name="to-create-an-empty-solution"></a>So erstellen Sie eine leere Projektmappe

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

::: moniker range="vs-2017"

2. Klicken Sie im linken Bereich (**Vorlagen**) auf **Andere Projekttypen** > **Visual Studio-Projektmappen** in der erweiterten Liste.

3. Wählen Sie im mittleren Bereich die Option **Leere Projektmappe** aus.

4. Geben Sie für die Projektmappe die Werte **Name** und **Speicherort** ein, und klicken Sie dann auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Geben Sie auf der Seite **Neues Projekt erstellen****Projektmappe** in das Suchfeld ein.

3. Wählen Sie die Vorlage **Leere Projektmappe** aus, und klicken Sie dann auf **Weiter**.

4. Geben Sie für die Projektmappe die Werte **Name** und **Speicherort** ein, und klicken Sie dann auf **Erstellen**.

::: moniker-end

Nachdem Sie eine leere Projektmappe erstellt haben, können Sie dieser neue oder vorhandene Projekte oder Elemente hinzufügen, indem Sie im Menü **Projekt** den Befehl **Neues Element hinzufügen** oder **Vorhandenes Element hinzufügen** auswählen.

Wie zuvor bereits erwähnt, können Sie Codedateien auch ohne Projekt oder Projektmappe öffnen. Weitere Informationen zu dieser Entwicklungsmethode finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Erstellen eines temporären Projekts

(Nur C# und Visual Basic)

Wenn Sie ein.NET-basiertes Projekt erstellen, ohne einen Speicherort auf einem Datenträger anzugeben, handelt es sich dabei automatisch um ein temporäres Projekt. Mithilfe von temporären Projekten können Sie mit .NET-Projekten experimentieren. Während Sie an dem temporären Projekt arbeiten, können Sie es jederzeit speichern oder verwerfen.

Gehen Sie zunächst zu **Extras** > **Optionen** > **Projekte und Projektmappen** > **Allgemein**, und deaktivieren Sie das Feld **Neue Projekte beim Erstellen speichern**, um ein temporäres Projekt zu erstellen. Öffnen Sie wie gewohnt das Dialogfeld **Neues Projekt**.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Löschen einer Projektmappe, eines Projekts oder eines Elements

Sie können das Kontextmenü (Rechtsklick) verwenden, um Projektmappen, Projekte oder Elemente in Visual Studio zu löschen bzw. zu entfernen. Dadurch werden sie jedoch lediglich aus der aktuellen Projektmappe bzw. dem aktuellen Projekt gelöscht.

Zum dauerhaften Löschen einer Projektmappe oder anderer Komponenten verwenden Sie den **Datei-Explorer** unter Windows, um den Ordner zu löschen, der die *SLN*- und *SUO*-Projektmappendateien enthält. (Bevor Sie eine Projektmappe löschen, sollten Sie Sicherungen Ihrer Projekte und Dateien für den Fall erstellen, dass Sie sie wieder benötigen.)

> [!NOTE]
> Bei der *SUO*-Datei handelt es sich um eine versteckte Datei, die bei den Standardeinstellungen des Datei-Explorers nicht angezeigt wird. Aktivieren Sie das Feld **Ausgeblendete Elemente** in der **Menüansicht** des Datei-Explorers, damit ausgeblendete Dateien angezeigt werden.

### <a name="permanently-delete-a-solution"></a>Endgültiges Löschen einer Projektmappe

Mithilfe des Projektmappen-Explorers in Visual Studio können Sie auf den Datei-Explorer von Windows zugreifen. Gehen Sie folgendermaßen vor:

1. Öffnen Sie im **Projektmappen-Explorer** per Rechtsklick das Kontextmenü der Projektmappe, die Sie löschen möchten, und wählen Sie dann **Ordner im Datei-Explorer öffnen** aus.

1. Navigieren Sie im Datei-Explorer eine Ebene höher.

1. Wählen Sie den Ordner aus, der die Projektmappe enthält, und drücken Sie dann **ENTF**.

## <a name="see-also"></a>Weitere Informationen

- [Einführung in Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)
- [Gefilterte Projektmappen in Visual Studio](filtered-solutions.md)
- [Microsoft's open source repositories on GitHub (Open Source-Repositorys von Microsoft auf GitHub)](https://github.com/Microsoft)
- [Entwickler-Codebeispiele](https://code.msdn.microsoft.com/)
- [Ressourcen für die Problembehandlung bei IDE-Fehlern in Visual Studio](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
