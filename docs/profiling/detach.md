---
title: Trennen | Microsoft-Dokumentation
description: Verwenden Sie die Option Detach von VSPerfCmd.exe, um die Verbindung zwischen dem Profiler und den angegebenen Prozessen zu trennen (oder allen Prozessen, wenn keine bestimmten angegeben sind).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45225e4478b0a1a3cddc7f74ae223c437bf4226e
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686596"
---
# <a name="detach"></a>Trennen
Die VSPerfCmd.exe-Option **Detach** (Trennen) trennt die Verbindung zwischen dem Profiler und den angegebenen Prozessen oder allen Prozessen, falls keine angegeben sind. Die Profilerstellung muss über die Samplingmethode initialisiert worden sein.

 Die Profilerstellung, die entweder mit der Option **Launch** (Starten) oder **Attach** (Anfügen) gestartet wurde, kann nun mit **Detach** getrennt werden. Der Profiler kann mithilfe anschließender **Attach**-Befehle erneut angefügt werden.

 **Detach** schließt die Datendatei der Profilerstellung nicht. Verwenden Sie die Option **Shutdown**, um die Profilerstellung zu beenden und die Datendatei zu schließen.

> [!NOTE]
> Wenn die Option **CrossSession** für die Option **Start** angegeben wurde, müssen alle Aufrufe von **VSPerfCmd /Attach** oder **VSPerfCmd /Detach** auch **CrossSession** angeben.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parameter
 `PIDs|ProcessNames` `PID`: Der numerische Systembezeichner für einen oder mehrere Prozesse.

 `ProcessNames`: der Prozessname Wenn mehrere Instanzen des benannten Prozesses ausgeführt werden, sind die Ergebnisse unvorhersehbar.

 Trennt mehrere Prozesse mit Komma voneinander ab.

 Wenn kein Prozess angegeben ist, wird der Profiler von allen Prozessen, für die ein Profil erstellt wird, getrennt.

## <a name="valid-options"></a>Gültige Optionen
 Die folgenden **VSPerfCmd**-Optionen können mit der Option **Attach** in derselben Befehlszeile kombiniert werden.

 **CrossSession:** aktiviert die Profilerstellung für Anwendungen in Sitzungen, die keine Anmeldesitzungen sind. Diese Option ist erforderlich, wenn die Option **Start** mit der Option **CrossSession** angegeben wurde.

## <a name="example"></a>Beispiel
 In diesem Fall hält der Befehl **Detach** die Profilerstellung an, und der Befehl **Shutdown** schließt die Profilerdatendatei.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
