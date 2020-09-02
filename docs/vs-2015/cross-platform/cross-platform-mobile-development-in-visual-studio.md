---
title: Plattformübergreifende mobile Entwicklung
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312755"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Plattformübergreifende, mobile Entwicklung in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Apps für Android-, iOS- oder Windows-Geräte mithilfe von Visual Studio erstellen.  Außerdem lassen sich Tools in Visual Studio verwenden, um verbundene Dienste wie Office 365, App Service oder Application Insights unkompliziert hinzufügen.

 Sie können die Apps mithilfe von C#, mit .NET Framework oder mithilfe von HTML, JavaScript oder C++ erstellen. Auch Code, Zeichenfolgen, Bilder und in einigen Fällen sogar die Benutzeroberfläche selbst können freigeben werden.

 Wenn Sie ein Spiel oder eine immersive grafische App erstellen möchten, installieren Sie die Visual Studio-Tools für Unity. Profitieren Sie von den leistungsstarken Produktivitätsfunktionen von Visual Studio-Tools für Unity, der beliebten plattformübergreifenden Spiele- und Grafik-Engine und Entwicklungsumgebung für Apps, die unter iOS, Android, Windows und auf anderen Plattformen ausgeführt wird.

 **In diesem Artikel:**

- [Erstellen einer App für Android, iOS und Windows(.NET Framework)](#NET)

  - [Android-, IOS-und Windows-Ziel aus einer einzelnen Codebasis](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Windows 10-Zielgeräte](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Erstellen einer APP für Android, IOS und Windows (HTML/JavaScript)](#HTML)

- [Erstellen einer APP für Android und Windows (C++)](#CPP)

- [Erstellen eines plattformübergreifenden Spiels für Android, iOS und Windows mithilfe von Visual Studio-Tools für Unity](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Erstellen einer APP für Android, IOS und Windows (.NET Framework)
 ![Geräte](../cross-platform/media/homedevices.png "HomeDevices")

 Mithilfe von Xamarin können Sie für Android, iOS und Windows mit der gleichen Projektmappe arbeiten und Code und sogar die Benutzeroberfläche freigeben.

|**Weitere Informationen**|
|--------------------|
|[Installieren von Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Informationen zu Xamarin in Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio und Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Library)|
|[Application Lifecycle Management (ALM) mit Xamarin-Apps](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Library)|
|[Weitere Informationen zu universellen Windows-apps in Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Informationen zu den Ähnlichkeiten zwischen Swift und C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Informationen zum Visual Studio Emulator für Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Android-, iOS und Windows-Zielgeräte aus einer einzigen Codebasis
 Sie können native Apps für Android, iOS und Windows mit C#- oder F# erstellen (Visual Basic wird derzeit nicht unterstützt).  Beginnen Sie mit der Installation von Visual Studio 2015, und wählen Sie im Installationsprogramm die Option **Benutzerdefiniert** aus. Aktivieren Sie anschließend das Kontrollkästchen unter **Plattformübergreifende, mobile Entwicklungg > C# / .NET (Xamarin)**. Sie können auch mit dem [Xamarin-Installationsprogramm](https://www.xamarin.com/download) beginnen, das für die Installation von Xamarin für Visual Studio 2013 erforderlich ist.

 Wenn Sie Visual Studio 2015 bereits installiert haben, führen Sie das Installationsprogramm über **Systemsteuerung > Programme und Funktionen** aus, und wählen Sie für Xamarin die gleiche Option **Benutzerdefiniert** aus wie oben beschrieben.

 Wenn Sie fertig sind, werden Projektvorlagen im Dialogfeld **Neues Projekt** angezeigt. Suchen Sie einfach auf „Xamarin“, wenn Sie Xamarin-Vorlagen benötigen.

 Xamarin bietet die native Funktionalität von Android, iOS und Windows als .NET-Objekten. Die Apps verfügen über vollen Zugriff auf native APIs und native Steuerelemente. Sie sind damit ebenso reaktionsfähig wie Apps, die in den nativen Plattformsprachen geschrieben werden.

 Nachdem Sie ein Projekt erstellen haben, nutzen Sie alle Produktivitätsfeatures von Visual Studio. Verwenden Sie beispielsweise einen Designer zum Erstellen von Seiten, oder nutzen Sie IntelliSense, um die nativen APIs der mobilen Plattformen zu untersuchen. Wenn Sie so weit sind, dass Sie die Anwendung ausführen und die Anzeige prüfen möchten, können Sie den Visual Studio-Emulator für Android oder den Android SDK-Emulator verwenden, die Windows-Apps nativ oder auf dem Windows Phone-Emulator ausführen. Sie können auch direkt angeschlossene Android- und Windows-Geräte nutzen. Bei iOS-Projekten stellen Sie eine Verbindung zu einem Mac-Computer in einem Netzwerk her und starten den Mac-Emulator in Visual Studio, oder Sie verwenden ein angeschlossenes Gerät.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Entwerfen Sie einen Satz von Seiten, die auf allen Geräten mithilfe von Xamarin.Forms gerendert werden.
 Je nach Komplexität des App-Entwurfs könnten Sie überlegen, sie mithilfe von *Xamarin.Forms* -Vorlagen in der Gruppe **Mobile Apps** der Projektvorlagen zu erstellen. Xamarin.Forms ist ein Benutzeroberflächen-Toolkit, mit dem Sie eine zentrale Benutzeroberfläche erstellen können, die Sie dann für Android und iOS sowie für Windows freigeben.  Beim Kompilieren einer Xamarin.Forms-Projektmappe erhalten Sie eine Android-App, eine iOS-App und eine Windows-App. Weitere Einzelheiten erfahren Sie unter [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Gemeinsames Verwenden von Code für Android-, iOS- und Windows-Apps
 Wenn Sie nicht Xamarin.Forms verwenden und stattdessen für jede Plattform einzeln entwickeln möchten, können Sie den größten Teil Ihres nicht für die Benutzeroberfläche selbst entwickelten Codes für alle Plattformprojekte (Android, iOS und Windows) verwenden. Dies umfasst beliebige Geschäftslogiken, Cloud-Integrationen, Datenbankzugriffe oder weitere Codes, die auf .NET Framework abzielen. Der einzige Code, den Sie nicht freigeben können, ist jener Code, der auf eine bestimmte Plattform abzielt.

 ![Freigeben von Code für Windows-, iOs-und Android-Benutzeroberflächen](../cross-platform/media/sharecode.png "ShareCode")

 Sie können Ihren Code mithilfe eines freigegebenen Projekts, eines Portable Class Library-Projekts oder mithilfe von beidem freigeben. Sie stellen unter Umständen fest, dass ein bestimmter Code sich am besten für ein freigegebenes Projekt eignet, während es bei einem anderen Code sinnvoller ist, diesen innerhalb eines Portable Class Library-Projekts anzuwenden.

|**Weitere Informationen**|
|--------------------|
|Sie können wählen, ob Sie den Code freigeben möchten, indem Sie gemeinsam genutzte Projekte, Portable Class Library-Projekte oder sowohl als auch verwenden.<br /><br /> [Plattformübergreifendes Freigeben von Code](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (.NET Framework-Blog)<br /><br /> [Sharing Code Options (Optionen für die Codefreigabe)](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Optionen für die Codefreigabe mit .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (MSDN Library)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Windows 10-Zielgeräte
 ![Windows-Geräte](../cross-platform/media/windowsdevices.png "Windows-Geräte")

 Wenn Sie eine App erstellen möchten, die für alle Windows 10-Geräte ausgelegt ist, erstellen Sie eine universelle Windows-App. Sie müssen die App mit einem einzelnen Projekt entwerfen. Ihre Seiten werden dann ordnungsgemäß gerendert, unabhängig davon, welches Gerät für die Anzeige verwendet wird.

 Beginnen Sie mit einer universellen Windows-App-Projektvorlage. Entwerfen Sie Ihre Seiten visuell, und öffnen Sie sie in einem Vorschaufenster, um ihre Darstellung auf den verschiedenen Arten von Geräten zu prüfen. Wenn Ihnen die Darstellung einer Seite auf einem Gerät nicht zusagt, können Sie die Seite an die Größe des Bildschirms, die Auflösung oder die verschiedenen Ausrichtungen wie Quer- oder Hochformat anpassen. All dies erfolgt mithilfe der intuitiven Toolfenster und der leicht zugänglichen Menüoptionen in Visual Studio. Wenn Sie bereit sind, Ihre APP auszuführen und den Code schrittweise auszuführen, finden Sie alle Geräte Emulatoren und Simulatoren für verschiedene Arten von Geräten zusammen in einer Dropdown Liste, die sich auf der **Standard** Symbolleiste befindet.

 Windows 10 ist noch recht neu, sodass Sie auch Projektvorlagen für Windows 8.1 vorfinden. Sie können diese Projektvorlagen für Apps verwenden, die auf Telefonen, Tablets und Computern unter Windows 10 ausgeführt werden sollen. Alle Geräte unter Windows 8.1 erhalten jedoch ein automatisches Upgrade auf Windows 10. Wenn Sie also über keine besonderen Gründe für Windows 8.1 als Ziel verfügen, ist es empfehlenswert, eine Projektvorlage mit Windows 10 als Ziel zu verwenden.

|**Weitere Informationen**|
|--------------------|
|[Informationen zu universellen Windows-Apps](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Erstellen der ersten App](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center)|
|[Entwickeln von Apps für die universelle Windows-Plattform (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrieren von Apps auf die universelle Windows-Plattform (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Erstellen einer App für Android, iOS und Windows (HTML/JavaScript)
 ![Geräte](../cross-platform/media/homedevices.png "HomeDevices")

 Wenn Sie als Webentwickler mit HTML und JavaScript vertraut sind, können Sie mithilfe von Visual Studio-Tools für Apache Cordova eine Nutzung unter Windows, Android und iOS ermöglichen. Diese Apps können auf allen drei Plattformen ausgeführt werden. Sie erstellen sie mithilfe Ihrer Kenntnisse und der Vorgehensweisen, mit denen Sie vertraut sind.

 Apache Cordova ist ein Framework, das ein Plug-In-Modell enthält. Dieses Plug-In-Modell bietet eine zentrale JavaScript-API, mit der Sie auf native Gerätefunktionen aller drei Plattformen (iOS, Android und Windows) zugreifen können.

 Da diese APIs plattformübergreifend sind, können Sie den größten Teil Ihres Code für alle drei Plattformen verwenden. Dies trägt zu geringeren Entwicklungs- und Wartungskosten bei. Darüber hinaus müssen Sie nicht jedes Mal von Grund auf neu anfangen. Wenn Sie andere Arten von Webanwendungen erstellt haben, können Sie diese Dateien für Ihre Cordova-App verwenden, ohne sie ändern oder umgestalten zu müssen.

 ![Hybrid-Apps für mehrere&#45;Geräte](../cross-platform/media/multidevicehybridapps.png "Multiabvicehybridapps")

 Installieren Sie zum Einstieg Visual Studio 2015, und wählen Sie während des Setups das **HTML/JavaScript (Apache Cordova)** -Feature. Wenn Sie Visual Studio 2013 verwenden, installieren Sie die Erweiterung „Visual Studio-Tools für Apache Cordova“. In jedem Fall installieren die Cordova-Tools automatisch sämtliche Drittanbieter-Software, die zum Erstellen der plattformübergreifenden App erforderlich ist.

 Nachdem Sie die Erweiterung installiert haben, öffnen Sie Visual Studio, und erstellen Sie ein **leeres App-Projekt (Apache Cordova)** . Anschließend können Sie die App mit JavaScript oder TypeScript entwickeln. Sie können darüber hinaus Plug-Ins zum Erweitern der App-Funktionen hinzufügen. Beim Schreiben von Code werden APIs aus Plug-Ins in IntelliSense angezeigt.

 Wenn Sie Ihre App ausführen und den Code durchlaufen möchten, wählen Sie einen Emulator (z.B. den Apache Ripple-Emulator oder den Visual Studio-Emulator für Android oder Windows Phone) und einen Browser oder ein Gerät aus, das Sie direkt an den Computer angeschlossen haben. Starten Sie dann Ihre App. Wenn Sie Ihre App auf einem Windows-Computer entwickeln, können Sie sie auch auf diesem ausführen. Alle diese Optionen werden in Visual Studio als Teil der Visual Studio-Tools für Apache Cordova integriert.

 Projektvorlagen für das Erstellen universeller Windows-Apps sind weiterhin in Visual Studio verfügbar, Sie können Sie also gerne zum Erstellen von Anwendungen für Windows-Geräte verwenden. Wenn Sie zu einem späteren Zeitpunkt Anwendungen für Android- und iOS-Geräte erstellen möchten, können Sie den Code immer noch in ein Cordova-Projekt portieren. Es stehen Open-Source-Versionen der WinJS-APIs zur Verfügung. Sie können somit jeden beliebigen Code wiederverwenden, welcher diese APIs nutzt. Dies bedeutet, wenn Sie in Zukunft Anwendungen für andere Plattformen entwickeln möchten, wird empfohlen, mit Visual Studio-Tools für Apache Cordova zu starten.

|**Weitere Informationen**|
|--------------------|
|[Installieren von Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Erste Schritte mit Visual Studio-Tools für Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Informationen zum Visual Studio Emulator für Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a>Erstellen einer App für Android und Windows (C++)
 ![Verwenden von C&#43;&#43; zum Entwickeln von Apps für Android, iOS und Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Installieren Sie zuerst Visual Studio 2015 und die Tools von Visual C++ für die plattformübergreifende, mobile Entwicklung. Anschließend können Sie eine native Activity-App für Android oder eine App für Windows-Geräte erstellen. C++-Vorlagen für iOS-Geräte sind noch nicht verfügbar. Sie können für Android- und Windows-Geräte mit der gleichen Projektmappe arbeiten und anschließend den Code mithilfe einer plattformübergreifenden statischen oder dynamischen freigegebenen Bibliothek für beide freigeben.

 Wenn Sie eine App für Android erstellen müssen, die eine erweiterte Grafikbearbeitung erfordert, z.B. ein Spiel, können Sie C++ dazu verwenden. Beginnen Sie mit dem Projekt **Native-Activity Application (Android)** . Dieses Projekt bietet vollständige Unterstützung für die Clang-Toolkette.

 ![Vorlage für Projekt mit nativer Aktivität](../cross-platform/media/cross-plat-cpp-native.png "Kreuz Plat_CPP_Native")

 Wenn Sie soweit sind, dass Sie die Anwendung ausführen und die Anzeige prüfen möchten, verwenden Sie den Visual Studio-Emulator für Android. Er ist schnell, zuverlässig und leicht zu installieren und konfigurieren.

 Sie können auch eine App für sämtliche Typen von Windows 10-Geräten mithilfe von C++ und der Projektvorlage für universelle Windows-Apps erstellen. Weitere Informationen hierzu finden Sie im Abschnitt [Windows 10-Zielgeräte](#WindowsHTML) weiter oben in diesem Thema.

 Sie können C++-Code für Android- und Windows-Geräten freigeben, indem Sie eine statische oder dynamische freigegebene Bibliothek erstellen.

 ![Statische und dynamische freigegebene Bibliotheken](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Sie können diese Bibliothek in einem Windows- oder Android-Projekt nutzen, wie sie weiter oben in diesem Abschnitt beschriebenen sind. Sie können sie auch in einer App verwenden, die Sie mithilfe von Xamarin, Java oder einer anderen Sprache erstellen, mit der Funktionen in einer nicht verwalteten DLL aufgerufen werden können.

 Beim Schreiben von Code in diesen Bibliotheken können Sie IntelliSense verwenden, um die systemeigenen APIs der Android- und Windows-Plattformen zu untersuchen. Diese Bibliotheksprojekte sind vollständig in den Visual Studio-Debugger integriert, sodass Sie mithilfe der erweiterten Funktionen des Debuggers Haltepunkte festlegen, Code durchlaufen und Probleme suchen und beheben können.

|**Weitere Informationen**|
|--------------------|
|[Laden Sie Visual Studio herunter.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Tools für Visual C++ für die plattformübergreifende Entwicklung installieren](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[Visual Studio C++ – Plattformübergreifende mobile Entwicklung](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Installieren der erforderlichen Tools und anschließendes Erstellen einer App mit systemeigener Aktivität für Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[Informationen zum Visual Studio Emulator für Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Weitere Informationen zum Freigeben von C++-Code mit Android- und Windows-Apps](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Beispiele für plattformübergreifende mobile Entwicklung](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Library)|
|[Weitere Beispiele für plattformübergreifende mobile Entwicklung für C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a> Erstellen eines plattformübergreifenden Spiels für Android, IOS und Windows mithilfe von Visual Studio-Tools für Unity
 Visual Studio-Tools für Unity ist eine kostenlose Erweiterung für Visual Studio, die die leistungsfähigen codebearbeitungs-, Produktivitäts-und Debuggingtools von Visual Studio mit *Unity*integriert, der beliebten plattformübergreifenden Spiele-und Grafik-Engine und Entwicklungsumgebung für immersive Apps für Windows, Ios, Android und andere Plattformen, einschließlich des Internets.

 ![VSTU-Entwicklungsumgebung](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Mithilfe der Visual Studio-Tools für Unity (VSTU) können Sie Visual Studio zum Schreiben von Spiel- und Editorskripts in C# verwenden und dann den leistungsfähigen Debugger zum Suchen und Beheben von Fehlern nutzen. Die neueste Version von VSTU unterstützt Unity 5 und bietet Syntaxfarben für die Shadersprache ShaderLab von Unity, eine optimierte Synchronisierung mit Unity, umfangreichere Debugfunktionen und verbesserte Codegenerierung für den MonoBehavior-Assistenten. Mit VSTU werden außerdem die Unity-Projektdateien, Konsolenmeldungen und die Möglichkeit zum Starten des Spiels in Visual Studio eingebunden, sodass beim Schreiben von Code weniger Zeit zum Umschalten in und aus dem Unity-Editor benötigt wird.

 Beginnen Sie noch heute damit, ein Spiel mit Unity und Visual Studio-Tools für Unity zu erstellen.

|**Weitere Informationen**|
|--------------------|
|[Weitere Informationen über das Erstellen von Unity-Spielen mit Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Weitere Informationen zu Visual Studio-Tools für Unity](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Library)|
|[Einstieg in Visual Studio-Tools für Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Library)|
|[Informationen zu den neusten Verbesserungen von Visual Studio Tools für Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio-Blog)|
|[Videoeinführung in Visual Studio Tools für Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Informationen zu Unity](https://unity.com/) (Unity-Website)|

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Office 365-APIs zu einem Visual Studio-Projekt](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
