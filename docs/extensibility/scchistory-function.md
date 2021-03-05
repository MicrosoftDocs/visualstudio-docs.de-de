---
description: Diese Funktion zeigt den Verlauf der angegebenen Dateien an.
title: Scchistory-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b7e1cd6fa6d5b9b3a5ab42cd1b4cafec215deca
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220572"
---
# <a name="scchistory-function"></a>SccHistory-Funktion
Diese Funktion zeigt den Verlauf der angegebenen Dateien an.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parameter
 `pvContext`

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 `hWnd`

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 `nFiles`

in Anzahl der im Array angegebenen Dateien `lpFileName` .

 `lpFileName`

in Array von voll qualifizierten Namen von Dateien.

 `fOptions`

in Befehlsflags (derzeit nicht verwendet).

 `pvOptions`

in Plug-in-spezifische Optionen für die Quell Code Verwaltung.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Versionsverlauf wurde erfolgreich abgerufen.|
|SCC_I_RELOADFILE|Das Quell Code Verwaltungssystem änderte die Datei auf dem Datenträger, während der Verlauf abgerufen wurde (z.b. durch Abrufen einer alten Version), sodass die IDE diese Datei erneut laden sollte.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_OPNOTSUPPORTED|Das Quell Code Verwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht geöffnet.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. Der Datei Versionsverlauf konnte nicht abgerufen werden.|

## <a name="remarks"></a>Bemerkungen
 Das Quellcodeverwaltungs-Plug-in kann ein eigenes Dialogfeld anzeigen, in dem der Verlauf der einzelnen Dateien angezeigt wird, wobei `hWnd` als übergeordnetes Fenster verwendet wird. Alternativ kann die optionale, für das [sccopenproject](../extensibility/sccopenproject-function.md) bereitgestellte Textausgabe-Rückruffunktion verwendet werden, sofern diese unterstützt wird.

 Beachten Sie, dass sich die Datei, die unter bestimmten Umständen überprüft wird, während der Ausführung dieses Aufrufes ändern kann. Der [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] Verlaufs Befehl gibt dem Benutzer beispielsweise die Möglichkeit, eine alte Version der Datei zu erhalten. In einem solchen Fall gibt das Quellcodeverwaltungs-Plug-in zurück, `SCC_I_RELOAD` um die IDE zu warnen, dass Sie die Datei erneut laden muss.

> [!NOTE]
> Wenn das Quellcodeverwaltungs-Plug-in diese Funktion für ein Array von Dateien nicht unterstützt, kann nur der Datei Versionsverlauf für die erste Datei angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
