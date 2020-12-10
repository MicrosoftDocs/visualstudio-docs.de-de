---
title: Verzeichnis Status Code-Enumerator | Microsoft-Dokumentation
description: Der sccdirstatus-Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses im Quell Code Verwaltungssystem angeben und von sccdirqueryinfo verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af72b9e14695cb954084abebc3a3c336c90af73d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996122"
---
# <a name="directory-status-code-enumerator"></a>Verzeichnis Statuscode-Enumerator
Der `SccDirStatus` Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses im Quell Code Verwaltungssystem angeben. Diese Enumeration wird von [sccdirqueryinfo](../extensibility/sccdirqueryinfo-function.md)verwendet. Dies wurde in Version 1,2 der Quellcodeverwaltungs-Plug-in-API eingeführt.

## <a name="syntax"></a>Syntax

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Member
 SCC_DIRSTATUS_INVALID Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.

 SCC_DIRSTATUS_NOTCONTROLLED Verzeichnis befindet sich nicht unter Quell Code Verwaltung.

 SCC_DIRSTATUS_CONTROLLED Verzeichnis befindet sich unter Quell Code Verwaltung.

 SCC_DIRSTATUS_EMPTYPROJ Projekt, das diesem Verzeichnis entspricht, ist leer.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
