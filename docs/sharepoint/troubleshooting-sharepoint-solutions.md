---
title: Problembehandlung bei SharePoint-Lösungen | Microsoft-Dokumentation
description: Sehen Sie sich an, welche Probleme oder Warnungen auftreten können, wenn Sie SharePoint-Lösungen mit dem Visual Studio-Debugger Debuggen.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9ef5e7d47f72b82e7a8fab52cc2f1f8716c83bf
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970286"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Problembehandlung bei SharePoint-Lösungen
  Die folgenden Probleme oder Warnungen können auftreten, wenn SharePoint-Lösungen mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers debuggt werden. Weitere Informationen finden Sie unter [Debuggen von SharePoint 2007-Workflow Lösungen](/previous-versions/bb386166(v=vs.100)).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Tokeneinschränkungen in visuellen Sandkasten-Webparts
 Visuelle Webparts in Sandkastenlösungen können Standardtokens wie $SPUrl, die die SharePoint-Laufzeit unterstützt, nicht verarbeiten. Daher wird die URL nicht ausgelöst, und Sie können den Inhalt nicht in der Entwurfsansicht im visuellen Webpartdesigner anzeigen, wenn Sie wie im folgenden Beispiel in einem Skriptelement direkt auf ihn verweisen:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Um diese Einschränkung zu umgehen und das Token aufzulösen, verweisen Sie mithilfe von Literalen darauf:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Zeichen Einschränkungen in Namen von Projekten und Projekt Elementen
 Namen von Projekten und Projektelementen dürfen nur Zeichen enthalten, die in einem Bereitstellungspfad in SharePoint 2010 gültig sind. Andere Zeichen sind nicht zulässig.

### <a name="error-message"></a>Fehlermeldung
 Fehlermeldung "ungültige Zeichen".

### <a name="resolution"></a>Lösung
 Verwenden Sie für Namen von SharePoint-Projekte und -Projektelemenen nur die folgenden Zeichen:

- Alphanumerische ASCII-Zeichen

- LeerZchn

- Punkt (.)

- Komma (,)

- Unterstrich (_)

- Bindestrich (-)

- Umgekehrter Schrägstrich (\\)

  Wenn ein Projekt verpackt wird, überprüft eine Validierungsregel, ob die Eigenschaft „Bereitstellungspfad“ bei jeder Datei, die bereitgestellt wird, nur diese gültigen Zeichen enthält.

## <a name="errors-when-creating-custom-fields"></a>Fehler beim Erstellen von benutzerdefinierten Feldern
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden benutzerdefinierte Felder in XML definiert. Fehler können auftreten, wenn ein Feld nicht definiert ist oder mit einem bestimmten Format auf das Feld verwiesen wird.

### <a name="error-message"></a>Fehlermeldung
 Fehlermeldung "ungültige Zeichen" zum Zeitpunkt der Paket Erstellung.

### <a name="resolution"></a>Lösung
 Die ID für eine Felddefinition muss eine GUID sein, die von geschweiften Klammern umgeben ist, wie im folgenden Beispiel dargestellt:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Wie im folgenden Beispiel gezeigt, muss ein Feldverweis in einem Inhaltstyp mit dem leeren Element Format () definiert werden \<FieldRef /> , nicht mithilfe von Start-/Endelementen ( \<FieldRef> \</FieldRef> ):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Wenn der XML-Quellcode für das Feld falsch formatiert ist, eine ungültige XML-Datei ist oder ein anderes ein Problem aufweist, tritt der Fehler "Cannot parse file" auf.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Neue nicht englische Site Definitionen werden nach der Bereitstellung nicht auf der Seite Website Erstellung angezeigt.
 Nachdem Sie eine Standort Definition mithilfe einer nicht englischen Version von erstellt und bereitgestellt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] haben (d. h. eine Version mit einem [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] anderen Gebiets Schema als 1033), wird die Registerkarte **SharePoint-Anpassungen** nicht im Feld **Vorlagen Auswahl** angezeigt, und die neue Website Vorlage wird nicht auf der Seite **neue SharePoint-Website** angezeigt.

