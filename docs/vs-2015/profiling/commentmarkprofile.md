---
title: CommentMarkProfile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 750ce3cbcae593aee315998ec8b205a71e004d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543044"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die `CommentMarkProfile`-Funktion fügt der VSP-Datei eine numerische Markierung und eine Textzeichenfolge hinzu. Damit die Markierung und der Kommentar eingefügt werden, muss die Profilerstellung für den Thread, der die `CommentMarkProfile`-Funktion enthält, auf ON festgelegt sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
  
 Profilmarkierungen sind im Bereich global. Wenn beispielsweise eine Profilmarkierung in einen Thread eingefügt wird, kann diese verwendet werden, um den Anfang oder das Ende eines Datensegments in jedem Thread der VSP-Datei zu markieren.  
  
> [!IMPORTANT]
> CommentMarkProfile-Methoden können nur mit der Instrumentierung verwendet werden.  
  
## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Funktionsinformationen  
  
|Element|Wert|  
|-|-|  
|**Header**|Enthält VSPerf.h|  
|**Bibliothek**|Verwendet VSPerf.lib|  
|**Unicode**|Als `CommentMarkProfileW` (Unicode) und `CommentMarkProfileA` (ANSI) implementiert.|  
  
## <a name="example"></a>Beispiel  
 Der folgende Code stellt den Funktionsaufruf „CommentMarkProfile“ dar. In diesem Beispiel wird vorausgesetzt, dass die Win32-Zeichenfolgenmakros und Unicode-Compilereinstellungen verwendet werden, um zu bestimmen, ob der Code den Funktionsaufruf [!INCLUDE[vcpransi](../includes/vcpransi-md.md)] abruft.  
  
```  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Profiler-API-Referenz (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)
