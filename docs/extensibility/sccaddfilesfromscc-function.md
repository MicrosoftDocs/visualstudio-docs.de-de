---
description: Diese Funktion fügt eine Liste von Dateien aus der Quell Code Verwaltung dem aktuell geöffneten Projekt hinzu.
title: Sccaddfilesfromscc-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27b695b2777aa32f77d49ced7b74436ce870df80
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220975"
---
# <a name="sccaddfilesfromscc-function"></a>Sccaddfilesfromscc-Funktion
Diese Funktion fügt eine Liste von Dateien aus der Quell Code Verwaltung dem aktuell geöffneten Projekt hinzu.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpuser

[in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Terminator).

 lpauxprojpath

[in, out] Zusätzliche Zeichenfolge, die das Projekt identifiziert (bis zur `SCC_PRJPATH_` Größe, einschließlich des NULL-Terminator).

 cFiles

in Anzahl von Dateien, die von angegeben werden `lpFilePaths` .

 lpfilepath

[in, out] Array von Dateinamen, die dem aktuellen Projekt hinzugefügt werden sollen.

 lpdestination

in Der Zielpfad, in den die Dateien geschrieben werden sollen.

 lpcomment

in Der Kommentar, der auf jede der hinzugefügten Dateien angewendet werden soll.

 pbresults

[in, out] Ein Array von Flags, die festgelegt werden, um einen Erfolg (ungleich 0 oder true) oder einen Fehler (null oder false) für jede Datei anzugeben (die Größe des Arrays muss mindestens `cFiles` lang sein).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht geöffnet.|
|SCC_E_OPNOTPERFORMED|Die Verbindung ist nicht mit dem Projekt identisch, das von angegeben wird. `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, die Datenbank zu aktualisieren.|
|SCC_E_NONSPECIFICERROR|Unbekannter Fehler.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
