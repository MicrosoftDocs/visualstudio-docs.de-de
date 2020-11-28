---
title: Erstellen von Projektmappen und Projekten
description: Erfahren Sie mehr über den Unterschied zwischen Projektmappen und Projekten und wie sie in Visual Studio verwendet werden können.
ms.custom: SEO-VS-2020
ms.date: 02/06/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bd893c06da9bc2c2c8d95fc4c085affa815edd2
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006444"
---
# <a name="create-solutions-and-projects"></a>Erstellen von Projektmappen und Projekten

*Projekte* enthalten die Elemente, die zum Erstellen Ihrer App in Visual Studio erforderlich sind. Dabei handelt es sich z. B. um Quellcodedateien, Bitmaps, Symbole sowie Verweise auf Komponenten und Dienste. Wenn Sie ein neues Projekt erstellen, erstellt Visual Studio dafür eine *Projektmappe*. Danach können Sie der Projektmappe nach Bedarf weitere neue oder vorhandene Projekte hinzufügen. Projektmappen können außerdem Dateien enthalten, die zu keinem bestimmten Projekt gehören.

![Hierarchie der Projektmappe bzw. des Projekts](./media/vside-proj-soln.png)

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Erstellen von Projekten in Visual Studio für Mac](/visualstudio/mac/create-new-projects).

Sie können Ihre Projektmappen und Projekte in dem Toolfenster **Projektmappen-Explorer** abrufen. Im untenstehenden Screenshot wird ein Beispiel für eine Projektmappe im **Projektmappen-Explorer** (**BikeSharing.Xamarin-UWP**) angezeigt, die zwei Projekte enthält: **BikeSharing.Clients.Core** und **BikeSharing.Clients.Windows**. In jedem Projekt sind mehrere Dateien, Ordner und Verweise enthalten. Der Name des *Startprojekts* – also das Projekt, das gestartet wird, wenn Sie die App ausführen – ist fett gedruckt. Sie können das Startprojekt selbst festlegen.

![Projektmappen-Explorer mit Projekten](./media/vside-solution-explorer-projects.png)

Visual Studio bietet eine Auswahl von Projektvorlagen, die Sie beim Starten unterstützen sollen. Sie können Projekte aber auch selbst gestalten, indem Sie alle notwendigen Dateien hinzufügen. Wenn Sie ein neues Projekt aus einer Vorlage erstellen, entsteht ein Projekt, dass alle für den Projekttyp benötigten Bestandteile enthält. Außerdem können Sie die Dateien umbenennen und nach Bedarf neuen oder vorhandenen Code sowie andere Ressourcen hinzufügen.

An dieser Stelle sollte erwähnt werden, dass Projektmappen und Projekte nicht unbedingt zum Entwickeln von Apps in Visual Studio benötigt werden. Sie können auch einfach nur den Code öffnen, den Sie aus Git geklont oder an anderer Stelle heruntergeladen haben. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Erstellen eines Projekts aus einer Projektvorlage

