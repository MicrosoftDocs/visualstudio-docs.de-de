---
title: Lptextoutproc | Microsoft-Dokumentation
description: Erfahren Sie mehr über den lptextoutproc-Funktionszeiger. Die Visual Studio-IDE implementiert die-Funktion zum Anzeigen von Fehlern und Status.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef05b65b1a018772f4354062aa1be285c40b0d90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952173"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Wenn der Benutzer einen Quell Code Verwaltungsvorgang innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) ausführt, möchte das Quellcodeverwaltungs-Plug-in möglicherweise Fehler-oder Statusmeldungen im Zusammenhang mit dem Vorgang übermitteln. Das Plug-in kann zu diesem Zweck seine eigenen Meldungs Felder anzeigen. Allerdings kann das Plug-in für eine nahtlose Integration Zeichen folgen an die IDE übergeben, die Sie dann in der nativen Weise anzeigen, in der Statusinformationen angezeigt werden. Der Mechanismus hierfür ist der `LPTEXTOUTPROC` Funktionszeiger. Die IDE implementiert diese Funktion (unten ausführlicher beschrieben) zum Anzeigen von Fehlern und Status.

Die IDE übergibt dem Quellcodeverwaltungs-Plug-in einen Funktionszeiger auf diese Funktion als `lpTextOutProc` Parameter, wenn das [sccopenproject](../extensibility/sccopenproject-function.md)aufgerufen wird. Während eines SCC-Vorgangs, z. b. in der Mitte eines Aufrufens von [sccget](../extensibility/sccget-function.md) , der viele Dateien umfasst, kann das Plug-in die `LPTEXTOUTPROC` Funktion aufrufen und regelmäßig Zeichen folgen zur Anzeige übergeben. In der IDE können diese Zeichen folgen ggf. auf einer Statusleiste, in einem Ausgabefenster oder in einem separaten Meldungs Feld angezeigt werden. Optional kann die IDE bestimmte Nachrichten mit der Schaltfläche " **Abbrechen** " anzeigen. Dadurch kann der Benutzer den Vorgang abbrechen, und die IDE erhält die Möglichkeit, diese Informationen an das Plug-in zurückzugeben.

## <a name="signature"></a>Signatur
 Die Ausgabefunktion der IDE weist die folgende Signatur auf:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>Parameter

display_string

Eine anzuzeigende Text Zeichenfolge. Diese Zeichenfolge sollte nicht mit einem Wagen Rücklauf oder Zeilenvorschub beendet werden.

mesg_type

