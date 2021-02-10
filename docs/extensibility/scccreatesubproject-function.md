---
title: Scckreatesubproject-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ed763635d5629400c70c53497c7a798e0ac38f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943126"
---
# <a name="scccreatesubproject-function"></a>Scckreatesubproject-Funktion
Diese Funktion erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt, das durch das-Argument angegeben wird `lpParentProjPath` .

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpuser

[in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Terminator).

 lpparameentprojpath

in Eine Zeichenfolge, die den Pfad des übergeordneten Projekts identifiziert (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

 lpsubprojname

in Der vorgeschlagene Unterprojekt Name (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

 lpauxprojpath

[in, out] Zusätzliche Zeichenfolge, die das Projekt identifiziert (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

 lpsubprojpath

[in, out] Ausgabe Zeichenfolge, die den Pfad für das Unterprojekt identifiziert (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Das Unterprojekt wurde erfolgreich erstellt.|
|SCC_E_INITIALIZEFAILED|Das übergeordnete Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quell Code Verwaltungssystem anmelden.|
|SCC_E_COULDNOTCREATEPROJECT|Das Unterprojekt kann nicht erstellt werden.|
|SCC_E_PROJSYNTAXERR|Ungültige Projekt Syntax.|
|SCC_E_UNKNOWNPROJECT|Das übergeordnete Projekt ist dem Quellcodeverwaltungs-Plug-in unbekannt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_CONNECTIONFAILURE|Es gab ein Verbindungsproblem mit dem Quellcodeverwaltungs-Plug-in.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Wenn bereits ein Unterprojekt mit dem Namen vorhanden ist, kann die Funktion den Standardnamen ändern, um einen eindeutigen Namen zu erstellen, z. b. durch Hinzufügen von "_ \<number> ". Der Aufrufer muss darauf vorbereitet sein, Änderungen an `lpUser` , und zu akzeptieren `lpSubProjPath` `lpAuxProjPath` . Das `lpSubProjPath` -Argument und das- `lpAuxProjPath` Argument werden dann in einem aufzurufenden [sccopproject-Projekt](../extensibility/sccopenproject-function.md)verwendet. Sie sollten nicht vom Aufrufer geändert werden, wenn Sie zurückkehren. Diese Zeichen folgen bieten dem Quellcodeverwaltungs-Plug-in die Möglichkeit, Informationen zu verfolgen, die Sie einem Projekt zuordnen müssen. Die Aufrufer-IDE zeigt diese beiden Parameter nicht bei Rückgabe an, da das Plug-in eine formatierte Zeichenfolge verwenden kann, die möglicherweise nicht für die Anzeige geeignet ist. Die Funktion gibt einen Erfolgs-oder Fehlercode zurück und füllt die Variable, wenn erfolgreich, `lpSubProjPath` mit dem vollständigen Projektpfad zum neuen Projekt.

 Diese Funktion ähnelt dem [sccgetprojpath](../extensibility/sccgetprojpath-function.md), mit der Ausnahme, dass im Hintergrund ein Projekt erstellt wird, anstatt den Benutzer aufzufordern, eine auszuwählen. Wenn die `SccCreateSubProject` Funktion aufgerufen wird, sind `lpParentProjName` und `lpAuxProjPath` nicht leer und entsprechen einem gültigen Projekt. Diese Zeichen folgen werden in der Regel von der IDE von einem vorherigen Aufrufen der- `SccGetProjPath` Funktion oder von [sccgetparser ProjectPath](../extensibility/sccgetparentprojectpath-function.md)empfangen.

 Das- `lpUser` Argument ist der Benutzername. Die IDE übergibt denselben Benutzernamen, den Sie zuvor erhalten `SccGetProjPath` hat, und das Quellcodeverwaltungs-Plug-in sollte den Namen als Standard verwenden. Wenn der Benutzer bereits über eine geöffnete Verbindung mit dem Plug-in verfügt, sollte das Plug-in versuchen, alle Aufforderungen zu entfernen, um sicherzustellen, dass die Funktion unbeaufsichtigt funktioniert. Wenn bei der Anmeldung jedoch ein Fehler auftritt, sollte das Plug-in den Benutzer zur Eingabe eines Anmelde namens auffordern und, wenn er einen gültigen Anmelde Namen erhält, den Namen zurückgeben `lpUser` . Da das Plug-in diese Zeichenfolge ändern kann, weist die IDE immer einen Puffer der Größe (SCC_USER_LEN + 1 oder SCC_USER_SIZE auf, der Platz für das NULL-Terminator umfasst). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmelde Name sein (mindestens so gültig wie die alte Zeichenfolge).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise zu "scckreatesubproject" und "sccgetparser ProjectPath"
 Das Hinzufügen von Projektmappen und Projekten zur Quell Code Verwaltung wurde in Visual Studio vereinfacht, um zu minimieren, wie oft ein Benutzer aufgefordert wird, Speicherorte im Quell Code Verwaltungssystem auszuwählen. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-in sowohl die neuen Funktionen `SccCreateSubProject` als auch unterstützt `SccGetParentProjectPath` . Der folgende Registrierungs Eintrag kann jedoch verwendet werden, um diese Änderungen zu deaktivieren und zur vorherigen Version von Visual Studio (Quellcodeverwaltungs-Plug-in-API Version 1,1) zurückzukehren:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "Donotkreatesolutionrootfolderinsourcecontrol" = DWORD: 00000001**

 Wenn dieser Registrierungs Eintrag nicht vorhanden ist oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio, die neuen Funktionen und zu verwenden `SccCreateSubProject` `SccGetParentProjectPath` .

 Wenn der Registrierungs Eintrag auf DWORD: 00000001 festgelegt ist, versucht Visual Studio nicht, diese neuen Funktionen zu verwenden, und die Vorgänge des Hinzufügens zur Quell Code Verwaltung funktionieren wie in früheren Versionen von Visual Studio.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
