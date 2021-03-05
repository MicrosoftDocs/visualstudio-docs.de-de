---
description: Diese Funktion ruft Statusinformationen für einen Satz ausgewählter Dateien unter Quell Code Verwaltung ab.
title: Sccqueryinfo-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 880cb2cf7db5c7a988d6549865de1864cb799e53
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221495"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo-Funktion
Diese Funktion ruft Statusinformationen für einen Satz ausgewählter Dateien unter Quell Code Verwaltung ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 nnoch

in Die Anzahl der im Array angegebenen Dateien `lpFileNames` und die Länge des `lpStatus` Arrays.

 lpfile-Namen

in Ein Array von Namen von Dateien, die abgefragt werden sollen.

 lpstatus

[in, out] Ein Array, in dem das Quellcodeverwaltungs-Plug-in die Statusflags für jede Datei zurückgibt. Weitere Informationen finden Sie unter [Datei Status Code](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Abfrage war erfolgreich.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, das wahrscheinlich auf Netzwerk-oder Konfliktprobleme zurückzuführen ist. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht unter Quell Code Verwaltung geöffnet.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Wenn `lpFileName` eine leere Zeichenfolge ist, sind zurzeit keine zu Aktualisier Ende Statusinformationen vorhanden. Andernfalls ist dies der vollständige Pfadname der Datei, für die die Statusinformationen geändert werden können.

 Das Rückgabe Array kann eine Bitmaske von `SCC_STATUS_xxxx` Bits sein. Weitere Informationen finden Sie unter [Datei Status Code](../extensibility/file-status-code-enumerator.md). Ein Quell Code Verwaltungssystem unterstützt möglicherweise nicht alle BITTypen. Wenn z. b `SCC_STATUS_OUTOFDATE` . nicht angeboten wird, wird das-Bit nicht festgelegt.

 Wenn Sie diese Funktion verwenden, um Dateien auszuchecken, beachten Sie die folgenden `MSSCCI` Status Anforderungen:

- `SCC_STATUS_OUTBYUSER` wird festgelegt, wenn der aktuelle Benutzer die Datei ausgecheckt hat.

- `SCC_STATUS_CHECKEDOUT` kann nur festgelegt werden, wenn `SCC_STATUS_OUTBYUSER` festgelegt ist.

- `SCC_STATUS_CHECKEDOUT` wird nur beim Auschecken der Datei in das angegebene Arbeitsverzeichnis festgelegt.

- Wenn die Datei vom aktuellen Benutzer in einem anderen Verzeichnis als dem Arbeitsverzeichnis ausgecheckt wird, `SCC_STATUS_OUTBYUSER` wird festgelegt, `SCC_STATUS_CHECKEDOUT` ist aber nicht.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Dateistatuscode](../extensibility/file-status-code-enumerator.md)
