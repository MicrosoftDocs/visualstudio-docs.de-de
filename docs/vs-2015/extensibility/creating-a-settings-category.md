---
title: Erstellen einer Einstellungs Kategorie | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d14e60ec28fb5f8ba80f9986c4316058539b35e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695021"
---
# <a name="creating-a-settings-category"></a>Erstellen einer Einstellungskategorie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie eine Visual Studio-Einstellungs Kategorie und verwenden Sie, um Werte zu speichern und Werte aus einer Einstellungsdatei wiederherzustellen. Eine Einstellungs Kategorie ist eine Gruppe verwandter Eigenschaften, die als "benutzerdefinierter Einstellungs Punkt" angezeigt werden. Das heißt, als Kontrollkästchen im Assistenten zum **importieren und Exportieren von Einstellungen** . (Sie finden es **im Menü Extras** .) Einstellungen werden als Kategorie gespeichert oder wieder hergestellt, und die einzelnen Einstellungen werden im Assistenten nicht angezeigt. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Sie erstellen eine Einstellungs Kategorie, indem Sie Sie von der- <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse ableiten.  
  
 Um diese exemplarische Vorgehensweise zu starten, müssen Sie zuerst den ersten Abschnitt der [Seite Erstellen einer Options Seite](../extensibility/creating-an-options-page.md)ausführen. Mit dem Eigenschaften Raster resultierende Optionen können Sie die Eigenschaften in der Kategorie überprüfen und ändern. Nachdem Sie die Eigenschaften Kategorie in einer Einstellungsdatei gespeichert haben, untersuchen Sie die Datei, um zu sehen, wie die Eigenschaftswerte gespeichert werden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Erstellen einer Einstellungskategorie  
 In diesem Abschnitt verwenden Sie einen benutzerdefinierten Einstellungs Punkt, um die Werte der Kategorie Einstellungen zu speichern und wiederherzustellen.  
  
#### <a name="to-create-a-settings-category"></a>So erstellen Sie eine Einstellungs Kategorie  
  
1. Vervollständigen Sie die [Seite Erstellen einer](../extensibility/creating-an-options-page.md)Option.  
  
2. Öffnen Sie die Datei "VSPackage. resx", und fügen Sie diese drei Zeichen folgen Ressourcen hinzu:  
  
    |Name|Wert|  
    |----------|-----------|  
    |106|Meine Kategorie|  
    |107|Meine Einstellungen|  
    |108|OptionInteger und optionfloat|  
  
     Dadurch werden Ressourcen erstellt, die die Kategorie "My Category", das Objekt "My Settings" und die Kategoriebeschreibung "OptionInteger" und "optionfloat" benennen.  
  
    > [!NOTE]
    > Von diesen drei wird nur der Kategoriename im Assistenten zum Importieren und Exportieren von Einstellungen angezeigt.  
  
3. Fügen Sie in MyToolsOptionsPackage.cs `float` der-Klasse eine Eigenschaft `OptionFloat` mit dem Namen hinzu `OptionPageGrid` , wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    > Die `OptionPageGrid` Kategorie mit dem Namen "My Category" besteht nun aus den beiden Eigenschaften `OptionInteger` und `OptionFloat` .  
  
