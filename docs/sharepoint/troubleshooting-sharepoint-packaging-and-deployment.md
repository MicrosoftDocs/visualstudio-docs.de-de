---
title: Problembehandlung bei SharePoint-Paketen und-bereit Stellungen | Microsoft-Dokumentation
description: Verstehen und beheben Sie verschiedene Probleme, die beim Packen und Bereitstellen von SharePoint-Lösungen auftreten können.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 07ce649a22573041768bfc316f65bfcdf7577b98
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95969924"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Problembehandlung bei der SharePoint-Verpackung und-Bereitstellung
  In diesem Thema werden verschiedene Probleme behandelt, die beim Packen und Bereitstellen von SharePoint-Lösungen auftreten können.

## <a name="enable-enhanced-debugging"></a>Erweitertes Debuggen aktivieren
 Für die Diagnose zwischen Visual Studio, SharePoint und anderen Ebenen können Sie den Registrierungsschlüssel "EnableDiagnostics" verwenden und so die Stapelüberwachung anzeigen. Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Projekt Ausgabe zum Lösungspaket hinzufügen
 Die Projektausgabe kann mithilfe des Paket-Designers einem Paket hinzugefügt werden. Vergewissern Sie sich jedoch beim Hinzufügen der Projektausgabe, dass die Plattform des Projekts der Plattform der SharePoint-Lösung entspricht. Es wird empfohlen, für die Assemblys, die Sie auf einem SharePoint-Server bereitstellen möchten, das **beliebige CPU** -Platt Form Ziel zu verwenden. Weitere Informationen finden Sie unter [Seite "kompilieren", Projekt-Designer &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) und [Dialog Feld "Erweiterte Compilereinstellungen" &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Validierungs Warnungen und-Fehler
 Von den SharePoint-Entwicklungstools in Visual Studio werden Validierungsschritte ausgeführt, um die ordnungsgemäße Formatierung des Lösungspakets zu überprüfen. Sie können auch benutzerdefinierte Validierungsschritte für die Funktionen und die Pakete erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von benutzerdefinierten Feature- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Auflösung von Bereitstellungs Konflikten
 Beim Bereitstellen einer SharePoint-Lösung können sich unter Umständen Konflikte ergeben, wenn Elemente auf dem Server den gleichen Namen, die gleiche URL oder die gleiche ID besitzen wie ein Element im Lösungspaket. Sie können die Eigenschaft **Bereitstellungs Konfliktlösung** ändern, um Konflikte für Module, Webparts, Listen Instanzen und Inhaltstypen aufzulösen, zu melden oder zu ignorieren.

 In der folgenden Tabelle werden die Einstellungen für die Eigenschaft **Bereitstellungs Konfliktlösung** veranschaulicht.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|Automatic|Erkennt Konflikte und löst die Konflikte automatisch.|
|Prompt|Erkennt Konflikte und meldet sie dem Entwickler vor dem Lösen der Konflikte.|
|Keine|Konflikte werden nicht erkannt.|

## <a name="differences-between-f5-deployment"></a>Unterschiede zwischen F5-Bereitstellung
 Wenn Sie das SharePoint-Projekt mithilfe von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zum Testen und Debuggen auf dem lokalen SharePoint-Server bereitstellen, werden von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] einige zusätzliche Schritte ausgeführt.

1. Zurücksetzen von Internetinformationsdienste (IIS) während des Bereitstellungsschritts

2. Automatisches Zuordnen von Workflows

3. Festlegen der Funktionsaktivierungsreihenfolge anhand der Hierarchie im Paket-Designer

   Sie können benutzerdefinierte Bereitstellungs Schritte hinzufügen, um das Verhalten von **F5** weiter zu ändern. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Anzeigen der SharePoint-Seite beim Bereitstellen eines visuellen Webparts
 Wird ein visuelles Webpart unter [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] oder [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] im Ordner "Bin" bereitgestellt, dauert es sehr lang, bis die SharePoint-Seite angezeigt wird. Wenn Sie Dateien in einem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Verzeichnis der obersten Ebene (beispielsweise im Verzeichnis "Bin") ändern, wird die gesamte Webanwendung neu kompiliert. Dies kann dazu führen, dass die SharePoint-Seite mit einer Verzögerung von bis zu 25 Sekunden gerendert wird.

