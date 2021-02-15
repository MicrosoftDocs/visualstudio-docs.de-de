---
title: Erstellen von Blazor-Web-Apps
description: In diesem Artikel finden Sie Informationen zur Blazor-Unterstützung in ASP.NET Core-Apps in Visual Studio für Mac.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 30e9a62e8bf0364a76cbd43995cbb77c1a5bd0c4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729417"
---
# <a name="create-blazor-web-apps"></a>Erstellen von Blazor-Web-Apps

Dieser Leitfaden bietet eine Einführung in die Erstellung Ihrer ersten Blazor-Web-App. Weitere ausführliche Anweisungen finden Sie unter [Einführung in ASP.NET Core für Blazor](/aspnet/core/blazor/index).

ASP.NET Core für Blazor unterstützt zwei verschiedene Hostingoptionen: Blazor WebAssembly (WASM) oder Blazor Server. Visual Studio für Mac unterstützt beide Hostingmodelle. Visual Studio für Mac 8.4 und höher unterstützt Blazor Server, Visual Studio für Mac 8.6 oder höher unterstützt beide Optionen. Weitere Informationen zu den Blazor-Hostingmodellen finden Sie unter [ASP.NET Core-Hostingmodelle für Blazor](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1&preserve-view=true). Unterstützung für das Debuggen von Blazor WebAssembly-Projekten in Visual Studio für Mac ist in der Vorschauversion von v8.8 verfügbar (über den Updatekanal für Vorschauen im Menü **Visual Studio > Nach Updates suchen...** ).

Was ist Blazor? Blazor ist ein Framework zum Erstellen von interaktiven, clientseitigen Webbenutzeroberflächen mit .NET, das den Webentwicklern folgende Vorteile bietet:

* Schreiben Sie Code in C# anstatt in JavaScript.
* Nutzen Sie das vorhandene .NET-Ökosystem von .NET-Bibliotheken.
* Geben Sie die App-Logik server- und clientübergreifend frei.
* Profitieren Sie von Leistung, Zuverlässigkeit und Sicherheit von .NET.
* Bleiben Sie mit Visual Studio unter Windows, Linux und macOS produktiv.
* Setzen Sie auf gebräuchliche Sprachen, Frameworks und Tools, die stabil, funktionsreich und einfach zu verwenden sind.

## <a name="create-a-new-blazor-webassembly-project"></a>Erstellen eines neuen Blazor WebAssembly-Projekts
1. Wählen Sie im **Startfenster** die Option **Neu** aus, um ein neues Projekt zu erstellen:

   ![Startfenster von Visual Studio für Mac mit hervorgehobener Auswahl von „Neu“](media/blazor-new-project.png)

1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **.NET Core** > **App** > **Blazor WebAssembly-App** aus, und klicken Sie dann auf **Weiter**: ![Screenshot des Dialogfelds „Neues Projekt“ mit hervorgehobener App ::no-loc(Blazor WebAssembly)::: im App-Bereich unter ASP.NET Core und der hervorgehoben Schaltfläche „Weiter“](media/blazor-wasm-project-template.png)

1. Wählen Sie .NET Core 3.1 als Zielframework und anschließend **Weiter** aus. 
   ![Dialogfeld „Neue Blazor WebAssembly- App konfigurieren“ mit ausgewähltem Zielframework „.NET Core 3.1“](media/blazor-wasm-select-target-framework.png)

1. Wählen Sie einen Namen für Ihr Projekt aus, und fügen Sie bei Bedarf Git-Unterstützung hinzu. Wählen Sie **Erstellen** aus, um das Projekt zu erstellen.
    ![Dialogfeld „Neue Blazor WebAssembly- App konfigurieren“ während der Eingabe des Projektnamens](media/blazor-wasm-name-project.png)

   Visual Studio für Mac öffnet Ihr Projekt im Codelayoutfenster.

