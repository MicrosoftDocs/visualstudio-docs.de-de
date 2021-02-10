---
title: VSPerfASPNetCmd | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit dem Befehlszeilentool VSPerfASPNetCmd.exe ASP.NET-Websites profilen können, ohne dass Sie Umgebungsvariablen festlegen oder Ihren Computer neu starten müssen.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1d886284a130d9c103d2f0d8a6bc24d2ebd69b6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911626"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Mit dem Befehlszeilentool **VSPerfASPNetCmd.exe** können Sie ein Profil für ASP.NET-Websites erstellen, ohne dass Sie Umgebungsvariablen festlegen und ohne dass Sie Ihren Computer neu starten müssen. Verwenden Sie statt [VSPerfCmd](../profiling/vsperfcmd.md)**VSPerfASPNetCmd.exe**, wenn Sie eine ASP.NET-Website profilen. Dann benötigen Sie nicht die zusätzlichen Funktionen, die **VSPerfCmd** bereitstellt. Weitere Informationen zu **VSPerfASPNETCmd** finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** ist das bevorzugte Befehlszeilentool, wenn mit dem eigenständigen Profiler ein Profil für ASP.NET-Websites erstellt wird.

## <a name="syntax"></a>Syntax
 **vsperfaspnetcmd** [/*Optionen*] *Website*

## <a name="options"></a>Optionen

|Option|Beschreibung|
|------------|-----------------|
|**/Sample** oder **/s**|Erstellt Profile für Websites mit der Samplingmethode. **/Sample** ist die Standardmethode. /Sample kann nicht mit **/Trace** verwendet werden.|
|**/Trace** oder **/t**|Erstellt Profile für Websites mit der Instrumentationsmethode. /Trace kann nicht mit **/Sample** verwendet werden.|
|**/Memory**[ **:** `Type`] oder **/m**[ **:** {**a**&#124;**l**}]|Erstellt ein Profil für die Arbeitsspeicherzuweisung und erstellt optional Profile für Objektlebensdauern (automatische Speicherbereinigung). **/Memory** kann weder mit der Sampling- noch mit der Instrumentationsmethode verwendet werden.<br /><br /> Als *Type* kann eines der folgenden Elemente verwendet werden:<br /><br /> -   **allocation** (oder **a**) erfasst nur Daten zur Arbeitsspeicherzuweisung<br />-   **lifetime** (oder **l**) erfasst Daten zur Speicherbelegung und zur Objektlebensdauer.<br /><br /> Der Standard-`Type` ist **allocation**.|
|**/Tip** oder **/i**|Fügt eine ausführliche ASP.NET-Anforderung und einen ADO.NET-Aufrufinformationen zu den Profilerstellungsdaten hinzu **/Tip** kann mit der Sampling- oder der Instrumentationsmethode verwendet werden und mit der Option **/Memory**.|
|**/Output:** `File` oder **/o:**`File`|Gibt den Namen und den Speicherort der Profilerstellungs-Datendatei (*VSP-Datei*) an|
|**/NoWait** oder **/n**|Gibt die Eingabeaufforderung sofort wieder zurück, damit zusätzliche Befehle im Eingabeaufforderungsfenster verwendet werden können. Sie müssen **VSPerfASPNETCmd /Shutdown** in eine Befehlszeile eingeben, um die Profilerstellung zu deaktivieren|
|**/PackSymbols**[:{**on**&#124;**off**} oder **/p**[:{**on**&#124;**off**}|Bettet Symbole (Funktions- und Parameternamen usw.) in Profilerstellungs-Datendateien ein ( *.vsp*).|
|**/Shutdown:** `Website`oder **/d:**`Website`|Deaktiviert die Profilerstellung Verwenden Sie diese Option in einer Befehlszeile nachdem Sie die Option **/NoWait** verwendet haben, um die Profilerstellung zu starten, oder wenn der Profiler unerwartet beendet wurde. Geben Sie die gleiche URL an, die Sie im ursprünglichen **VSPerfASPNETCmd**-Befehl verwendet haben.|
|`Website`|Die URL der Website, für die ein Profil erstellt werden soll|

## <a name="see-also"></a>Siehe auch
- [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
