---
title: CommentMarkProfile | Microsoft-Dokumentation
description: Verwenden Sie die CommentMarkProfile-Funktion, um einen numerischen Marker und eine Textzeichenfolge in die *VSP*-Datei einzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e943be08ffd586347ab5de54cb803bcedc8c24d7
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533588"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
Die `CommentMarkProfile`-Funktion fügt in der *VSP*-Datei einen numerischen Marker und eine Textzeichenfolge ein. Damit die Markierung und der Kommentar eingefügt werden, muss die Profilerstellung für den Thread, der die `CommentMarkProfile`-Funktion enthält, auf ON festgelegt sein.

## <a name="syntax"></a>Syntax

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parameter
 `lMarker`

 Die numerische Markierung, die eingefügt werden soll. Die Markierung muss größer oder gleich 0 (null) sein.

 `szComment`

 Der Zeiger auf die einzufügende Textzeichenfolge. Die Zeichenfolge muss einschließlich des NULL-Abschlusszeichens weniger als 256 Zeichen enthalten.

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 Die Funktion gibt mithilfe der **PROFILE_COMMAND_STATUS**-Enumeration einen Erfolg oder Fehler an. Einer der folgenden Werte kann zurückgegeben werden:

|Enumerator|Beschreibung|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Der Parameter ist kleiner oder gleich 0 (null). Diese Werte sind reserviert. Die Markierung und der Kommentar werden nicht aufgezeichnet.|
|MARK_ERROR_MODE_NEVER|Der Profilerstellungsmodus wurde beim Aufruf der Funktion auf NEVER festgelegt. Die Markierung und der Kommentar werden nicht aufgezeichnet.|
|MARK_ERROR_MODE_OFF|Der Profilerstellungsmodus wurde beim Aufruf der Funktion auf OFF festgelegt. Die Markierung und der Kommentar werden nicht aufgezeichnet.|
|MARK_ERROR_NO_SUPPORT|In diesem Kontext werden keine Markierungen unterstützt. Die Markierung und der Kommentar werden nicht aufgezeichnet.|
|MARK_ERROR_OUTOFMEMORY|Der Arbeitsspeicher war nicht verfügbar, um das Ereignis aufzuzeichnen. Die Markierung und der Kommentar werden nicht aufgezeichnet.|
|MARK_TEXTTOOLONG|Die Zeichenfolge überschreitet die maximale Länge von 256 Zeichen. Die Kommentarzeichenfolge wurde abgeschnitten, und die Markierung und der Kommentar werden aufgezeichnet.|
|MARK_OK|Bei Erfolg wird MARK_OK zurückgegeben.|

## <a name="remarks"></a>Hinweise
 Der Profilerstellungsstatus für den Thread, der die Funktion „Mark profile“ („Profil markieren“) enthält, muss auf ON festgelegt sein, wenn Markierungen und Kommentare über den Mark-Befehl „VSInstr“ oder über Funktionen („CommentMarkAtProfile“, „CommentMarkProfile“, oder „MarkProfile“) eingefügt werden.

 Profilmarkierungen sind im Bereich global. Beispielsweise kann eine Profilmarkierung in einen Thread eingefügt werden, um den Anfang oder das Ende eines Datensegments eines Threads in der *VSP*-Datei zu markieren.

> [!IMPORTANT]
> CommentMarkProfile-Methoden können nur mit der Instrumentierung verwendet werden.

## <a name="net-framework-equivalent"></a>.NET Framework-Entsprechung
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Funktionsinformationen

|Element|Wert|
|-|-|
|**Header**|Enthält VSPerf.h|
|**Bibliothek**|Verwendet VSPerf.lib|
|**Unicode**|Als `CommentMarkProfileW` (Unicode) und `CommentMarkProfileA` (ANSI) implementiert.|

## <a name="example"></a>Beispiel
 Der folgende Code stellt den Funktionsaufruf „CommentMarkProfile“ dar. In diesem Beispiel wird vorausgesetzt, dass die Win32-Zeichenfolgenmakros und Unicode-Compilereinstellungen verwendet werden, um zu bestimmen, ob der Code den Funktionsaufruf [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] abruft.

```cpp
void ExerciseCommentMarkProfile()
{
    // Declare and initalize variables to pass to
    // CommentMarkProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkProfile(
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Siehe auch
- [Referenz für Profiler-APIs in Visual Studio (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)