Informationen zum Erstellen eines neuen Projekts aus einer Vorlage finden Sie unter [Erstellen eines neuen Projekts in Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Erstellen eines Projekts aus vorhandenen Codedateien

Auflistungen von Quellcodedateien können Sie dem Projekt bei Bedarf hinzufügen.

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt aus vorhandenem Code** aus.

1. Wählen Sie im Assistenten **Create Project from Existing Code Files** („Projekt aus vorhandenen Codedateien erstellen“) den gewünschten Projekttyp im Dropdown-Listenfeld **Welchen Typ von Projekt möchten Sie erstellen?** aus, und klicken Sie dann auf die Schaltfläche **Weiter**.

1. Wechseln Sie im Assistenten zum Speicherort der Dateien, und geben Sie dann einen Namen für das neue Projekt in das Feld **Name** ein. Wenn Sie diesen Vorgang abschlossen haben, klicken Sie auf die Schaltfläche **Fertig stellen**.

> [!NOTE]
> Diese Option funktioniert am besten für relativ einfache Sammlungen von Dateien. Derzeit werden nur die Projekttypen C++, Apache Cordova, Visual Basic und C# unterstützt.

## <a name="add-files-to-a-solution"></a>Hinzufügen von Dateien zu einer Projektmappe

Dateien, die für mehrere Projekt gelten, wie Infodateien zur Projektmappe oder andere Dateien, die eher auf Projektmappenebene als auf Projektebene abgelegt werden sollten, können Sie zur Projektmappe hinzufügen. Öffnen Sie das Kontextmenü des Projektmappenknotens im **Projektmappen-Explorer** mit einem Rechtsklick, und wählen Sie **Hinzufügen** > **Neues Element** oder **Hinzufügen** > **Vorhandenes Element** aus, um der Projektmappe ein Element hinzuzufügen.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Erstellen eines .NET-Projekts, das für eine bestimmte Version von .NET Framework vorgesehen ist

Bei der Erstellung eines .NET Framework-Projekts können Sie angeben, welche Version von .NET Framework Sie verwenden möchten. (Wenn Sie ein .NET Core-Projekt erstellen, geben Sie keine Frameworkversion an.)

::: moniker range="vs-2017"

Wählen Sie das **Framework**-Dropdownmenü im Dialogfeld **Neues Projekt** aus, um eine .NET Framework-Version anzugeben.

![Framework-Dropdownliste im Dialogfeld „Neues Projekt“](./media/vside-newproject-framework.png)

> [!NOTE]
> Sie müssen auf dem System .NET Framework 3.5 installiert haben, um auf frühere Frameworkversionen als .NET Framework 4 zugreifen zu können.

::: moniker-end

::: moniker range=">=vs-2019"

Wählen Sie das **Framework**-Dropdownmenü auf der Seite **Neues Projekt erstellen** aus, um eine .NET Framework-Version anzugeben.

![Frameworkauswahl in „Neues Projekt konfigurieren“](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Erstellen von leeren Projektmappen

Sie können auch leere Projektmappen ohne Projekt erstellen. Dies erweist sich unter Umständen als nützlich, wenn Sie die Projektmappe und Projekte von Grund auf neu erstellen möchten.

### <a name="to-create-an-empty-solution"></a>So erstellen Sie eine leere Projektmappe

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

::: moniker range="vs-2017"

2. Klicken Sie im linken Bereich (**Vorlagen**) auf **Andere Projekttypen** > **Visual Studio-Projektmappen** in der erweiterten Liste.

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

Sie können zwar Projektmappen und deren Inhalte dauerhaft löschen, jedoch funktioniert dies nicht über die Visual Studio-IDE. Wenn Sie Elemente aus Visual Studio löschen, werden sie nur aus der aktuellen Projektmappe oder dem aktuellen Projekt entfernt. Wenn Sie eine Projektmappe oder andere Komponenten dauerhaft von Ihrem System löschen möchten, verwenden Sie den Datei-Explorer, um den Ordner zu löschen, der die *SLN-* und *SUO-Projektmappendateien* enthält. Bevor Sie allerdings eine Projektmappe dauerhaft löschen, wird empfohlen, dass Sie sämtliche Projekte oder Dateien sichern, falls Sie diese noch einmal benötigen sollten.

> [!NOTE]
> Die *SUO-Datei* wird ausgeblendet und nicht in den Standardeinstellungen des Datei-Explorers angezeigt. Aktivieren Sie das Feld **Ausgeblendete Elemente** in der **Menüansicht** des Datei-Explorers, damit ausgeblendete Dateien angezeigt werden.

### <a name="permanently-delete-a-solution"></a>Endgültiges Löschen einer Projektmappe

1. Wählen Sie im **Projektmappen-Explorer** im Kontextmenü die zu löschende Projektmappe aus, und wählen Sie dann **Ordner in Datei-Explorer öffnen**.

1. Navigieren Sie im Datei-Explorer eine Ebene höher.

1. Klicken Sie auf den Ordner, der die Projektmappe enthält, und drücken Sie dann die Taste **ENTF**.

## <a name="see-also"></a>Weitere Informationen

- [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)
- [Microsoft's open source repositories on GitHub (Open Source-Repositorys von Microsoft auf GitHub)](https://github.com/Microsoft)
- [Entwickler-Codebeispiele](https://code.msdn.microsoft.com/)
- [Erstellen von Projekten (Visual Studio für Mac)](/visualstudio/mac/create-new-projects)
