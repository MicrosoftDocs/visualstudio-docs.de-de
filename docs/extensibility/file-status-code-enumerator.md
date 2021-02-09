---
title: Datei Status Code-Enumerator | Microsoft-Dokumentation
description: Der sccstatus-Enumerator enthält Konstante Werte, die den Status einer Datei im Quell Code Verwaltungssystem angeben und von sccqueryinfo und poplistfunc verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 981e4e4561db7bc7fb8a9f0ce92522d34e4b34fa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874047"
---
# <a name="file-status-code-enumerator"></a>Dateistatus Code-Enumerator
Der `SccStatus` Enumerator enthält benannte Konstante Werte, die den Zustand einer Datei im Quell Code Verwaltungssystem angeben. Diese Enumeration wird von der [sccqueryinfo](../extensibility/sccqueryinfo-function.md) -Funktion und der `POPLISTFUNC` Callback-Funktion verwendet (Weitere Informationen finden Sie unter [poplistfunc](../extensibility/poplistfunc.md) ).

## <a name="syntax"></a>Syntax

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Member
 SCC_STATUS_INVALID Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.

 SCC_STATUS_NOTCONTROLLED Datei befindet sich nicht unter Quell Code Verwaltung.

 SCC_STATUS_CONTROLLED Datei befindet sich unter Quell Code Verwaltung.

 SCC_STATUS_CHECKEDOUT vom aktuellen Benutzer auf dem lokalen Datenträger ausgecheckt.

 SCC_STATUS_OUTOTHER Datei wird von einem anderen Benutzer ausgecheckt.

 SCC_STATUS_OUTEXCLUSIVE Datei ist exklusiv ausgecheckt.

 SCC_STATUS_OUTMULTIPLE Datei wird von mehr als einem Benutzer ausgecheckt.

 SCC_STATUS_OUTOFDATE ist die Datei nicht die aktuellste.

 SCC_STATUS_DELETED Datei wurde aus dem Projekt gelöscht.

 SCC_STATUS_LOCKED Datei ist gesperrt. Es sind keine weiteren Versionen zulässig.

 SCC_STATUS_MERGED Datei wurde zusammengeführt, aber noch nicht korrigiert/überprüft.

 SCC_STATUS_SHARED Datei wird von Projekten gemeinsam verwendet.

 SCC_STATUS_PINNED Datei ist für eine explizite Version freigegeben.

 SCC_STATUS_MODIFIED Datei wurde geändert/beschädigt/verletzt.

 SCC_STATUS_OUTBYUSER Datei wird vom aktuellen Benutzer ausgecheckt.

 SCC_STATUS_NOMERGE Datei kann nie zusammengeführt werden und muss nicht vor einem Get-Zeitpunkt gespeichert werden.

 SCC_STATUS_RESERVED_1 für die interne Verwendung reserviert.

 SCC_STATUS_RESERVED_2 für die interne Verwendung reserviert.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
