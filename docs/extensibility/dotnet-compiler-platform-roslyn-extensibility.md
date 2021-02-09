---
title: .NET Compiler Platform ( &quot; Roslyn &quot; )-Erweiterbarkeit | Microsoft-Dokumentation
description: Erfahren Sie mehr über das .NET Compiler Platform, das es Tools und Entwicklern ermöglicht, die umfassenden Informationen zu Programmen zu verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c0286bb35f8a58a2f5fd6cfa95cff62d523567c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883557"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform ( &quot; Roslyn &quot; )-Erweiterbarkeit
Die Hauptaufgabe des .NET Compiler Platform ("Roslyn") besteht darin, die c#-und Visual Basic Compiler zu öffnen und Tools und Entwickler zu ermöglichen, die umfassenden Informationen zu Programmen zu verwenden. Code Analysetools verbessern die Codequalität, und Code-Generatoren helfen bei der Anwendungs Erstellung. Da Tools intelligenter werden, benötigen Sie Zugriff auf mehr und mehr von Deep Code-wissen, das nur Compiler besitzen. Anstatt nicht transparente Konvertierer (Quellcode in und Objektcode out) zu werden, bieten die Roslyn-Compiler APIs, die Sie für Code bezogene Aufgaben in ihren Tools und Anwendungen verwenden können.

 Der beste Teil besteht darin, dass die Roslyn-Compiler, ihre APIs, Beispiele und Exemplarische Vorgehensweisen und die echten Tools, die auf diesen APIs basieren, vollständig Open Source unter [GitHub.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn)sind. Besuchen Sie die OSS-Website, um weitere Informationen zu erhalten, und beginnen Sie mit Roslyn. Links zum Abrufen der neuesten c#-und Visual Basic Features, die Sie als Endbenutzer verwenden können, sowie Links zu den ersten Schritten als Tool Generator, der die Roslyn-APIs nutzt.

## <a name="see-also"></a>Weitere Informationen
- [Einstieg in Roslyn-Analysen](../extensibility/getting-started-with-roslyn-analyzers.md)
