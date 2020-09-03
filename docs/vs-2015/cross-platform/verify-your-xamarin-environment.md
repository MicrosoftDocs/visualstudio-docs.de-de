---
title: Überprüfen Ihrer Xamarin-Umgebung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: 98925402b91bea62e10b47312e7834ed92a1a178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918742"
---
# <a name="verify-your-xamarin-environment"></a>Überprüfen Ihrer Xamarin-Umgebung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem die Installationsprogramme abgeschlossen wurden (siehe dazu [Setup and install (Setup und Installation)](../cross-platform/setup-and-install.md)), sollten Sie ein paar Minuten investieren, um zu überprüfen, ob alles für den Einstieg in die Xamarin-Entwicklung bereit ist.  
  
 Nach Abschluss dieser Überprüfung können Sie eine oder beide der folgenden exemplarischen Vorgehensweisen verwenden:  
  
- [Grundlegendes zur Erstellung von Apps mit Xamarin.Forms in Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
- [Erstellen von Apps mit nativer Benutzeroberfläche über Xamarin in Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Alle Plattformen  
 Wählen Sie **Extras > Optionen** aus, erweitern Sie **Xamarin > Other** (Andere), und klicken Sie auf den Link **Check now** (Jetzt überprüfen). Sie müssen Xamarin 4.0.3.214 oder höher verwenden, um Probleme mit früheren Lizenzierungen zu vermeiden.  
  
 Erstellen Sie in Visual Studio eine neue Xamarin-Projektmappe mithilfe von **Datei > Neues Projekt**. Erweitern Sie im Dialogfeld **Vorlagen > Andere Sprachen > Visual C# > Plattformübergreifend**, wählen Sie **Leere App (nativ portabel)** aus, und klicken Sie auf „OK“. Dadurch wird eine Projektmappe mit einem Projekt der gemeinsamen portablen Klassenbibliothek und einzelnen Projekten für Android, iOS und Windows erstellt:  
  
 ![Ergebnisse der Erstellung eines neuen Projekts aus der leeren App &#40;Native Portable&#41; Vorlage](../cross-platform/media/crossplat-xamarin-verify-1.png "Crossplat xamarin Verify 1")  
  
> [!NOTE]
> Wenn die Vorlagen nicht vorhanden sind, lesen Sie [Are the Xamarin project templates missing? Try this](#missing) am Ende dieser Seite.  
  
## <a name="android"></a>Android  
  
1. Überprüfen Sie, ob Sie die aktuellen Android SDK-Tools installiert haben. Wechseln Sie hierzu zu **Tools > Android > Android SDK-Manager**, und installieren Sie die neueste Version der Android SDK-Tools, der Android SDK Plattformtools und der Android SDK-Buildtoolskomponenten. Es ist nicht erforderlich, immer die neueste Android-API-Ebene zu installieren. Welche API erforderlich ist, hängt von der Plattformebene ab, die Sie als Ziel auswählen. Im Allgemeinen wird bei der Installation von Xamarin die erforderliche Plattformebene installiert.  

2. Überprüfen Sie den Android-Designer: Öffnen Sie im Android-Projekt im Projektmappen-Explorer die Datei **Ressourcen > Layout > Main.axml**. (Wenn die Datei nicht direkt angezeigt wird, suchen Sie im Projektmappen-Explorer danach. Sie ist nur im Android-Projekt enthalten, im iOS-Projekt dagegen nicht.)  
  
    - Wenn die Fehlermeldung „The installed Android SDK is too old (Das installierte Android SDK ist veraltet)“ angezeigt wird, klicken Sie in dieser Meldung auf **Open Android SDK (Android SDK öffnen)**, und installieren Sie die Tools der neuesten SDK-Version, wie weiter oben in Schritt 1 beschrieben. 
  
3. Überprüfen des Erstellens und des Debuggens im Emulator (oder Gerät):  
  
    - Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das Android-Projekt, und wählen Sie **Als Startprojekt festlegen**aus.  
  
         ![Visual Studio-Option „Als Startprojekt festlegen“](../cross-platform/media/crossplat-xamarin-verify-2.png "Crossplat xamarin Verify 2")  
  
    - Wählen Sie entsprechend der Android-Zielversion einen geeigneten Emulator aus. Ist ein Android-Entwicklungsgerät an Ihren Computer angeschlossen, wird dieses Gerät hier zusammen mit den Emulatoren aufgelistet:  
  
        - Windows 8 +: Wählen Sie in der Debug-Dropdown Liste von Visual Studio ein **vs-Emulator** -Ziel aus, wie unten dargestellt, und starten Sie den Debugger durch Drücken von **F5**. Weitere Informationen finden Sie unter [Einführung in den Visual Studio-Emulator für Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (Visual Studio Alm-Blog). Wenn bei der Inbetriebnahme des Emulators Probleme auftreten, finden Sie Hilfe unter [Troubleshooting the Visual Studio Emulator for Android (Problembehandlung beim Visual Studio-Emulator für Android)](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Sie können auch neue Geräteprofile für den Emulator erstellen, indem Sie **Tools > Visual Studio-Emulator for Android...** (Extras > Visual Studio Emulator für Android...) auswählen.  
  
             ![Auswählen des Visual Studio-Emulators für Android als Debugziel](../cross-platform/media/crossplat-xamarin-verify-3.png "Crossplat xamarin Verify 3")  
  
             Hinweis: Wenn die Menüoption **Tools > Visual Studio Emulator for Android...** (Extras > Visual Studio Emulator für Android...) nicht angezeigt wird, ist der Emulator möglicherweise nicht installiert. Wechseln Sie zu **Systemsteuerung > Programme und Funktionen**, wählen Sie **Microsoft Visual Studio** aus, und klicken Sie auf **Ändern**, um das Installationsprogramm erneut auszuführen. Klicken Sie im Installationsprogramm auf **Ändern**, aktivieren Sie das Kontrollkästchen **Plattformübergreifende, mobile Entwicklung > Microsoft Visual Studio Emulator für Android**, und klicken Sie auf **Aktualisieren**.  
  
        - Für Windows 7 und früher: wählen Sie stattdessen in der Dropdownliste den Xamarin Player für Android aus, und drücken Sie F5, um ihn auszuführen. Ausführliche Informationen über den Xamarin Player und dessen Geräte-Manager sowie Tipps zur Fehlerbehebung finden Sie unter [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com).  
  
> [!NOTE]
> In Visual Studio sehen Sie möglicherweise das Symbol für den Android Emulator Manager (AVD) in der Symbolleiste (siehe unten), über das der Geräte-Manager geöffnet wird, mit dem sich speziell der Google Android-Emulator konfigurieren lässt.  Dieses Symbol bedingt keine Auswirkungen auf den Visual Studio-Emulator für Android oder den Xamarin Player, die jeweils ihren eigenen Geräte-Manager zum Konfigurieren von Profilen haben.  Weitere Informationen finden Sie unter [Einführung in den Visual Studio-Emulator für Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (Visual Studio Alm-Blog) und [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (xamarin.com).  
> ![CrossPlat Xamarin Verify 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin Verify 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1. Überprüfen des Windows Phone-Designers: Öffnen Sie im Windows Phone-Projekt im Projektmappen-Explorer die Datei **MainPage.xaml** .  
  
2. Überprüfen Sie das Erstellen und das Debuggen im Emulator oder auf einem Gerät (Hinweis: dieser Schritt erfordert, dass der Windows Phone-Emulator mithilfe von Visual Studio-Setup installiert wurde oder ein verbundenes Gerät vorhanden ist):  
  
    - Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das Windows Phone-Projekt, und wählen Sie **Als Startprojekt festlegen**aus.  
  
    - Wählen Sie in der Debug-Dropdown Liste von Visual Studio ein **Emulator 8,1** -Ziel oder ein angefügtes Gerät aus, wie unten dargestellt, und starten Sie den Debugger durch Drücken von F5  
  
         ![Auswählen eines Windows Phone-Emulators als Debugziel](../cross-platform/media/crossplat-xamarin-verify-4.png "Crossplat xamarin Verify 4")  
  
    - Wenn Sie beim Arbeiten mit dem Emulator auf Probleme stoßen, lesen Sie [Troubleshooting the Windows Phone 8 Emulator](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1. Überprüfen Sie, ob der Mac im Netzwerk verfügbar und mit Visual Studio gepaart ist, wie unter [Connecting to the Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (xamarin.com) beschrieben.  
  
2. Überprüfen des Storyboard-Designers: Öffnen Sie im iOS-Projekt im Projektmappen-Explorer die Datei **Main.storyboard** . Hier bildet Visual Studio den Host für den Designer, der remote auf dem Mac ausgeführt wird.  
  
3. Überprüfen von Erstellen und Debuggen:  
  
    1. Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das iOS-Projekt, und wählen Sie **Als Startprojekt festlegen**aus.  
  
    2. Wählen Sie in der Build-Dropdown Liste von Visual Studio das Ziel **iphonesimulator** aus, wie unten gezeigt, oder das **iPhone** -Ziel, wenn Sie ein verbundenes Gerät haben. Wenn keine Simulatoren aufgelistet sind, starten Sie Xcode auf Ihrem Mac, wählen Sie **Xcode->Einstellungen**aus, und klicken Sie auf **herunterladen**. Unter **Komponenten** sollten die für den Download verfügbaren Simulatorversionen zu sehen sein. Weitere Anweisungen zum Debuggen finden Sie auf der Seite [Debuggen](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) von xamarin (xamarin.com).  
  
         ![Auswählen des iPhoneSimulator-Buildziels](../cross-platform/media/crossplat-xamarin-verify-5.png "Crossplat xamarin Verify 5")  
  
    3. Wählen Sie in der Debug-Dropdownliste von Visual Studio ein iPhone-Ziel aus, und starten Sie den Debugger, indem Sie F5 drücken. Dadurch wird der Simulator auf dem Mac gestartet, auf dem Sie mit der App interagieren, während das Debuggen in Visual Studio erfolgt. Wenn Sie mit einem physischen iPhone oder iPad arbeiten, das mit dem Mac verbunden ist, wird es hier angezeigt, und Sie können es stattdessen auswählen. Wenn keine Geräte oder Simulatoren aufgelistet werden, überprüfen Sie die Verbindung mit dem Mac, indem Sie das in Schritt 1 oben verknüpfte Thema überprüfen oder indem Sie zu **Tools**  > **IOS**  > **xamarin Mac Agent** wechseln.  
  
         ![Auswählen eines iPhone-Debugziels](../cross-platform/media/crossplat-xamarin-verify-6.png "Crossplat xamarin Verify 6")  
  
    4. Gibt es Probleme beim Herstellen einer Verbindung mit dem Mac, lesen [Connection Troubleshooting](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting) (xamarin.com).  
  
    5. Wird die Fehlermeldung „No installed provisioning profiles match the installed iOS signing keys“ angezeigt, gehen Sie wie folgt vor:  
  
        - Vergewissern Sie sich, dass Ihr Apple ID-Konto in Xcode auf dem Mac hinzugefügt wurde, wie dies unter [Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com) beschrieben ist.  Nachdem Ihr Konto hinzugefügt wurde, müssen Sie sowohl Visual Studio als auch Xcode neu starten.  
  
             ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")  
  
        - Stellen Sie sicher, dass in den iOS-Projekteigenschaften auf der Registerkarte „iOS-Bundle-Signierung“ das Feld „Benutzerdefinierte Berechtigungen“ für die aktive Debugkonfiguration leer ist.  Hinweis: Sie sollten nur dann versuchen, diese Einstellung zu löschen, wenn die oben genannte Fehlermeldung angezeigt wurde.  
  
## <a name="are-the-xamarin-project-templates-missing-try-this"></a><a name="missing"></a> Fehlen die Xamarin-Projektvorlagen? Versuchen Sie Folgendes  
 Wenn Sie Xamarin direkt von der Xamarin-Website installieren und Visual Studio 2013 und Visual Studio 2015 parallel installiert sind, fehlen möglicherweise die Vorlagen. Es ist jedoch einfach zu beheben: Aktivieren Sie einfach die Funktion **xamarin für Visual Studio 2015** im xamarin-Setup Programm.  
  
1. Öffnen Sie in der Systemsteuerung **Programme und Features**, wählen Sie das **Xamarin** -Element aus, und klicken Sie auf **Ändern**.  
  
2. Klicken Sie im Setup-Assistenten von Xamarin, der dann angezeigt wird, auf **Weiter** und dann auf **Ändern**.  
  
3. Erweitern Sie in der Liste der optional zu installierenden Features **Xamarin für Visual Studio 2015**, wählen Sie **wird auf dem lokalen Laufwerk installiert**aus, und klicken Sie auf **Weiter** , um mit dem Hinzufügen des Features fortzufahren.
