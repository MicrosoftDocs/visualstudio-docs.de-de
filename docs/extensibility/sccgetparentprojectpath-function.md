---
description: Diese Funktion bestimmt den übergeordneten Projektpfad eines angegebenen Projekts.
title: Sccgetparser ProjectPath-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e624d8765da65dc6231c0128e87ffd9d6cdf848d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220611"
---
# <a name="sccgetparentprojectpath-function"></a>Sccgetparser ProjectPath-Funktion
Diese Funktion bestimmt den übergeordneten Projektpfad eines angegebenen Projekts. Diese Funktion wird aufgerufen, wenn der Benutzer ein Visual Studio-Projekt zur Quell Code Verwaltung hinzufügt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parameter
 pContext

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpuser

[in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Terminator).

 lpprojpath

in Zeichenfolge, die den Projektpfad identifiziert (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

 lpauxprojpath

[in, out] Zusätzliche Zeichenfolge, die das Projekt identifiziert (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

 lpparameentprojpath

[in, out] Ausgabe Zeichenfolge, die den übergeordneten Projektpfad identifiziert (bis SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der übergeordnete Projektpfad wurde erfolgreich abgerufen.|
|SCC_E_INITIALIZEFAILED|Das Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quellcodeverwaltungs-Plug-in anmelden.|
|SCC_E_UNKNOWNPROJECT|Das Projekt ist dem Quellcodeverwaltungs-Plug-in unbekannt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_PROJSYNTAXERR|Ungültige Projekt Syntax.|
|SCC_E_CONNECTIONFAILURE|Fehler beim Speichern der Verbindung.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion gibt einen Erfolgs-oder Fehlercode zurück und füllt die Variable, wenn erfolgreich, `lpParentProjPath` mit dem vollständigen Projektpfad zum angegebenen Projekt.

 Diese Funktion gibt den übergeordneten Projektpfad eines vorhandenen Projekts zurück. Für das Stamm Projekt gibt die-Funktion den Projektpfad zurück, der an (d. h. den gleichen Pfad des Stamm Projekts) übermittelt wurde. Beachten Sie, dass ein Projektpfad eine Zeichenfolge ist, die nur für das Quellcodeverwaltungs-Plug-in sinnvoll ist.

 Die IDE ist darauf vorbereitet, auch Änderungen an `lpUser` den `lpAuxProjPath` Parametern und zu akzeptieren. Die IDE speichert diese Zeichen folgen und übergibt sie an das [sccopenproject](../extensibility/sccopenproject-function.md) , wenn der Benutzer dieses Projekt zukünftig öffnet. Diese Zeichen folgen bieten somit eine Möglichkeit für das Quellcodeverwaltungs-Plug-in, um die Informationen zu verfolgen, die Sie einem Projekt zuordnen müssen.

 Diese Funktion ähnelt dem [sccgetprojpath](../extensibility/sccgetprojpath-function.md), mit dem Unterschied, dass der Benutzer nicht aufgefordert wird, ein Projekt auszuwählen. Außerdem erstellt er nie ein neues Projekt, funktioniert aber nur mit einem vorhandenen Projekt.

 Wenn `SccGetParentProjectPath` aufgerufen wird, werden `lpProjPath` und `lpAuxProjPath` nicht leer sein und einem gültigen Projekt entsprechen. Diese Zeichen folgen werden in der Regel von der IDE von einem vorherigen aufrufsbefehl empfangen `SccGetProjPath` .

 Das- `lpUser` Argument ist der Benutzername. Die IDE übergibt denselben Benutzernamen, den Sie zuvor von der `SccGetProjPath` Funktion erhalten hat, und das Quellcodeverwaltungs-Plug-in sollte den Namen als Standard verwenden. Wenn der Benutzer bereits über eine geöffnete Verbindung mit dem Plug-in verfügt, sollte das Plug-in versuchen, alle Aufforderungen zu entfernen, um sicherzustellen, dass die Funktion unbeaufsichtigt funktioniert. Wenn bei der Anmeldung jedoch ein Fehler auftritt, sollte das Plug-in den Benutzer zur Eingabe eines Anmelde namens auffordern und, wenn er einen gültigen Anmelde Namen erhält, den Namen zurückgeben `lpUser` . Da das Plug-in diese Zeichenfolge ändern kann, wird von der IDE immer ein Puffer der Größe ( `SCC_USER_LEN` + 1) zugeteilt. Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmelde Name sein (mindestens so gültig wie die alte Zeichenfolge).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise zu "scckreatesubproject" und "sccgetparser ProjectPath"
 Das Hinzufügen von Projektmappen und Projekten zur Quell Code Verwaltung wurde in Visual Studio vereinfacht, um zu minimieren, wie oft ein Benutzer aufgefordert wird, Speicherorte im Quell Code Verwaltungssystem auszuwählen. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-in sowohl die neuen Funktionen als auch [scckreatesubproject](../extensibility/scccreatesubproject-function.md) und die-Funktion unterstützt `SccGetParentProjectPath` . Der folgende Registrierungs Eintrag kann jedoch verwendet werden, um diese Änderungen zu deaktivieren und zum vorherigen Visual Studio-Verhalten (Quellcodeverwaltungs-Plug-in-API Version 1,1) zurückzukehren:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "Donotkreatesolutionrootfolderinsourcecontrol" = DWORD: 00000001**

 Wenn dieser Registrierungs Eintrag nicht vorhanden ist oder auf DWORD: 00000000 festgelegt ist, versucht Visual Studio, die neuen Funktionen und zu verwenden `SccCreateSubProject` `SccGetParentProjectPath` .

 Wenn der Registrierungs Eintrag auf DWORD: 00000001 festgelegt ist, versucht Visual Studio nicht, diese neuen Funktionen zu verwenden, und die Vorgänge des Hinzufügens zur Quell Code Verwaltung funktionieren wie in früheren Versionen von Visual Studio.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