4. Fügen Sie der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` -Klasse einen hinzu, und geben Sie ihm den CategoryName "My Category", den ObjectName "My Settings" und istoolsoptionpage auf true fest. Legen Sie "categoryresourceid", "objectnameresourceid" und "descriptionresourceid" auf die entsprechenden zuvor erstellten Zeichen folgen Ressourcen-IDs fest.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5. Erstellen Sie das Projekt, und starten Sie das Debugging. In der experimentellen Instanz sollten Sie sehen, dass **meine Raster Seite** nun sowohl ganzzahlige als auch float-Werte enthält.  
  
## <a name="examining-the-settings-file"></a>Überprüfen der Einstellungsdatei  
 In diesem Abschnitt Exportieren Sie Eigenschafts Kategoriewerte in eine Einstellungsdatei. Sie untersuchen die Datei und importieren dann die Werte wieder in die Eigenschaften Kategorie.  
  
1. Starten Sie das Projekt im Debugmodus, indem Sie F5 drücken. Dadurch wird die experimentelle Instanz gestartet.  
  
2. Öffnen Sie das Dialogfeld Extras **/Optionen** .  
  
3. Erweitern Sie in der Strukturansicht im linken Bereich **Meine Kategorie** , und klicken Sie dann auf **meine Raster Seite**.  
  
4. Ändern Sie den Wert von **optionfloat** in 3,1416 und **OptionInteger** in 12. Klicken Sie auf **OK**.  
  
5. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**.  
  
     Der Assistent zum **importieren und Exportieren von Einstellungen** wird angezeigt.  
  
6. Stellen Sie sicher, dass **Ausgewählte Umgebungseinstellungen exportieren** ausgewählt ist, und klicken Sie dann auf **weiter**.  
  
     Die Seite **Einstellungen für den Export auswählen** wird angezeigt.  
  
7. Klicken Sie auf **meine Einstellungen**.  
  
     Die **Beschreibung** ändert sich zu " **OptionInteger" und "optionfloat**".  
  
8. Stellen Sie sicher, dass **meine Einstellungen** die einzige Kategorie ist, die ausgewählt ist, und klicken Sie dann auf **weiter**.  
  
     Die Seite **Name der Einstellungsdatei** wird angezeigt.  
  
9. Benennen Sie die neue Einstellungsdatei, `MySettings.vssettings` und speichern Sie Sie in einem entsprechenden Verzeichnis. Klicken Sie auf **Fertig stellen**.  
  
     Die Seite **Export Complete (exportieren abgeschlossen** ) meldet, dass die Einstellungen erfolgreich exportiert wurden.  
  
10. Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**. Suchen `MySettings.vssettings` und öffnen Sie die Datei.  
  
     Die Eigenschaften Kategorie, die Sie exportiert haben, finden Sie im folgenden Abschnitt der Datei (Ihre GUIDs unterscheiden sich).  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     Beachten Sie, dass der vollständige Kategoriename durch Hinzufügen eines Unterstrichs zum Kategorienamen, gefolgt vom Objektnamen, gebildet wird. Optionfloat und OptionInteger werden in der Kategorie sowie die exportierten Werte angezeigt.  
  
11. Schließen Sie die Einstellungsdatei, ohne Sie zu ändern.  
  
12. Klicken Sie **im Menü Extras** auf **Optionen**, erweitern Sie **Meine Kategorie**, klicken Sie auf **meine Raster Seite** , und ändern Sie dann den Wert von **optionfloat** in 1,0 und **OptionInteger** in 1. Klicken Sie auf **OK**.  
  
13. Klicken Sie **im Menü Extras** auf **Einstellungen importieren und exportieren**, wählen Sie **Ausgewählte Umgebungseinstellungen importieren**aus, und klicken Sie dann auf **weiter**.  
  
     Die Seite **Aktuelle Einstellungen speichern** wird angezeigt.  
  
14. Wählen Sie **Nein, nur neue Einstellungen importieren aus,** und klicken Sie dann auf **weiter**.  
  
     Die Seite **Sammlung der zu importierenden Einstellungen auswählen** wird angezeigt.  
  
15. Wählen Sie die `MySettings.vssettings` Datei im Knoten **eigene Einstellungen** der Strukturansicht aus. Wenn die Datei nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Durchsuchen** , und suchen Sie Sie. Klicken Sie auf **Weiter**.  
  
     Das Dialogfeld **zu importierende Einstellungen auswählen** wird angezeigt.  
  
16. Stellen Sie sicher, dass **meine Einstellungen** ausgewählt ist, und klicken Sie dann auf **Fertig**stellen. Wenn die Seite **Import Vorgang abgeschlossen** angezeigt wird, klicken Sie auf **Schließen**.  
  
17. Klicken Sie **im Menü Extras** auf **Optionen**, erweitern Sie **Meine Kategorie**, klicken Sie auf **meine Raster Seite** , und überprüfen Sie, ob die Werte der Eigenschaften Kategorie wieder hergestellt wurden.
