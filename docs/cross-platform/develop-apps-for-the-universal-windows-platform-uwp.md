---
title: Entwickeln von Apps für die universelle Windows-Plattform (UWP)
description: Hier erfahren Sie mehr über das Erstellen von Apps mithilfe von Visual Studio und den Entwicklungstools der universellen Windows-App.
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: e9cff517c60a67ee9bbf929c59a1150d5ace3757
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671418"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Entwickeln von Apps für die universelle Windows-Plattform (UWP)

Mit Universelle Windows-Plattform und unserem zentralen Windows-Kern können Sie die gleiche App auf jedem Windows 10-Gerät ausführen, egal ob es sich um Smartphones oder Desktop-PCs handelt. Erstellen Sie diese universellen Windows-Apps mit Visual Studio und den universellen Windows-App-Entwicklungstools.

![Universelle Windows-Plattform](../cross-platform/media/uwp_coreextensions.png)

Führen Sie Ihre App auf einem Windows 10-Phone, Windows 10-Desktop oder einer Xbox aus. Es ist das gleiche App-Paket. Mit der Einführung eines einzelnen, einheitlichen Windows 10-Kerns kann ein App-Paket auf allen Plattformen ausgeführt werden. Mehrere Plattformen verfügen über Erweiterungs-SDKs, die Sie zu Ihrer App hinzufügen können, um die Vorteile bestimmter plattformspezifischer Verhaltensweisen zu nutzen. Mit dem Erweiterungs-SDK für Mobilgeräte wird z. B. die auf einem Windows Phone gedrückte ZURÜCK-Taste behandelt. Wenn Sie in Ihrem Projekt auf ein Erweiterungs-SDK verweisen, fügen Sie einfach Laufzeitüberprüfungen hinzu, um zu prüfen, ob dieses SDK für diese Plattform verfügbar ist. Auf dieses Weise können Sie das gleiche App-Paket für alle Plattformen verwenden.

**Was ist Windows Core?**

Zum ersten Mal wurde Windows so umgestaltet, dass ein gemeinsamer Kern für alle Windows 10-Plattformen verwendet wird. Es ist eine gemeinsame Quelle, ein gemeinsamer Windows-Kernel, ein Datei-E/A-Stapel und ein App-Modell vorhanden. Für die Benutzeroberfläche ist nur ein XAML-Benutzeroberlächen-Framework und ein HTML-Benutzeroberflächen-Framework vorhanden. Sie können sich auf das Entwickeln einer tollen App konzentrieren, weil wir die Bereitstellung Ihrer App auf unterschiedlichen Windows 10-Geräten vereinfacht haben.

**Was ist die Universelle Windows-Plattform?**

Universelle Windows-Plattform ist einfach eine Sammlung von Verträgen und Versionen. Mit diesen können Sie die Ziele auswählen, für die Ihre App ausgeführt werden kann. Ihr Ziel ist nicht länger ein Betriebssystem, sondern Sie können den Fokus auf eine oder mehrere Gerätefamilien legen. Weitere Informationen finden Sie unter [Einführung in Universelle Windows-Plattform](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Requirements (Anforderungen)

Die Entwicklungstools für universelle Windows-Apps verfügen über Emulatoren, die Sie verwenden können, um zu prüfen, wie Ihre App auf unterschiedlichen Geräten aussieht. Wenn Sie diesen Emulatoren verwenden möchten, müssen Sie diese Software auf einem physischen Computer installieren. Auf dem physischen Computer muss Windows 8.1 (X 64) Professional Edition oder höher installiert sein, und er muss über einen Prozessor verfügen, der Hyper-V für Clients und SLAT (Second Level Address Translation) unterstützt. Die Emulatoren können nicht verwendet werden, wenn Visual Studio auf einem virtuellen Computer installiert ist.

Hier finden Sie die Liste erforderlicher Softwarekomponenten:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017 unterstützt die UWP-Entwicklung nur unter Windows 10. Weitere Informationen finden Sie unter [Platform targeting](/visualstudio/productinfo/vs2017-compatibility-vs) (Zielplattformen) und [Systemanforderungen](/visualstudio/productinfo/vs2017-system-requirements-vs) auf Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Sie benötigen ebenso die Entwicklungsworkload von Universelle Windows-Plattform.

     ![UWP-Workload](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019 unterstützt die UWP-Entwicklung nur unter Windows 10. Weitere Informationen finden Sie unter [Platform targeting](/visualstudio/releases/2019/compatibility/) (Zielplattformen) und [Systemanforderungen](/visualstudio/releases/2019/system-requirements/) auf Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/downloads). Sie benötigen ebenso die Entwicklungsworkload von Universelle Windows-Plattform.

     ![UWP-Workload](media/uwp_workload.png)

::: moniker-end

Nach der Installation der Software müssen Sie Ihr Windows 10-Gerät für die Entwicklung aktivieren. Weitere Informationen finden Sie unter [Aktivieren von Geräten für die Entwicklung](/windows/uwp/get-started/enable-your-device-for-development). Eine Entwicklerlizenz für jedes Windows 10-Gerät wird nicht mehr benötigt.

## <a name="universal-windows-apps"></a>Universelle Windows-Apps

Wählen Sie aus C#, Visual Basic, C++ oder JavaScript Ihre bevorzugte Entwicklungssprache aus, um eine UWP-App für Geräte unter Windows 10 zu erstellen. Lesen Sie [Erstellen der ersten App](/windows/uwp/get-started/your-first-app), oder sehen Sie sich das Video [Tools for Windows 10 Overview (Übersicht über Tools für Windows 10)](https://channel9.msdn.com/Series/ConnectOn-Demand/229) an.

Wenn Sie über Windows Store 8.1-Apps, Windows Phone 8.1-Apps oder mit Visual Studio 2015 erstellte universelle Windows-Apps verfügen, müssen Sie diese Apps portieren, um die neueste Version von Universelle Windows-Plattform verwenden zu können. Weitere Informationen finden Sie unter [Wechsel von Windows-Runtime 8.x zu UWP](/windows/uwp/porting/w8x-to-uwp-root).

Nachdem Sie die universelle Windows-App erstellt haben, müssen Sie Ihre App packen, um sie auf einem Windows 10-Gerät zu installieren oder an den Windows Store zu übermitteln. Weitere Informationen finden Sie unter [Packaging apps (Packen von Apps)](/windows/uwp/packaging/index).

## <a name="see-also"></a>Siehe auch

- [Plattformübergreifende Mobile-Entwicklung in Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
