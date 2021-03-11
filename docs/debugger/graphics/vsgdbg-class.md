---
description: Stellt eine Schnittstelle für die programmgesteuerte Kontrolle der In-App-Komponente der Grafikdiagnose dar.
title: VsgDbg-Klasse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a4847e0d6c72d4de611edc47481477d2862a55
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160459"
---
# <a name="vsgdbg-class"></a>VsgDbg-Klasse
Stellt eine Schnittstelle für die programmgesteuerte Kontrolle der In-App-Komponente der Grafikdiagnose dar.

## <a name="syntax"></a>Syntax

```C++
class VsgDbg;
```

## <a name="members"></a>Member
 Die `VsgDbg`-Klasse unterstützt die folgenden Member:

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)|Erstellt eine Instanz der `VsgDbg`-Klasse und bereitet optional die In-App-Komponente der Grafikdiagnose vor, Grafikinformationen aktiv zu erfassen und aufzuzeichnen.|
|[VsgDbg::~VsgDbg (Destructor)](vsgdbg-tilde-vsgdbg-destructor.md)|Zerstört eine Instanz der `VsgDbg`-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[AddMessage](addmessage.md)|Fügt dem Grafikdiagnose-HUD (Head-up-Display) eine benutzerdefinierte Meldung hinzu.|
|[BeginCapture](begincapture.md)|Startet ein Erfassungsintervall, das mit `EndCapture` endet.|
|[CaptureCurrentFrame](capturecurrentframe.md)|Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.|
|[Kopieren (Programmgesteuerte Aufzeichnung)](copy-programmatic-capture.md)|Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.|
|[EndCapture](endcapture.md)|Beendet ein Erfassungsintervall, das mit `BeginCapture` gestartet wurde.|
|[Init](init.md)|Bereitet die In-App-Komponente der Grafikdiagnose vor, um Grafikinformationen aktiv zu erfassen und aufzuzeichnen.|
|[ToggleHUD](togglehud.md)|Schaltet die Grafikdiagnose-HUD-Überlagerung ein oder aus.|
|[UnInit](uninit.md)|Schließt die Grafikprotokolldatei ab, schließt sie und gibt Ressourcen frei, die verwendet wurden, während die App aktiv Grafikinformationen aufzeichnete.|

## <a name="remarks"></a>Hinweise
 Die `VsgDbg`-Klasse stellt eine Schnittstelle dar, die Sie verwenden können, um Grafikdiagnosefunktionen programmgesteuert zu steuern. Sie können einige Funktionen sogar dann verwenden, wenn Sie Grafikinformationen nicht aktiv erfassen und aufzeichnen. Hierzu gehören die `AddMessage`-Memberfunktion und die `ToggleHUD`-Memberfunktion. Die anderen Memberfunktionen bereiten entweder die In-App-Komponente der Grafikdiagnose vor, um die aktive Erfassung von Grafikinformationen zu starten oder zu beenden, oder sie müssen aufgerufen werden, während die App aktiv Grafikinformationen in einer Grafikprotokolldatei erfasst und aufzeichnet.
