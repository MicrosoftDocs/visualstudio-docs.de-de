---
title: Debugging von SharePoint-Lösungen | Microsoft-Dokumentation
description: Debuggen Sie SharePoint-Lösungen mit dem Visual Studio-Debugger. Erkunden Sie den Debug-und Bereitstellungs Prozess von F5, debugworkflows und Debugereignis-Ereignis Empfänger.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c0bd1996f5d42561cb2d44879ab702d6b6c4b4f7
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672859"
---
# <a name="debug-sharepoint-solutions"></a>SharePoint-Lösungen Debuggen
  SharePoint-Lösungen können mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers gedebuggt werden. Wenn Sie das Debuggen starten, werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Projektdateien auf dem SharePoint-Server bereitgestellt, und anschließend wird eine Instanz der SharePoint-Website im Webbrowser geöffnet. In den folgenden Abschnitte wird erklärt, wie SharePoint-Anwendungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gedebuggt werden.

- [Debugging aktivieren](#enable-debugging)

- [Debug-und Bereitstellungs Prozess von F5](#f5-debug-and-deployment-process)

- [SharePoint-Projektfunktionen](#sharepoint-project-features)

- [Debuggen von Workflows](#debug-workflows)

- [Debugermerkungsereignisempfänger](#debug-feature-event-receivers)

- [Aktivieren von ehancierten Debuginformationen](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Aktivieren des Debuggings
 Wenn Sie eine SharePoint-Lösung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstmals debuggen, werden Sie in einem Dialogfeld darauf hingewiesen, dass die Datei web.config nicht zum Aktivieren des Debuggens konfiguriert ist. (Die Datei web.config wird erstellt, wenn Sie SharePoint-Server installieren. Weitere Informationen finden Sie unter [Arbeiten mit Web.config Dateien](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)).) Im Dialogfeld können Sie entweder das Projekt ohne Debuggen ausführen oder die web.config Datei ändern, um das Debuggen zu aktivieren. Wenn Sie die erste Option auswählen, wird das Projekt normal ausgeführt. Bei Auswahl der zweiten Option wird die Datei "web.config" für Folgendes konfiguriert:

- Aktivieren der Aufrufliste (`CallStack="true"`)

- Deaktivieren von benutzerdefinierten Fehlern in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- Aktivieren von Kompilierungsdebugging (`<compilation debug="true">`)

  Die resultierende Datei web.config sieht wie folgt aus:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 Um die Änderungen umzukehren und das Debuggen zu deaktivieren, ändern Sie Folgendes [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in der web.config-Datei:

- Deaktivieren der Aufrufliste (`CallStack="false"`)

- Aktivieren von benutzerdefinierten Fehlern in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- Deaktivieren von Kompilierungsdebugging (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>Debug-und Bereitstellungs Prozess von F5
 Wenn Sie das SharePoint-Projekt im Debugmodus ausführen, werden im SharePoint-Bereitstellungsprozess die folgenden Aufgaben ausgeführt:

1. Die anpassbaren Befehle vor der Bereitstellung werden ausgeführt.

2. Es wird eine Weblösungspaketdatei (.wsp) mithilfe von [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]-Befehlen erstellt. Die WSP-Datei enthält alle erforderlichen Dateien und Funktionen. Weitere Informationen finden Sie unter [Übersicht über Lösungen](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Wenn die SharePoint-Lösung eine Farmlösung ist, wird der [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]-Anwendungspool für die angegebene Website-[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] wiederverwendet. In diesem Schritt werden vom [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]-Arbeitsprozess gesperrte Dateien freigegeben.

4. Wenn bereits eine frühere Version des Pakets vorhanden ist, wird die frühere Version der Funktionen und Dateien in der WSP-Datei zurückgenommen. In diesem Schritt werden die Funktionen deaktiviert, das Lösungspaket deinstalliert und anschließend das Lösungspaket auf dem SharePoint-Server gelöscht.

5. Die aktuelle Version der Funktionen und Dateien in der WSP-Datei wird installiert. In diesem Schritt wird die Lösung auf dem SharePoint-Server hinzugefügt und installiert.

6. Für Workflows wird die Workflowassembly installiert. Sie können den Speicherort ändern, indem Sie die Eigenschaft *Assemblyspeicherort* verwenden.

7. Die Funktion des Projekts wird in SharePoint aktiviert, wenn der Gültigkeitsbereich Website oder Web ist. Funktionen in den Gültigkeitsbereichen Farm und WebApplication werden nicht aktiviert.

8. Verknüpft bei Workflows den Workflow mit der SharePoint-Bibliothek,-Liste oder-Website, die Sie im Assistenten zum Anpassen von **SharePoint** ausgewählt haben.

   > [!NOTE]
   > Diese Zuordnung findet nur statt, wenn Sie im Assistenten die Option **Workflow automatisch zuordnen** ausgewählt haben.

9. Die anpassbaren Befehle nach der Bereitstellung werden ausgeführt.

10. Fügt den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Debugger an den [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] Prozess an (*w3wp.exe*). Wenn Sie mit dem Projekttyp die Eigenschaft der *Sandkasten Lösung* ändern können und deren Wert auf **true** festgelegt ist, wird der Debugger an einen anderen Prozess (*SPUCWorkerProcess.exe*) angefügt. Weitere Informationen finden Sie unter [Überlegungen zu Sandkasten Lösungen](../sharepoint/sandboxed-solution-considerations.md).

11. Der JavaScript-Debugger wird gestartet, wenn die SharePoint-Lösung eine Farmlösung ist.

12. Die entsprechende Bibliothek, Liste oder Websiteseite wird im Webbrowser an.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zeigt eine Statusmeldung im Ausgabefenster an, nachdem die einzelnen Aufgaben abgeschlossen wurden. Wenn eine Aufgabe nicht abgeschlossen werden kann, zeigt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine Fehlermeldung im Fenster Fehlerliste an.

## <a name="sharepoint-project-features"></a>SharePoint-Projektfunktionen
 Bei einer Funktion handelt es sich um eine portable und modulare Funktionseinheit, die das Ändern von Websites mithilfe von Websitedefinitionen vereinfacht. Außerdem handelt es sich um ein Paket von [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS)-Elementen, das für einen bestimmten Bereich aktiviert werden kann und das Benutzer beim Ausführen eines bestimmten Ziels oder einer Aufgabe unterstützt. Vorlagen werden als Funktionen bereitgestellt.

 Wenn Sie ein Projekt im Debugmodus ausführen, erstellt der Bereitstellungs Prozess einen Ordner im *Funktions* Verzeichnis unter *%COMMONPROGRAMFILES%\Microsoft Shared\Web Server Extensions\14\Template\Features*. Funktionsnamen haben das Format *Projektname* _Feature *x*, z. b. TestProject_Feature1.

 Der Ordner der Projekt Mappe im Featureverzeichnis enthält eine *Featuredefinitionsdatei* und eine *Workflow Definitions* Datei. In der Featuredefinitionsdatei (Feature.xml) werden die Dateien im Projekt Feature beschrieben. in der Projekt Definitionsdatei (*Elements.xml*) wird die Projektvorlage beschrieben. *Elements.xml* können in **Projektmappen-Explorer** gefunden werden, beim Erstellen des Lösungs Pakets wird jedoch Feature.xml generiert. Weitere Informationen zu diesen Dateien finden Sie unter [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Debuggen von Workflows
 Wenn Sie Workflowprojekte debuggen, fügt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Workflowvorlage (abhängig von deren Typ) einer Bibliothek oder einer Liste hinzu. Sie können dann die Workflowvorlage manuell oder durch Hinzufügen oder Aktualisieren eines Elements starten. Anschließend können Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwenden, um den Workflow zu debuggen.

> [!NOTE]
> Wenn Sie Verweise auf andere Assemblys hinzufügen, stellen Sie sicher, dass diese Assemblys im globalen Assemblycache () installiert sind [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] . Andernfalls tritt bei der Workflowlösung ein Fehler auf. Weitere Informationen zum Installieren von Assemblys finden Sie unter [Manuelles Starten eines Workflows für ein Dokument oder Element](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Der Workflow wird jedoch nicht vom Bereitstellungsprozess gestartet. Der Workflow muss von der SharePoint-Site gestartet werden. Der Workflow kann auch mithilfe einer Clientanwendung wie Microsoft Office Word 2010 oder mithilfe eines gesonderten serverseitigen Codes gestartet werden. Verwenden Sie einen der im **SharePoint-Anpassungs-Assistenten** angegebenen Ansätze.

 Wenn Sie beispielsweise angegeben haben, dass der Workflow manuell gestartet werden kann, starten Sie den Workflow direkt vom Element in der Bibliothek oder der Liste. Weitere Informationen zum manuellen Starten eines Workflows finden Sie unter [Manuelles Starten eines Workflows für ein Dokument Element](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Debugermerkungsereignisempfänger
 Wenn Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-SharePoint-Anwendung ausführen, werden deren Funktionen standardmäßig automatisch auf dem SharePoint-Server aktiviert. Dies verursacht jedoch Probleme, wenn Sie Funktions Ereignis Empfänger Debuggen, denn wenn eine Funktion durch aktiviert wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wird Sie in einem anderen Prozess als der Debugger ausgeführt. Dies bedeutet, dass einige Debugfunktionen, z. B. Haltepunkte, nicht ordnungsgemäß funktionieren.

 Um die automatische Aktivierung der Funktion in SharePoint zu deaktivieren und das ordnungsgemäße Debuggen von Funktions Ereignis Empfängern zuzulassen, legen Sie den Wert der **aktiven Bereitstellungs Konfigurations** Eigenschaft des Projekts auf **keine Aktivierung** vor dem Debuggen fest. Wenn Sie Ihre SharePoint-Anwendung dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuggen, aktivieren Sie die Funktion manuell in SharePoint. Um die Funktion zu aktivieren, öffnen Sie das Menü **Website Aktionen** in SharePoint, wählen Sie **Website Einstellungen** aus, wählen Sie den Link **Website Features verwalten** aus, und klicken Sie dann neben der Funktion auf die Schaltfläche **aktivieren** , um das Debuggen fortzusetzen.

## <a name="enable-enhanced-debugging-information"></a>Erweiterte Debuginformationen aktivieren
 Aufgrund der manchmal komplexen Interaktionen zwischen dem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Prozess (devenv.exe), dem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Host Prozess (*vssphost4.exe*), SharePoint und der WCF-Ebene kann die Diagnose von Fehlern, die beim Aufbau, bei der Bereitstellung usw. auftreten, eine Herausforderung darstellen. Um Unterstützung beim Beheben solcher Fehler zu erhalten, können Sie erweiterte Debuginformationen aktivieren. Wechseln Sie hierzu in die Windows-Registrierung zum folgenden Registrierungsschlüssel:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Wenn der Wert "EnableDiagnostics" **REG_DWORD** nicht bereits vorhanden ist, erstellen Sie ihn manuell. Legen Sie für den Wert "EnableDiagnostics" den Wert "1" fest.

 Wenn dieser Schlüsselwert auf 1 festgelegt wird, werden Stapel Überwachungsinformationen im Fenster **Ausgabe** angezeigt, wenn Projekt Systemfehler auftreten, während Sie in Ausführen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Legen Sie "EnableDiagnostics" wieder auf 0 fest oder löschen ihn, um erweiterte Debuginformationen zu deaktivieren.

 Weitere Informationen zu anderen SharePoint-Registrierungs Schlüsseln finden Sie unter [Debugerweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md)
