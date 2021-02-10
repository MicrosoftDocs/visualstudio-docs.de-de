---
title: SuspendProfile | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur SuspendProfile-Methode. Diese erhöht den Suspend/Resume-Zähler für die angegebene Profilerstellungsebene.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6be94fafb1e41390236977a7a06b59cf7ac71a84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868204"
---
# <a name="suspendprofile"></a>SuspendProfile
Die `SuspendProfile`-Methode erhöht den Suspend/Resume-Zähler für die angegebene Profilerstellungsebene.

## <a name="syntax"></a>Syntax

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parameter
 `Level`

 Gibt die Profilebene an, auf die die Sammlung von Leistungsdaten angewendet werden kann. Die folgenden **PROFILE_CONTROL_LEVEL**-Enumeratoren können verwendet werden, um eine der drei Ebenen anzugeben, auf die die Sammlung der Leistungsdaten angewendet werden kann:

|Enumerator|Beschreibung|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Die Einstellung globaler Ebene wirkt sich auf alle Prozesse und Threads bei der Profilerstellung aus.|
|PROFILE_PROCESSLEVEL|Die Einstellung auf die Prozessebene wirkt sich auf alle Threads aus, die Teil des angegebenen Prozesses sind.|
|PROFILE_THREADLEVEL|Die Einstellung auf Threadebene der Profilerstellung wirkt sich auf den angegebenen Thread aus.|

 `dwId`

 Der Prozess- oder Threadbezeichner, der vom System generiert wird.

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 Die Funktion gibt mithilfe der **PROFILE_COMMAND_STATUS**-Enumeration einen Erfolg oder Fehler an. Einer der folgenden Werte kann zurückgegeben werden:

|Enumerator|Beschreibung|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|Die Profilerstellungselement-ID ist nicht vorhanden.|
|PROFILE_ERROR_LEVEL_NOEXIST|Die angegebene Profilerstellungsebene ist nicht vorhanden.|
|PROFILE_ERROR_MODE_NEVER|Der Profilerstellungsmodus wurde beim Aufruf der Funktion auf NEVER festgelegt.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Der Funktionsaufruf der Profilerstellung, die Profilerstellungsebene oder eine Kombination aus dem Aufruf und der Ebene sind noch nicht implementiert.|
|PROFILE_OK|Der Aufruf war erfolgreich.|

## <a name="remarks"></a>Bemerkungen
 Der Anfangswert des Suspend/Resume-Zählers ist 0. Jeder Aufruf von SuspendProfile addiert 1 zur der Suspend/Resume-Anzahl. Für jeden Aufruf von ResumeProfile wird 1 subtrahiert.

 Wenn die Suspend/Resume-Anzahl größer als 0 ist, ist der Suspend/Resume-Status für die Ebene OFF. Wenn die Anzahl kleiner oder gleich 0 ist, ist der Status von Suspend/Resume ON.

 Wenn sowohl der Status von Start/Stop als auch der von Suspend/Resume auf ON festgelegt ist, ist auch der Profilerstellungsstatus der Ebene auf ON festgelegt. Damit das Profil eines Threads erstellt werden kann, muss der Status des Threads sowohl auf globaler, Prozess- und Threadebene ON sein.

## <a name="net-framework-equivalent"></a>.NET Framework-Entsprechung
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Funktionsinformationen
 Header: in *VSPerf.h* deklariert

 Importbibliothek: *VSPerf.lib*

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die SuspendProfile-Methode veranschaulicht. Dieses Beispiel geht davon aus, dass ein vorheriger Aufruf von StartProfile für den Thread oder Prozess ausgeführt wurde, der durch [PROFILE_CURRENTID](../profiling/profile-currentid.md) identifiziert wurde.

```cpp
void ExerciseSuspendProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the
    // Suspend/Resume count; each call
    // to ResumeProfile subtracts 1.

    // Variables used to print output
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to SuspendProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = SuspendProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("SuspendProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Siehe auch
- [Referenz für Profiler-APIs in Visual Studio (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)
