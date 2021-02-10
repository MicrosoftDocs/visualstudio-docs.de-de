---
title: Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
description: Debugerweiterungen für die SharePoint-Tools in Visual Studio. Debuggen Sie Erweiterungen für SharePoint-Tools in der experimentellen Instanz oder der regulären Instanz von im Vergleich zu
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b098ac007825745e13481592760be9d2badeb55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948907"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio
  Sie können SharePoint-Tools-Erweiterungen in der experimentellen Instanz oder in der regulären Instanz von Visual Studio debuggen. Wenn Sie Fehler im Verhalten einer Erweiterung beheben müssen, können Sie auch Registrierungswerte ändern, um weitere Fehlerinformationen anzuzeigen und die Ausführung von SharePoint-Befehlen durch Visual Studio zu konfigurieren.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Debuggen von Erweiterungen in der experimentellen Instanz von Visual Studio
 Um Ihre Visual Studio-Entwicklungsumgebung vor versehentlicher Beschädigung durch nicht getestete Erweiterungen zu schützen, bietet das Visual Studio SDK eine Alternative Visual Studio-Instanz, die als *experimentelle Instanz* bezeichnet wird und die Sie zum Installieren und Testen von Erweiterungen verwenden können. Die Entwicklung neuer Erweiterungen wird in der regulären Instanz von Visual Studio vorgenommen, das Debugging und die Ausführung erfolgen dagegen in der experimentellen Instanz. Weitere Informationen finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).

 Wenn Sie die Erweiterung mithilfe eines VSIX-Projekts bereitstellen und es sich bei dem VSIX-Projekt um das Startprojekt in der Lösung handelt, wird die Erweiterung automatisch in der experimentellen Instanz installiert und ausgeführt, wenn Sie die Lösung debuggen. Das Startprojekt ist das Projekt, das beim Debuggen einer Lösung mit mehreren Projekten gestartet wird. Weitere Informationen zum Bereitstellen der Erweiterung mithilfe eines VSIX-Projekts finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 In den folgenden exemplarischen Vorgehensweisen finden Sie Beispiele, die das Debuggen verschiedener Arten von Erweiterungen in der experimentellen Instanz von Visual Studio veranschaulichen:

