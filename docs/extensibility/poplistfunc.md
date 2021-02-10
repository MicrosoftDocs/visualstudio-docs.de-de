---
title: Poplistfunc | Microsoft-Dokumentation
description: Erfahren Sie mehr über die poplistfunc-Rückruffunktion, die vom Quellcodeverwaltungs-Plug-in zum Aktualisieren einer Liste von Dateien oder Verzeichnissen verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddf641cf309eb5b5352904da2ac07b64b0886f97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967357"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Dieser Rückruf wird von der IDE für [sccpopulatelist](../extensibility/sccpopulatelist-function.md) bereitgestellt und wird vom Quellcodeverwaltungs-Plug-in verwendet, um eine Liste der Dateien oder Verzeichnisse (auch für die Funktion bereitgestellt) zu aktualisieren `SccPopulateList` .

 Wenn ein Benutzer den Befehl **Get** in der IDE auswählt, zeigt die IDE ein Listenfeld aller Dateien an, die der Benutzer erhalten kann. Leider kennt die IDE nicht die genaue Liste aller Dateien, die der Benutzer möglicherweise erhält. Diese Liste ist nur für das Plug-in enthalten. Wenn andere Benutzer dem Quell Code Verwaltungsprojekt Dateien hinzugefügt haben, sollten diese Dateien in der Liste angezeigt werden, aber die IDE kennt Sie nicht. Die IDE erstellt eine Liste der Dateien, die Sie vom Benutzer erhalten kann. Bevor die Liste für den Benutzer angezeigt wird, wird die [sccpopulatelist](../extensibility/sccpopulatelist-function.md) aufgerufen, die `,` dem Quellcodeverwaltungs-Plug-in die Möglichkeit bietet, Dateien in der Liste hinzuzufügen und zu löschen.

## <a name="signature"></a>Signatur
 Das Quellcodeverwaltungs-Plug-in ändert die Liste, indem eine IDE-implementierte Funktion mit dem folgenden Prototyp aufgerufen wird:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parameter
 pvcallerdata der vom Aufrufer `pvCallerData` (der IDE) an [sccpopulatelist](../extensibility/sccpopulatelist-function.md)übergebenen Parameter. Das Quellcodeverwaltungs-Plug-in sollte nichts über den Inhalt dieses Parameters ausgehen.

 fadressverschiebungif `TRUE` , wenn `lpFileName` eine Datei ist, die der Datei Liste hinzugefügt werden soll. Wenn `FALSE` `lpFileName` der Wert ist, wird eine Datei gelöscht, die aus der Datei Liste gelöscht werden soll.

 nStatus Status von `lpFileName` (eine Kombination der `SCC_STATUS` Bits; ausführliche Informationen finden Sie unter [Dateistatus Code](../extensibility/file-status-code-enumerator.md) ).

 lpFileName vollständiger Verzeichnispfad des Datei namens, der in der Liste hinzugefügt oder gelöscht werden soll.

## <a name="return-value"></a>Rückgabewert

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`TRUE`|Das Plug-in kann diese Funktion weiterhin aufrufen.|
|`FALSE`|Es ist ein Problem auf der IDE-Seite aufgetreten (z. b. eine nicht genügend Arbeitsspeicher Situation). Das Plug-in sollte den Vorgang abbrechen.|

## <a name="remarks"></a>Bemerkungen
 Für jede Datei, die das Quellcodeverwaltungs-Plug-in der Datei Liste hinzufügen oder aus ihr löschen möchte, wird diese Funktion aufgerufen, wobei der übergeben wird `lpFileName` . Das- `fAddRemove` Flag gibt eine neue Datei an, die der Liste hinzugefügt werden soll, oder eine alte zu löschende Datei. Der- `nStatus` Parameter gibt den Status der Datei an. Wenn das SCC-Plug-in das Hinzufügen und Löschen von Dateien abgeschlossen hat, wird der [sccpopulatelist](../extensibility/sccpopulatelist-function.md) -Befehl zurückgegeben.

> [!NOTE]
> Das Funktionalitäts `SCC_CAP_POPULATELIST` Bit ist für Visual Studio erforderlich.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Dateistatus Code](../extensibility/file-status-code-enumerator.md)
