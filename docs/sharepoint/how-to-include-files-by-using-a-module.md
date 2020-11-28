---
title: 'Vorgehensweise: einschließen von Dateien mithilfe eines Moduls | Microsoft-Dokumentation'
description: Informieren Sie sich über das Einschließen von Dateien mithilfe eines Moduls. dabei handelt es sich um einen Container, mit dem Sie Dateien wie ASPX-Masterseiten, Textdateien oder Bilder in SharePoint bereitstellen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 381cb529db3f4116a9c42041c26e0e1e242073df
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305412"
---
# <a name="how-to-include-files-by-using-a-module"></a>How to: Einbinden von Dateien mithilfe eines Moduls
  *Module* (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Modulen) sind Container, die es Ihnen ermöglichen, Dateien wie ASPX-Masterseiten, Textdateien oder Bilder in SharePoint bereitzustellen.

 Sie können eine Datei in einer Dokumentbibliothek oder als normale Datei (z. b. default. aspx) außerhalb einer Dokumentbibliothek bereitstellen. Um einer Dokumentbibliothek eine Datei hinzuzufügen, geben Sie `Type="GhostableInLibrary"` als Attribut im **File** -Element an. Diese Einstellung weist SharePoint an, ein Listenelement zu erstellen, um die Datei zu erstellen, wenn Sie der Bibliothek hinzugefügt wird. Um eine Datei außerhalb einer Dokumentbibliothek bereitzustellen, müssen Sie entweder `Type="Ghostable"` das **Type** -Attribut angeben oder einfach weglassen.

## <a name="add-a-module-to-a-sharepoint-solution"></a>Hinzufügen eines Moduls zu einer SharePoint-Lösung

#### <a name="to-add-a-module"></a>So fügen Sie ein Modul hinzu

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Öffnen oder erstellen Sie ein SharePoint-Projekt in.

     Weitere Informationen finden Sie unter [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen**.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

3. Wählen Sie in der Liste der SharePoint-Vorlagen die **Modul** Vorlage aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     In diesem Schritt wird ein Knoten im Projekt mit dem Namen Module1 erstellt.

4. Löschen Sie unter Module1 die Datei *Sample.txt* .

     Sample.txt ist beispielsweise in allen neuen Modulen enthalten und wird nicht benötigt. (Beachten Sie, dass durch das Löschen der Datei auch der zugehörige Eintrag aus der *Elements.xml* Datei des Moduls entfernt wird.)

5. Wenn Sie möchten, dass die Dateien in einer bestimmten Ordnerstruktur in SharePoint bereitgestellt werden, erstellen Sie diese Ordner unter Module1 in, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] indem Sie den Knoten Module1 auswählen, und wählen Sie dann in der Menüleiste die Option **Projekt**, **neuer Ordner** aus.

6. Wählen Sie den Ordner aus, in dem Sie die Datei hinzufügen möchten, und wählen Sie dann in der Menüleiste die Option **Projekt**, **Vorhandenes Element hinzufügen** aus.

7. Wählen Sie mindestens eine Datei aus, die Sie in SharePoint bereitstellen möchten, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Wenn Sie dem Projekt eine Datei hinzufügen, wird der Elements.xml Datei des Moduls automatisch ein Eintrag hinzugefügt. Wenn das Projekt bereitgestellt wird, werden die Dateien in den SharePoint-Server kopiert, relativ zum Stammverzeichnis des Projekts, das durch das **URL** -Attribut des **File** -Elements angegeben wird, z `Url="Module1/New Folder/SomeFile.doc` . b.. Wenn Sie den Bereitstellungs Speicherort für eine Datei ändern möchten, verschieben Sie ihn in **Projektmappen-Explorer** in einen anderen Ordner, oder ändern Sie die **URL** -Einstellung.

8. Fügen Sie für alle Dateien, die in einer Dokumentbibliothek angezeigt werden sollen, das- `Type="GhostableInLibrary"` Attribut an Ihren Eintrag in *Elements.xml* an. Beispiel:

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Stellen Sie das Projekt bereit.

     Die Dateien, die an die angegebenen Speicherorte in SharePoint kopiert werden.

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