1. Wählen Sie **Ausführen** > **Ohne Debuggen starten** aus, um die App auszuführen.

   Visual Studio startet [Kestrel](/aspnet/core/fundamentals/servers/kestrel), öffnet `https://localhost:5001` in einem Browser und zeigt Ihre Blazor-Web-App an.

   ![Blazor-Web-App in Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-blazor-server-project"></a>Erstellen eines neuen Blazor Server-Projekts

1. Wählen Sie im **Startfenster** die Option **Neu** aus, um ein neues Projekt zu erstellen:

   ![Startfenster von Visual Studio für Mac mit hervorgehobener Auswahl von „Neu“](media/blazor-new-project.png)
1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **.NET Core** > **App** > **Blazor Server-App** aus, und klicken Sie dann auf **Weiter**: ![Screenshot des Dialogfelds „Neues Projekt“ mit hervorgehobener Server-App Blazor im App-Bereich unter ASP.NET Core und der hervorgehoben Schaltfläche „Weiter“](media/blazor-project-template.png)

1. Wählen Sie .NET Core 3.1 als Zielframework und anschließend **Weiter** aus. 
   ![Dialogfeld „Neue Blazor- Server-App konfigurieren“ mit ausgewähltem Zielframework „.NET Core 3.1“](media/blazor-select-target-framework.png)

1. Wählen Sie einen Namen für Ihr Projekt aus, und fügen Sie bei Bedarf Git-Unterstützung hinzu. Wählen Sie **Erstellen** aus, um das Projekt zu erstellen.
   ![Dialogfeld „Neue Blazor- Server-App konfigurieren“ während der Eingabe des Projektnamens](media/blazor-name-project.png)

   Visual Studio für Mac öffnet Ihr Projekt im Codelayoutfenster.
1. Wählen Sie **Ausführen** > **Ohne Debuggen starten** aus, um die App auszuführen.

   Visual Studio startet [Kestrel](/aspnet/core/fundamentals/servers/kestrel), öffnet `https://localhost:5001` in einem Browser und zeigt Ihre Blazor-Web-App an.

   ![Blazor-Web-App in Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Blazor-Unterstützung in Visual Studio für Mac

Visual Studio für Mac (ab Version 8.4) enthält neue Features, mit denen Sie neue Blazor Server-Projekte erstellen können. Außerdem unterstützt der Dienst die Standardfeatures wie das Kompilieren, Ausführen und Debuggen von Blazor-Projekten. In Visual Studio für Mac 8.6 wurde Unterstützung für das Erstellen, Kompilieren und Ausführen von Blazor WebAssembly-Projekten hinzugefügt.

In der oben beschriebenen exemplarischen Vorgehensweise haben Sie gesehen, wie die Blazor-Server-App-Projektvorlage Sie bei der Erstellung eines neuen Blazor-Server-App- oder Blazor WebAssembly-App-Projekts unterstützt. Nun werden einige der zusätzlichen Features vorgestellt, die Visual Studio für Mac zur Unterstützung der Blazor-Projektentwicklung bietet.

### <a name="editor-support-for-razor-files"></a>Editor-Unterstützung für *.razor*-Dateien
Visual Studio für Mac unterstützt das Bearbeiten von RAZOR-Dateien. Dieser Dateityp wird bei der Erstellung von Blazor-Anwendungen hauptsächlich verwendet. Visual Studio für Mac bietet vollständige Unterstützung für die farbliche Kennzeichnung und Vervollständigung Ihrer RAZOR-Dateien, einschließlich Vervollständigung der im Projekt deklarierten Razor-Komponenten.

![Editor-Fenster für Visual Studio für Mac mit IntelliSense für Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Veröffentlichen von Blazor-Anwendungen in Azure App Service
Sie können Blazor-Anwendungen auch direkt in Azure App Service veröffentlichen. Wenn Sie kein Azure-Konto besitzen, um Ihre Blazor-App in Azure auszuführen, können Sie sich [hier für ein kostenloses Konto registrieren](https://azure.microsoft.com/free). Dieses Konto bietet zudem 12 Monate lang eine kostenlose Nutzung beliebter Dienste, kostenloses Azure-Guthaben über 200 USD und über 25 immer kostenlose Dienste.

![Visual Studio für Mac mit Azure-Veröffentlichungserfahrung](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Projektanatomie

Blazor-Web-Apps enthalten standardmäßig einige Verzeichnisse und Dateien. Hier sind die wichtigsten, mit denen Sie sich für Ihre ersten Schritte vertraut machen müssen:

### <a name="pages-folder"></a>Ordner „Seiten“

Dieser Ordner enthält die Webseiten eines Projekts, die die Dateierweiterung *.razor* verwenden.

### <a name="shared-folder"></a>Freigegebener Ordner

Dieser Ordner enthält freigegebene Komponenten, die ebenfalls die Erweiterung *.razor* verwenden. Sie werden feststellen, dass dieser die Datei *MainLayout.razor* umfasst, mit der das allgemeine Layout in der gesamten Anwendung definiert wird. Er enthält auch die gemeinsame Komponente *NavMenu.razor*, die auf allen Seiten verwendet wird. Wenn Sie wiederverwendbare Komponenten erstellen, werden diese in den Ordner **Freigegeben** verschoben.

### <a name="app-settings"></a>App-Einstellungen

Die Datei *appSettings.json* enthält Konfigurationsdaten wie Verbindungszeichenfolgen.

Weitere Informationen zur Konfiguration finden Sie unter [Konfiguration in ASP.NET Core](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Ordner „wwwroot“

Dieser Ordner enthält statische Dateien, z. B. HTML-, JavaScript- und CSS-Dateien. Weitere Informationen finden Sie unter [Statische Dateien in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Diese Datei enthält den Einstiegspunkt für das Programm. Weitere Informationen finden Sie unter [ASP.NET Core-Webhost](/aspnet/core/fundamentals/host/web-host).

### <a name="blazor-server-app-specific-files"></a>Spezifische Dateien für die Blazor-Server-App
#### <a name="app-settings"></a>App-Einstellungen

Die Datei *appSettings.json* enthält Konfigurationsdaten wie Verbindungszeichenfolgen.

Weitere Informationen zur Konfiguration finden Sie unter [Konfiguration in ASP.NET Core](/aspnet/core/fundamentals/configuration/index).

#### <a name="startupcs"></a>Startup.cs

Diese Datei enthält Code, mit dem das App-Verhalten konfiguriert wird, z. B., ob die App Zustimmung für Cookies erfordert. Weitere Informationen finden Sie unter [Anwendungsstart in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Zusammenfassung
In diesem Tutorial haben Sie gelernt, wie Sie eine neue Blazor-Server-App oder Blazor WebAssembly-App in Visual Studio für Mac erstellen. Zudem haben Sie einige der Features kennengelernt, mit denen Visual Studio für Mac Sie bei der Entwicklung von Blazor-Anwendungen unterstützt.

## <a name="see-also"></a>Siehe auch

Eine umfassendere Anleitung zum Erstellen von Blazor-Web-Apps finden Sie unter [Einführung in ASP.NET Core für Blazor](/aspnet/core/blazor/index).