### <a name="error-message"></a>Fehlermeldung
 Keine

### <a name="resolution"></a>Lösung
 Dieses Problem tritt aufgrund eines falschen Werts in der **Pfad** -Eigenschaft für die webtemp-Site Definitions Konfigurationsdatei auf, z. b. *webtemp_SiteDefinitionProject1.xml*. Ändern Sie in der Eigenschaft **Pfad** für die webtemp-Datei, die sich unter dem **Bereitstellungs Speicherort** befindet, 1033 in das entsprechende Gebiets Schema [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Soll also beispielsweise das Gebietsschema für Japanisch verwendet werden, ändern Sie den Wert zu "1041". Weitere Informationen finden Sie unter [Von Microsoft zugewiesene Gebietsschemabezeichner (LCIDs)](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Fehler tritt auf, wenn ein Workflow Projekt auf einem sauberen System bereitgestellt wird.
 Dieses Problem tritt auf, wenn ein Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf einem unveränderten System bereitgestellt wird. Ein unverändertes System ist ein Computer mit einer neuen Installation von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und SharePoint, aber ohne bereitgestellte Workflowprojekte.

### <a name="error-message"></a>Fehlermeldung
 Die SharePoint-Liste kann nicht gefunden werden: Workflowverlauf.

### <a name="resolution"></a>Lösung
 Dieser Fehler tritt aufgrund einer fehlenden Workflowverlaufsliste auf. Da es sich bei der Entwicklungsumgebung um ein unverändertes System handelt, sind keine Workflows bereitgestellt, und die Workflowverlaufsliste ist noch nicht vorhanden. Öffnen Sie den Workflow-Assistenten, um dieses Problem zu beheben. Dadurch wird die Workflowverlaufsliste erstellt.

##### <a name="to-reenter-the-workflow-wizard"></a>So starten Sie den Workflow-Assistenten erneut

1. Wählen Sie in **Projektmappen-Explorer** den Knoten Workflow aus.

2. Wählen Sie im Fenster **Eigenschaften** die Schaltfläche mit den Auslassungs Punkten (...) für jede Eigenschaft mit der Schaltfläche mit den Auslassungs Punkten aus.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Der Benutzer muss die Anwendungsseite im Browser aktualisieren, um das aktualisierte Bild anzuzeigen.
 Wenn Sie eine SharePoint-Lösung mit einer Anwendungsseite debuggen, die ein Steuerelement mit einem Bild (beispielsweise ein [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]-Bild-Steuerelement) enthält, muss die Seite im Browser aktualisiert werden, damit am Bild vorgenommene Änderungen angezeigt werden.

## <a name="error-the-site-location-is-not-valid"></a>Fehler: der Speicherort der Site ist ungültig.
 Dieses Problem kann auftreten, wenn [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] nicht installiert ist. Dies kann auch vorkommen, wenn Sie keinen Administrator Zugriff auf die SharePoint-Website haben, die im **SharePoint-Anpassungs-Assistenten** angegeben ist.

### <a name="error-message"></a>Fehlermeldung

- Der Speicherort der SharePoint-Site ist nicht gültig.

### <a name="resolution"></a>Lösung

- Installieren von [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Stellen Sie sicher, dass Sie über Administratorzugriff auf die SharePoint-Website verfügen. Weitere Informationen finden Sie [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] im Online Artikel [zuweisen oder Entfernen von Administratoren von Dienst Anwendungen in SharePoint Server](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Das Website Lösch-Webereignis tritt im Ereignis Empfänger Projekt nicht auf.
 Wenn Sie ein Ereignisempfängerprojekt erstellen und Sie bestimmte Webereignisse auswählen, z. B. "eine Website wird gelöscht", tritt das Ereignis nie ein.

### <a name="error-message"></a>Fehlermeldung
 Keine

### <a name="resolution"></a>Lösung
 Dieses Problem tritt auf, da der Funktionsbereich „Site“ sein muss, um Ereignisse auf Websiteebene zu behandeln, der Standardfunktionsbereich für Ereignisempfängerprojekte ist jedoch „Internet“. Die betroffenen Webereignisse sind:

- Eine Website wird gelöscht (WebDeleting)

- Eine Website wurde gelöscht (WebDeleted)

- Eine Website wird verschoben (WebMoving)

- Eine Website wurde verschoben (WebMoved)

  Zum Beheben des Problems ändern Sie den Funktionsbereich des Ereignisempfängers wie folgt:

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>So ändern Sie den Funktionsbereich des Ereignisempfängers

1. Öffnen Sie in **Projektmappen-Explorer** die *. Feature* -Datei des Ereignis Empfängers im **Funktions-Designer** , indem Sie entweder auf die Datei doppelklicken oder das Kontextmenü öffnen und dann **Öffnen** auswählen.

2. Wählen Sie den Pfeil neben **Bereich** aus, und wählen Sie dann in der angezeigten Liste **Site** aus.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Bereitstellungs Fehler wird angezeigt, nachdem der Name eines Bezeichners in einem Business Data Connectivity-Modell-Projekt geändert wurde.
 Dieses Problem tritt auf, wenn Sie den Bezeichnernamen einer Entität in einem Business Data Connectivity-Modell (BDC-Modell) ändern, und dann versuchen, die Projektmappe bereitzustellen.

### <a name="error-messages"></a>Fehlermeldungen

- \<*model name*> hat folgende externe Inhaltstyp-Aktivierungs Fehler...

- Der IMetadataObject-Wert mit dem Namen ' \<*model name*> ' weist einen Wert im Feld ' Name ' auf, der dupliziert wird...

### <a name="resolution"></a>Lösung
 Um dieses Problem zu beheben, löschen Sie das Modell manuell, und stellen Sie anschließend die Projektmappe erneut bereit.  Sie können das Modell mit einem der folgenden Tools löschen:

- SharePoint 2010-Zentraladministration. Weitere Informationen finden Sie auf der Microsoft TechNet-Website unter [BDC-Modellverwaltung](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) .

- Windows PowerShell. Sie können das Modell löschen, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben: **Remove-spbusinessdatacatalogmodel**. Weitere Informationen finden Sie auf der Microsoft TechNet-Website unter [Allgemeine Cmdlets (SharePoint Server 2010)](/powershell/module/sharepoint-server) .

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Wenn Sie versuchen, ein visuelles Webpart in SharePoint anzuzeigen, tritt ein Fehler auf.
 Dieses Problem tritt auf, wenn die **path** -Eigenschaft des Benutzer Steuer Elements nicht mit der Zeichenfolge "ControlTemplates \\ " beginnt.

### <a name="error-messages"></a>Fehlermeldungen

- Die Datei "/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* . ascx" ist nicht vorhanden.

- Serverfehler in Anwendung '/'.

### <a name="resolution"></a>Lösung

##### <a name="to-resolve-this-issue"></a>Lösung

1. Wählen Sie in **Projektmappen-Explorer** die Benutzer Steuerelement Datei mit der Dateinamenerweiterung *. ascx* aus.

2. Wählen Sie in der Menüleiste **Ansicht**  >  **Eigenschaften Fenster** aus.

3. Erweitern Sie im Fenster **Eigenschaften** den Knoten **Bereitstellungs Speicherort** .

4. Stellen Sie sicher, dass der Wert der **path** -Eigenschaft mit der Zeichenfolge "ControlTemplates \\ " beginnt.

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Der Fehler tritt auf, wenn ein importierter, wiederverwendbarer Workflow mit einem Aufgaben Formularfeld ausgeführt wird.
 Dieses Problem tritt auf, wenn Sie einen Workflow importieren, der ein Aufgabenformular enthält, das über ein Feld verfügt, und dann den neuen Workflow auf dem gleichen System ausführen, aus dem Sie ihn importiert haben.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungs Schritt "Funktionen aktivieren": das in der Funktion [*GUID*] definierte Feld mit der ID [*GUID*] wurde in der aktuellen Website Sammlung oder einer unter Website gefunden.

### <a name="resolution"></a>Lösung
 Dieser Fehler ist das Ergebnis von Feld-ID-Konflikten, die auftreten, weil das Projekt "wiederverwendbares Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] keine Aufgaben Formularfeld-IDs ändert. Wenn Sie einen importierten Workflow auf dem gleichen Server bereitstellen, der den ursprünglichen Workflow enthält, treten Feld-ID-Konflikte auf.

 Um dieses Problem zu beheben, verwenden Sie die Funktion „Suchen und Ersetzen“, um den Wert des Feld-ID-Attributs in allen importierten Workflowdateien zu ändern.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Beim Ausführen einer umbenannten importierten Listen Instanz wird ein Fehler angezeigt
 Dieses Problem tritt auf, wenn Sie eine importierte Listeninstanz umbenennen und diese dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausführen.

### <a name="error-message"></a>Fehlermeldung
 Buildfehler: Fehler im Bereitstellungs Schritt "Funktionen aktivieren": die Datei "template\features \\ [*Import Project*<em>Feature</em>*Name*] \files\lists \\ [*Old*<em>List Name</em>]" \Schema.xml nicht vorhanden.

### <a name="resolution"></a>Lösung
 Wenn Sie eine Listeninstanz importieren, wird der Datei "Elements.xml" der Listeninstanz ein Attribut namens "CustomSchema" hinzugefügt. Die Datei "Elements.xml" schließt den Pfad einer benutzerdefinierten Datei "schema.xml" für die Listeninstanz ein. Wenn Sie die Listeninstanz in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umbenennen, ändert sich der Bereitstellungspfad für die benutzerdefinierte Datei "schema.xml", der Pfadwert des CustomSchema-Attributs wird jedoch nicht aktualisiert. Daher kann die Listen Instanz die *schema.xml* Datei im alten Pfad, der vom CustomSchema-Attribut angegeben wird, nicht finden, wenn die Funktion aktiviert wird.

 Um dieses Problem zu beheben, aktualisieren Sie den Pfad des Bereitstellungs Speicher Orts der *schema.xml* Datei im CustomSchema-Attribut.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Die SharePoint-Debugsitzung wurde von IIS beendet.
 Dieses Problem tritt auf, wenn Sie in einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Lösung einen Haltepunkt festlegen, die **F5** -Taste drücken, um Sie auszuführen, und dann an einem Haltepunkt verbleiben, der länger als 90 Sekunden ist.

### <a name="error-message"></a>Fehlermeldung
 Der Webserverprozess, der debuggt wurde, wurde von Internetinformationsdienste (Internet Information Services, IIS) beendet. Sie können dieses Problem vermeiden, indem Sie die Ping-Einstellungen des Anwendungspools in den Internetinformationsdiensten konfigurieren. Weitere Informationen finden Sie in der Hilfe.

### <a name="resolution"></a>Lösung
 Standardmäßig wartet der IIS-Anwendungspool 90 Sekunden auf die Antwort einer Anwendung, bevor diese geschlossen wird. Dieser Prozess wird als "Pingen" der Anwendung bezeichnet. Um dieses Problem zu beheben, können Sie entweder die Wartezeit verlängern oder das Pingen der Anwendung komplett deaktivieren.

##### <a name="to-access-the-iis-app-pool-settings"></a>So greifen Sie auf die IIS-Einstellungen für den Anwendungspool zu

1. Öffnen Sie IIS-Manager.

2. Erweitern Sie im Bereich **Verbindungen** den Knoten SharePoint-Server, und wählen Sie dann den Knoten **Anwendungs Pools** aus.

3. Wählen Sie auf der Seite **Anwendungs Pools** den SharePoint-Anwendungs Pool (in der Regel "SharePoint-80") aus, und wählen Sie dann im **Aktions** Bereich den Link **Erweiterte Einstellungen** aus.

4. Um die Wartezeit vor dem IIS-Timeout zu erhöhen, ändern Sie den Wert für **Maximale Ping-Antwortzeit (Sekunden)** in einen Wert, der größer als 90 Sekunden ist.

5. Um das Pingen von IIS zu deaktivieren, legen Sie **Ping aktiviert** auf **false** fest.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Automatisches zurückziehen verlässt die verwaiste Listen Instanz in SharePoint.
 Dieses Problem tritt auf, wenn Sie die folgenden Schritte ausführen:

1. Erstellen einer Listendefinition, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine Listeninstanz hat.

2. Drücken Sie die Taste **F5** , um die Projekt Mappe auszuführen.

3. Beenden des Debugvorgangs oder Schließen der SharePoint-Website.

4. Erneutes Öffnen der SharePoint-Website und Öffnen der Listeninstanz.

### <a name="error-message"></a>Fehlermeldung
 Serverfehler in Anwendung '/'.

### <a name="resolution"></a>Lösung
 Dies geschieht, weil die Funktion zum automatischen Zurückziehen die Lösung zurückzieht, nachdem Sie eine Debugsitzung einer SharePoint-Lösung geschlossen haben. Die Zurückziehen löscht die Listendefinition aus SharePoint, jedoch nicht die Instanz der Liste. Die zugrunde liegende Listendefinition ist für die Listeninstanz erforderlich.

 Um dieses Problem zu beheben, stellen Sie die Projekt Mappe bereit, indem Sie in der Menüleiste die Option **Build** bereitstellen auswählen  >  **Deploy**. (Debuggen Sie die Projekt Mappe nicht, indem Sie die Taste **F5** drücken.) Löschen Sie dann die Listen Instanz in SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Die ursprüngliche SharePoint-Lösung wird durch eine exportierte Version ersetzt.
 Wenn Sie eine SharePoint-Lösung exportieren, die Projektmappe in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importieren und dann wieder auf der gleichen Website bereitstellen, von der sie exportiert wurde, wird die ursprüngliche SharePoint-Lösung ersetzt. Dieses Problem tritt nicht auf, wenn Sie die Projektmappe auf einem Server bereitstellen, auf dem die ursprüngliche Projektmappe nicht aktiviert ist.

### <a name="error-message"></a>Fehlermeldung
 Keine

### <a name="resolution"></a>Lösung
 Um zu verhindern, dass eine Projektmappe auf der Website überschreiben wird, von der sie exportiert wurde, ändern Sie die GUIDS der SolutionID und der Funktions-IDs aller importierten Funktionen im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekt.

## <a name="error-appears-when-debugging-starts"></a>Fehler beim Starten des Debuggens
 Wenn Sie das Debuggen einer SharePoint-Lösung in Visual Studio starten, erhalten Sie eine Fehlermeldung, dass Visual Studio die Datei "Web.config" nicht laden konnte, da der angegebene Schlüssel nicht im Wörterbuch vorhanden ist.

### <a name="error-message"></a>Fehlermeldung
 Die Konfigurationsdatei "Web.config" konnte nicht geladen werden. Überprüfen Sie die Datei auf falsch formatierte XML-Elemente, und versuchen Sie es erneut. Fehler: Der angegebene Schlüssel war im Wörterbuch nicht vorhanden.

### <a name="resolution"></a>Lösung
 Um dieses Problem zu beheben, stellen Sie sicher, dass der Site-URL-Eigenschaftswert des SharePoint-Projekts in Visual Studio eine Entsprechung für die URL findet, die der Standardzone für die alternativen Zugriffszuordnungen der Webanwendung zugewiesen wurde. Sie können diesen Fehler nicht beheben, indem Sie eine andere Zone, z. B. Intranet, für die URL verwenden. Die Site-URL für das Projekt und die URL in der Standardzone müssen übereinstimmen. Öffnen Sie zum Zugreifen auf Alternative Zugriffs Zuordnungen das Dienstprogramm SharePoint 2010-zentral Administration, wählen Sie den Link **Anwendungs Verwaltung** aus, und klicken Sie dann unter **Webanwendungen** auf den Link **alternativen Zugriffs Zuordnungen konfigurieren** . Weitere Informationen finden Sie unter [Erstellen von Zonen für Webanwendungen](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Weitere Informationen

- [Problembehandlung bei der SharePoint-Verpackung und-Bereitstellung](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md)