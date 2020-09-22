---
title: MarkProfile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 566cb2e7222aacbf992dc1693d8ce1de102605a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840936"
---
# <a name="markprofile"></a>MarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die `MarkProfile`-Methode fügt eine Profilmarkierung in die VSP-Datei ein. Damit die Markierung eingefügt wird, muss die Profilerstellung für den Thread, der die `MarkProfile`-Funktion enthält, auf ON festgelegt sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### <a name="parameters"></a>Parameter  
 `lMarker`  
  
 Die Markierung, die eingefügt werden soll. Die Markierung muss größer oder gleich 0 (null) sein.  
  
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
  
## <a name="remarks"></a>Bemerkungen  
 Der Markierungswert wird jedes Mal in die VSP-Datei eingefügt, wenn der Code ausgeführt wird und ein Profil für den Thread, der die MarkProfile-Funktion enthält, erstellt wird. Sie können MarkProfile mehrmals aufrufen.  
  
 Profilmarkierungen sind im Bereich global. Wenn beispielsweise eine Profilmarkierung in einen Thread eingefügt wird, kann diese verwendet werden, um den Anfang oder das Ende eines Datensegments in jedem Thread der VSP-Datei zu markieren.  
  
 Der Profilerstellungsstatus für den Thread, der die Funktion „mark profile“ (Profil markieren) enthält, muss auf ON festgelegt sein, wenn Markierungen und Kommentare mit dem Mark-Befehl oder mit API-Funktionen (CommentMarkAtProfile, CommentMarkProfile, oder MarkProfile) eingefügt werden.  
  
> [!IMPORTANT]
> Die MarkProfile-Methode sollte nur mit der Instrumentierungsprofilerstellung verwendet werden.  
  
## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Funktionsinformationen  
 Header: in VSPerf.h deklariert  
  
 Importbibliothek: VSPerf.lib  
  
## <a name="example"></a>Beispiel  
 Der folgende Code stellt den Funktionsaufruf von MarkProfile dar.  
  
```  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Profiler-API-Referenz (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)
