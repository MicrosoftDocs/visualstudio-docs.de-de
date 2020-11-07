---
title: Codeanalyse für verwalteten Code
ms.date: 08/27/2020
description: Erfahren Sie mehr über .NET Compiler Platform basierte Code Analyse in Visual Studio. Erfahren Sie, warum diese Analytiker die statische FxCop-Analyse verwalteter Assemblys ersetzen.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348527"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Übersicht über die Code Analyse für .net in Visual Studio

Visual Studio kann eine Code Analyse von verwaltetem Code auf zweierlei Weise durchführen: mit [Legacy Analyse](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), auch als "FxCop Static Analysis of Managed Assemblys" bezeichnet, und mit den moderneren [.NET Compiler Platform basierten Code](../code-quality/roslyn-analyzers-overview.md)Analysemodulen. .NET Compiler Platform basierten Code Analysen, die Ihren Code während der durch zugabeart analysieren, ersetzen Sie die statische Code Analyse der veralteten FxCop-Code, die nur kompilierten Code analysiert.
