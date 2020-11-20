---
title: Bitflags, die von bestimmten Befehlen verwendet werden | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Bitflags, die von der Quellcodeverwaltungs-Plug-in-API verwendet werden, geordnet nach der Funktion, die Sie verwendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c6c48dbad986d8bc4be58f1ebd9c5bd1fffbd57
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974596"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags, die von bestimmten Befehlen verwendet werden
Das Verhalten einer Reihe von Funktionen in der Quellcodeverwaltungs-Plug-in-API kann geändert werden, indem ein oder mehrere Bits in einem einzelnen Wert festgelegt werden. Diese Werte werden als Bitflags bezeichnet. Die verschiedenen Bitflags, die von der Quellcodeverwaltungs-Plug-in-API verwendet werden, werden hier aufgeführt, gruppiert nach der Funktion, die Sie verwendet.

## <a name="checked-out-flag"></a>Auschecken von Flag
 Dieses Flag kann entweder für [sccadd](../extensibility/sccadd-function.md) oder [scccheckin](../extensibility/scccheckin-function.md)festgelegt werden.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Lassen Sie die Datei ausgecheckt.|

## <a name="add-flags"></a>Flags hinzufügen
 Diese Flags werden von [sccadd](../extensibility/sccadd-function.md)verwendet.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Das Quellcodeverwaltungs-Plug-in erkennt automatisch, ob es sich um eine Text-oder Binärdatei handelt.|
|`SCC_FILETYPE_TEXT`|0x01|Dateityp ist Text.|
|`SCC_FILETYPE_BINARY`|0x04|Dateityp ist binär. **Hinweis:** `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Flags schließen sich gegenseitig aus.   Legen Sie genau einen oder keines von beiden fest.|
|`SCC_ADD_STORELATEST`|0x02|Nur die aktuelle Version speichern (keine Delta).|

## <a name="diff-flags"></a>Diff-Flags
 Der [sccdiff](../extensibility/sccdiff-function.md) verwendet diese Flags, um den Bereich eines Vergleichs Vorgangs zu definieren. Die `SCC_DIFF_QD_xxx` Flags schließen sich gegenseitig aus. Wenn eine davon angegeben ist, wird kein visuelles Feedback angegeben. In einem "schnellen diff" (QD) bestimmt das Plug-in nicht, wie sich die Datei unterscheidet, sondern nur, wenn Sie anders ist. Wenn keines dieser Flags angegeben ist, wird ein "visueller diff" ausgeführt. Ausführliche Datei Unterschiede werden berechnet und angezeigt. Wenn die angeforderte QD nicht unterstützt wird, wechselt das Plug-in zum nächsten. Wenn die IDE z. bbweise eine Prüfsumme anfordert und das Plug-in diese nicht unterstützt, führt das Plug-in eine Überprüfung der vollständigen Inhalte durch (immer noch viel schneller als eine visuelle Darstellung).

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Groß-/Kleinschreibung ignorieren.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorieren von leer Raum unterschieden. **Hinweis:**  Die `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` Flags und sind optionale Bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD durch Vergleichen des gesamten Datei Inhalts.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD nach Prüfsumme.|
|`SCC_DIFF_QD_TIME`|0x0040|QD nach Datei Datum/Zeitstempel.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Dies ist eine Maske, mit der alle QD-Bitflags überprüft werden. Er sollte nicht an eine Funktion übermittelt werden. die drei QD-Bitflags schließen sich gegenseitig aus. QD bedeutet immer, dass die Benutzeroberfläche nicht angezeigt wird.|

## <a name="populatelist-flag"></a>Populatelist-Flag
 Dieses Flag wird von [sccpopulatelist](../extensibility/sccpopulatelist-function.md) im-Parameter verwendet `fOptions` .

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|Die IDE übergibt Verzeichnisse und keine Dateien.|

## <a name="populatedirlist-flags"></a>Populatedirlist-Flags
 Diese Flags werden von [sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md) im-Parameter verwendet `fOptions` .

|Optionswert|Wert|BESCHREIBUNG|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Untersuchen Sie nur eine Ebene der Verzeichnisse für Verzeichnisse (Dies ist die Standardeinstellung).|
|SCC_PDL_RECURSIVE|0x0001|Untersuchen Sie rekursiv alle Verzeichnisse unter jedem angegebenen Verzeichnis.|
|SCC_PDL_INCLUDEFILES|0x0002|Schließt Dateinamen in den Untersuchungsprozess ein.|

## <a name="openproject-flags"></a>OpenProject-Flags
 Diese Flags werden von [sccopenproject](../extensibility/sccopenproject-function.md) im-Parameter verwendet `dwFlags` .

|Optionswert|Wert|BESCHREIBUNG|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Wenn das Projekt in der Quell Code Verwaltung nicht vorhanden ist, erstellen Sie es. Wenn dieses Flag nicht festgelegt ist, fordern Sie den Benutzer auf, zu Erstell zu erstellen (sofern nicht `SCC_OP_SILENTOPEN` Flag angegeben ist).|
|SCC_OP_SILENTOPEN|0x00000002L|Benutzer nicht zum Erstellen eines Projekts auffordern; Geben Sie einfach zurück `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Get-Flags
 Diese Flags werden von [sccget](../extensibility/sccget-function.md) und [scccheckout](../extensibility/scccheckout-function.md)verwendet.

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Die IDE übergibt Verzeichnisse und keine Dateien: alle Dateien in diesen Verzeichnissen abzurufen.|
|`SCC_GET_RECURSIVE`|0x00000002L|Die IDE übergibt Verzeichnisse: Sie erhalten diese Verzeichnisse und alle Unterverzeichnisse.|

## <a name="noption-values"></a>noptions-Werte
 Diese Flags werden von [sccsetoption](../extensibility/sccsetoption-function.md) im-Parameter verwendet `nOption` .

|Flag|Wert|BESCHREIBUNG|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Legen Sie den Status der Ereignis Warteschlange fest.|
|`SCC_OPT_USERDATA`|0x00000002L|Geben Sie Benutzerdaten für an `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003l|Die IDE kann abbrechen verarbeiten.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Legen Sie einen Rückruf für Namensänderungen fest.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005l|Deaktivieren Sie das Quellcodeverwaltungs-Plug-in UI Checkout, und legen Sie kein Arbeitsverzeichnis fest.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006l|Fügen Sie aus dem Quell Code Verwaltungssystem hinzu, um ein Arbeitsverzeichnis anzugeben. Versuchen Sie, die Freigabe im zugeordneten Projekt auszuführen, wenn es sich um einen direkt Nachfolger handelt.|

## <a name="dwval-bitflags"></a>dwval-Bitflags
 Diese Flags werden von [sccsetoption](../extensibility/sccsetoption-function.md) im-Parameter verwendet `dwVal` .

|Flag|Wert|BESCHREIBUNG|Wird als `nOption` Wert verwendet|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00l|Hält die Aktivität der Ereignis Warteschlange an.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01l|Aktiviert die Ereignis Warteschlange|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|Vorgegebene Hat keinen Abbruch Modus; das Plug-in muss bei Bedarf bereitstellen.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1 L|Die IDE verarbeitet den Abbruch.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|Vorgegebene Zum Auschecken von der Plug-in-Benutzeroberfläche das Arbeitsverzeichnis wird festgelegt.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1 L|Kein Plug-in-UI-Checkout, kein Arbeitsverzeichnis.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Weitere Informationen:
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
