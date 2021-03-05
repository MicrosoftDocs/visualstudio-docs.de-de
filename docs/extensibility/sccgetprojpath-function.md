---
description: Diese Funktion fordert den Benutzer zur Eingabe eines Projekt Pfads auf, der eine Zeichenfolge ist, die nur für das Quellcodeverwaltungs-Plug-in sinnvoll ist.
title: Sccgetprojpath-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3a08c09e1b04cf5e5f826520efcf64ead9113be
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220702"
---
# <a name="sccgetprojpath-function"></a>Sccgetprojpath-Funktion
Diese Funktion fordert den Benutzer zur Eingabe eines Projekt Pfads auf, der eine Zeichenfolge ist, die nur für das Quellcodeverwaltungs-Plug-in sinnvoll ist. Sie wird aufgerufen, wenn der Benutzer ist:

- Erstellen eines neuen Projekts

- Hinzufügen eines vorhandenen Projekts zur Versionskontrolle

- Es wird versucht, ein vorhandenes Versions Kontroll Projekt zu finden

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpuser

[in, out] Der Benutzername (nicht überschreiten SCC_USER_SIZE, einschließlich des NULL-Terminator).

 lpprojname

[in, out] Der Name des IDE-Projekts, des Projekt Arbeitsbereichs oder Makefile (nicht überschreiten SCC_PRJPATH_SIZE, einschließlich des NULL-Terminator).

 lplocalpath

[in, out] Der Arbeits Pfad des Projekts. Wenn `bAllowChangePath` `TRUE` den Wert hat, kann das Quellcodeverwaltungs-Plug-in diese Zeichenfolge ändern (nicht um _MAX_PATH zu überschreiten, einschließlich des NULL-Terminator).

 lpauxprojpath

[in, out] Ein Puffer für den zurückgegebenen Projektpfad (nicht, um SCC_PRJPATH_SIZE zu überschreiten, einschließlich des NULL-Terminator).

 ballowchangepath

in Wenn dies der Wert ist `TRUE` , kann das Quellcodeverwaltungs-Plug-in die `lpLocalPath` Zeichenfolge anfordern und ändern.

 pbnew

[in, out] Der Wert in gibt an, ob ein neues Projekt erstellt werden soll. Der zurückgegebene Wert gibt an, dass ein Projekt erfolgreich erstellt wurde:

|Eingehend|Interpretation|
|--------------|--------------------|
|TRUE|Der Benutzer kann ein neues Projekt erstellen.|
|FALSE|Der Benutzer kann kein neues Projekt erstellen.|

|Ausgehend|Interpretation|
|--------------|--------------------|
|TRUE|Ein neues Projekt wurde erstellt.|
|FALSE|Ein vorhandenes Projekt wurde ausgewählt.|

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Projekt wurde erfolgreich erstellt oder abgerufen.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen.|
|SCC_E_CONNECTIONFAILURE|Beim Versuch, eine Verbindung mit dem Quell Code Verwaltungssystem herzustellen, ist ein Problem aufgetreten.|
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Der Zweck dieser Funktion besteht darin, dass die IDE die Parameter `lpProjName` und erhält `lpAuxProjPath` . Nachdem das Quellcodeverwaltungs-Plug-in den Benutzer zur Eingabe dieser Informationen aufgefordert hat, übergibt es diese beiden Zeichen folgen an die IDE. Die IDE speichert diese Zeichen folgen in ihrer Projektmappendatei und übergibt sie an das [sccopenproject](../extensibility/sccopenproject-function.md) , wenn der Benutzer dieses Projekt öffnet. Mit diesen Zeichen folgen kann das Plug-in die einem Projekt zugeordneten Informationen nachverfolgen.

 Wenn die-Funktion erstmalig aufgerufen wird, `lpAuxProjPath` wird auf eine leere Zeichenfolge festgelegt. `lProjName` kann auch leer sein oder den IDE-Projektnamen enthalten, den das Quellcodeverwaltungs-Plug-in verwenden oder ignorieren kann. Wenn die Funktion erfolgreich zurückgegeben wurde, gibt das Plug-in die beiden entsprechenden Zeichen folgen zurück. Die IDE nimmt keine Annahmen über diese Zeichen folgen, verwendet Sie nicht und gestattet es dem Benutzer nicht, Sie zu ändern. Wenn der Benutzer die Einstellungen ändern möchte, ruft die IDE erneut auf `SccGetProjPath` und übergibt die gleichen Werte, die Sie zuvor erhalten haben. Dadurch erhält das Plug-in die gesamte Kontrolle über diese beiden Zeichen folgen.

 Für gibt `lpUser` die IDE möglicherweise einen Benutzernamen an oder übergibt einfach einen Zeiger auf eine leere Zeichenfolge. Wenn ein Benutzername vorhanden ist, sollte das Quellcodeverwaltungs-Plug-in als Standard verwendet werden. Wenn jedoch kein Name übergeben wurde oder wenn die Anmeldung mit dem angegebenen Namen fehlgeschlagen ist, sollte das Plug-in den Benutzer zur Eingabe eines Anmelde namens auffordern und den Namen zurückgeben, `lpUser` Wenn er einen gültigen Anmelde Namen erhält. Da das Plug-in diese Zeichenfolge ändern kann, wird von der IDE immer ein Puffer der Größe ( `SCC_USER_LEN` + 1) zugeteilt.

