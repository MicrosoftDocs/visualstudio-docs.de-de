---
title: Fehler Codes | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste der Fehlercodes, Werte und Beschreibungen für Plug-in-API-Funktionen der Quell Code Verwaltung.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77f869936531dbc41cc3bd1d9b510bf44c35cec
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994718"
---
# <a name="error-codes"></a>Fehlercodes
Wenn eine API-Funktion für Quellcodeverwaltungs-Plug-ins einen Fehler zurückgibt, wird davon ausgegangen, dass Sie einen der folgenden Fehlercodes erwartet. Alle Fehler sind negativ, Warnungen oder Informations Fehlercodes sind positiv, und der Erfolg ist 0.

|Fehlercode|Wert|BESCHREIBUNG|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Plug-in unterstützt das Hinzufügen von Dateien aus der Quell Code Verwaltung in zwei Schritten. Weitere Informationen finden Sie unter [sccsetoption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Die lokale Datei unterscheidet sich von der Datei in der Quellcode-Verwaltungs Datenbank (z. b. kann [sccdiff](../extensibility/sccdiff-function.md) diesen Wert zurückgeben).|
|`SCC_I_RELOADFILE`|5|Die lokale Datei wurde während des Quell Code Verwaltungs Vorgangs geändert. die IDE sollte die Datei nach Möglichkeit erneut laden.|
|`SCC_I_FILENOTAFFECTED`|4|Die Datei ist nicht betroffen.|
|`SCC_I_PROJECTCREATED`|3|Das Projekt wurde während des Quell Code Verwaltungs Vorgangs erstellt (z. b. während eines Aufrufens von [sccopenproject](../extensibility/sccopenproject-function.md) , wenn `SCC_OP_CREATEIFNEW` Flag angegeben ist).|
|`SCC_I_OPERATIONCANCELED`|2|Vorgang wurde abgebrochen.|
|`SCC_I_ADV_SUPPORT`|1|Das Plug-in unterstützt erweiterte Optionen für den angegebenen Befehl. Weitere Informationen finden Sie unter [sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Erfolg.|
|`SCC_E_INITIALIZEFAILED`|-1|Fehler: Fehler bei der Initialisierung.|
|`SCC_E_UNKNOWNPROJECT`|-2|Fehler: das Projekt ist unbekannt.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Fehler: das Projekt konnte nicht erstellt werden.|
|`SCC_E_NOTCHECKEDOUT`|–4|Fehler: die Datei ist nicht ausgecheckt.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Fehler: die Datei ist bereits ausgecheckt.|
|`SCC_E_FILEISLOCKED`|–6|Fehler: die Datei ist gesperrt.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Fehler: die Datei ist exklusiv ausgecheckt.|
|`SCC_E_ACCESSFAILURE`|-8|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|`SCC_E_CHECKINCONFLICT`|–9|Fehler: beim Einchecken ist ein Konflikt aufgetreten.|
|`SCC_E_FILEALREADYEXISTS`|-10|Fehler: die Datei ist bereits vorhanden.|
|`SCC_E_FILENOTCONTROLLED`|-11|Fehler: die Datei befindet sich nicht unter Quell Code Verwaltung.|
|`SCC_E_FILEISCHECKEDOUT`|6-12|Fehler: die Datei ist ausgecheckt.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Fehler: Es ist keine bestimmte Version vorhanden.|
|`SCC_E_OPNOTSUPPORTED`|-14|Fehler: der Vorgang wird nicht unterstützt.|
|`SCC_E_NONSPECIFICERROR`|14-15|Nicht spezifischer Fehler.|
|`SCC_E_OPNOTPERFORMED`|-16|Fehler, der Vorgang wurde nicht ausgeführt.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Fehler: der Dateityp, z. b. Binary, wird vom Quell Code Verwaltungssystem nicht unterstützt.|
|`SCC_E_VERIFYMERGE`|–18|Die Datei wurde automatisch zusammengeführt, aber nicht überprüft, weil die Benutzer Überprüfung aussteht.|
|`SCC_E_FIXMERGE`|-19|Die Datei wurde automatisch zusammengeführt, aber aufgrund eines Mergekonflikts, der manuell aufgelöst werden muss, nicht eingeglichen.|
|`SCC_E_SHELLFAILURE`|-20|Fehler aufgrund eines shellfehlers.|
|`SCC_E_INVALIDUSER`|-21|Fehler: der Benutzer ist ungültig.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Fehler: das Projekt ist bereits geöffnet.|
|`SCC_E_PROJSYNTAXERR`|-23|Projekt Syntax Fehler.|
|`SCC_E_INVALIDFILEPATH`|-24|Fehler: der Dateipfad ist ungültig.|
|`SCC_E_PROJNOTOPEN`|-25|Fehler: das Projekt ist nicht geöffnet.|
|`SCC_E_NOTAUTHORIZED`|-26|Fehler: der Benutzer ist nicht autorisiert, diesen Vorgang auszuführen.|
|`SCC_E_FILESYNTAXERR`|-27|Datei Syntax Fehler.|
|`SCC_E_FILENOTEXIST`|-28|Fehler: die lokale Datei ist nicht vorhanden.|
|`SCC_E_CONNECTIONFAILURE`|-29|Fehler: Verbindungsfehler.|
|`SCC_E_UNKNOWNERROR`|-30|Unbekannter Fehler.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Der Get-Hintergrund Vorgang wird zurzeit ausgeführt.|

## <a name="macros-provided-for-quick-checking"></a>Zur schnell Überprüfung bereitgestellte Makros

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Bemerkungen
 Alle API-Funktionen des Quellcodeverwaltungs-Plug-ins (mit Ausnahme von [sccadd](../extensibility/sccadd-function.md), [scccheckin](../extensibility/scccheckin-function.md)und [sccdiff](../extensibility/sccdiff-function.md)) werden erfolgreich ausgeführt, wenn die lokalen Dateien, die als Argumente übergeben werden, nicht im Arbeitsordner vorhanden sind. Die IDE kann z. b. einen aufzurufenden [scccheckout](../extensibility/scccheckout-function.md) -oder [sccuncheckout](../extensibility/sccuncheckout-function.md) -Vorgang für eine Datei ausgeben, die nicht im Arbeitsordner vorhanden ist, aber im Quell Code Verwaltungssystem vorhanden ist. Dieser Vorgang ist erfolgreich. Nur wenn im Arbeitsordner oder im Quell Code Verwaltungssystem keine Datei vorhanden ist, wird die Funktion als fehlgeschlagen erwartet.

 Bestimmte Funktionen, z. b. `SccAdd` und `SccCheckin` , sollten explizit zurückgeben, `SCC_E_FILENOTEXIST` Wenn die Datei im Arbeitsordner nicht vorhanden ist. Es wird erwartet, dass andere Funktionen erfolgreich sind, wenn die Arbeitsdatei nicht vorhanden ist, wenn die Funktionen mit einem gültigen Dateinamen im Quell Code Verwaltungssystem arbeiten.

 Das Quellcodeverwaltungs-Plug-in sollte keine Annahmen bezüglich der Berechtigungen für eine Datei im Arbeitsordner machen, auch wenn das Plug-in die Datei bei einem Vorgang als schreibgeschützt gekennzeichnet hätte. Eine Datei im Arbeitsordner kann verschoben, gelöscht und außerhalb der Steuerung des Plug-Ins geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
