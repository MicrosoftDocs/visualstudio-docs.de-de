---
title: Sccdirdiff-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b7f045669a0d4b7e4e206c6ad8e85db55edc4ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929211"
---
# <a name="sccdirdiff-function"></a>Sccdirdiff-Funktion
Diese Funktion zeigt die Unterschiede zwischen dem aktuellen lokalen Verzeichnis auf dem Client Datenträger und dem entsprechenden Projekt unter Quell Code Verwaltung an.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pContext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpdirname

in Der voll qualifizierte Pfad zum lokalen Verzeichnis, für das ein visueller Unterschied angezeigt werden soll.

 dwFlags

in Befehlsflags (siehe Abschnitt "Hinweise").

 pvoptions

in Plug-in-spezifische Optionen für die Quell Code Verwaltung.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Das Verzeichnis auf dem Datenträger ist mit dem Projekt in der Quell Code Verwaltung identisch.|
|SCC_I_FILESDIFFER|Das Verzeichnis auf dem Datenträger unterscheidet sich von dem Projekt in der Quell Code Verwaltung.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|
|SCC_E_FILENOTCONTROLLED|Das Verzeichnis befindet sich nicht unter Quell Code Verwaltung.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|
|SCC_E_FILENOTEXIST|Das lokale Verzeichnis konnte nicht gefunden werden.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird verwendet, um das Quellcodeverwaltungs-Plug-in anzuweisen, dem Benutzer eine Liste von Änderungen an einem angegebenen Verzeichnis anzuzeigen. Das Plug-in öffnet ein eigenes Fenster im Format seiner Wahl, um die Unterschiede zwischen dem Verzeichnis des Benutzers auf dem Datenträger und dem entsprechenden Projekt unter Versionskontrolle anzuzeigen.

 Wenn ein Plug-in den Vergleich der Verzeichnisse unterstützt, muss es den Vergleich von Verzeichnissen auf Dateinamen Basis unterstützen, auch wenn die Optionen für "schnell Vergleich" nicht unterstützt werden.

|`dwFlags`|Interpretation|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Vergleich ohne Berücksichtigung der Groß-/Kleinschreibung (kann sowohl für kurze Unterschiede als auch für Visual verwendet werden)|
|SCC_DIFF_IGNORESPACE|Ignoriert Leerraum (kann sowohl für die schnell-als auch für die Visualisierung verwendet werden).|
|SCC_DIFF_QD_CONTENTS|Wenn das Quellcodeverwaltungs-Plug-in unterstützt wird, wird das Verzeichnis, Byte mit Byte, im Hintergrund verglichen.|
|SCC_DIFF_QD_CHECKSUM|Wenn das Plug-in vom Plug-in unterstützt wird, wird das Verzeichnis automatisch über eine Prüfsumme verglichen oder, falls nicht unterstützt, auf SCC_DIFF_QD_CONTENTS zurückgegriffen.|
|SCC_DIFF_QD_TIME|Wenn das Plug-in vom Plug-in unterstützt wird, wird das Verzeichnis automatisch über den Zeitstempel verglichen, oder, falls nicht unterstützt, wird auf SCC_DIFF_QD_CHECKSUM oder SCC_DIFF_QD_CONTENTS zurückgegriffen.|

> [!NOTE]
> Diese Funktion verwendet die gleichen [Befehlsflags wie der sccdiff](../extensibility/sccdiff-function.md). Ein Quellcodeverwaltungs-Plug-in kann jedoch den Vorgang "schnell Vergleich" für Verzeichnisse nicht unterstützen.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
