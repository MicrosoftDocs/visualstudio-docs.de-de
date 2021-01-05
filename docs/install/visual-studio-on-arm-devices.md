---
title: Visual Studio auf ARM-basierten Geräten
description: Empfehlungen zum Einsatz von Visual Studio auf Geräten mit ARM-basierten Prozessoren.
ms.date: 09/10/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 367b3681d2ff8a828ee45f59359043b5fede3d26
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668104"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio auf ARM-basierten Geräten

> [!IMPORTANT]
> Visual Studio wird nur auf Geräten unterstützt, die einen x86- oder AMD64/x64-basierten Prozessor verwenden.

Visual Studio ist auf Prozessoren ausgerichtet, die auf der x86-Architektur basieren, und es gibt keine Versionen von Visual Studio für ARM-basierte Prozessoren. Windows bietet jedoch [x86-Emulation auf ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), die von Visual Studio ausgeführt werden kann. Durch das Ausführen von Visual Studio auf einem ARM-Prozessor über eine x86-Emulation wird die Leistung von Visual Studio stark beeinträchtigt, und verschiedene Funktionen in Visual Studio sind nicht für die Verwendung in diesem Szenario konzipiert. Daher sollte Visual Studio nicht auf Geräten ausgeführt werden, die ARM-basierte Prozessoren verwenden. Stattdessen sollten Remote-ARM-Geräte verwendet werden.

## <a name="remote-targeting-arm-devices"></a>Remote-ARM-Geräte
Um die optimale Leistung zu erzielen, sollten Sie Visual Studio auf einem separaten, x86-gestützten Computer einsetzen und die Remotebereitstellungs- und Debugfunktionen in Visual Studio verwenden, um das ARM-basierte Gerät zu verwenden. Informationen zum Debuggen von bereits auf dem Gerät installierten universellen Windows-Anwendungen finden Sie in der Dokumentation [Installiertes App-Paket debuggen](../debugger/debug-installed-app-package.md). Informationen zum Bereitstellen einer neuen App finden Sie unter [Debuggen von UWP-Apps auf Remotecomputern in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md). Informationen zu allen anderen Anwendungstypen finden Sie in der Dokumentation [Remote Debugging](../debugger/remote-debugging.md).

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Tipps zum Ausführen von Visual Studio auf ARM-Geräten

### <a name="use-only-when-needed"></a>Nur bei Bedarf anwenden
Optimieren Sie Ihre Zeit, indem Sie Visual Studio nur dann für ARM-spezifische Arbeit verwenden, wenn es erforderlich ist. Die Leistung ist auf allen ARM-Geräten schlecht, und Sie werden sie wahrscheinlich für die reguläre Verwendung ungeeignet finden.

### <a name="install-time"></a>Installationszeit
Planen Sie für Visual Studio eine längere Installationszeit ein, und gehen Sie davon aus, dass die Installation zeitweise stockt oder ein Neustart erforderlich ist.
 
### <a name="remote-tools"></a>Remotetools
Um eine App zu debuggen, die auf einem Remotegerät ausgeführt wird, müssen Sie die [Remotetools für ARM herunterladen und installieren](../debugger/remote-debugging.md#download-and-install-the-remote-tools).

### <a name="start-debugging-f5"></a>Debuggen starten (F5)
Nicht alle Visual Studio-Projekte sind so konfiguriert, dass Projekte lokal gestartet werden, wenn Sie das Debuggen (**F5**) auf einem ARM-Gerät starten. Möglicherweise müssen Sie Visual Studio auch dann für das Remotedebuggen konfigurieren, wenn Ihre App lokal ausgeführt wird. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Wir benötigen Ihre Hilfe!
Wenn Sie möchten, dass Visual Studio nativ auf ARM-Geräten ausgeführt wird, würden wir uns freuen, von Ihnen etwas über die Szenarios und die notwendige Unterstützung zu erfahren. Sie erreichen uns, indem Sie Beiträge in der [Entwicklercommunity](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html) veröffentlichen.
