---
description: Diese Funktion Ruft eine Kopie einer oder mehrerer Dateien zum Anzeigen und kompilieren ab, jedoch nicht zur Bearbeitung.
title: Sccget-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 799d51c607ce720502c269cf82fe5a857ec7a826
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220832"
---
# <a name="sccget-function"></a>Sccget-Funktion
Diese Funktion Ruft eine Kopie einer oder mehrerer Dateien zum Anzeigen und kompilieren ab, jedoch nicht zur Bearbeitung. In den meisten Systemen werden die Dateien als schreibgeschützt gekennzeichnet.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur des Quellcodeverwaltungs-Plug-ins.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 nnoch

in Anzahl der im Array angegebenen Dateien `lpFileNames` .

 lpfile-Namen

in Array von voll qualifizierten Namen von Dateien, die abgerufen werden sollen.

 f-Optionen

in Befehlsflags ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvoptions

in Plug-in-spezifische Optionen für die Quell Code Verwaltung.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg des Get-Vorgangs.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_OPNOTSUPPORTED|Das Quell Code Verwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_FILEISCHECKEDOUT|Die Datei, die der Benutzer zurzeit ausgecheckt hat, kann nicht angezeigt werden.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NOSPECIFIEDVERSION|Es wurde eine ungültige Version angegeben.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. die Datei wurde nicht synchronisiert.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diese Operation auszuführen.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird mit einer Anzahl und einem Array von Namen der Dateien aufgerufen, die abgerufen werden sollen. Wenn die IDE das-Flag übergibt `SCC_GET_ALL` , bedeutet dies, dass es sich bei den Elementen in `lpFileNames` nicht um Dateien, sondern um Verzeichnisse handelt und dass alle Dateien unter Quell Code Verwaltung in den angegebenen Verzeichnissen abgerufen werden sollen.

 Das- `SCC_GET_ALL` Flag kann mit dem- `SCC_GET_RECURSIVE` Flag kombiniert werden, um auch alle Dateien in den angegebenen Verzeichnissen und allen Unterverzeichnissen abzurufen.

> [!NOTE]
> `SCC_GET_RECURSIVE` sollte nie ohne "" übermittelt werden `SCC_GET_ALL` . Beachten Sie außerdem, dass, wenn die Verzeichnisse *c:\a* und *c:\a\b* bei einem rekursiven Get-Vorgang übergeben werden, *c:\a\b* und alle zugehörigen Unterverzeichnisse tatsächlich zweimal abgerufen werden. Es ist die Verantwortung der IDE – und nicht die – des Quell Code Verwaltungs-Plug-ins, um sicherzustellen, dass Duplikate wie diese aus dem Array heraus aufbewahrt werden.

 Auch wenn ein Quellcodeverwaltungs-Plug-in das `SCC_CAP_GET_NOUI` Flag für die Initialisierung angegeben hat, das angibt, dass keine Benutzeroberfläche für einen get-Befehl vorhanden ist, wird diese Funktion möglicherweise dennoch von der IDE aufgerufen, um Dateien abzurufen. Das Flag bedeutet einfach, dass die IDE kein get-Menü Element anzeigt und dass das Plug-in keine Benutzeroberfläche bereitstellt.

## <a name="rename-files-and-sccget"></a>Umbenennen von Dateien und sccget
 Situation: ein Benutzer checkt eine Datei aus, z. b. *a.txt*, und ändert Sie. Bevor *a.txt* eingecheckt werden können, benennt ein zweiter Benutzer *a.txt* in die *b.txt* der Quell Code Verwaltungs Datenbank um, checkt *b.txt* aus, nimmt einige Änderungen an der Datei vor und überprüft die Datei in. Der erste Benutzer möchte die Änderungen, die vom zweiten Benutzer vorgenommen werden, damit der erste Benutzer seine lokale Version *a.txt* Datei in *b.txt* benennt und eine Get-Datei für die Datei ausführt. Der lokale Cache, der die Versionsnummern nachverfolgt, meint jedoch immer noch, dass die erste Version von *a.txt* lokal gespeichert wird, sodass die Quell Code Verwaltung die Unterschiede nicht auflösen kann.

 Es gibt zwei Möglichkeiten, diese Situation zu beheben, bei der der lokale Cache der Quell Code Verwaltungs Versionen nicht mehr mit der Quellcode-Verwaltungs Datenbank synchronisiert wird:

1. Das Umbenennen einer Datei in der Quellcodeverwaltungs-Datenbank, die zurzeit ausgecheckt ist, ist nicht zulässig.

2. Gehen Sie wie folgt vor: "Delete Old" gefolgt von "Add New". Der folgende Algorithmus ist eine Möglichkeit, dies zu erreichen.

    1. Verwenden Sie die [sccquerychanges](../extensibility/sccquerychanges-function.md) -Funktion, um mehr über das Umbenennen von *a.txt* in *b.txt* in der Quellcode-Verwaltungs Datenbank zu erfahren.

    2. Benennen Sie die lokale *a.txt* in *b.txt* um.

    3. Die `SccGet` -Funktion wird sowohl für *a.txt* als auch für *b.txt* aufgerufen.

    4. Da *a.txt* in der Quellcode-Verwaltungs Datenbank nicht vorhanden ist, wird der lokale Versions Cache aus den fehlenden *a.txt* Versionsinformationen gelöscht.

    5. Die *b.txt* ausgecheckte Datei wird mit dem Inhalt der lokalen *b.txt* Datei zusammengeführt.

    6. Die aktualisierte *b.txt* Datei kann jetzt eingeglichen werden.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md)
