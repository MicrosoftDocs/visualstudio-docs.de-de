---
title: ClickOnce-Sicherheit und-Bereitstellung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Visual Studio-Unterstützung für ClickOnce, eine Bereitstellungs Technologie, mit der Sie selbst aktualisierbare Windows-basierte Anwendungen erstellen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8bb0bdeae09f22a2b45e3029fbc9097c00911d2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930017"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce-Sicherheit und -Bereitstellung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist eine Bereitstellungs Technologie, mit der Sie selbst Aktualisier Ende Windows-basierte Anwendungen erstellen können, die mit minimaler Benutzerinteraktion installiert und ausgeführt werden können. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet vollständige Unterstützung für das Veröffentlichen und Aktualisieren von Anwendungen, die mit ClickOnce-Technologie bereitgestellt werden, wenn Sie Ihre Projekte mit Visual Basic und Visual c# entwickelt haben Weitere Informationen zum Bereitstellen von Visual C++ Anwendungen finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Bereitstellung wird drei Hauptprobleme bei der Bereitstellung überschreiten:

- **Schwierigkeiten beim Aktualisieren von Anwendungen.** Bei der Microsoft Windows Installer-Bereitstellung kann der Benutzer jedes Mal, wenn eine Anwendung aktualisiert wird, ein Update, eine MSP-Datei installieren und auf das installierte Produkt anwenden. mit der- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung können Sie Updates automatisch bereitstellen. Nur die Teile der Anwendung, die geändert wurden, werden heruntergeladen, und anschließend wird die vollständig aktualisierte Anwendung aus einem neuen parallelen Ordner neu installiert.

- **Auswirkung auf den Computer des Benutzers.** Bei der Windows Installer-Bereitstellung basieren Anwendungen häufig auf gemeinsam genutzten Komponenten, mit dem Potenzial von Versions Konflikten. bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung ist jede Anwendung eigenständig und kann andere Anwendungen nicht beeinträchtigen.

- **Sicherheits Berechtigungen.** Windows Installer Bereitstellung erfordert administrative Berechtigungen und ermöglicht nur eine eingeschränkte Benutzer Installation. mithilfe der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung können Benutzer ohne Administratorrechte nur die Code Zugriffs Sicherheits Berechtigungen installieren, die für die Anwendung erforderlich sind.

  In der Vergangenheit haben diese Probleme manchmal dazu geführt, dass Entwickler Webanwendungen anstelle von Windows-basierten Anwendungen erstellen konnten, sodass Sie eine umfassende Benutzeroberfläche für eine einfache Installation aufopferungs. Mithilfe von Anwendungen, die mit bereitgestellt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] werden, können Sie über das Beste beider Technologien verfügen.

