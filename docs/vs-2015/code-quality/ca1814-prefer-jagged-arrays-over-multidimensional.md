---
title: 'CA1814: verzweigte Arrays über mehrdimensional bevorzugen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ece9105e8a0a854837924e4a2d4f4ec485a5e202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543935"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Jagged Arrays mehrdimensionalen Arrays vorziehen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Member wird als mehrdimensionales Array deklariert.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führt, dass weniger Speicherplatz vergeudet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das mehrdimensionale Array in ein Jagged Array.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn das mehrdimensionale Array keinen Speicherplatz verschwendet.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Deklarationen für verzweigte und mehrdimensionale Arrays.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
