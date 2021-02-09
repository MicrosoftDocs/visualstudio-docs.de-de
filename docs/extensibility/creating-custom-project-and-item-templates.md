---
title: Erstellen von benutzerdefinierten Projekt- und Elementvorlagen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit Vorlagen zur Vorlagenerstellung im Visual Studio SDK Vorlagen in größere Erweiterungen einschließen können.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc5f347e3f5823613d11c8c217fcb2d29635867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851347"
---
# <a name="create-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt- und Elementvorlagen

Das Visual Studio SDK enthält Projektvorlagen, aus denen eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Elementvorlage erstellt werden können. Diese Vorlagen enthalten häufige Parameterersetzungen und sind als ZIP-Dateien gepackt. Sie werden nicht automatisch bereitgestellt und sind nicht in der experimentellen Instanz verfügbar. Sie müssen die generierte ZIP-Datei in das Verzeichnis für Benutzervorlagen kopieren.

Mit den Vorlagen zur Vorlagenerstellung können Sie Vorlagen in größere Erweiterungen einschließen. So können Sie die Versionskontrolle in Quelldateien implementieren und Vorlagenprojekte in einem VSIX-Paket erstellen.

Sie können auch eine Vorlage für die Installation von NuGet-Paketen konfigurieren. Weitere Informationen finden Sie unter [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates).

Bei der Erstellung einfacher Vorlagen sollten Sie den Assistenten **Vorlage exportieren** verwenden, der eine komprimierte Datei generiert. Weitere Informationen zur Erstellung einfacher Vorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Ab Visual Studio 2017 werden keine Scans nach benutzerdefinierten Projekt- und Elementvorlagen mehr durchgeführt. Die Erweiterung muss nun Vorlagenmanifestdateien mit dem Installationspfad dieser Vorlagen enthalten. Sie können Ihre VSIX-Erweiterungen mithilfe von Visual Studio 2017 aktualisieren. Wenn Sie eine Erweiterung über eine MSI-Datei bereitstellen, müssen Sie die Vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das Vorlagenmanifestschema ist in der [Referenz zum Visual Studio-Vorlagenmanifestschema](../extensibility/visual-studio-template-manifest-schema-reference.md) dokumentiert.

## <a name="create-a-project-template"></a>Erstellen einer Projektvorlage

1. Erstellen Sie ein Projektvorlagenprojekt. Sie finden die Projektvorlage im Dialogfeld **Neues Projekt**, wenn Sie nach „Projektvorlage“ suchen und dann die Version für C# oder Visual Basic auswählen.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine *VSTEMPLATE*-Datei, eine bearbeitbare Projektdatei namens *ProjectTemplate.vbproj* oder *ProjectTemplate.csproj* und einige Dateien, die üblicherweise von anderen Projekttypen generiert werden, z. B. eine *resources.resx*-Datei, eine *AssemblyInfo*-Datei und eine *SETTINGS*-Datei. Jede Codedatei enthält die benötigten gängigen Parameterersetzungen.

![Projektvorlage und Projektauswahl](media/project-template-selection.png)

2. Fügen Sie nach Bedarf Elemente zum Projekt hinzu, oder löschen Sie Elemente aus dem Projekt. Entfernen Sie die bearbeitbare Datei, die *AssemblyInfo*-Datei und die *VSTEMPLATE*-Datei nicht.

3. Aktualisieren Sie die *VSTEMPLATE*-Datei den hinzugefügten und entfernten Elementen entsprechend. Das [Project](../extensibility/project-element-visual-studio-templates.md)-Element muss ein [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)-Element für jede Datei enthalten, die der Vorlage hinzugefügt wird.

4. Bearbeiten Sie Codedateien und andere Inhalte für Benutzer, und fügen Sie die entsprechenden Parameterersetzungen hinzu.

5. Bearbeiten Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine *ZIP-Datei*, die Ihre Vorlage enthält. Diese wird nicht bereitgestellt und ist nicht in der experimentellen Instanz verfügbar.

## <a name="create-an-item-template"></a>Erstellen einer Elementvorlage

1. Erstellen Sie ein Elementvorlagenprojekt.

     Diese Vorlage erstellt eine Klassendatei, ein Symbol, eine *VSTEMPLATE*-Datei und eine *AssemblyInfo*-Datei. Die Klassendatei enthält einige gängige Parameterersetzungen.

2. Fügen Sie nach Bedarf Elemente zum Projekt hinzu, oder löschen Sie Elemente aus dem Projekt.

3. Aktualisieren Sie die *VSTEMPLATE*-Datei den hinzugefügten und entfernten Elementen entsprechend. Das [Project](../extensibility/project-element-visual-studio-templates.md)-Element muss ein [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)-Element für jede Datei enthalten, die der Vorlage hinzugefügt wird.

4. Bearbeiten Sie Codedateien und andere Inhalte für Benutzer, und fügen Sie die entsprechenden Parameterersetzungen hinzu.

5. Bearbeiten Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine komprimierte Datei, die Ihre Vorlage enthält. Diese wird nicht bereitgestellt und ist nicht in der experimentellen Instanz verfügbar.

## <a name="deployment"></a>Bereitstellung

### <a name="to-deploy-the-project-or-item-template"></a>Bereitstellen der Projekt- oder Elementvorlage

1. Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

2. Legen Sie das VSIX-Projekt als Startprojekt fest. Klicken Sie im **Projektmappen-Explorer** auf den VSIX-Projektknoten, klicken Sie mit der rechten Maustaste, und wählen Sie **Als Startprojekt festlegen** aus.

3. Legen Sie das Projektvorlagenprojekt als Objekt des VSIX-Projekts fest. Öffnen Sie die *VSIXMANIFEST*-Datei. Wechseln Sie zur Registerkarte **Objekte**, und klicken Sie auf **Neu**.

    1. Legen Sie das Feld **Typ** auf **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate** fest.

    2. Wählen Sie für die Quelle die Option **Ein Projekt in der aktuellen Projektmappe** und dann das Projekt aus, das Ihre Vorlage enthält.

4. Drücken Sie **F5**, um die Projektmappe zu kompilieren. Die experimentelle Instanz wird geöffnet.

5. Bei einem Projektvorlagenprojekt sollte die Projektvorlage im Dialogfeld **Neues Projekt** (**Datei** > **Neu** > **Projekt**) unter Visual C# oder Visual Basic aufgeführt werden. Bei einem Elementvorlagenprojekt sollte die Elementvorlage im Dialogfeld **Neues Element hinzufügen** aufgeführt werden. Sie können das Dialogfeld **Neues Element hinzufügen** aufrufen, indem Sie im **Projektmappen-Explorer** auf den Projektknoten und dann auf **Hinzufügen** > **Neues Element** klicken.

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu Visual Studio-Vorlagen](../ide/creating-project-and-item-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)
