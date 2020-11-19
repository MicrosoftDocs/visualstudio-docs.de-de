---
title: 'Vorgehensweise: Importieren einer Master Seite oder eines Designs | Microsoft-Dokumentation'
description: Erstellen Sie Vorlagen für Masterseiten und Designs in SharePoint Designer, und importieren Sie Sie dann in Visual Studio, um Seiten auf Ihrer SharePoint-Website ein konsistentes Erscheinungsbild zu geben.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c17f4e7477a20ea245eaa359a6f9611a8dc4ece6
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903493"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Vorgehensweise: Importieren einer Master Seite oder eines Designs
  Sie können Seiten auf Ihrer SharePoint-Website ein konsistentes Erscheinungsbild bereit halten, indem Sie Masterseiten und Designs erstellen und verwenden. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bietet keine Vorlagen für diese Elemente, Sie können Sie jedoch in SharePoint Designer erstellen und dann in importieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [Baustein: Seiten und Benutzeroberfläche](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) auf der Microsoft-Website.

### <a name="to-import-a-master-page-or-theme"></a>So importieren Sie eine Master Seite oder ein Design

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Erstellen oder öffnen Sie in ein SharePoint-Projekt.

     Weitere Informationen zum Erstellen eines SharePoint-Projekts finden Sie unter [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

3. Erweitern Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie in der Liste der SharePoint-Vorlagen die **Modul** Vorlage aus, und geben Sie dann einen Namen für das Modul an.

     Ein Modul enthält Dateien (z. b. Masterseiten-oder Designdateien) für die Bereitstellung an einem Speicherort, den Sie in SharePoint angeben.

5. Löschen Sie im-Modul die Standarddatei mit dem Namen *Sample.txt*.

6. Wählen Sie den Modul Knoten aus.

7. Wählen Sie in der Menüleiste die Option **Projekt**  >  **Vorhandenes Element hinzufügen** aus, und wählen Sie dann die Master Seite oder Designdatei aus.

     Masterseiten Dateien haben die Erweiterung ". Master", und Designdateien haben die Erweiterung ". THMX".

8. Wenn Sie eine Master Seite hinzugefügt haben, ändern Sie die Einstellung für die **Bereitstellungs Konfliktlösung** in den Eigenschaften des Moduls in **automatisch** .

    > [!NOTE]
    > Fehler können auftreten, wenn der Name der Master Seite mit dem Namen einer vorhandenen Master Seite identisch ist, die entweder als Standard Master Seite oder als benutzerdefinierte Master Seite gekennzeichnet ist. Informationen dazu, wie Sie dieses Problem beheben können, finden Sie unter Exemplarische Vorgehensweise [: Importieren einer benutzerdefinierten Master Seite und Website Seite mit einem Image](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. Öffnen Sie im-Modul *Elements.xml*.

     Sie müssen die *Elements.xml* Datei aktualisieren, um auf die hinzugefügte Master Seite oder das hinzugefügte Design zu verweisen.

10. Ersetzen Sie für eine Master Seite das vorhandene Modul Markup durch das folgende Markup.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Ersetzen Sie für ein Design das vorhandene Modul Markup durch das folgende Markup.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Stellen Sie sicher, dass Sie die Platzhalter Werte durch die tatsächlichen Namen des Moduls und die Master Seite oder das Design ersetzen.

     Das `Type="GhostableInLibrary"` -Attribut gibt an, dass das Element der Inhalts Datenbank hinzugefügt wird, und das- `Url` Attribut des Moduls gibt an, wo die Datei in der SharePoint-Inhalts Datenbank gespeichert werden soll.

11. Um den Bereitstellungs Bereich für eine Master Seite zu ändern, öffnen Sie in **Projektmappen-Explorer** die Featuredatei im Funktions-Designer, und wählen Sie dann einen neuen Bereitstellungs Bereich aus der Liste **Bereich** aus.

     Der Wert **Web** bedeutet, dass die Master Seite nur für die Website gilt, die derzeit im Projekt angegeben ist. Der Wert **Site** bedeutet, dass die Master Seite auf die aktuelle Website Sammlung angewendet wird, die alle untergeordneten Sites und das Stammweb enthält. Die anderen Werte gelten nicht.

    > [!NOTE]
    > Da Designs nur auf die Website Sammlungs Ebene angewendet werden, wird empfohlen, dass Sie den Bereich eines Designs nicht auf " **Site**" festlegen. Fehler können auftreten, wenn ein Design in einer unter Website verwendet wird.

12. Wählen Sie in der Menüleiste **Erstellen** Projekt Mappe erstellen aus  >  **Deploy Solution**.

13. Um zu überprüfen, ob die Dateien ordnungsgemäß bereitgestellt wurden, öffnen Sie die SharePoint-Website, wählen Sie das Menü **Website Aktionen** aus, wählen Sie den Befehl **Site Einstellungen** aus, und wählen Sie dann entweder den Link **Master Seiten** **oder den Link** Designs.

     Die Liste der Masterseiten oder Designs wird angezeigt und enthält entweder die Master Seite oder das Design, das Sie importiert haben.

## <a name="see-also"></a>Weitere Informationen
- [Master Seiten](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Erstellen von Seiten für SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Verwenden von Modulen zum Einbinden von Dateien in eine Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)
