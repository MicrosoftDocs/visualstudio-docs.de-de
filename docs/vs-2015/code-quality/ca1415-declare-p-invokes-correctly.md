---
title: 'CA1415: P deklarieren: ordnungsgemäße Aufrufe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547848"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invokes korrekt deklarieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der P/Aufruf, der den Parameter deklariert, außerhalb der Assembly nicht sichtbar ist. Unterbrechung: Wenn der P/Aufruf, der den Parameter deklariert, außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Eine Platt Form Aufruf Methode wurde falsch deklariert.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mithilfe des- `Declare` Schlüssel Worts in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oder definiert <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Derzeit sucht diese Regel nach Platt Form Aufruf-Methoden Deklarationen, die auf Win32-Funktionen abzielen, die einen Zeiger auf einen übergebenen Struktur Parameter aufweisen, und der entsprechende verwaltete Parameter ist kein Zeiger auf eine- <xref:System.Threading.NativeOverlapped?displayProperty=fullName> Struktur.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, deklarieren Sie die Platt Form Aufruf Methode ordnungsgemäß.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Platt Form Aufruf Methoden, die gegen die Regel verstoßen und die Regel erfüllen.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 [Interoperabilität mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
