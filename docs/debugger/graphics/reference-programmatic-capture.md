---
title: Verweis (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
description: Verwenden der programmgesteuerten Erfassungs-API, um die Erfassungsfunktionen der Grafikdiagnose programmgesteuert zu steuern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30cf44d6d16da46e9d6f08ffae4971d35136db58
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996109"
---
# <a name="reference-programmatic-capture"></a>Verweis (Programmgesteuerte Aufzeichnung)
Die Grafikdiagnose unterstützt die programmgesteuerte Kontrolle über ihre Erfassungsfunktionen durch die programmgesteuerte Erfassungs-API. Sie können diese API verwenden, um Meldungen an das Grafikdiagnose-HUD (Head-Up-Display) ein- und auszuschalten und hinzuzufügen, Grafikprotokolldateien zu initialisieren und zu erstellen und Grafikinformationen zu erfassen.

## <a name="programmatic-capture-apis"></a>Programmgesteuerte Erfassungs-APIs

### <a name="classes"></a>Klassen

|name|Beschreibung|
|----------|-----------------|
|[VsgDbg-Klasse](vsgdbg-class.md)|Stellt die Schnittstelle dar, durch die die In-App-Komponente der Grafikdiagnose programmgesteuert kontrolliert wird.|

### <a name="preprocessor-symbols"></a>Präprozessorsymbole

|name|Beschreibung|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definiert durch das Vorhandensein, ob die Grafikprotokolldatei im Verzeichnis der temporären Dateien des Benutzers gespeichert wird.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definiert den Standarddateinamen der Grafikprotokolldatei.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definiert durch das Vorhandensein, ob eine Standardinstanz der `VsgDbg`-Klasse bereitgestellt wird.|

## <a name="related-articles"></a>Verwandte Artikel

| Titel | Beschreibung |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Zeigt wie Grafikinformationen aus Ihrer DirectX-basierten App erfasst werden können, sodass Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Grafikdiagnosetools verwenden können, um Renderingprobleme zu diagnostizieren. |
| [Übersicht](overview-of-visual-studio-graphics-diagnostics.md) | Zeigt, wie die Grafikdiagnose helfen kann, Renderingfehler in DirectX-Spielen und -Apps zu debuggen. |
