---
title: 'DA0011: Speicherintensive CompareTo-Funktionen | Microsoft-Dokumentation'
description: Die CompareTo-Methode des Typs ist aufwändig oder belegt Arbeitsspeicher.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 91219bed2ca0e8b4bbc28825e1505b9d5f78bbc8
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466153"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Speicherintensive CompareTo-Funktionen

|Element|Wert|
|-|-|
|Regel-ID|DA0011|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Sampling<br /><br /> .NET-Arbeitsspeicher|
|Meldung|CompareTo-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen. Reduzieren Sie daher, wenn möglich, die Komplexität der CompareTo-Funktionen.|
|Regeltyp|Warnung|

## <a name="cause"></a>Ursache
 Die CompareTo-Methode des Typs ist aufwändig oder belegt Arbeitsspeicher.

## <a name="rule-description"></a>Regelbeschreibung
 CompareTo-Methoden sollten effizient sein und keinen Arbeitsspeicher zuordnen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Verringern Sie die Komplexität der CompareTo-Methode.
