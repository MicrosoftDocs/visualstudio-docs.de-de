---
description: Wenn eine Liste lokaler Dateien angegeben ist, bestimmt diese Funktion, welche Dateien sich von den entsprechenden Versionen in der Quell Code Verwaltungs Datenbank unterscheiden.
title: Sccenumchangedfiles-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9349172ac60f1e02f82327424cdbc3a3b1d4f865
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221534"
---
# <a name="sccenumchangedfiles-function"></a>Sccenumchangedfiles-Funktion
Wenn eine Liste lokaler Dateien angegeben ist, bestimmt diese Funktion, welche Dateien sich von den entsprechenden Versionen in der Quell Code Verwaltungs Datenbank unterscheiden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 cFiles

in Anzahl der im Array angegebenen Dateinamen `lpFileNames` . Gibt auch die Größe des `plIsFileDifferent` Arrays an.

 lpfile-Namen

in Array der lokalen Dateinamen, die überprüft werden sollen.

 plisfiledifferent

[in, out] Ein Array von-Werten, die den Differenz Status der einzelnen Dateien angeben (Array muss mindestens `cFiles` Einträge aufweisen). Ungleich 0 bedeutet, dass die Datei anders ist.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Operation erfolgreich abgeschlossen.|
|SCC_UNSPECIFIEDERROR|Allgemeiner Fehler.|

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
