---
title: User (VSPerfCmd) | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur User-Option. Diese gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des Prozesses ist, für den ein Profil erstellt wurde.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0240a4dcf0830dca6667bcbd055d677ef7bc204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886001"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
Die **User**-Option gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte **Prozesse** in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.

 Die **User**-Option kann nur in einer Befehlszeile angegeben werden, die auch die **Start**-Option enthält.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parameter
 `Domain`: der Name der Domäne des Benutzers.

 `UserName`: der Name des Benutzers.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option **User** kann nur mit der Option **Start** verwendet werden.

 **Start:** `Method` initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung der **User**-Option gezeigt.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
