---
title: 'Vorgehensweise: Verwenden von Grafikdiagnose mit einem Arm-Gerät | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bbe12449849b656af2658c5bab667b0e611515e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685872"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Gewusst wie: Verwenden der Grafikdiagnose mit einem ARM-Gerät
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Grafikdiagnose unterstützt Remotedebugging von Direct3D-Apps auf ARM-basierten Geräten, auf denen Windows RT 8.1 oder Windows Phone 8.1. läuft. Sie können Grafikinformationen von Ihrer Direct3D-App erfassen, während diese auf dem Gerät läuft, oder das Gerät als Wiedergabecomputer für zuvor erfasste Grafikinformationen verwenden.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Verwendung der Grafikdiagnose mit einem ARM-basierten Gerät  
 Da Visual Studio nicht auf ARM-basierten Geräten läuft, müssen Sie den Remotedebugger verwenden, um Apps zu analysieren, die darauf laufen. Der Remotedebugger unterstützt Grafikerfassung und -wiedergabe, sodass Sie Rendering-Fehler diagnostizieren und die Grafikleistung auf diesen Geräten bewerten können. Dies ist so einfach wie das Debuggen Ihrer App.  
  
 Wenn Sie Grafikdiagnosefunktionen verwenden möchten, aktivieren Sie zunächst Remotedebugging auf Ihrem Gerät.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>So aktivieren Sie Remotedebugging auf Ihrem ARM-basierten Gerät  
  
1. Installieren Sie die [Arm-Kits-Richtlinie](https://msdn.microsoft.com/windows/desktop/dn469188) auf Ihrem Arm-basierten Gerät.  
  
2. Installieren Sie die [Remotedebugtools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) auf Ihrem Arm-basierten Gerät.  
  
> [!IMPORTANT]
> Im Falle von Windows Phone 8.1-Geräten müssen Sie Ihr Gerät eventuell für die Entwicklung registrieren. Dafür müssen Sie ein registrierter Entwickler sein. Weitere Informationen finden Sie unter Bereitstellen [und Ausführen einer APP für Windows Phone 8](https://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Wenn Sie Remotedebugging auf Ihrem Gerät aktiviert haben, machen Sie dieses zu Ihrem Debugging-Ziel, und starten Sie die Grafikdiagnose.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>So konfigurieren und starten Sie die Grafikdiagnose auf Ihrem Gerät  
  
1. Wählen Sie in der Dropdown Liste Projektmappenplattformen die Option **Arm** , sodass Ihr Arm-basiertes Gerät als remotedebuggingziel verfügbar ist. **Solution Platforms**  
  
2. Wählen Sie in der Dropdown Liste **Debugziel** Ihr Arm-Gerät aus.  
  
3. Klicken Sie im Menü auf **Debuggen**, **Grafik**und **Diagnose starten**. (Tastatur: Alt+F5)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Windows Store-Apps auf einem Remote Computer](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Vorgehensweise: Ändern des Grafikdiagnose-Wiedergabecomputers](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
