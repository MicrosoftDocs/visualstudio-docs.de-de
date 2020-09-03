---
title: Erstellen benutzerdefinierter Ansichten von verwalteten Objekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72578026"
---
# <a name="create-custom-views-of-managed-objects"></a>Erstellen von benutzerdefinierten Ansichten von verwalteten Objekten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.  
  
## <a name="attributes"></a>Attribute  
 In C# und Visual Basic können Sie Erweiterungen für benutzerdefinierte Daten mit <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerBrowsableAttribute> hinzufügen.  
  
 In [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]-Code bietet Visual Basic keine Unterstützung des DebuggerBrowsable-Attributs. Diese Einschränkung wurde in aktuelleren Versionen von .NET Framework entfernt.  
  
## <a name="visualizers"></a>Schnellansichten  
 Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>nativer Code  
 Für nativen Code können Sie der Datei autoexp.dat benutzerdefinierte Datentyperweiterungen hinzufügen. Diese Datei befindet sich im Verzeichnis Programme\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. Anweisungen zum Schreiben von Regeln für die Datei `autoexp` befinden sich in der Datei selbst.  
  
> [!CAUTION]
> Die Struktur dieser Datei und die Syntax der autoexp-Regeln können in den verschiedenen Releases von Visual Studio unterschiedlich sein.  
  
 Auch die Ansichten von systemeigenen Typen können angepasst werden, und zwar durch das Schreiben eines Expression Evaluator-Add-Ins. Weitere Informationen finden Sie unter [Beispiel: Beispiel: Debuggen des Ausdrucks Auswerters-Add-ins](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des Attributs "tbuggertypeproxy"](../debugger/using-debuggertypeproxy-attribute.md)   
 [Verwenden des Attributs "enbuggerdisplay"](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Fenster "überwachen und schnell Überwachung"](../debugger/watch-and-quickwatch-windows.md)   
 [Verbessern des Debuggens mit den Debuggeranzeigeattributen](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