- [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungs Schritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Exemplarische Vorgehensweise: Abrufen des SharePoint-Client Objektmodells in einer Server-Explorer-Erweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Debugerweiterungen in der regulären Instanz von Visual Studio
 Installieren Sie zunächst die Erweiterung in der regulären Instanz, wenn Sie das Erweiterungsprojekt in der regulären Instanz von Visual Studio debuggen möchten. Fügen Sie dann den Debugger an einen zweiten Visual Studio-Prozess an. Anschließend können Sie die Erweiterung entfernen, damit sie auf dem Entwicklungscomputer nicht mehr geladen wird.

#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung

1. Schließen Sie alle Instanzen von Visual Studio.

2. Öffnen Sie im Buildausgabeordner für das Erweiterungsprojekt die *VSIX* -Datei, indem Sie darauf doppelklicken, oder öffnen Sie das Kontextmenü, und wählen Sie dann **Öffnen**:

3. Wählen Sie im Dialogfeld **Installer für Visual Studio-Erweiterungen** die Edition von Visual Studio aus, in der Sie die Erweiterung installieren möchten, und klicken Sie dann auf die Schaltfläche **Installieren** .

     Visual Studio installiert die Erweiterungs Dateien unter%USERPROFILE%\appdata\local\microsoft\visualstudio\11.0\Extensions \\ *Author* Name \\ *Extension Name* \\ *Version*. Die letzten drei Ordner in diesem Pfad werden aus den `Author` Elementen, `Name` und `Version` in der *Extension. vsixmanifest* -Datei für die Erweiterung erstellt.

4. Nachdem die Erweiterung von Visual Studio installiert wurde, wählen Sie die Schaltfläche **Schließen** aus.

#### <a name="to-debug-the-extension"></a>So debuggen Sie die Erweiterung

1. Öffnen Sie Visual Studio mit Administratorrechten, und öffnen Sie das Erweiterungsprojekt. Die folgenden Schritte beziehen sich auf diese Instanz von Visual Studio als *erste Instanz*.

2. Starten Sie eine weitere Instanz von Visual Studio mit Administratorrechten. Die folgenden Schritte beziehen sich auf diese Instanz von Visual Studio als *zweite Instanz*.

3. Wechseln Sie zur ersten Instanz von Visual Studio.

4. Wählen Sie in der Menüleiste **Debuggen**, **an den Prozess anhängen** aus.

5. Wählen Sie in der Liste **Verfügbare Prozesse** die Option *devenv.exe* aus. In diesem Eintrag wird auf die zweite Instanz von Visual Studio verwiesen. Dies ist die Instanz zum Debuggen der Projekterweiterung.

6. Wählen Sie die Schaltfläche **Anfügen** .

     Das Erweiterungsprojekt wird im Debugmodus ausgeführt.

7. Wechseln Sie zur zweiten Instanz von Visual Studio.

8. Erstellen Sie ein neues SharePoint-Projekt, von dem die Erweiterung geladen wird. Wenn Sie z. b. eine Erweiterung für Projekt Elemente für Listen Definitionen Debuggen, erstellen Sie ein **Listen Definitions** Projekt.

9. Führen Sie die erforderlichen Schritte zum Testen des Erweiterungscodes aus.

10. Schließen Sie die zweite Instanz von Visual Studio, wenn das Debugging der Erweiterung abgeschlossen ist.

#### <a name="to-remove-the-extension"></a>So entfernen Sie die Erweiterung

1. **Wählen Sie** in Visual Studio auf der Menüleiste Extras, **Erweiterungen und Updates** aus.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen den Namen der Erweiterung aus, und klicken Sie dann auf die Schaltfläche **deinstallieren** .

3. Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.

4. Wählen Sie die Schaltfläche **jetzt neu starten** aus, um die Installation abzuschließen.

## <a name="debug-sharepoint-commands"></a>SharePoint-Befehle Debuggen
 Wenn Sie einen SharePoint-Befehl Debuggen möchten, der Teil einer SharePoint-Tools-Erweiterung ist, müssen Sie den Debugger an den *vssphost4.exe* -Prozess anfügen. Hierbei handelt es sich um den 64-Bit-Hostprozess zum Ausführen von SharePoint-Befehlen. Weitere Informationen zu SharePoint-Befehlen und *vssphost4.exe* finden Sie unter " [Aufrufe in die SharePoint-Objekt Modelle](../sharepoint/calling-into-the-sharepoint-object-models.md)".

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>So fügen Sie den Debugger an den Prozess vssphost4.exe an

1. Debuggen Sie die Erweiterung in der experimentellen Instanz von Visual Studio oder in der regulären Instanz von Visual Studio, indem Sie die obigen Anweisungen befolgen.

2. Wählen Sie in der Instanz von Visual Studio, in der Sie den Debugger ausführen, in der Menüleiste **Debuggen**, **an den Prozess anhängen** aus.

3. Wählen Sie in der Liste **Verfügbare Prozesse** die Option *vssphost.exe* aus.

    > [!NOTE]
    > Wenn vssphost.exe nicht in der Liste angezeigt wird, müssen Sie den *vssphost4.exe* Prozess in der Instanz von Visual Studio starten, in der Sie die Erweiterung ausführen. In der Regel führen Sie dazu eine Aktion aus, durch die eine Verbindung von Visual Studio mit der SharePoint-Website auf dem Entwicklungscomputer hergestellt wird. Beispielsweise wird Visual Studio *vssphost4.exe* gestartet, wenn Sie einen Site Verbindungsknoten (einen Knoten, der eine Website-URL anzeigt) unter dem Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** erweitern, oder wenn Sie bestimmte SharePoint-Projekt Elemente, wie z. b. **Listen Instanzen** oder **Ereignis Empfänger** Elemente, einem SharePoint-Projekt hinzufügen.

4. Wählen Sie die Schaltfläche **Anfügen** .

5. Führen Sie in der Instanz von Visual Studio, für die das Debugging durchgeführt wird, die zum Ausführen des Befehls erforderlichen Schritte aus.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Ändern von Registrierungs Werten zum Debuggen von Erweiterungen für SharePoint-Tools
 Wenn Sie eine Erweiterung der SharePoint-Tools in Visual Studio debuggen, können Sie Werte in der Registrierung ändern, um die Problembehandlung für die Erweiterung zu erleichtern. Die Werte sind unter dem **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** Schlüssel vorhanden. Diese Werte sind standardmäßig nicht vorhanden.

 Um die Problembehandlung für Erweiterungen der SharePoint-Tools zu erleichtern, können Sie den Wert von EnableDiagnostics erstellen und festlegen. Dieser Wert wird der folgenden Tabelle beschrieben.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD, der angibt, ob Diagnosemeldungen im **Ausgabe** Fenster angezeigt werden.<br /><br /> Legen Sie diesen Wert auf "1" fest, wenn Diagnosemeldungen angezeigt werden sollen. Wenn keine Meldungen mehr angezeigt werden sollen, legen Sie diesen Wert auf 0 (null) fest, oder löschen Sie den Wert.<br /><br /> Um Nachrichten aus einer SharePoint-Tools-Erweiterung in das **Ausgabe** Fenster zu schreiben, verwenden Sie den SharePoint-Projekt Dienst. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).|

 Wenn die Erweiterung einen SharePoint-Befehl einschließt, können Sie weitere Werte erstellen und festlegen, um die Problembehandlung des Befehls zu erleichtern. In der folgenden Tabelle werden diese Werte beschrieben.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD, der angibt, ob ein Dialogfeld angezeigt werden soll, in dem Sie den Debugger an *vssphost4.exe* anfügen können, sobald er gestartet wird. Dies ist hilfreich, wenn der Befehl, für den das Debugging ausgeführt werden soll, direkt nach dem Start von vssphost.exe ausgeführt wird und die Zeit nicht ausreicht, um den Debugger vor dem Ausführen des Befehls manuell anzufügen. Um das Dialogfeld anzuzeigen, ruft *vssphost4.exe* die-Methode auf, <xref:System.Diagnostics.Debugger.Break%2A> Wenn Sie gestartet wird.<br /><br /> Legen Sie diesen Wert auf 1 fest, um dieses Verhalten zu aktivieren. Legen Sie diesen Wert auf 0 (null) fest, oder löschen Sie den Wert, um dieses Verhalten zu deaktivieren.<br /><br /> Wenn Sie diesen Wert auf 1 festlegen, sollten Sie den hostprocessstartuptimeout-Wert auch erhöhen, um sich genug Zeit zum Anfügen des Debuggers zu verschaffen, bevor Visual Studio erwartet, dass *vssphost4.exe* signalisiert, dass er erfolgreich gestartet wurde.|
