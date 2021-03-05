---
description: Diese Funktion zeigt die Unterschiede zwischen der aktuellen Datei (auf dem lokalen Datenträger) und der zuletzt eingecheckten Version im Quell Code Verwaltungssystem an (oder überprüft Sie optional).
title: Sccdiff-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f7573cafd8ea06537a7655897f3cc5907448cfa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220845"
---
# <a name="sccdiff-function"></a>Sccdiff-Funktion
Diese Funktion zeigt die Unterschiede zwischen der aktuellen Datei (auf dem lokalen Datenträger) und der zuletzt eingecheckten Version im Quell Code Verwaltungssystem an (oder überprüft Sie optional).

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpFileName

in Der Dateiname, für den der Unterschied angefordert wird.

 f-Optionen

in Befehlsflags. Einzelheiten finden Sie in den Hinweisen.

 pvoptions

in Plug-in-spezifische Optionen für die Quell Code Verwaltung.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Arbeitskopie und die Server Version sind identisch.|
|SCC_I_FILESDIFFERS|Die Arbeitskopie unterscheidet sich von der Version unter Quell Code Verwaltung.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. der Datei Unterschied konnte nicht abgerufen werden.|
|SCC_E_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion dient zwei verschiedenen Zwecken. Standardmäßig wird eine Liste der Änderungen an einer Datei angezeigt. Das Quellcodeverwaltungs-Plug-in öffnet ein eigenes Fenster in jedem beliebigen Format, um die Unterschiede zwischen der Datei des Benutzers auf dem Datenträger und der aktuellen Version der Datei in der Quell Code Verwaltung anzuzeigen.

 Alternativ muss die IDE einfach bestimmen, ob sich eine Datei geändert hat. Beispielsweise muss die IDE möglicherweise ermitteln, ob es sicher ist, eine Datei Auschecken, ohne den Benutzer zu informieren. In diesem Fall übergibt die IDE das- `SCC_DIFF_CONTENTS` Flag. Das Quellcodeverwaltungs-Plug-in muss die Datei auf dem Datenträger (Byte-für-Byte) für die Datei mit der Quell Code Verwaltung überprüfen und einen Wert zurückgeben, der angibt, ob sich die beiden Dateien unterscheiden, ohne den Benutzer anzuzeigen.

 Als Leistungsoptimierung verwendet das Quellcodeverwaltungs-Plug-in möglicherweise eine Alternative, die auf einer Prüfsumme oder einem Zeitstempel basiert, anstelle des Byte-by-Byte-Vergleichs, der von aufgerufen wird `SCC_DIFF_CONTENTS` : Diese Vergleichs Formen sind offensichtlich schneller, aber weniger zuverlässig. Nicht alle Quell Code Verwaltungssysteme unterstützen möglicherweise diese alternativen Vergleichsmethoden, und das Plug-in muss möglicherweise auf einen Inhalts Vergleich zurückgreifen. Alle Quellcodeverwaltungs-Plug-Ins müssen mindestens einen Inhalts Vergleich unterstützen.

> [!NOTE]
> Die Flags für die schnelle Differenz schließen sich gegenseitig aus. Es ist zulässig, keine Flags zu übergeben, aber es ist nicht zulässig, gleichzeitig mehr als eine zu übergeben. `SCC_DIFF_QUICK_DIFF`, eine Maske, die alle Flags kombiniert, kann zum Testen verwendet werden, sollte jedoch nie als Parameter übergeben werden.

|`fOption`|Bedeutung|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Vergleich ohne Berücksichtigung der Groß-/Kleinschreibung (kann entweder für den schnellen oder visuellen Unterschied verwendet werden).|
|SCC_DIFF_IGNORESPACE|Ignoriert Leerraum (kann entweder für den schnellen oder den visuellen Unterschied verwendet werden).|
|SCC_DIFF_QD_CONTENTS|Vergleicht die Datei im Hintergrund mit Byte und Byte.|
|SCC_DIFF_QD_CHECKSUM|Vergleicht die Datei automatisch über eine Prüfsumme, wenn dies unterstützt wird. Wenn dies nicht unterstützt wird, wird auf einen Vergleich von Inhalten zurückgegriffen.|
|SCC_DIFF_QD_TIME|Vergleicht die Datei automatisch über den Zeitstempel, wenn dies unterstützt wird. Wenn dies nicht unterstützt wird, wird auf einen Vergleich von Inhalten zurückgegriffen.|

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
