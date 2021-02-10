---
title: Grafikframe-Überprüfung | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Tool „Frame-Überprüfung“ für Grafiken in Visual Studio. In diesem Tool werden Fehler und Warnungen im Zusammenhang mit der Ereignisliste angezeigt.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d52d04565b03d988d5d01a64e561fc0da8a16e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885247"
---
# <a name="graphics-frame-validation"></a>Grafikframe-Überprüfung
<!-- VERSIONLESS -->
Ab Visual Studio 2017 wird das Tool **Frame-Überprüfung** unterstützt.  Im Fenster „Frame-Überprüfung“ werden Fehler und Warnungen im Zusammenhang mit der Ereignisliste angezeigt.  Um dieses Fenster anzuzeigen, wählen Sie das Menü **Ansicht > Frame-Überprüfung** aus.

![Frame-Überprüfung](media/gfx_diag_frame_validation.png)

Klicken Sie in der linken oberen Ecke auf die Schaltfläche **Überprüfung ausführen**, um die Analyse zu initiieren.  Je nach Komplexität des Frames kann dieser Vorgang mehrere Minuten dauern.  Die hier angezeigten Daten sind eine Kombination aus zwei Quellen: den Nachrichten, die D3D ausgibt, wenn [SDK-Layer](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) aktiviert sind, und den Daten, die von der eigenen internen Zustandsüberwachung des Tools gesammelt werden. Nach Abschluss des Vorgangs werden mehrere Datenspalten angezeigt:

| **Spalte** | **Beschreibung** |
|------------| - |
| Ereignis-ID | ID, die einem Eintrag im Fenster [Ereignisliste](graphics-event-list.md) zugeordnet ist. |
| Schweregrad | Beschädigung, Fehler, Warnung, Info oder Meldung. |
| Kategorie | Anwendung definiert, Verschiedenes, Initialisierung, Bereinigung, Kompilierung, Zustandserstellung, Zustandseinstellung, Zustandsabruf, Ausführung, Ressourcenbearbeitung, Shader, Redundant und Nicht verwendet. |
| Meldung | Die dem Ereignis zugeordnete Meldung. |
| event | Das dem Fehler oder der Warnung zugeordnete Ereignis. |

## <a name="see-also"></a>Siehe auch
[Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->