## <a name="what-is-a-clickonce-application"></a>Was ist eine ClickOnce-Anwendung?
 Eine- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ist eine beliebige Windows Presentation Foundation (*. XBAP*), Windows Forms (*. exe*), Konsolenanwendung (*. exe*) oder eine Office-Projekt Mappe (*. dll*), die mithilfe der-Technologie veröffentlicht wurde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Sie können eine- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf drei verschiedene Arten veröffentlichen: über eine Webseite, über eine Netzwerkdatei Freigabe oder über Medien wie eine CD-ROM. Eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung kann auf dem Computer des Endbenutzers installiert und lokal ausgeführt werden, auch wenn der Computer offline ist, oder Sie kann in einem reinen Online Modus ausgeführt werden, ohne dass auf dem Computer des Endbenutzers eine permanente Installation erfolgt. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können selbst aktualisiert werden. Sie können nach neueren Versionen suchen, sobald Sie verfügbar werden, und automatisch alle aktualisierten Dateien ersetzen. Der Entwickler kann das Aktualisierungsverhalten festlegen. Der Netzwerkadministrator kann ebenfalls Aktualisierungsstrategien steuern und eine Aktualisierung z.B. als obligatorisch kennzeichnen. Updates können auch vom Endbenutzer oder von einem Administrator auf eine frühere Version zurückgesetzt werden. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

 Da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen isoliert sind, kann das Installieren oder Ausführen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung vorhandene Anwendungen nicht unterbrechen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen sind eigenständig. Jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird in einem sicheren Cache pro Benutzer und pro Anwendung installiert und ausgeführt. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen werden im Internet oder in intranetsicherheitszonen ausgeführt. Falls notwendig, kann die Anwendung erhöhte Sicherheitsberechtigungen anfordern. Weitere Informationen finden Sie unter [sichere ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

## <a name="how-clickonce-security-works"></a>Funktionsweise der ClickOnce-Sicherheit
 Die Kern [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Sicherheit basiert auf Zertifikaten, Richtlinien für die Code Zugriffssicherheit und der ClickOnce-Vertrauensstellungs Aufforderung.

### <a name="certificates"></a>Zertifikate
 Authenticode-Zertifikate werden verwendet, um die Echtheit des Herausgebers der Anwendung zu überprüfen. Durch die Verwendung von Authenticode für die Anwendungs Bereitstellung hilft ClickOnce dabei, ein schädliches Programm daran zu hindern, sich selbst als ein legitimer Programm aus einer etablierten vertrauenswürdigen Quelle darzustellen. Optional können Zertifikate auch zum Signieren der Anwendungs-und Bereitstellungs Manifeste verwendet werden, um nachzuweisen, dass die Dateien nicht manipuliert wurden. Weitere Informationen finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md). Zertifikate können auch verwendet werden, um Client Computer so zu konfigurieren, dass Sie eine Liste der vertrauenswürdigen Herausgeber aufweisen. Wenn eine Anwendung von einem vertrauenswürdigen Herausgeber stammt, kann Sie ohne Benutzereingriff installiert werden. Weitere Informationen finden Sie unter [Übersicht über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).

### <a name="code-access-security"></a>Codezugriffssicherheit
 Mit der Code Zugriffssicherheit wird der Zugriff von Code auf geschützte Ressourcen beschränkt. In den meisten Fällen können Sie die Zonen "Internet" oder "Lokales Intranet" auswählen, um die Berechtigungen einzuschränken. Verwenden Sie die Seite **Sicherheit** im **Projekt-Designer** , um die für die Anwendung geeignete Zone anzufordern. Sie können auch Anwendungen mit eingeschränkten Berechtigungen debuggen, um die Endbenutzer Funktionen zu emulieren. Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md).

