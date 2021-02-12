---
title: Installieren von Visual Studio 2017 für Mac
description: Anweisungen zum Installieren von Visual Studio für Mac und zusätzlicher erforderlichen Komponenten für die plattformübergreifende Entwicklung
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: be799764c3d6913cd2a13c6d631fc3450f8875a0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719915"
---
# <a name="install-visual-studio-2017-for-mac"></a>Installieren von Visual Studio 2017 für Mac

> [!NOTE]
> Visual Studio 2019 für Mac ist [jetzt verfügbar](installation.md?view=vsmac-2019&preserve-view=true). Informationen für ältere Versionen von Visual Studio für Mac finden Sie auf der [Downloadseite](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac) von Visual Studio.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Sie möchten von Visual Studio 2019 für Mac herabstufen?

Um ein optimales Ergebnis zu erzielen, sollten Sie Visual Studio 2019 für Mac vor dem Downgrade unbedingt [deinstallieren](uninstall.md). Wenn Probleme Sie zum Herabstufen zwingen, teilen Sie uns dies unbedingt mit, indem Sie [ein Problem berichten](report-a-problem.md).
 
## <a name="requirements"></a>Anforderungen

Um mit der Entwicklung nativer, plattformübergreifender Apps zu beginnen, wenn Sie Visual Studio für Mac heruntergeladen haben, müssen Sie vorher verschiedene Installationen und Setups durchführen.

Damit Visual Studio unter iOS funktioniert, benötigen Sie Folgendes:

- Ein Mac mit macOS High Sierra 10.13 oder höher.
- Xcode 9.3 oder höher. Für gewöhnlich wird die neuste stabile Version empfohlen.
- eine Apple-ID Erstellen Sie eine kostenlose Apple-ID unter https://appleid.apple.com, wenn Sie noch keine besitzen. Dies ist für die Installation von und die Anmeldung bei Xcode erforderlich.

## <a name="install"></a>Installieren

1. Laden Sie Visual Studio für Mac unter [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac) herunter.

2. Wenn das Installer-Paket heruntergeladen wurde, klicken Sie auf die Datei **VisualStudioForMacInstaller.dmg**, um den Installer einzubinden, und führen Sie ihn dann aus, indem Sie das Logo wie in der folgenden Abbildung veranschaulicht doppelklicken:

   ![Dialogfeld „Installer“](media/installer-image1.png)

3. Möglicherweise wird ein Warnungsdialogfeld wie das folgende angezeigt. Klicken Sie in einem solchen Fall auf **Öffnen**:

   ![Warnungsdialogfeld](media/installer-image2.png)

4. Der Installer prüft Ihr System, um zu bestimmen, welche Komponenten installiert oder aktualisiert werden müssen:

   ![Bewerten Ihres Systems](media/installer-image3.png)

5. Dann wird ein Warnungsdialogfeld angezeigt, über das Sie aufgefordert werden, die Datenschutz- und Lizenzbedingungen zu akzeptieren. Klicken Sie auf die Schaltfläche **Weiter**, um die Bedingungen zu akzeptieren.

   ![Dialogfeld „Lizenz“](media/installer-image4.png)

