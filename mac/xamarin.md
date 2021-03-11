---
title: Xamarin
description: 'Wenn Sie Xamarin in Visual Studio für Mac verwenden, können Sie plattformübergreifende Anwendungen für iOS, Mac, Android, tvOS und watchOS erstellen. '
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: overview
ms.openlocfilehash: 41b26eb75454299aed86a3cdb3905d6c66efb098
ms.sourcegitcommit: 35fa920126b34c8d3839da53e3a4c2c6f509968f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2021
ms.locfileid: "102473347"
---
# <a name="xamarin-mobile-app-development"></a>Entwicklung mobiler Apps mit Xamarin

Mit der herausragenden Unterstützung für [Xamarin](/xamarin) können Sie beeindruckende native Benutzererfahrungen für Android, macOS, iOS, tvOS sowie watchOS entwickeln. Mit plattformübergreifenden Xamarin.Forms-Anwendungen können Sie XAML-basierten UI-Code zwischen Android, iOS und macOS freigeben, ohne den Zugriff auf native Funktionen einzuschränken.

## <a name="xamarinforms"></a>Xamarin.Forms

XAML Hot Reload für Xamarin.Forms ist ab Version 8.3 in Visual Studio für Mac integriert. Wenn dieses Feature aktiviert ist, werden Änderungen sofort in Ihrer ausgeführten App widergespiegelt, wenn Sie die Datei speichern.

Sie können XAML Hot Reload aktivieren, indem Sie das Kontrollkästchen **Neuladen von XAML im laufenden Betrieb aktivieren** unter **Visual Studio > Einstellungen > Projekte > Xamarin Hot Reload** aktivieren.

Weitere Informationen über Hot Reload finden Sie in der Dokumentation zu [XAML Hot Reload für Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

## <a name="android"></a>Android

Visual Studio für Mac verfügt über einen eigenen integrierten Android SDK-Manager, über den Sie auf die SDKs zugreifen können, auf die Ihre App ausgerichtet sein soll.

Für Android-Anwendungen enthält Visual Studio für Mac einen eigenen Designer, der mit `.axml`-Dateien für Android arbeitet, um Benutzeroberflächen visuell zu entwerfen. Visual Studio für Mac öffnet diese Dateien wie im folgenden Bild dargestellt in seinem Android Designer:

![Android-Benutzeroberflächen-Designer](media/intro-image31.png)

Weitere Informationen zum Android Designer finden Sie im Dokument [Xamarin.Android Designer Overview (Übersicht zum Xamarin.Android-Designer)](/xamarin/android/user-interface/android-designer/index).

## <a name="ios"></a>iOS

Der iOS Designer ist vollständig in Visual Studio für Mac integriert und ermöglicht die visuelle Bearbeitung von -xib- und Storyboard-Dateien, um Übergänge und Benutzeroberflächen für iOS, tvOS und WatchOS zu erstellen. Die gesamte Benutzeroberfläche kann erstellt werden, indem die Drag & Drop-Funktionen zwischen der Toolbox und der Entwurfsoberfläche verwendet werden, während ein intuitiver Ansatz zur Behandlung von Ereignissen verwendet wird. Der iOS Designer unterstützt auch [custom controls (benutzerdefinierte Steuerelemente)](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) mit dem zusätzlichen Vorteil von Rendering zur Entwurfszeit.

![iOS Storyboard-Designer](media/intro-image30.png)

Weitere Informationen zur Verwendung des iOS-Designers finden Sie in den Anleitungen zum [Designer](/xamarin/ios/user-interface/designer/?tabs=macos).

### <a name="mac"></a>Mac

Xamarin stellt native Mac-API-Bindungen bereit, die Ihnen die Erstellung ansprechender Mac-Anwendungen ermöglicht.

Weitere Informationen zum Schreiben von Mac-Anwendungen mit Visual Studio für Mac finden Sie in den [Xamarin.Mac](/xamarin/mac/get-started/index)-Anleitungen.

## <a name="xamarin-enterprise-features"></a>Xamarin Enterprise-Features

> [!Note]
> Diese Produkte können nur mit einem Abonnement für Visual Studio Enterprise verwendet werden.

### <a name="profiler"></a>Profiler

Der Xamarin Profiler verfügt über drei Instrumente zur Profilerstellung. Der Leitfaden [Introduction to the Xamarin Profiler (Einführung in den Xamarin Profiler)](/xamarin/tools/profiler/index?tabs=macos) erläutert, was diese Instrumente messen und wie sie Ihre Anwendung analysieren. Außerdem wird die Bedeutung der Daten verdeutlicht, die auf jedem Bildschirm dargestellt werden.

### <a name="inspector"></a>Inspector

Der Xamarin Inspector stellt eine interaktive C#-Konsole mit Benutzertools bereit. Er kann bei der Überprüfung aktiver Anwendungen beim Debuggen oder bei der Diagnose behilflich sein und weiterhin als Lerntool, Dokumentationstool oder Experimentiertool verwendet werden.

![Xamarin Inspector](media/intro-inspector.png)

Er besteht aus einer eigenständigen Anwendung, die eine umfangreiche und auf verschiedene Programmierplattformen (Android, iOS, Mac und Windows) ausgerichtete C#-Konsole und eine Integration in den Debuggingworkflow Ihrer IDE bereitstellt.

Weitere Informationen finden Sie im Leitfaden zum [Xamarin Inspector](/xamarin/tools/inspector/release-notes/1.5).
