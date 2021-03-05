---
description: Diese Funktion fordert den Benutzer auf, erweiterte Optionen für einen angegebenen Befehl zu erhalten.
title: Sccgetcommandoptions-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 400b778cf5e26b0cabad0fb19c548b2faa0a803f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220806"
---
# <a name="sccgetcommandoptions-function"></a>Sccgetcommandoptions-Funktion
Diese Funktion fordert den Benutzer auf, erweiterte Optionen für einen angegebenen Befehl zu erhalten.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 hWnd

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 ICommand

in Der Befehl, für den Erweiterte Optionen angefordert werden (siehe [Befehls Code](../extensibility/command-code-enumerator.md) für mögliche Werte).

 ppvoptions

in Die Options Struktur (kann auch sein `NULL` ).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg.|
|SCC_I_ADV_SUPPORT|Das Quellcodeverwaltungs-Plug-in unterstützt erweiterte Optionen für den Befehl.|
|SCC_I_OPERATIONCANCELED|Der Benutzer hat das Dialogfeld **Optionen** für das Quellcodeverwaltungs-Plug-in abgebrochen.|
|SCC_E_OPTNOTSUPPORTED|Das Quellcodeverwaltungs-Plug-in unterstützt diesen Vorgang nicht.|
|SCC_E_ISCHECKEDOUT|Dieser Vorgang kann nicht für eine Datei durchgeführt werden, die zurzeit ausgecheckt ist.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Die IDE ruft diese Funktion zum ersten Mal mit `ppvOptions` = `NULL` auf, um zu bestimmen, ob das Quellcodeverwaltungs-Plug-in die Funktion "Erweiterte Optionen" für den angegebenen Befehl unterstützt. Wenn das Plug-in die Funktion für diesen Befehl unterstützt, ruft die IDE diese Funktion erneut auf, wenn der Benutzer erweiterte Optionen (in der Regel als **Erweiterte** Schaltfläche in einem Dialogfeld implementiert) anfordert und einen nicht-NULL-Zeiger angibt, der `ppvOptions` auf einen `NULL` Zeiger zeigt. Das Plug-in speichert alle erweiterten Optionen, die vom Benutzer in einer privaten Struktur angegeben werden, und gibt einen Zeiger auf diese Struktur in zurück `ppvOptions` . Diese Struktur wird dann an alle anderen API-Funktionen für Quellcodeverwaltungs-Plug-ins weitergegeben, die Sie kennen müssen, einschließlich der nachfolgenden Aufrufe der `SccGetCommandOptions` Funktion.

 Ein Beispiel kann dazu beitragen, diese Situation zu verdeutlichen.

 Ein Benutzer wählt den Befehl **Get** aus, und die IDE zeigt ein Dialogfeld **Get** an. Die IDE Ruft die `SccGetCommandOptions` -Funktion `iCommand` auf, wobei auf festgelegt `SCC_COMMAND_GET` und `ppvOptions` auf festgelegt wird `NULL` . Dies wird vom Quellcodeverwaltungs-Plug-in als Frage wie folgt interpretiert: "verfügen Sie über erweiterte Optionen für diesen Befehl?" Wenn das Plug-in zurückgegeben `SCC_I_ADV_SUPPORT` wird, zeigt die IDE im Dialogfeld **Get** eine Schaltfläche **erweitert** an.

 Wenn der Benutzer das erste Mal auf die Schaltfläche " **erweitert** " klickt, ruft die IDE erneut die- `SccGetCommandOptions` Funktion auf, diesmal mit einem, der nicht `NULL``ppvOptions` auf einen `NULL` Zeiger zeigt. Das Plug-in zeigt ein eigenes Dialogfeld **Get-Optionen** an, fordert den Benutzer zur Eingabe von Informationen auf, fügt diese Informationen in eine eigene Struktur ein und gibt einen Zeiger auf diese Struktur in zurück `ppvOptions` .

 Wenn der Benutzer im gleichen Dialogfeld erneut auf **erweitert** klickt, ruft die IDE die `SccGetCommandOptions` Funktion erneut auf `ppvOptions` , ohne zu ändern, sodass die Struktur an das Plug-in zurückgegeben wird. Dadurch kann das Plug-in sein Dialogfeld erneut mit den Werten initialisieren, die der Benutzer zuvor festgelegt hat. Das Plug-in ändert die Struktur vor der Rückgabe.

 Wenn der Benutzer im Dialogfeld " **Get** " der IDE auf **OK** klickt, ruft die IDE den [sccget](../extensibility/sccget-function.md)auf und übergibt dabei die in zurückgegebene Struktur, die `ppvOptions` die erweiterten Optionen enthält.

> [!NOTE]
> Der-Befehl `SCC_COMMAND_OPTIONS` wird verwendet, wenn die IDE ein Dialogfeld " **Optionen** " anzeigt, mit dem Benutzereinstellungen festlegen können, die die Funktionsweise der Integration Steuern. Wenn das Quellcodeverwaltungs-Plug-in ein eigenes Einstellungs Dialogfeld bereitstellen möchte, kann es über die Schaltfläche **erweitert** im Dialogfeld Einstellungen der IDE angezeigt werden. Das Plug-in ist allein dafür verantwortlich, diese Informationen zu erhalten und zu speichern. die IDE verwendet Sie nicht oder ändert Sie.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Befehls Code](../extensibility/command-code-enumerator.md)
