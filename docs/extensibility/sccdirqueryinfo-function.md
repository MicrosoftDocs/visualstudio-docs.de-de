---
title: Sccdirqueryinfo-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d15809623067d9612eb2648d593264d61f08f6e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943087"
---
# <a name="sccdirqueryinfo-function"></a>Sccdirqueryinfo-Funktion
Mit dieser Funktion wird eine Liste der voll qualifizierten Verzeichnisse für Ihren aktuellen Status überprüft.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parameter
 pContext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 ndirs

in Die Anzahl der Verzeichnisse, die abgefragt werden sollen.

 lpdirnames

in Ein Array von voll qualifizierten Pfaden der Verzeichnisse, die abgefragt werden sollen.

 lpstatus

[in, out] Eine Array Struktur für das Quellcodeverwaltungs-Plug-in zum Zurückgeben der Statusflags (Weitere Informationen finden Sie unter [Verzeichnis Statuscode](../extensibility/directory-status-code-enumerator.md) ).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Abfrage war erfolgreich.|
|SCC_E_OPNOTSUPPORTED|Das Quell Code Verwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Die-Funktion füllt das Rückgabe Array mit einer Bitmaske von Bits aus der- `SCC_DIRSTATUS` Familie (siehe [Verzeichnis Statuscode](../extensibility/directory-status-code-enumerator.md)), einem Eintrag für jedes angegebene Verzeichnis. Das Status Array wird vom Aufrufer zugeordnet.

 Die IDE verwendet diese Funktion, bevor ein Verzeichnis umbenannt wird, um zu überprüfen, ob das Verzeichnis der Quell Code Verwaltung unterliegt, indem abgefragt wird, ob es ein entsprechendes Projekt aufweist. Wenn das Verzeichnis nicht der Quell Code Verwaltung unterliegt, kann die IDE dem Benutzer die richtige Warnung bereitstellen.

> [!NOTE]
> Wenn ein Quellcodeverwaltungs-Plug-in einen oder mehrere der Statuswerte nicht implementiert, sollten nicht implementierte Bits auf 0 (null) festgelegt werden.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Verzeichnis Statuscode](../extensibility/directory-status-code-enumerator.md)
