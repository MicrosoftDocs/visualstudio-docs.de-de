---
title: HRESULT-Informationen in verwaltetem Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: jillfra
ms.openlocfilehash: 4f80b575656c2d8b1740f217f2e144f89f254078
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681634"
---
# <a name="hresult-information-in-managed-code"></a>HRESULT-Informationen in verwaltetem Code
Die Interaktion zwischen verwaltetem Code und COM kann Probleme verursachen, wenn HRESULT-Rückgabewerte gefunden werden.  
  
 In einer COM-Schnittstelle kann ein HRESULT-Rückgabewert die folgenden Rollen erfüllen:  
  
- Bereitstellen von Fehlerinformationen (z. B. <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>)  
  
- Bereitstellen von Statusinformationen zum normalen Programmverhalten  
  
  Wenn COM Aufrufe in verwaltetem Code ausführt, können HRESULTs die folgenden Probleme verursachen:  
  
- COM-Funktionen, die HRESULT-Werte kleiner als 0 (Fehlercodes) zurückgeben, generieren Ausnahmen.  
  
- COM-Methoden, die regelmäßig zwei oder mehr unterschiedliche Erfolgscodes (z. B. <xref:Microsoft.VisualStudio.VSConstants.S_OK> oder <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>) zurückgeben, können nicht unterschieden werden.  
  
  Weil viele [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] -COM-Funktionen entweder HRESULT-Werte kleiner als 0 (null) oder unterschiedliche Erfolgscodes zurückgeben, wurden die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] -Interop-Assemblys geschrieben, damit die Methodensignaturen beibehalten werden. Alle [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] -Interop-Methoden sind vom Typ `int` . HRESULT-Werte werden über die Interop-Schicht ohne Veränderung und ohne Generierung von Ausnahmen übergeben.  
  
  Da eine COM-Funktion ein HRESULT an die sie aufrufende verwaltete Methode zurückgibt, muss die aufrufende Methode das HRESULT überprüfen und ggf. Ausnahmen auslösen.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Behandeln von HRESULTs, die von COM an verwalteten Code zurückgegeben werden  
 Wenn Sie eine COM-Schnittstelle in verwaltetem Code aufrufen, überprüfen Sie den HRESULT-Wert, und lösen Sie ggf. eine Ausnahme aus. Die <xref:Microsoft.VisualStudio.ErrorHandler>-Klasse enthält die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode, die abhängig vom Wert des an sie übergebenen HRESULTs eine COM-Ausnahme auslöst.  
  
 Die <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>-Methode löst standardmäßig eine Ausnahme aus, wenn ihr ein HRESULT mit einem Wert kleiner als 0 (null) übergeben wird. In Fällen, in denen solche HRESULTs zulässige Werte aufweisen und keine Ausnahme ausgelöst werden soll, müssen die Werte der zusätzlichen HRESULTS nach dem Überprüfen der Werte an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergeben werden. Wenn das überprüfte HRESULT explizit an <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> übergebenen HRESULT-Werten entspricht, wird keine Ausnahme ausgelöst.  
  
> [!NOTE]
> Die- <xref:Microsoft.VisualStudio.VSConstants> Klasse enthält Konstanten für allgemeine HRESULTs, z. b. <xref:Microsoft.VisualStudio.VSConstants.S_OK> und <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , sowie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULTs, z <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . b <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . und. <xref:Microsoft.VisualStudio.VSConstants> enthält auch die Methoden <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> und <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, die den Makros SUCCEEDED und FAILED in COM entsprechen.  
  
 Betrachten Sie beispielsweise den folgenden Funktionsaufruf, bei dem <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ein zulässiger Rückgabewert ist, aber alle anderen HRESULTs kleiner als 0 (null) einen Fehler darstellen.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Wenn es mehrere zulässige Rückgabewerte gibt, können zusätzliche HRESULT-Werte einfach an die Liste in dem Aufruf von <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> angefügt werden.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Von verwaltetem Code an COM zurückgegebene HRESULTS  
 Wenn keine Ausnahme auftritt, gibt der verwaltete Code <xref:Microsoft.VisualStudio.VSConstants.S_OK> an die aufrufende COM-Funktion zurück. COM-Interop unterstützt allgemeine Ausnahmen, die in verwaltetem Code stark typisiert sind. Eine Methode, die ein unzulässiges `null`-Argument empfängt, löst beispielsweise eine <xref:System.ArgumentNullException> aus.  
  
 Wenn Sie nicht sicher sind, welche Ausnahme ausgelöst werden soll, aber das HRESULT kennen, das an COM zurückgegeben werden soll, können Sie die <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>-Methode verwenden, um eine entsprechende Ausnahme auszulösen. Dies funktioniert auch bei einem nicht standardmäßigen Fehler, z. B. <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> versucht, das übergebene HRESULT einer stark typisierten Ausnahme zuzuordnen. Wenn dies nicht möglich ist, wird stattdessen eine generische COM-Ausnahme ausgelöst. Als endgültiges Ergebnis wird das an <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> übergebene HRESULT vom verwaltetem Code an die aufrufende COM-Funktion zurückgegeben.  
  
> [!NOTE]
> Ausnahmen beeinträchtigen die Leistung und dienen als Hinweis auf anormale Programmbedingungen. Häufig auftretende Bedingungen sollten inline behandelt werden, statt eine Ausnahme auszulösen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltete VSPackages](../misc/managed-vspackages.md)   
 [Interoperabilität mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Gewusst wie: Zuordnen von HRESULTs und Ausnahmen](https://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Entwickeln von COM-Komponenten für die Interoperation](https://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Verwaltete VSPackages](../misc/managed-vspackages.md)