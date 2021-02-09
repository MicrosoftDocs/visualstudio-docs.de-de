---
title: Funktionsflags | Microsoft-Dokumentation
description: Erfahren Sie mehr über die SCC_CAP_xxx Flags, die die Funktionen eines Quellcodeverwaltungs-Plug-ins angeben, und die SCC_EXCAP_xxx Flags, die erweiterte Funktionen angeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d626f2390138c7e4e6e2471d285bcda940d7f30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882283"
---
# <a name="capability-flags"></a>Funktionsflags
Die SCC_CAP_ *xxx* -Flags sind Bitflags, die verwendet werden, um die Funktionen eines Quellcodeverwaltungs-Plug-ins anzugeben. Die SCC_EXCAP_ *xxx* -Flags sind inkrementelle Flags, die erweiterte Funktionen angeben und in ganzzahlige Werte auflösen.

|Funktions Code|Wert|Beschreibung|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Unterstützt das [SCUP](../extensibility/sccremove-function.md) -und den-Befehl.|
|`SCC_CAP_RENAME`|0x00000002L|Unterstützt den Befehl [sccrename](../extensibility/sccrename-function.md) und.|
|`SCC_CAP_DIFF`|0x00000004L|Unterstützt den [sccdiff](../extensibility/sccdiff-function.md) -und den-Befehl.|
|`SCC_CAP_HISTORY`|0x00000008L|Unterstützt den [scchistory](../extensibility/scchistory-function.md) -und den-Befehl.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Unterstützt die [sccproperties](../extensibility/sccproperties-function.md) und den Befehl.|
|`SCC_CAP_RUNSCC`|0x00000020l|Unterstützt den Befehl [sccrunscc](../extensibility/sccrunscc-function.md) und.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040l|Unterstützt den [sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md) -Befehl und den-Befehl.|
|`SCC_CAP_QUERYINFO`|0x00000080l|Unterstützt den [sccqueryinfo](../extensibility/sccqueryinfo-function.md) -Befehl und den-Befehl.|
|`SCC_CAP_GETEVENTS`|0x00000100l|Unterstützt die [sccgetevents](../extensibility/sccgetevents-function.md) -und-Befehle.|
|`SCC_CAP_GETPROJPATH`|0x00000200l|Unterstützt den [sccgetprojpath](../extensibility/sccgetprojpath-function.md) -Befehl und den-Befehl.|
|`SCC_CAP_ADDFROMSCC`|0x00000400l|Unterstützt den Befehl [sccaddfromscc](../extensibility/sccaddfromscc-function.md) und.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800l|Unterstützt einen Kommentar beim Auschecken.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000l|Unterstützt einen Kommentar zum Einchecken.|
|`SCC_CAP_COMMENTADD`|0x00002000l|Unterstützt einen Kommentar zum Hinzufügen.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000l|Unterstützt einen Kommentar beim Entfernen.|
|`SCC_CAP_TEXTOUT`|0x00008000l|Schreibt Text in eine von der IDE bereitgestellte Ausgabefunktion.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000l|Unterstützt das Speichern von Dateien ohne Delta.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000l|Unterstützt mehrere Datei Versions Verläufe.|
|`SCC_CAP_IGNORECASE`|0x00800000l|Unterstützt Datei Vergleiche ohne Berücksichtigung der Groß-/Kleinschreibung|
|`SCC_CAP_IGNORESPACE`|0x01000000l|Unterstützt den Dateivergleich, der Leerzeichen ignoriert.|
|`SCC_CAP_POPULATELIST`|0x02000000l|Unterstützt das Suchen zusätzlicher Dateien.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000l|Unterstützt Kommentare zu Create Project.|
|`SCC_CAP_DIFFALWAYS`|0x10000000l|Unterstützt den diff in allen Zuständen, wenn unter der Kontrolle.|
|`SCC_CAP_GET_NOUI`|0x20000000l|Das Plug-in unterstützt keine Benutzeroberfläche für Get, aber die IDE Ruft möglicherweise trotzdem [sccget](../extensibility/sccget-function.md)auf.|
|`SCC_CAP_REENTRANT`|0x40000000l|Das Plug-in ist Wiedereintritts fähige und Thread sicher. In Version 1,0 wurde davon ausgegangen, dass die Plug-ins wieder einentrant und Thread sicher sind. Wenn dieses Bit von einem 1,1-Plug-in festgelegt wird, können mehrere Projekte parallel geöffnet werden.|

## <a name="capability-bits-added-in-version-12"></a>Funktions Bits in Version 1,2 hinzugefügt

|Funktions Code|Wert|Beschreibung|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000l|Unterstützt [scckreatesubproject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000l|Unterstützt [sccgetparser ProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000l|Unterstützt [sccbeginbatch](../extensibility/sccbeginbatch-function.md) und [sccendbatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000l|Unterstützt [sccdirqueryinfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000l|Unterstützt [sccdirdiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000l|Unterstützt mehrere Auschecken für eine Datei und [sccismulticheckoutenabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000l|Unterstützt die Datei *Mssccprj. SCC* (unter dem Überschreiben von Benutzer/Administrator) und [sccwillkreatesccfile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Funktions Bits in Version 1,3 hinzugefügt
 Diese Flags werden nacheinander an die [sccgetextendedfunctions](../extensibility/sccgetextendedcapabilities-function.md) -Funktion übergeben, um zu bestimmen, ob die Funktion unterstützt wird.

|Erweiterter Funktions Code|Wert|Beschreibung|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Unterstützt die- `SCC_CHECKOUT_LOCALVER` Option für Auscheck Vorgänge.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Unterstützt [sccbackgroundget](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Unterstützt [sccenumchangedfiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Unterstützt das Suchen zusätzlicher Verzeichnisse.|
|`SCC_EXCAP_QUERYCHANGES`|5|Unterstützt das Auflisten von Dateiänderungen.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Unterstützt [sccaddfilesfromscc](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Unterstützt [sccgetuseroption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Unterstützt das Aufrufen von sccqueryinfo für mehrere Threads.|
|`SCC_EXCAP_REMOVE_DIR`|9|Unterstützt die sckremuvedir-Funktion.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Ausgecheckte Dateien können gelöscht werden.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Können ausgecheckte Dateien umbenennen.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