Der Typ der Meldung. In der folgenden Tabelle sind die unterstützten Werte für diesen Parameter aufgeführt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Die Meldung wird als Information, Warnung oder Fehler betrachtet.|
|`SCC_MSG_STATUS`|Die Meldung zeigt den Status an und kann in der Statusleiste angezeigt werden.|
|`SCC_MSG_DOCANCEL`|Gesendet ohne Meldungs Zeichenfolge.|
|`SCC_MSG_STARTCANCEL`|Beginnt mit dem Anzeigen der Schaltfläche **Abbrechen** .|
|`SCC_MSG_STOPCANCEL`|Beendet die Anzeige einer Schaltfläche " **Abbrechen** ".|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Fragt IDE, ob der Hintergrund Vorgang abgebrochen werden soll: IDE gibt zurück `SCC_MSG_RTN_CANCEL` , wenn der Vorgang abgebrochen wurde; andernfalls wird zurückgegeben `SCC_MSG_RTN_OK` . Der- `display_string` Parameter wird als [sccmsgdataisabgeb Rochen](#LinkSccMsgDataIsCancelled) -Struktur umgewandelt, die vom Quellcodeverwaltungs-Plug-in bereitgestellt wird.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Teilt der IDE eine Datei zu, bevor Sie aus der Versionskontrolle abgerufen wird. Der- `display_string` Parameter wird als [sccmsgdataonbeforegetfile](#LinkSccMsgDataOnBeforeGetFile) -Struktur umgewandelt, die vom Quellcodeverwaltungs-Plug-in bereitgestellt wird.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Teilt der IDE eine Datei zu, nachdem Sie aus der Versionskontrolle abgerufen wurde. Der- `display_string` Parameter wird als [sccmsgdataonaftergetfile](#LinkSccMsgDataOnAfterGetFile) -Struktur umgewandelt, die vom Quellcodeverwaltungs-Plug-in bereitgestellt wird.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Teilt der IDE den aktuellen Status eines Hintergrund Vorgangs mit. Der- `display_string` Parameter wird als [sccmsgdataonmessage](#LinkSccMsgDataOnMessage) -Struktur umgewandelt, die vom Quellcodeverwaltungs-Plug-in bereitgestellt wird.|

## <a name="return-value"></a>Rückgabewert

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_MSG_RTN_OK|Die Zeichenfolge wurde angezeigt, oder der Vorgang wurde erfolgreich abgeschlossen.|
|SCC_MSG_RTN_CANCEL|Der Benutzer möchte den Vorgang abbrechen.|

## <a name="example"></a>Beispiel
 Angenommen, die IDE ruft [sccget](../extensibility/sccget-function.md) mit zwanzig Dateinamen auf. Das Quellcodeverwaltungs-Plug-in möchte verhindern, dass der Vorgang in der Mitte einer Datei abrufen abgebrochen wird. Nachdem jede Datei aufgerufen wurde, ruft Sie `lpTextOutProc` auf, übergibt ihr die Statusinformationen für jede Datei und sendet eine `SCC_MSG_DOCANCEL` Meldung, wenn Sie keinen Status zum Bericht hat. Wenn das Plug-in den Rückgabewert von `SCC_MSG_RTN_CANCEL` der IDE erhält, wird der Get-Vorgang sofort abgebrochen, sodass keine weiteren Dateien mehr abgerufen werden.

## <a name="structures"></a>Strukturen

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> Sccmsgdataisabgeb Rochen

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Diese Struktur wird mit der `SCC_MSG_BACKGROUND_IS_CANCELLED` Nachricht gesendet. Sie wird verwendet, um die ID des Hintergrund Vorgangs zu übermitteln, der abgebrochen wurde.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> Sccmsgdataonbeforegetfile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Diese Struktur wird mit der `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` Nachricht gesendet. Sie wird verwendet, um den Namen der abzurufenden Datei und die ID des Hintergrund Vorgangs zu übermitteln, der den Abruf Vorgang durchläuft.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> Sccmsgdataonaftergetfile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Diese Struktur wird mit der `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` Nachricht gesendet. Sie wird verwendet, um das Ergebnis des Abrufens der angegebenen Datei sowie die ID des Hintergrund Vorgangs zu übermitteln, der vom abgerufen wurde. Sehen Sie sich die Rückgabewerte für [sccget](../extensibility/sccget-function.md) für die Ergebnisse an.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> Sccmsgdataonmessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Diese Struktur wird mit der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht gesendet. Sie wird verwendet, um den aktuellen Status eines Hintergrund Vorgangs zu übermitteln. Der Status wird als Zeichenfolge ausgedrückt, die von der IDE angezeigt wird, und `bIsError` zeigt den Schweregrad der Nachricht an ( `TRUE` für eine Fehlermeldung, `FALSE` eine Warnung oder eine Informations Meldung). Die ID des Hintergrund Vorgangs, der den Status sendet, wird ebenfalls angegeben.

## <a name="code-example"></a>Codebeispiel
 Im folgenden finden Sie ein kurzes Beispiel für das Aufrufen von `LPTEXTOUTPROC` zum Senden der `SCC_MSG_BACKGROUND_ON_MESSAGE` Nachricht, das zeigt, wie die-Struktur für den-Aufruf umgewandelt wird.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