### <a name="clickonce-trust-prompt"></a>ClickOnce-Vertrauensaufforderung
 Wenn die Anwendung mehr Berechtigungen anfordert, als die Zone zulässt, kann der Endbenutzer aufgefordert werden, eine Entscheidung über die Vertrauenswürdigkeit zu treffen. Der Endbenutzer kann entscheiden, ob ClickOnce-Anwendungen, wie z. b. Windows Forms Anwendungen, Windows Presentation Foundation Anwendungen, Konsolen Anwendungen, XAML-Browser Anwendungen und Office-Projektmappen vertrauenswürdig sind. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren des Verhaltens der ClickOnce-Vertrauens Aufforderung](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="how-clickonce-deployment-works"></a>Wie funktioniert die ClickOnce-Bereitstellung?
 Die grundlegende [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs Architektur basiert auf zwei XML-Manifest-Dateien: einem Anwendungs Manifest und einem Bereitstellungs Manifest. Die Dateien werden verwendet, um zu beschreiben, wo die ClickOnce-Anwendungen installiert werden, wie Sie aktualisiert werden und wann Sie aktualisiert werden.

### <a name="publish-clickonce-applications"></a>Veröffentlichen von ClickOnce-Anwendungen
 Das Anwendungs Manifest beschreibt die Anwendung selbst. Dies schließt die Assemblys, die Abhängigkeiten und Dateien aus, aus denen die Anwendung besteht, die erforderlichen Berechtigungen und den Speicherort, an dem Updates verfügbar sein werden. Der Anwendungsentwickler Ersteller das Anwendungs Manifest mithilfe des Veröffentlichungs-Assistenten in Visual Studio oder der Manifest Generation and Editing Tool (*Mage.exe*) in der [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

 In dem Bereitstellungsmanifest wird die Bereitstellung der Anwendung beschrieben. Dies umfasst den Speicherort des Anwendungs Manifests und die Version der Anwendung, die von Clients ausgeführt werden soll.

### <a name="deploy-clickonce-applications"></a>Bereitstellen von ClickOnce-Anwendungen
 Nachdem Sie erstellt wurde, wird das Bereitstellungs Manifest an den Bereitstellungs Speicherort kopiert. Hierbei kann es sich um einen Webserver, eine Dateifreigabe im Netzwerk oder einen Datenträger wie eine CD handeln. Das Anwendungs Manifest und alle Anwendungs Dateien werden ebenfalls an einen Bereitstellungs Speicherort kopiert, der im Bereitstellungs Manifest angegeben ist. Dabei kann es sich um denselben Bereitstellungsspeicherort oder einen anderen Speicherort handeln. Wenn Sie den **Webpublishing-Assistenten** in Visual Studio verwenden, werden die Kopiervorgänge automatisch ausgeführt.

### <a name="install-clickonce-applications"></a>Installieren von ClickOnce-Anwendungen
 Nachdem Sie am Bereitstellungs Speicherort bereitgestellt wurde, können Endbenutzer die Anwendung herunterladen und installieren, indem Sie auf ein Symbol klicken, das die Bereitstellungs Manifest-Datei auf einer Webseite oder in einem Ordner darstellt. In den meisten Fällen wird dem Endbenutzer ein einfaches Dialogfeld angezeigt, in dem der Benutzer aufgefordert wird, die Installation zu bestätigen. Danach wird die Installation fortgesetzt, und die Anwendung wird ohne zusätzlichen Eingriff gestartet. In Fällen, in denen die Anwendung erhöhte Berechtigungen erfordert, oder wenn die Anwendung nicht von einem vertrauenswürdigen Zertifikat signiert ist, wird der Benutzer im Dialogfeld ebenfalls aufgefordert, die Berechtigung zu erteilen, bevor die Installation fortgesetzt werden kann. Obwohl ClickOnce-Installationen pro Benutzer erfolgen, ist möglicherweise eine Berechtigungs Erweiterung erforderlich, wenn erforderliche Komponenten vorhanden sind, für die Administratorrechte erforderlich sind. Weitere Informationen zu erweiterten Berechtigungen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).

 Zertifikate können auf Computer-oder Unternehmensebene als vertrauenswürdig eingestuft werden, damit ClickOnce-Anwendungen, die mit einem vertrauenswürdigen Zertifikat signiert sind, unbeaufsichtigt installiert werden können Weitere Informationen zu vertrauenswürdigen Zertifikaten finden Sie unter [Übersicht über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).

 Die Anwendung kann dem **Startmenü** des Benutzers und der Gruppe "Software" **in der** **Systemsteuerung** hinzugefügt werden. Anders als bei anderen Bereitstellungs Technologien wird dem Ordner " **Programme** " oder der Registrierung nichts hinzugefügt, und für die Installation sind keine Administratorrechte erforderlich.

> [!NOTE]
> Es ist auch möglich, zu verhindern, dass die Anwendung dem **Startmenü** hinzugefügt und die Software Gruppe **hinzugefügt oder entfernt** wird, sodass Sie sich wie eine Webanwendung verhält. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).

### <a name="update-clickonce-applications"></a>Aktualisieren von ClickOnce-Anwendungen
 Wenn die Anwendungsentwickler eine aktualisierte Version der Anwendung erstellen, generieren Sie ein neues Anwendungs Manifest und kopieren Dateien an einen Bereitstellungs Speicherort – in der Regel ein gleich geordneter Ordner in den ursprünglichen Anwendungs Bereitstellungs Ordner. Der Administrator aktualisiert das Bereitstellungs Manifest so, dass es auf den Speicherort der neuen Version der Anwendung verweist.

> [!NOTE]
> Der **Veröffentlichungs-Assistent** in Visual Studio kann verwendet werden, um diese Schritte auszuführen.

 Neben dem Bereitstellungs Speicherort enthält das Bereitstellungs Manifest auch einen Update Speicherort (eine Webseite oder eine Netzwerkdatei Freigabe), bei dem die Anwendung auf aktualisierte Versionen prüft. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Mithilfe von **Veröffentlichungs** Eigenschaften können Sie angeben, wann und wie oft die Anwendung nach Updates suchen soll. Das Aktualisierungs Verhalten kann im Bereitstellungs Manifest angegeben werden, oder es kann mithilfe der APIs als Benutzeroptionen in der Benutzeroberfläche der Anwendung angezeigt werden [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Außerdem können die Eigenschaften zum **Veröffentlichen** verwendet werden, um Updates als obligatorisch zu kennzeichnen oder die Anwendung auf eine frühere Version zurückzusetzen. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

### <a name="third-party-installers"></a>Installationsprogramme von Drittanbietern
 Sie können den ClickOnce-Installer so anpassen, dass Komponenten von Drittanbietern zusammen mit der Anwendung installiert werden. Sie müssen über das verteilbare Paket (exe-oder MSI-Datei) verfügen und das Paket mit einem sprach neutralen Produkt Manifest und einem sprachspezifischen Paket Manifest beschreiben. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).

## <a name="clickonce-tools"></a>ClickOnce-Tools
 In der folgenden Tabelle sind die Tools aufgeführt, die Sie zum generieren, bearbeiten, Signieren und erneuten Signieren der Anwendungs-und Bereitstellungs Manifeste verwenden können.

|Tool|BESCHREIBUNG|
|----------|-----------------|
|[Seite "Sicherheit", Projekt-Designer](../ide/reference/security-page-project-designer.md)|Signiert die Anwendungs-und Bereitstellungs Manifeste.|
|[Seite "Veröffentlichen", Projekt-Designer](../ide/reference/publish-page-project-designer.md)|Generiert und bearbeitet die Anwendungs-und Bereitstellungs Manifeste für Visual Basic-und Visual c#-Anwendungen.|
|[*Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Generiert die Anwendungs-und Bereitstellungs Manifeste für Visual Basic-, Visual c#-und Visual C++-Anwendungen.<br /><br /> Signiert und signiert die Anwendungs-und Bereitstellungs Manifeste neu.<br /><br /> Kann in Batch Skripts und an der Eingabeaufforderung ausgeführt werden.|
|[*MageUI.exe* (Manifest Generation and Editing Tool, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Generiert und bearbeitet die Anwendungs-und Bereitstellungs Manifeste.<br /><br /> Signiert und signiert die Anwendungs-und Bereitstellungs Manifeste neu.|
|[GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md)|Generiert das Anwendungs Manifest.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [MSBuild-Referenz](../msbuild/msbuild-reference.md).|
|[GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md)|Generiert das Bereitstellungs Manifest.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [MSBuild-Referenz](../msbuild/msbuild-reference.md).|
|[SignFile-Aufgabe](../msbuild/signfile-task.md)|Signiert die Anwendungs-und Bereitstellungs Manifeste.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [MSBuild-Referenz](../msbuild/msbuild-reference.md).|
|[Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|Entwickeln Sie Ihre eigene Anwendung, um die Anwendungs-und Bereitstellungs Manifeste zu generieren.|

 Die folgende Tabelle zeigt die .NET Framework Version, die zur Unterstützung von ClickOnce-Anwendungen in diesen Browsern erforderlich ist.

|Browser|.NET Framework-Version|
|-------------|----------------------------|
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|
|Firefox|2.0 SP1, 3.5 SP1, 4|
|Chrome|3,5|
|Microsoft Edge|3,5|

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Bereitstellung unter Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Bereitstellen von COM-Komponenten mit ClickOnce](../deployment/deploying-com-components-with-clickonce.md)
- [Erstellen von ClickOnce-Anwendungen über die Befehlszeile](../deployment/building-clickonce-applications-from-the-command-line.md)
- [Debuggen von ClickOnce-Anwendungen, die System. Deployment. Application verwenden](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
