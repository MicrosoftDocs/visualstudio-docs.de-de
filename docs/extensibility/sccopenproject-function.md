---
title: Sccopenproject-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ebc78c73c37a5db3c1808cc3bb4b6715e85bcebe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836942"
---
# <a name="sccopenproject-function"></a>SccOpenProject-Funktion
Diese Funktion öffnet ein vorhandenes Quell Code Verwaltungsprojekt oder erstellt ein neues Projekt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpuser

[in, out] Der Name des Benutzers (nicht überschreiten SCC_USER_SIZE, einschließlich des NULL-Terminator).

 lpprojname

in Die Zeichenfolge, die den Namen des Projekts identifiziert.

 lplocalprojpath

in Der Pfad zum Arbeitsordner für das Projekt.

 lpauxprojpath

[in, out] Eine optionale zusätzliche Zeichenfolge, die das Projekt identifiziert (nicht überschreiten SCC_AUXPATH_SIZE, einschließlich des NULL-Terminator).

 lpcomment

in Kommentieren Sie ein neues Projekt, das erstellt wird.

 lptextoutproc

in Eine optionale Rückruffunktion zum Anzeigen der Textausgabe aus dem Quellcodeverwaltungs-Plug-in.

 dwFlags

in Signalisiert, ob ein neues Projekt erstellt werden muss, wenn das Projekt dem Quellcodeverwaltungs-Plug-in unbekannt ist. Der Wert kann eine Kombination aus und sein. `SCC_OP_CREATEIFNEW``SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Erfolg beim Öffnen des Projekts.|
|SCC_E_INITIALIZEFAILED|Das Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quell Code Verwaltungssystem anmelden.|
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt war vor dem-Befehl nicht vorhanden.  Das `SCC_OPT_CREATEIFNEW` Flag wurde festgelegt, aber das Projekt konnte nicht erstellt werden.|
|SCC_E_PROJSYNTAXERR|Ungültige Projekt Syntax.|
|SCC_E_UNKNOWNPROJECT|Das Projekt ist dem Quellcodeverwaltungs-Plug-in unbekannt, und das `SCC_OPT_CREATEIFNEW` Flag wurde nicht festgelegt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECFICERROR|Ein nicht spezifischer Fehler. das Quell Code Verwaltungssystem wurde nicht initialisiert.|

## <a name="remarks"></a>Bemerkungen
 Die IDE kann einen Benutzernamen () übergeben `lpUser` , oder es kann einfach ein Zeiger auf eine leere Zeichenfolge übergeben werden. Wenn ein Benutzername vorhanden ist, sollte das Quellcodeverwaltungs-Plug-in als Standard verwendet werden. Wenn jedoch kein Name übergeben wurde, oder wenn die Anmeldung mit dem angegebenen Namen fehlgeschlagen ist, muss das Plug-in den Benutzer zur Anmeldung auffordern und den gültigen Namen in zurückgeben, `lpUser` Wenn er einen gültigen Anmelde Namen empfängt, `.` da das Plug-in die Benutzernamen Zeichenfolge ändern kann. die IDE weist immer einen Puffer der Größe ( `SCC_USER_LEN` + 1 oder SCC_USER_SIZE auf, der Platz für das NULL-

> [!NOTE]
> Die erste Aktion, die die IDE ausführen kann, ist möglicherweise ein Aufrufen der- `SccOpenProject` Funktion oder des [sccgetprojpath](../extensibility/sccgetprojpath-function.md)-Vorgangs. Aus diesem Grund haben beide einen identischen `lpUser` Parameter.

 `lpAuxProjPath` und `lpProjName` werden aus der Projektmappendatei gelesen, oder Sie werden von einem Rückruf der-Funktion zurückgegeben `SccGetProjPath` . Diese Parameter enthalten die Zeichen folgen, die das Quellcodeverwaltungs-Plug-in dem Projekt zuordnet, und sind nur für das Plug-in sinnvoll. Wenn keine dieser Zeichen folgen in der Projektmappendatei gefunden wird und der Benutzer nicht zum Durchsuchen aufgefordert wurde (was eine Zeichenfolge durch die-Funktion zurückgeben würde `SccGetProjPath` ), übergibt die IDE leere Zeichen folgen sowohl für `lpAuxProjPath` als auch für und `lpProjName` erwartet, dass diese Werte durch das Plug-in aktualisiert werden, wenn diese Funktion zurückgibt.

 `lpTextOutProc` ist ein Zeiger auf eine Rückruffunktion, die von der IDE zum Quellcodeverwaltungs-Plug-in bereitgestellt wird, um die Befehls Ergebnis Ausgabe anzuzeigen. Diese Rückruffunktion wird in [lptextoutproc](../extensibility/lptextoutproc.md)ausführlich beschrieben.

> [!NOTE]
> Wenn das Quellcodeverwaltungs-Plug-in diese Vorteile nutzen soll, muss das- `SCC_CAP_TEXTOUT` Flag in [sccinitialize](../extensibility/sccinitialize-function.md)festgelegt sein. Wenn dieses Flag nicht festgelegt wurde oder die IDE dieses Feature nicht unterstützt, ist `lpTextOutProc` `NULL` .

 Der- `dwFlags` Parameter steuert das Ergebnis im Fall, dass das geöffnete Projekt derzeit nicht vorhanden ist. Sie besteht aus zwei Bitflags: `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN` . Wenn das geöffnete Projekt bereits vorhanden ist, öffnet die Funktion das Projekt einfach und gibt zurück `SCC_OK` . Wenn das Projekt nicht vorhanden ist und das- `SCC_OP_CREATEIFNEW` Flag auf ON fest steht, kann das Quellcodeverwaltungs-Plug-in das Projekt im Quell Code Verwaltungssystem erstellen, es öffnen und zurückgeben `SCC_OK` . Wenn das Projekt nicht vorhanden ist und das Flag deaktiviert `SCC_OP_CREATEIFNEW` ist, sollte das Plug-in dann das Flag überprüfen `SCC_OP_SILENTOPEN` . Wenn dieses Flag nicht on ist, fordert das Plug-in den Benutzer möglicherweise auf, einen Projektnamen einzugeben. Wenn dieses Flag auf ON fest steht, sollte das Plug-in einfach zurückgeben `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Aufruf Reihenfolge
 Im normalen Verlauf der Ereignisse wird [sccinitialize](../extensibility/sccinitialize-function.md) zuerst aufgerufen, um eine Quell Code Verwaltungssitzung zu öffnen. Eine Sitzung kann aus einem Aufruf von bestehen `SccOpenProject` , gefolgt von anderen API-Funktionsaufrufen des Quell Code Verwaltungs-Plug-ins und endet mit einem Aufruf von [scccloseproject](../extensibility/scccloseproject-function.md). Solche Sitzungen können mehrmals wiederholt werden, bevor [sccuninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.

 Wenn das Quellcodeverwaltungs-Plug-in das `SCC_CAP_REENTRANT` Bit in festlegt `SccInitialize` , kann die obige Sitzungs Sequenz mehrmals parallel wiederholt werden. Mit unterschiedlichen `pvContext` Strukturen werden die verschiedenen Sitzungen verfolgt, in denen jeweils jeweils `pvContext` einem geöffneten Projekt zugeordnet ist. Basierend auf dem- `pvContext` Parameter kann das Plug-in bestimmen, auf welches Projekt in einem bestimmten-Befehl verwiesen wird. Wenn das `SCC_CAP_REENTRANT` funktionsbit nicht festgelegt ist, sind nicht wieder eintretende Quellcodeverwaltungs-Plug-ins in der Lage, mit mehreren Projekten zu arbeiten.

> [!NOTE]
> Das `SCC_CAP_REENTRANT` Bit wurde in Version 1,1 der Quellcodeverwaltungs-Plug-in-API eingeführt. Er ist in Version 1,0 nicht festgelegt oder wird ignoriert, und alle Quellcodeverwaltungs-Plug-ins der Version 1,0 werden als nicht wieder eintretig angenommen.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Einschränkungen für die Längen von Zeichenfolgen](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