> [!NOTE]
> Bei der ersten Aktion, die die IDE ausführt, kann es sich um einen-Vorgang `SccOpenProject` oder die- `SccGetProjPath` Funktion handeln. Daher verfügen beide über einen identischen `lpUser` Parameter, der es dem Quellcodeverwaltungs-Plug-in ermöglicht, den Benutzer jederzeit zu protokollieren. Auch wenn die Rückgabe von der Funktion auf einen Fehler hinweist, muss das Plug-in diese Zeichenfolge mit einem gültigen Anmelde Namen ausfüllen.

 `lpLocalPath` ist das Verzeichnis, in dem der Benutzer das Projekt beibehält. Möglicherweise handelt es sich um eine leere Zeichenfolge. Wenn derzeit kein Verzeichnis definiert ist (wie bei einem Benutzer, der versucht, ein Projekt aus dem Quell Code Verwaltungssystem herunterzuladen) und wenn `bAllowChangePath` `TRUE` den Wert hat, kann das Quellcodeverwaltungs-Plug-in den Benutzer zur Eingabe auffordern oder eine andere Methode zum Platzieren der eigenen Zeichenfolge verwenden `lpLocalPath` . Wenn den Wert `bAllowChangePath` `FALSE` hat, sollte das Plug-in die Zeichenfolge nicht ändern, da der Benutzer bereits im angegebenen Verzeichnis arbeitet.

 Wenn der Benutzer ein neues Projekt erstellt, das unter Quell Code Verwaltung eingefügt werden soll, wird es vom Quellcodeverwaltungs-Plug-in möglicherweise nicht im Quell Code Verwaltungssystem erstellt, wenn `SccGetProjPath` aufgerufen wird. Stattdessen wird die Zeichenfolge zusammen mit einem Wert ungleich 0 (null) zurück `pbNew` geben, der angibt, dass das Projekt im Quell Code Verwaltungssystem erstellt wird.

 Wenn beispielsweise ein Benutzer im Assistenten für **neue Projekte** in Visual Studio das Projekt der Quell Code Verwaltung hinzufügt, ruft Visual Studio diese Funktion auf, und das Plug-in bestimmt, ob es in Ordnung ist, ein neues Projekt im Quell Code Verwaltungssystem zu erstellen, das das Visual Studio-Projekt enthält. Wenn der Benutzer vor dem Abschließen des Assistenten auf **Abbrechen** klickt, wird das Projekt nicht erstellt. Wenn der Benutzer auf **OK** klickt, wird Visual Studio aufgerufen `SccOpenProject` und übergeben, `SCC_OPT_CREATEIFNEW` und das Projekt mit der Quell Code Verwaltung wird zu diesem Zeitpunkt erstellt.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