### <a name="error-message"></a>Fehlermeldung
 Keine

### <a name="resolution"></a>Lösung
 Führen Sie die folgenden Schritte aus, um dieses Problem zu umgehen:

1. Installieren Sie das Update KB967535 wie im Microsoft-Support Artikel [Korrektur: ein Hotfix ist verfügbar, um zwei Probleme in ASP.net auf IIS 7,0 für Windows Vista und Windows Server 2008 zu beheben](https://support.microsoft.com/help/967535).

2. Fügen Sie der Datei "Web.config" die folgende Zeile hinzu:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Die SharePoint-Projekt Bereitstellung schlägt mit dem Fehler "Fehler beim Extrahieren der CAB-Datei in der Lösung" fehl.
 Wenn der Name eines SharePoint-Projektelements Klammern enthält, schlägt die Projektmappe mit einem Fehler bei der Bereitstellung fehl.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Fehler beim Extrahieren der CAB-Datei in der Projektmappe.

### <a name="resolution"></a>Lösung
 Um dieses Problem zu umgehen, entfernen Sie alle Klammern in den Namen von SharePoint-Projektelementen.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Beim Bereitstellen eines visuellen Webparts auf einer Website in einer anderen Webanwendung tritt ein Fehler auf.
 Wenn Sie ein visuelles Webpart das erste Mal auf einer Website einer anderen Webanwendung als der bereitstellen, auf der es aktuell bereitgestellt ist (durch Ändern der SiteUrl-Eigenschaft des visuellen Webparts), wird ein Fehler ausgegeben.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungsschritt „Lösung hinzufügen“: Eine Funktion mit der ID [#] wurde in dieser Farm bereits installiert. Verwenden Sie das force-Attribut, um die Funktion explizit neu zu installieren.

### <a name="resolution"></a>Lösung
 Dieser Fehler tritt aufgrund des Verfahrens auf, mit dem visuelle Webpartfunktionen in SharePoint zurückgenommen werden. Um das visuelle Webpart erfolgreich bereitzustellen, stellen Sie die Lösung erneut bereit, indem Sie die **F5** -Taste auswählen.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Warnung wird beim Bereitstellen von eingefügten Benutzer Steuerelementen
 Diese Warnung wird ausgegeben, wenn Sie eine SharePoint-Lösung bereitstellen, die Benutzersteuerelemente geschachtelt hat, z. B. ein visuelles Webpart, das ein Benutzersteuerelement enthält, oder ein Benutzersteuerelement, das ein visuelles Webpart oder ein anderes Benutzersteuerelement enthält. Diese Warnung tritt auf, unabhängig davon, ob Sie einem Designer ein Steuerelement hinzufügen, indem Sie es aus der Toolbox ziehen oder die- @Register Direktive in der Quell Ansicht verwenden.

### <a name="error-message"></a>Fehlermeldung
 Warnung 1 Element ' [*Steuerelement Name*] ' ist kein bekanntes Element. Dies kann auftreten, wenn es einen Kompilierungsfehler in der Website gibt, oder die Datei "web.config" fehlt.

### <a name="resolution"></a>Lösung
 Wenn das [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projekt System kein in einem Steuerelement ersteuertes Benutzer Steuerelement kennt, kann es IntelliSense nicht bereitstellen, und es wird die Warnung ausgegeben. Das Projektsystem hat keine Kenntnis von einem geschachtelten Benutzersteuerelement, wenn das Projekt nicht erstellt wird und der Designer nicht geschlossen und erneut geöffnet wird, oder wenn die Option zum automatischen Zurückziehen aktiviert wird, was dazu führt, dass das Benutzersteuerelement nach Debugging von der SharePoint-Struktur zurückgenommen wird.

 Um diese Warnung zu entfernen, erstellen Sie entweder das Projekt und schließen und öffnen den Designer dann erneut, oder deaktivieren Sie für das Projekt die Option zum automatischen Zurückziehen. Deaktivieren Sie hierzu im Dialogfeld Projekteigenschaften auf der Registerkarte **SharePoint** das Kontrollkästchen **nach dem Debuggen automatisch zurückziehen** .

## <a name="see-also"></a>Weitere Informationen

- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)