---
title: 'Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner | Microsoft-Dokumentation'
description: Hinzufügen und Entfernen von zugeordneten Ordnern zu einem Projekt in SharePoint.  Ändern Sie den Bereitstellungs Speicherort eines zugeordneten Ordners. Umbenennen oder Entfernen von zugeordneten Ordnern.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e6771482925a935d1b6424412d4176db5e9ad6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923482"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner
  Einige häufig verwendete Ordner in SharePoint, z. b. Bilder und Layouts, sind tief in die Datei Hierarchie eingebettet. Sie können diese Ordner einem SharePoint-Projekt zuordnen, um leichter auf diese Ordner zuzugreifen. Zugeordnete Ordner sind Ordner im SharePoint-Projekt, die dem physischen Speicherort der Dateien in der Installation von SharePoint Server entsprechen.

 Beim Bereitstellen einer SharePoint-Anwendung werden die Inhalte des zugeordneten Ordners und aller zugehörigen Unterordner vom Lösungspaket (. wsp) auf den Server kopiert, auf dem SharePoint an der angegebenen Position in der SharePoint-Ordnerstruktur ausgeführt wird. Dieser Speicherort wird durch die Eigenschaft **Bereitstellungsort** festgelegt, die für den zugeordneten Ordner festgelegt ist. Alle Unterordner im zugeordneten Ordner sind relativ zum **Bereitstellungs Speicherort** des zugeordneten Ordners. Beachten Sie, dass die Eigenschaft **Bereitstellungsort** und nicht der Name des zugeordneten Ordners bestimmt, wo Elemente bereitgestellt werden.
Sie können zugeordnete Ordner einem Projekt hinzufügen, indem Sie die Befehle auf der Menüleiste oder das Kontextmenü für das Projekt verwenden. Sie können die Ordner Befehle **SharePoint-Images hinzufügen** und **SharePoint-Layouts hinzufügen** verwenden, um die zugeordneten Ordner hinzuzufügen, die am häufigsten verwendet werden. Sie können beliebige der anderen verfügbaren SharePoint-Ordner dem Projekt zuordnen, indem Sie den Befehl SharePoint-zugeordneten **Ordner hinzufügen** im Kontextmenü verwenden und dann die Ordner im Dialogfeld " **zugeordneter SharePoint-Ordner hinzufügen** " angeben.

## <a name="add-mapped-folders-to-a-project"></a>Hinzufügen von zugeordneten Ordnern zu einem Projekt
 Im folgenden Verfahren wird beschrieben, wie einem Visual Web Part-Projekt zwei zugeordnete Ordner hinzugefügt werden. Erstellen Sie zunächst ein visuelles Webpartprojekt.

#### <a name="to-add-mapped-folders-to-a-project"></a>So fügen Sie einem Projekt zugeordnete Ordner hinzu

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie im Dialogfeld **Neues Projekt** entweder den Knoten **Visual Basic** oder **Visual c#** , erweitern Sie den Knoten **Office/SharePoint** , und wählen Sie dann den Knoten **SharePoint-Lösungen** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Vorlage **SharePoint 2013 Visual Web Part** aus.

4. Geben Sie im Feld **Name den Namen** **TestProject1** ein, und klicken Sie dann auf die Schaltfläche **OK** .

5. Wählen Sie im Assistenten zum Anpassen von **SharePoint** die Schaltfläche **Fertig** stellen aus, um die Standardeinstellungen beizubehalten.

6. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Hinzufügen SharePoint "Images" zugeordneter Ordner**.

     In Ihrem Projekt wird ein Ordner mit dem Namen **Images** angezeigt, der einen Unterordner mit dem Namen TestProject1 enthält. Dieser zugeordnete Ordner enthält Bilder für das Visual Web Part-Projekt.

7. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus, und klicken Sie dann auf der Menüleiste auf **Projekt**  >  **Hinzufügen von SharePoint zugeordneten Ordner hinzu** fügen, um das Dialogfeld zugeordneten **SharePoint-Ordner hinzufügen** anzuzeigen.

8. Wählen Sie in der Strukturansicht der Ordner, die für die Zuordnung verfügbar sind, den Ordner **Ressourcen** aus, und klicken Sie dann auf die Schaltfläche **OK** .

     In Ihrem Projekt wird ein Ordner mit dem Namen " **Resources** " angezeigt. In diesem Ordner können Elemente wie Zeichen folgen-Ressourcen Dateien gespeichert werden. Unterordner können nützlich sein, um den Inhalt eines zugeordneten Ordners zu organisieren. Sie werden jedoch nicht automatisch erstellt, wenn Sie einen zugeordneten Ordner mit dem Befehl **Hinzufügen von SharePoint-Ordner hinzu** fügen hinzufügen. Wählen Sie zum Hinzufügen eines unter Ordners den Ordner **Ressourcen** aus, und wählen Sie dann in der Menüleiste die Option **Projekt**  >  **neuer Ordner** aus.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Ändern des Bereitstellungs Speicher Orts eines zugeordneten Ordners
 Standardmäßig werden zugeordnete Ordner bestimmten Speicherorten relativ zum SharePoint-Stamm Installationspfad hinzugefügt, der vom Token \<SharePointRoot> angegeben wird. Sie können diesen Speicherort jedoch ändern, indem Sie die Eigenschaft **Bereitstellungsort** des zugeordneten Ordners ändern. Jeder zugeordnete Ordner verfügt über eine eigene Eigenschaft für den **Bereitstellungsort** .

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>So ändern Sie den Bereitstellungs Speicherort eines zugeordneten Ordners

1. Wählen Sie in dem Projekt, das Sie zuvor erstellt haben, einen zugeordneten Ordner aus.

2. Wählen Sie im **Eigenschaften** Fenster in der Eigenschaft **Bereitstellungsort** die Schaltfläche mit den Auslassungs Zeichen (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) aus.

3. Navigieren Sie im Dialogfeld "zugeordnete **SharePoint-Ordner hinzufügen** " zu dem Ordner, auf den der zugeordnete Ordner verweisen soll.

4. Wählen Sie den Knoten aus, und klicken Sie dann auf die Schaltfläche **OK** .

## <a name="rename-or-remove-mapped-folders"></a>Umbenennen oder Entfernen von zugeordneten Ordnern

#### <a name="to-rename-or-remove-a-mapped-folder"></a>So benennen Sie einen zugeordneten Ordner um oder entfernen ihn

1. Wählen Sie in dem Projekt, das Sie zuvor erstellt haben, einen zugeordneten Ordner aus.

2. Um den zugeordneten Ordner umzubenennen, öffnen Sie das Kontextmenü, wählen Sie **Umbenennen** aus, geben Sie den neuen Namen ein, und drücken Sie dann die EINGABETASTE.

     Als Alternative können Sie den zugeordneten Ordner auswählen, den Sie umbenennen möchten, öffnen Sie das Fenster **Eigenschaften** , und legen Sie dann den Wert der Eigenschaft **Ordnername** auf den neuen Namen fest.

3. Wenn Sie einen zugeordneten Ordner aus dem Projekt entfernen möchten, öffnen Sie das Kontextmenü, wählen Sie **Löschen** aus, und wählen Sie dann im Dialogfeld die Schaltfläche **OK** aus, um das Entfernen zu bestätigen.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
