---
title: Sccgetevents-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4502dd1cdf5cb23f317cd29bee74460c5911482c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965160"
---
# <a name="sccgetevents-function"></a>Sccgetevents-Funktion
Diese Funktion Ruft ein Status Ereignis in der Warteschlange ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 lpFileName

[in, out] Puffer, in dem das Quellcodeverwaltungs-Plug-in den zurückgegebenen Dateinamen einfügt (bis _MAX_PATH Zeichen).

 lpstatus

[in, out] Gibt den Statuscode zurück (siehe [Dateistatus Code](../extensibility/file-status-code-enumerator.md) für mögliche Werte).

 pnetventsrestdauer

[in, out] Gibt nach diesem-Befehl die Anzahl der in der Warteschlange verbleibenden Einträge zurück. Wenn diese Zahl groß ist, kann der Aufrufer den Aufruf von [sccqueryinfo](../extensibility/sccqueryinfo-function.md) durchsetzen, um alle Informationen gleichzeitig abzurufen.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Get-Ereignisse erfolgreich.|
|SCC_E_OPNOTSUPPORTED|Diese Funktion wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird während der Leerlauf Verarbeitung aufgerufen, um zu überprüfen, ob für Dateien unter Quell Code Verwaltung Statusaktualisierungen vorhanden sind. Das Quellcodeverwaltungs-Plug-in verwaltet den Status aller bekannten Dateien. Wenn eine Änderung des Status durch das Plug-in angegeben wird, werden der Status und die zugehörige Datei in einer Warteschlange gespeichert. Wenn `SccGetEvents` aufgerufen wird, wird das oberste Element der Warteschlange abgerufen und zurückgegeben. Diese Funktion ist so eingeschränkt, dass nur zuvor zwischengespeicherte Informationen zurückgegeben werden, und es muss sich um eine sehr schnelle Ablauf Steuerung (d. h. das Lesen des Datenträgers oder das Abrufen des Status des Quell Code Verwaltungssystems) Andernfalls kann die Leistung der IDE zu einer Herabstufung werden.

 Wenn keine Statusaktualisierung vorhanden ist, speichert das Quellcodeverwaltungs-Plug-in eine leere Zeichenfolge im Puffer, auf die von verwiesen wird `lpFileName` . Andernfalls speichert das Plug-in den vollständigen Pfadnamen der Datei, für die die Statusinformationen geändert wurden, und gibt den entsprechenden Statuscode zurück (einen der Werte, der im [Dateistatus Code](../extensibility/file-status-code-enumerator.md)ausführlich erläutert wird).

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Dateistatus Code](../extensibility/file-status-code-enumerator.md)
