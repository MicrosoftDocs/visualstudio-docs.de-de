---
title: 'Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows in SharePoint Designer | Microsoft-Dokumentation'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise importieren Sie einen wiederverwendbaren Workflow, der in SharePoint Designer erstellt wurde, in ein Visual Studio SharePoint-Workflow Projekt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1421b061c50277177b5a30f0357725e9a042f3bd
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970184"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows in SharePoint Designer

  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein in SharePoint Designer 2010 erstellter wiederverwendbarer Workflow in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Workflow Projekt importiert wird.

 Workflows, die in SharePoint Designer oder *deklarativen Workflows* erstellt wurden, bestehen aus [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Anweisungen anstelle von Code. SharePoint Designer 2010 führt wieder *verwendbare Workflows* ein, bei denen es sich um Portable, deklarative Workflows handelt, die von verschiedenen Listen in SharePoint-Websites verwendet werden können.

 Workflows, die in erstellt werden [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , z. b. sequenzielle Workflows und Status Computer Workflows, werden als *Code Workflows* bezeichnet Code Workflows bestehen aus XML-Dateien und Code Modulen, in denen Benutzer das Verhalten des Workflows anpassen können.

 Visual Studio ermöglicht es Ihnen, wiederverwendbare Workflows zu importieren, die in SharePoint Designer 2010 erstellt wurden, und Sie in Code Workflows zur Verwendung in den SharePoint-Websites zu konvertieren.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen eines einfachen, wiederverwendbaren Workflows in SharePoint Designer.

- Exportieren des wiederverwendbaren Workflows von SharePoint Designer in eine *wsp* -Datei und in SharePoint.

- Importieren der *wsp* -Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe des Projekts zum Importieren von wiederverwendbaren Workflows.

- Ändern des Workflows durch Hinzufügen von Code.

- Verwenden des importierten Workflows auf einer SharePoint-Website.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Ziel-SharePoint-unter Websites erstellen
 Zuerst erstellen Sie zwei neue SharePoint-unter Websites: eine zum Hosten der wiederverwendbaren Workflows aus SharePoint Designer, eine weitere zum Hosten der konvertierten Workflows.

#### <a name="to-create-sharepoint-subsites"></a>So erstellen Sie SharePoint-unter Websites

1. Wählen Sie in SharePoint Designer 2010 in der Menüleiste **Datei**  >  **neu leere Website** aus.

2. Navigieren Sie im Dialogfeld **neue leere Website** zu einer SharePoint-Website, auf der Sie den Workflow erstellen möchten, oder verwenden Sie den Wert von http://<em>Systemname</em>/, und klicken Sie dann auf die Schaltfläche **OK** .

    Die Startseite wird angezeigt.

3. Wählen Sie im Abschnitt **unter Standorte** die Schaltfläche **neu** aus.

4. Wählen Sie im Dialogfeld **neu** in der Liste im linken Bereich **SharePoint-Vorlagen** aus, und wählen Sie in der Liste im rechten Bereich **Team Site** aus.

5. Ersetzen Sie im Feld **Geben Sie den Speicherort der Website** an die Word **-unter Website** in der URL durch **SPD1**, und wählen Sie dann die Schaltfläche **OK** aus.

    Dadurch wird die neue unter Website in SharePoint Designer geöffnet. Schließen Sie diese Instanz von SharePoint Designer, und kehren Sie zurück zur ersten Instanz (der Standort der obersten Ebene).

6. Wiederholen Sie die Schritte 3-5, um den zweiten unter Standort zu erstellen. ersetzen Sie dieses Mal die Word- **unter Website** im [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] durch **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Erstellen eines wiederverwendbaren Workflows in SharePoint Designer
 Da SharePoint keine wiederverwendbaren Workflows enthält, die Sie für dieses Beispiel verwenden können, erstellen Sie eines. Wenn ein Benutzer in diesem einfachen Workflow eine neue Aufgabe in der Aufgabenliste mit einem bestimmten Titel eingibt, wird die Aufgabe diesem Benutzer zugewiesen.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>So erstellen Sie einen wiederverwendbaren Workflow in SharePoint Designer

1. Wählen Sie im Abschnitt **unter Sites** die **SPD1** -Website aus, um Sie zu ändern.

2. Wählen Sie im Menüband die Schaltfläche wieder **verwendbarer Workflow** aus.

     Der Assistent zum Erstellen von wiederverwendbaren Workflows wird angezeigt.

3. Geben Sie im Feld **Name** den Text **SPD-Aufgaben Workflow** ein.

4. Wählen Sie in der Liste **Inhaltstyp** die Option **Aufgabe** aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Workflow wird im SharePoint Designer-Workflow-Designer geöffnet.

5. Wählen Sie im Workflow-Designer Schritt 1 aus, und wählen Sie dann im Menüband die Schaltfläche **Bedingung** aus.

6. Wählen Sie in der Liste der Bedingungen aus, **ob das aktuelle Element Feld "Value**" ist.

     In diesem Schritt wird eine Bedingung hinzugefügt, die heißt, **Wenn Field den Wert** hat.

7. Wählen Sie im **Feld wenn der Wert "Wert** " ist, den **feldlink** aus.

8. Wählen Sie in der Liste der Werte **Titel** aus.

9. Wählen Sie im **Feld wenn der Wert** Bedingung den Wert " **value** " aus.

10. Geben Sie im Feld **neue Aufgabe** ein.

     Die Condition-Anweisung liest jetzt, **Wenn das aktuelle Element: Title der neuen Aufgabe ist**.

11. Wählen Sie die Zeile unter der Bedingungs Anweisung aus, und wählen Sie dann im Menüband die Schaltfläche **Aktion** aus.

12. Wählen Sie in der Liste der Aktionen die Option **Feld in aktuellem Element festlegen** aus.

13. Wählen Sie in der Aktion **Feld auf Wert festlegen** den **feldlink** aus, und wählen Sie dann in der Liste **zugewiesen zu** aus.

14. Wählen Sie in der Aktion **Feld auf Wert festlegen** den **Wert** Link aus, und wählen Sie dann in der Liste der vorhandenen Benutzer und Gruppen die Option Benutzer aus, der **das Element erstellt** hat.

15. Klicken Sie auf die Schaltfläche **Hinzufügen** , und wählen Sie dann die Schaltfläche **OK** .

     Die action-Anweisung liest nun **festgelegte zugewiesen zu auf Aktuelles Element: "kreatedby**".

## <a name="save-and-deploy-the-reusable-workflow"></a>Speichern und Bereitstellen des wiederverwendbaren Workflows
 Da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nur *wsp* -Dateien importieren kann, müssen Sie den wiederverwendbaren Workflow als *wsp* -Datei speichern und in SharePoint bereitstellen, bevor Sie ihn in importieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Wenn Sie mit dem folgenden Verfahren einen Laufzeitfehler erhalten, müssen Sie das Verfahren in einem System ausführen, das Zugriff auf die SharePoint-Website hat.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>So speichern Sie den wiederverwendbaren Workflow und stellen ihn bereit

1. Wählen Sie oben in SharePoint Designer die Schaltfläche **Speichern** , um den Fortschritt zu speichern, und klicken Sie dann auf die Schaltfläche **veröffentlichen** , um den Workflow auf der **SPD1** SharePoint-Website bereitzustellen.

2. Wählen Sie im Navigationsbereich das Objekt **Workflows** aus.

3. Wählen Sie unter wieder **verwendbarer Workflow** **SPD-Aufgaben Workflow** aus.

4. Wählen Sie im Menüband die Schaltfläche **als Vorlage speichern** aus, um den Workflow als *wsp* -Datei zu speichern.

5. Öffnen Sie die **SPD1** SharePoint-Website in einem Browser, um die *wsp* -Datei in SharePoint anzuzeigen.

6. Wählen Sie auf der Schnellstartleiste den Link **Bibliotheken** aus.

7. Wählen Sie im Abschnitt **Dokument Bibliotheken** den Link **Site Assets** aus.

     Die **SPD-Aufgaben Workflow** Datei wird mit anderen Website Ressourcen aufgelistet.

8. Wählen Sie in der Liste der Dateien den Namen der Datei aus.

9. Klicken Sie im Dialogfeld **Datei Download** auf die Schaltfläche **Speichern** , um die *wsp* -Datei auf Ihrem lokalen System zu speichern.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importieren der wsp-Datei in Visual Studio
 Importieren Sie die *wsp* -Datei in, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] indem Sie ein wiederverwendbares Workflow Projekt importieren. Dieses Projekt konvertiert den Workflow von einem wiederverwendbaren, deklarativen Workflow in einen Code Workflow. Nachdem der Workflow konvertiert wurde, verwenden Sie Code, um sein Verhalten zu ändern.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>So importieren Sie einen Workflow aus einer wsp-Datei und ändern ihn

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Wählen Sie in in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **SharePoint** unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich **Vorlagen** die Option wieder **verwendbare SharePoint 2010-Workflow Vorlage importieren** aus, belassen Sie den Namen des Projekts als **WorkflowImportProject1**, und klicken Sie dann auf die Schaltfläche **OK** .

    Der Assistent zum Anpassen von SharePoint wird angezeigt.

4. Geben Sie auf der Seite **Geben Sie die Website und die Sicherheitsstufe für das Debuggen** an den [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für die zweite SharePoint-unter Website ein, die Sie zuvor erstellt haben: http://<em>Systemname</em>/SPD2.

5. Wählen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **weiter** .

    Weitere Informationen zu Sandkasten-und Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

6. Navigieren Sie auf der Seite **neue Projekt Quelle angeben** zum Speicherort auf dem System, in dem Sie zuvor die *wsp* -Datei gespeichert haben, öffnen Sie die Datei, und klicken Sie dann auf die Schaltfläche **weiter** .

   > [!NOTE]
   > Wählen Sie die Schaltfläche **Fertig** stellen aus, um alle verfügbaren Elemente in der *wsp* -Datei zu importieren.

    Dadurch wird eine Liste der wiederverwendbaren Workflows angezeigt, die zum Importieren verfügbar sind

7. Wählen Sie im Feld **zu importierende Elemente auswählen** den Workflow Workflow der **SPD-Aufgabe** aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

    Nachdem der Import Vorgang abgeschlossen ist, wird ein Projekt mit dem Namen **WorkflowImportProject1** erstellt, das einen Workflow mit dem Namen **SPD_Workflow_TestFT** enthält. In diesem Ordner befindet sich die Definitionsdatei des Workflows *Elements.xml* und die Workflow-Designer-Datei (*. xoml*). Der Designer enthält zwei Dateien: die Regeldatei (. Rules) und die Code-Behind-Datei (entweder *. cs* oder *. vb*, abhängig von der Programmiersprache Ihres Projekts).

8. Löschen Sie in **Projektmappen-Explorer** den Ordner **importierte Dateien** .

9. Löschen Sie *Elements.xml* in der DateiElements.xml`InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. Wählen **Solution Explorer** Sie in Projektmappen-Explorer **WorkflowImportProject1** aus, und wählen Sie dann in der Menüleiste **Projekt**  >  **als Startprojekt festlegen** aus, um **WorkflowImportProject1** als Start Element festzulegen.

     Dadurch wird die Liste sofort angezeigt, wenn Sie das Projekt Debuggen.

11. Da durch die wieder **verwendbare SharePoint 2010-Workflow Vorlage importieren** nicht die Zuordnungs Eigenschaftswerte für den importierten Workflow importiert werden, müssen Sie diese eingeben. Gehen Sie dazu wie folgt vor:

    1. Wählen Sie in **Projektmappen-Explorer** den Knoten **SPD_Workflow_TestFT** aus.

    2. Wählen Sie die Schaltfläche mit den Auslassungs Zeichen (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) neben einer der Listen Eigenschaften aus, z. b. die Eigenschaft **Ziel Liste** .

    3. Geben Sie die fehlenden Werte in den Anpassungs-Assistenten von SharePoint ein, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

12. Wählen Sie die XOML-Datei aus, und wählen Sie dann in der Menüleiste **Ansicht**-  >  **Designer** aus, um den importierten Workflow im Workflow-Designer anzuzeigen.

13. Führen Sie im Knoten **Windows Workflow v 3.0** der **Toolbox** einen der folgenden Schritte aus:

    - Öffnen Sie das Kontextmenü für die **Code** Aktivität, und wählen Sie dann **Kopieren** aus. Öffnen Sie im Workflow-Designer das Kontextmenü für die Zeile unter der **SequenceActivity1** -Aktivität, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie die **Code** -Aktivität aus der **Toolbox** in den Workflow-Designer, und verbinden Sie Sie mit der Zeile unter der **SequenceActivity1** -Aktivität.

      Dadurch wird dem Workflow-Designer eine Aktivität mit dem Namen **CodeActivity1** hinzugefügt. In dieser Aktivität fügen Sie eine Code Aktion hinzu, die eine Ankündigung in der Liste Ankündigungen erstellt, wenn der Benutzer den Workflow startet.

14. Führen Sie einen der folgenden Schritte aus:

    - Doppelklicken Sie auf **CodeActivity1** , um einen Ereignishandler zu generieren und den Code anzuzeigen.

    - Legen Sie im **Eigenschaften** Fenster für **CodeActivity1** den Wert der **ExecuteCode** -Eigenschaft auf **codeActivity_ExecuteCode** fest.

15. Fügen Sie unter den vorhandenen **using** -oder **Imports** -Direktiven Folgendes hinzu:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Ersetzen Sie `codeActivity1_ExecuteCode` durch Folgendes:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Bereitstellen des Projekts und Zuordnen des Workflows
 Führen Sie als nächstes WorkflowImportProject1 aus, um es auf einer SharePoint-Website bereitzustellen, und ordnen Sie dann den Workflow der Aufgabenliste zu, um den geänderten, konvertierten Workflow anzuzeigen und zu testen.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>So stellen Sie das Projekt bereit und ordnen den Workflow zu

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Wählen Sie in die Taste **F5** aus, um das konvertierte Workflow Projekt auszuführen und bereitzustellen.

2. Wählen Sie auf der Schnellstartleiste den Link **Aufgaben** aus, um die Aufgabenliste anzuzeigen.

3. Wählen Sie auf der Registerkarte **Listen Tools** die Schaltfläche **Elemente** aus, und wählen Sie dann die Schaltfläche **Neues Element** aus.

     Das Dialogfeld **Tasks-neues Element** wird geöffnet.

4. Geben Sie im Feld **Titel** den Namen **neue Aufgabe** ein, und klicken Sie dann auf die Schaltfläche **Speichern** .

5. Wählen Sie auf der Registerkarte **Listen Tools** die Schaltfläche **Liste** aus, und klicken Sie dann auf die Schaltfläche **Einstellungen auflisten** .

     Die Seite " **Listen Einstellungen** " wird angezeigt.

6. Wählen Sie im Abschnitt **Berechtigungen und Verwaltung** den Link **Workflow Einstellungen** aus.

     Die Seite **Workflow Einstellungen** wird angezeigt.

7. Wählen Sie den Link **Workflow hinzufügen** aus.

8. Wählen Sie in der Liste **Workflow** den **WorkflowImportProject1-SPD-Workflow Test** aus.

9. Geben Sie im Feld **Name** den Text **SPD-Workflow Test** ein, und klicken Sie dann auf die Schaltfläche **OK** .

10. Wählen Sie in der Schnellstartleiste die Liste **Aufgaben** aus.

11. Wählen Sie den Pfeil neben **neue Aufgabe** aus, und wählen Sie dann in der Liste **Workflows** aus.

12. Wählen Sie im Abschnitt **neuen Workflow starten** den Link für den **SPD-Workflow Test** aus, und klicken Sie dann auf die Schaltfläche **Start** , um den Workflow zu initiieren.

    > [!NOTE]
    > Alternativ können Sie einen Workflow automatisch einer Liste zuordnen, indem Sie den Assistenten für Workflow Einstellungen ausführen und den Workflow auf automatisch zuordnen festlegen.

     Beachten Sie, dass zwei Aktionen vom Workflow ausgeführt werden: Ihr Name wird in der **zugewiesen zu** Spalte der Aufgabe angezeigt, und in der Liste **Ankündigungen** wird eine Ankündigung angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
