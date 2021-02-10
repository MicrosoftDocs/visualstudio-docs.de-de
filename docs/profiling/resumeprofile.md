---
title: ResumeProfile | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur ResumeProfile-Methode. Diese verringert den Suspend/Resume-Zähler für die angegebene Profilerstellungsebene.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5607efbf9e979ff427d772089731af01cdd71867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950155"
---
# <a name="resumeprofile"></a>ResumeProfile
Die `ResumeProfile`-Methode verringert den Suspend/Resume-Zähler für die angegebene Profilerstellungsebene.

## <a name="syntax"></a>Syntax

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
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
 Das folgende Beispiel veranschaulicht die ResumeProfile-Funktion. Im Beispiel wird davon ausgegangen, dass ein Aufruf der SuspendProfile-Methode für den selben Thread oder Prozess ausgeführt wurde, der durch [PROFILE_CURRENTID](../profiling/profile-currentid.md) identifiziert wurde.

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Siehe auch
- [Referenz für Profiler-APIs in Visual Studio (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)
