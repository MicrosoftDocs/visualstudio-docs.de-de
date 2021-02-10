---
title: Erstellen von benutzerdefinierten Ansichten von verwalteten Objekten | Microsoft-Dokumentation
description: Der Visual Studio-Debugger zeigt Daten in seinen Variablenfenstern an. Hier erfahren Sie, wie Sie das Anzeigen von Datentypen (einschließlich benutzerdefinierter Typen) anpassen können.
ms.custom: SEO-VS-2020
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c054d3bcfbb06d0093f04190ab8b4825b5cbf20f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865799"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Erstellen von benutzerdefinierten Ansichten von verwalteten Objekten (C#, Visual Basic, F#, C++/CLI)
Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.

## <a name="attributes"></a>Attribute

In C#, Visual Basic, F# und C++ (nur C++-/CLI-Code) können Sie Erweiterungen für benutzerdefinierte Daten mit <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerBrowsableAttribute> hinzufügen.

In .NET Framework 2.0-Code bietet Visual Basic keine Unterstützung des DebuggerBrowsable-Attributs. Diese Einschränkung wurde in aktuelleren Versionen von .NET entfernt.

## <a name="visualizers"></a>Schnellansichten

Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Schnellansicht](create-custom-visualizers-of-data.md).

> [!NOTE]
> Für C++-Code können Sie mit dem Natvis-Framework benutzerdefinierte Datentyperweiterungen hinzufügen, wie unter [Erstellen benutzerdefinierter Ansichten von C++-Objekten im Debugger](create-custom-views-of-native-objects.md) beschrieben wird.

## <a name="see-also"></a>Siehe auch

- [Debugger mit dem DebuggerDisplay-Attribut anweisen, was angezeigt werden soll](../debugger/using-the-debuggerdisplay-attribute.md)
- [Debugger mit dem DebuggerTypeProxy-Attribut anweisen, welcher Typ angezeigt werden soll](../debugger/using-debuggertypeproxy-attribute.md)
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
