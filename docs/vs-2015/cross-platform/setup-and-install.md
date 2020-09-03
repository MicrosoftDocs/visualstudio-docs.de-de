---
title: Setup und Installation | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: dbdeeab49da1a63562bb9a4188a264a8d3d99da2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917046"
---
# <a name="setup-and-install"></a>Setup und Installation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Erstellen von systemeigenen iOS- Android- und Windows-Apps aus einer gemeinsamen C#/.NET-Codebasis mithilfe von Xamarin benötigen Sie die folgenden Komponenten:  
  
- Für das Arbeiten mit Windows- und Android-Apps: einen Windows-Entwicklungscomputer mit installiertem Visual Studio 2015 und Xamarin 4 (siehe Hinweis weiter unten). (Sie können auch Visual Studio 2013 verwenden, indem Sie die Anweisungen für die [direkte xamarin-Installation](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) befolgen.)   
  
- Für das Arbeiten mit iOS-Apps: einen Mac mit OS X Yosemite (10.10.5) oder höher, mit installiertem XCode und Xamarin.  
  
  Sie können die Windows- und Mac-Computer gleichzeitig einrichten, und während die Installationsprogramme ausgeführt werden, können Sie in [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) das erforderliche Hintergrundmaterial durchlesen und ansehen.  
 