6. Der Installer zeigt eine Liste der erforderlichen Komponenten an, die fehlen und die heruntergeladen und installiert werden müssen. Wählen Sie hier die Produkte aus, die Sie herunterladen möchten:

   ![Auswählen von Elementen](media/installer-image5.png)

   Wenn Sie nicht alle Plattformen installieren möchten, lesen Sie den nachfolgenden Leitfaden, um die zu installierenden Plattformen festzulegen:

   * **Apps mit Xamarin**:
      - Xamarin.Forms: Wählen Sie die Plattformen **Android** und **iOS** aus.
      - Nur iOS: Wählen Sie die **iOS**-Plattform aus. (Hinweis: Sie müssen [**Xcode**](https://developer.apple.com/xcode/) installieren.)
      - Nur Android: Wählen Sie die **Android**-Plattform aus. (Hinweis: Sie sollten darüber hinaus die entsprechenden Abhängigkeiten auswählen.)
      - Nur Mac: Wählen Sie die **macOS**-Plattform aus. (Hinweis: Sie müssen [**Xcode**](https://developer.apple.com/xcode/) installieren.)
      - Vollständig plattformübergreifende Xamarin-Apps: Wählen Sie die Plattformen **Android**, **iOS** und **macOS** aus.
   * **.NET Core-Anwendungen**: Wählen Sie die **.NET Core**-Plattform aus.
   * **ASP.NET Core-Webanwendungen**: Wählen Sie die **.NET Core**-Plattform aus.
   * **Entwicklung von plattformübergreifenden Unity-Spielen**: Neben Visual Studio für Mac müssen keine zusätzlichen Plattformen installiert werden. Weitere Informationen zur Installation der Unity-Erweiterung finden Sie im [Leitfaden zur Einrichtung von Unity](./setup-vsmac-tools-unity.md).

   Auf dieser Installationsseite wird die Version und Größe jeder einzelnen Komponente angezeigt. Sie können auf jede Komponente klicken, um eine Liste mit deren Abhängigkeiten (für Android), zusätzliche heruntergeladenen Pakete (für .NET Core) oder zusätzliche erforderliche Anwendungen (für iOS und macOS) anzuzeigen.

   ![Zusätzliche Abhängigkeiten von Android](media/installer-image6.png)

7. Sobald Sie mit Ihrer Auswahl zufrieden sind, klicken Sie auf die Schaltfläche **Installieren und aktualisieren**, um mit dem Installationsprozess zu beginnen.

8. Der Installer startet mit dem Download- und Installationsprozess der ausgewählten Elemente:

   ![Starten der Installation](media/installer-image7.png)

   ![Herunterladen von Xamarin.Mac](media/installer-image8.png)

   ![Fertigstellen der Installation](media/installer-image9.png)

9. Möglicherweise werden Sie dazu aufgefordert, die erforderlichen Berechtigungen für einzelne Komponenten zu erhöhen, die zum Abschluss der Installation erforderlich sind. Geben Sie hier Ihre Administratoranmeldeinformationen ein, um mit dem Installationsprozess fortzufahren:

   ![Eingeben der Berechtigungen zum Fortfahren des Installers](media/installer-image10.png)

10. Sobald die Installation erfolgreich abgeschlossen wurde, können Sie mit der Entwicklung von Apps in Visual Studio beginnen, indem Sie auf **Start** drücken.

    ![Öffnen Sie Visual Studio.](media/installer-image11.png)

> [!NOTE]
> Wenn Sie sich gegen die Installation einer Plattform oder eines Tools während der ursprünglichen Installation entschieden haben (indem Sie die Auswahl in Schritt 6 gelöscht haben), müssen Sie den [Installer](https://visualstudio.microsoft.com/vs/) erneut ausführen, wenn Sie die Komponenten später hinzufügen möchten.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installieren von Visual Studio für Mac hinter einer Firewall oder einem Proxyserver

Für die Installation von Visual Studio für Mac hinter einer Firewall müssen bestimmte Endpunkte zugänglich gemacht werden, um die Downloads der erforderlichen Tools und Updates für Ihre Software zuzulassen.

Konfigurieren Sie Ihr Netzwerk, damit der Zugriff auf die folgenden Speicherorte gewährt wird:

- [Visual Studio-Endpunkte](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Nächste Schritte

Die Installation von Visual Studio für Mac ermöglicht Ihnen das Schreiben von Code für Ihre Apps. Hinsichtlich der nächsten Schritte zum Schreiben und Bereitstellen von Projekten werden folgende Leitfäden bereitgestellt:

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Device Provisioning](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (Gerätebereitstellung) (zum Ausführen Ihrer Anwendung auf dem Gerät)

### <a name="android"></a>Android

1. [Using the Xamarin Android SDK Manager (Verwenden des Xamarin.Android SDK-Managers)](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK-Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Set Up Device for Development (Einrichten eines Geräts für die Entwicklung)](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Entwicklung von .NET Core-Apps, ASP.NET Core-Web-Apps und Unity-Spielen

Informationen zu anderen Workloads finden Sie auf der Seite zu den [Workloads](./workloads.md).

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Siehe auch

- [Installieren von Visual Studio 2017 (unter Windows)](/visualstudio/install/install-visual-studio)