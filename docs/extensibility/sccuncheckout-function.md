---
description: Mit dieser Funktion wird ein vorheriger Auscheck Vorgang aufgehoben, wodurch der Inhalt der ausgewählten Datei oder Dateien vor dem Auschecken in den Zustand wieder hergestellt wird.
title: Sccuncheckout-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33e0c4904a92d71e000d8c911d551eb8d0aab621
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221352"
---
# <a name="sccuncheckout-function"></a>SccUncheckout-Funktion
Mit dieser Funktion wird ein vorheriger Auscheck Vorgang aufgehoben, wodurch der Inhalt der ausgewählten Datei oder Dateien vor dem Auschecken in den Zustand wieder hergestellt wird. Alle Änderungen, die seit dem Auschecken an der Datei vorgenommen wurden, gehen verloren.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 nnoch

in Anzahl der im Array angegebenen Dateien `lpFileNames` .

 lpfile-Namen

in Array von voll qualifizierten lokalen Pfadnamen von Dateien, für die ein Auschecken rückgängig gemacht werden soll.

 f-Optionen

in Befehlsflags (nicht verwendet).

 pvoptions

in Plug-in-spezifische Optionen für die Quell Code Verwaltung.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Auschecken rückgängig gemacht.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quell Code Verwaltung.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. Rückgängig-Auschecken war nicht erfolgreich.|
|SCC_E_NOTCHECKEDOUT|Der Benutzer hat die Datei nicht ausgecheckt.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht aus der Quell Code Verwaltung geöffnet.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|

## <a name="remarks"></a>Bemerkungen
 Nach diesem Vorgang werden die `SCC_STATUS_CHECKEDOUT` -und-Flags für die Dateien, für die das Auschecken `SCC_STATUS_MODIFIED` rückgängig gemacht wurde, gelöscht.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