Wenn Sie nach dem Setup und der Installation Probleme mit der Verwendung von Xamarin haben, posten Sie Ihre Frage auf [forums.xamarin.com](https://forums.xamarin.com/).
  
> [!NOTE]
> Seit dem 31. März 2016 ist Xamarin ohne zusätzliche Kosten im Lieferumfang aller Editionen von Visual Studio enthalten. Eine separate Lizenz ist nicht erforderlich. Xamarin Studio Community für Mac ist auch für Studenten, OSS-Entwickler und kleine Teams kostenlos. Beachten Sie, dass Sie für vorhandene Installationen von Visual Studio, die mit früheren Xamarin-Lizenzen konfiguriert sind, Xamarin auf Version 4.0.3.214 oder höher aktualisieren müssen. Informationen hierzu finden Sie unter **Extras > Optionen > Xamarin > Sonstige**, klicken Sie auf **Jetzt prüfen**, und laden Sie das Update 4.0.3.214 herunter. Wenn Sie Visual Studio neu starten, wechseln Sie zu **Extras > Xamarin-Konto...**. Dort sollten Sie den aktualisierten Status sehen.  
  
 **In diesem Thema:**  
  
- [Voraussetzungen](#prereq)  
  
- [Windows-Setup (Visual Studio und Xamarin)](#windows)  
  
- [Mac-Setup (Apple ID, Xcode und Xamarin)](#mac)  
  
## <a name="pre-requisites"></a><a name="prereq"></a> Voraussetzungen  
  
1. Für Windows und Android:  
  
    1. Empfohlen: Ein physischer Windows-Computer (keine VM), auf dem Windows 8 oder höher ausgeführt wird, was die Verwendung des schnellen Visual Studio-Emulators für Android ermöglicht, wenn Sie kein Android-Gerät haben. (Haben wir erwähnt, dass Sie einen physischen Computer benötigen anstelle einer VM?)  
  
    1. Sie können einen Computer mit Windows 7 oder früher verwenden. In diesem Fall müssen Sie jedoch den Xamarin Player für Android als Emulator verwenden. 
    
    1. Bei beiden Konfigurationen können Sie Apps immer direkt auf verbundenen physischen Geräten ausführen.  
  
1. Für iOS:  
  
    1. Mac oder Mac mini mit OS X Yosemite unter OS X 10.10.5 oder höher (für Xcode 7.1 erforderlich).  
  
    1. Bei Verwendung von Visual Studio auf einem Windows-Computer (7 und höher) als primäre Entwicklungsumgebung ist ein vernetzter Mac nur zum Kompilieren und Debuggen von iOS-Apps, Anschließen an den iOS-Simulator oder verbundene Geräte und Verwenden des Storyboard-Designers in Visual Studio für das Design der Benutzeroberfläche. Ältere Mac-Modelle sind für diese sekundäre Rolle völlig ausreichend.  
  
## <a name="windows-setup-visual-studio-and-xamarin"></a><a name="windows"></a> Windows-Setup (Visual Studio und xamarin)  
  
> [!TIP]
> Diese Anweisungen gelten für Visual Studio 2015. Befolgen Sie die Anweisungen für die [direkte xamarin-Installation](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com), um xamarin mit Visual Studio 2013 zu verwenden (Update 2 ist erforderlich).  
  
1. [Laden Sie das Installationsprogramm für eine beliebige Edition von Visual Studio 2015 herunter, und führen Sie es aus](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional oder Enterprise). Visual Studio 2015 Community ist die kostenlose Edition; die Editionen Professional und Enterprise können als Testversion 30 Tage, nachdem Sie eine Lizenz gekauft haben, verwendet werden.  
  
   1. Wenn Sie Visual Studio bereits installiert haben, öffnen Sie **Systemsteuerung > Programme und Features**, wählen Sie **Visual Studio 2015** aus, und klicken Sie auf **Ändern**. Wenn das Installationsprogramm geöffnet wird, klicken Sie auf **Ändern**, und wechseln Sie zum Schritt 3 weiter unten.  
  
2. (Nur Neuinstallationen) Wählen Sie im Installationsprogramm eine **Benutzerdefinierte** Installation aus:  
  
    ![Auswählen der Option „Benutzerdefiniert“ bei Visual Studio-Installation](../cross-platform/media/cross-plat-xamarin-setup-1.png "Plattformübergreifendes xamarin-Setup 1")  
  
3. Aktivieren Sie die folgenden Felder:  
  
   1. **Plattformübergreifende mobile Entwicklung > C#/.NET (Xamarin)**. Dadurch werden unter „Häufig verwendete Tools und Software Development Kits“ auch automatisch verschiedene Android-Tools ausgewählt. Diese Option sollte auch alle vorhandenen Xamarin-Installationen aktualisieren.  
  
        ![Wählen Sie unter Cross&#45;Platform Mobile Development die Option xamarin aus.](../cross-platform/media/cross-plat-xamarin-setup-2.png "Plattformübergreifendes xamarin-Setup 2")  
  
   2. Für Windows 8+: **Plattformübergreifende mobile Entwicklung > Microsoft Visual Studio-Emulator für Android**. Hinweis: Wenn Sie einen Computer mit Windows 7 oder früher verwenden oder Windows auf einem Mac ausführen, achten Sie darauf, dass die Option *nicht aktiviert* ist. Weitere Informationen finden Sie unter „Hinweis zu Emulatoren auf Windows-Computern“ nach Schritt 5. Sie können diese Option deaktiviert lassen, wenn Sie nur auf physischen Android-Geräten debuggen möchten.  
  
   3. (Optional) Wenn Sie Windows-Geräte als Zielplattform vorgesehen haben, aktivieren Sie außerdem **Windows- und Webentwicklung > Entwicklungstools für universelle Windows-Apps** und/oder **Windows 8.1 und Windows Phone 8.0/8.1 Tools**. Diese umfassen Optionen zum Installieren von Emulatorimages, deren Download längere Zeit beansprucht; Sie können auch später jederzeit zum Visual Studio-Installationsprogramm zurückkehren, um sie hinzuzufügen.  
  
4. Klicken Sie auf die Schaltfläche „Installieren“, und führen Sie den Vorgang aus. Dieser Vorgang nimmt ebenfalls einige Zeit in Anspruch. In der Zwischenzeit können Sie mit den Anweisungen zum Mac-Setup fortfahren oder [Erfahren Sie mehr über die Entwicklung für mobile Plattformen mit Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) durcharbeiten.  
  
5. Starten Sie Visual Studio nach dem Abschluss der Installation, und melden Sie sich mit Ihrem Microsoft-Konto an, wenn Sie dazu aufgefordert werden (es handelt sich um das gleiche Konto, das Sie für Windows verwenden). Suchen Sie anschließend mithilfe von **Extras > Optionen > Xamarin** oder **Extras > Optionen > Xamarin > Sonstige** nach Xamarin-Updates; dazu dient der Link **Jetzt überprüfen**:  
  
    ![Überprüfung auf Xamarin-Updates in den Visual Studio-Optionen](../cross-platform/media/cross-plat-xamarin-setup-3.png "Plattformübergreifendes xamarin-Setup 3")  
  
   > [!NOTE]
   > Wie bereits erwähnt, müssen Sie Xamarin auf Version 4.0.3.214 oder höher aktualisieren, um Probleme mit früheren Xamarin-Lizenzen zu vermeiden.  

   Wenn Sie unter **Tools > Optionen** keine Option für Xamarin sehen, überprüfen Sie die Installation erneut, oder starten Sie Visual Studio neu. Sie können auch Xamarin im Dialogfeld „Optionen“ suchen.
      
6. Für Windows 7 und früher oder die Ausführung von Windows auf einem Mac verwenden Sie den [Android SDK-Emulator](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/), wenn Sie keine physischen Geräte haben. Siehe Hinweis weiter unten.  
  
   **Hinweis zu Emulatoren auf Windows-Computern:** Da die CPUs jeweils nur eine Virtualisierungstechnologie unterstützen, ist es am besten, nur eine Virtualisierungstechnologie auf einem Entwicklungs Computer zu verwenden. Die drei wichtigsten Virtualisierungstechnologien sind Hyper-V (das vom Visual Studio Emulator für Android und dem Windows Phone-Emulator verwendet wird), Virtual Box (das von Genymotion verwendet wird) und Intel HAXM (das vom Android SDK-Emulator verwendet wird). Aufgrund von verschiedenen Problemen zwischen Hyper-V und Virtual Box sollten auf einem Computer jeweils nur Emulatoren eines dieser Typen verwendet werden; darauf beziehen sich auch die oben genannten Empfehlungen für den Einsatz von Hyper-V auf Computern mit Windows 8 und höher und Intel HAXM-Emulatoren auf Windows 7 sowie bei der Ausführung von Windows auf einem Mac.  
  
## <a name="mac-setup-apple-id-xcode-and-xamarin"></a><a name="mac"></a> Mac-Setup (Apple ID, Xcode und xamarin)  
  
1. Erstellen Sie eine kostenlose Apple-ID unter, [https://appleid.apple.com](https://appleid.apple.com/) Wenn Sie noch keine besitzen. Dies ist für die Installation von und die Anmeldung bei Xcode erforderlich.  
  
2. Laden Sie Xcode von herunter, und installieren Sie es  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) , und fügen Sie Ihre Apple-ID wie unter [Hinzufügen Ihres Kontos zu Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com) beschrieben hinzu.  
  
3. Laden Sie Xamarin herunter, und installieren Sie es, indem Sie die Anweisungen unter [Installing and Configuring Xamarin.iOS](/xamarin/ios/get-started/installation/mac) (xamarin.com) befolgen.  
  
4. Nachdem Sie die Installation von xamarin auf dem Windows-und dem Mac-Computer abgeschlossen haben, befolgen Sie die Anweisungen unter [Herstellen einer Verbindung mit dem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (xamarin.com), sodass Sie mit IOS und dem Mac in Visual Studio auf dem Windows-Computer arbeiten können.  
  
     Beide Computer müssen sich im selben lokalen Netzwerk befinden.
