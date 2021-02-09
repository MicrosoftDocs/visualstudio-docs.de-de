---
title: Nachrichtenenumerator | Microsoft-Dokumentation
description: Die Member dieses Enumerators werden für die textoutproc-Funktion verwendet, bei der es sich um eine Rückruffunktion handelt, die die IDE beim Aufrufen von sccopenproject bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00d6b3e27b87e4bac8cee196a60e7fc934f6187d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886742"
---
# <a name="message-enumerator"></a>Nachrichtenenumerator
Die folgenden Flags werden für die- `TEXTOUTPROC` Funktion verwendet, bei der es sich um eine Rückruffunktion handelt, die die IDE beim Aufrufen von [sccopenproject](../extensibility/sccopenproject-function.md) bereitstellt (Weitere Informationen zur Rückruffunktion finden Sie unter [lptextoutproc](../extensibility/lptextoutproc.md) ).

 Wenn die IDE aufgefordert wird, den Prozess abzubrechen, erhält Sie möglicherweise eine der Abbruch Nachrichten. In diesem Fall verwendet das Quellcodeverwaltungs-Plug-in `SCC_MSG_STARTCANCEL` , um die IDE zum Anzeigen der Schaltfläche **Abbrechen** aufzufordern. Danach können alle normalen Nachrichten gesendet werden. Wenn eine dieser zurückgibt `SCC_MSG_RTN_CANCEL` , beendet das Plug-in den Vorgang und gibt zurück. Das Plug-in fragt auch `SCC_MSG_DOCANCEL` regelmäßig ab, ob der Benutzer den Vorgang abgebrochen hat. Wenn alle Vorgänge abgeschlossen sind, oder wenn der Benutzer abgebrochen wurde, sendet das Plug-in `SCC_MSG_STOPCANCEL` . Die `SCC_MSG_INFO` Typen, SCC_MSG_WARNING und SCC_MSG_ERROR werden für Nachrichten verwendet, die in der scrollliste der Nachrichten angezeigt werden. `SCC_MSG_STATUS` ein spezieller Typ, der angibt, dass der Text in einer Statusleiste oder einem temporären Anzeigebereich angezeigt werden soll. Er bleibt nicht dauerhaft in der Liste.

## <a name="syntax"></a>Syntax

```
enum { 
   SCC_MSG_RTN_CANCEL = -1, 
   SCC_MSG_RTN_OK = 0, 
   SCC_MSG_INFO = 1 
   SCC_MSG_WARNING, 
   SCC_MSG_ERROR, 
   SCC_MSG_STATUS, 
   SCC_MSG_DOCANCEL, 
   SCC_MSG_STARTCANCEL, 
   SCC_MSG_STOPCANCEL 
};
```

## <a name="members"></a>Member
 SCC_MSG_RTN_CANCEL Rückgabe von Callback, um den Abbruch anzugeben.

 SCC_MSG_RTN_OK vom Rückruf zurück, um den Vorgang fortzusetzen.

 SCC_MSG_INFO Meldung dient nur zu Informationszwecken.

 SCC_MSG_WARNING Meldung ist eine Warnung.

 SCC_MSG_ERROR Meldung ist ein Fehler.

 SCC_MSG_STATUS Nachricht ist für die Status Leiste vorgesehen.

 SCC_MSG_DOCANCEL keinen Text; IDE gibt `SCC_MSG_RTN_OK` oder zurück `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL startet eine Abbruch Schleife.

 SCC_MSG_STOPCANCEL beendet die Cancel-Schleife.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