|ChannelOperationTimeout|REG_DWORD-Wert (in Sekunden), der angibt, wie lange von Visual Studio auf die Ausführung eines SharePoint-Befehls gewartet wird. Wird der Befehl nicht innerhalb des Zeitlimits ausgeführt, wird eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 120 Sekunden.|
|HostProcessStartupTimeout|REG_DWORD, der die Zeit in Sekunden angibt, die Visual Studio darauf wartet, dass *vssphost4.exe* signalisiert, dass der Vorgang erfolgreich gestartet wurde. Wenn *vssphost4.exe* keinen erfolgreichen Startzeitpunkt signalisiert, wird eine ausgelöst <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> .<br /><br /> Der Standardwert ist 60 Sekunden.|
|MaxReceivedMessageSize|REG_DWORD, der die maximal zulässige Größe von WCF-Nachrichten in Byte angibt, die zwischen Visual Studio und *vssphost4.exe* übermittelt werden.<br /><br /> Der Standardwert ist 1.048.576 Bytes (1 MB).|
|MaxStringContentLength|REG_DWORD, der die maximal zulässige Größe von Zeichen folgen, die zwischen Visual Studio und *vssphost4.exe* übermittelt werden, in Byte angibt.<br /><br /> Der Standardwert ist 1.048.576 Bytes (1 MB).|

## <a name="see-also"></a>Weitere Informationen

- [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
