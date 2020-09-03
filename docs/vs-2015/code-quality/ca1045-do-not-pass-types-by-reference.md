---
title: 'CA1045: Typen nicht als Verweis übergeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dad2f90a51a4247a4c111ef51e85a28ba1a118ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548472"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Typen nicht als Verweis übergeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über einen `ref` Parameter, der einen primitiven Typ, einen Verweistyp oder einen Werttyp annimmt, bei dem es sich nicht um einen der integrierten Typen handelt.

## <a name="rule-description"></a>Beschreibung der Regel
 Die Übergabe von Typen als Verweis (mit `out` oder `ref` ) erfordert die Verwendung von Zeigern, das Verständnis der Unterschiede zwischen Werttypen und Verweis Typen sowie die Behandlung von Methoden mit mehreren Rückgabe Werten. Außerdem wird der Unterschied zwischen `out` -und- `ref` Parametern nicht häufig verstanden.

 Wenn ein Verweistyp als Verweis übergeben wird, beabsichtigt die Methode, den-Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. (Die Übergabe eines Verweis Typs als Verweis wird auch als Verwendung eines doppelten Zeigers, Zeiger auf einen Zeiger oder doppelte Dereferenzierung bezeichnet.) Mit der Standard Aufruf Konvention, die als Wert übergeben wird, erhält ein Parameter, der einen Verweistyp annimmt, bereits einen Zeiger auf das Objekt. Der Zeiger, nicht das Objekt, auf das es verweist, wird als Wert übermittelt. Das übergeben nach Wert bedeutet, dass die Methode den Zeiger nicht ändern kann, damit Sie auf eine neue Instanz des Verweis Typs verweist, kann jedoch den Inhalt des Objekts ändern, auf das es verweist. Dies ist für die meisten Anwendungen ausreichend und liefert das gewünschte Verhalten.

 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie den Rückgabewert der-Methode, um dies zu erreichen. Eine Reihe <xref:System.String?displayProperty=fullName> von Methoden, die mit Zeichen folgen arbeiten und eine neue Instanz einer Zeichenfolge zurückgeben, finden Sie unter der-Klasse. Wenn dieses Modell verwendet wird, wird es dem Aufrufer überlassen, zu entscheiden, ob das ursprüngliche Objekt beibehalten wird.

 Obwohl Rückgabewerte alltäglich und stark verwendet werden, sind für die korrekte Anwendung von `out` -und- `ref` Parametern zwischen Entwurfs-und Codierungs Fähigkeiten erforderlich. Bibliotheks Architekten, die für eine allgemeine Zielgruppe entwerfen, sollten nicht erwarten, dass Benutzer die Arbeit mit- `out` oder- `ref` Parametern meistern.

> [!NOTE]
> Wenn Sie mit Parametern arbeiten, die große Strukturen darstellen, können die zusätzlichen Ressourcen, die erforderlich sind, um diese Strukturen zu kopieren, beim übergeben nach Wert einen Leistungs Effekt verursachen. In diesen Fällen können Sie die Verwendung der `ref` Parameter oder in Erwägung gezogen `out` .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, der durch einen Werttyp verursacht wird, lassen Sie die Methode das Objekt als Rückgabewert zurückgeben. Wenn die Methode mehrere Werte zurückgeben muss, entwerfen Sie Sie so um, dass eine einzelne Instanz eines Objekts zurückgegeben wird, das die Werte enthält.

 Um einen Verstoß gegen diese Regel zu beheben, der durch einen Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten eine neue Instanz des Verweises zurückgeben soll. Wenn dies der Fall ist, sollte die Methode ihren Rückgabewert verwenden, um dies zu tun.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Dieser Entwurf kann jedoch Probleme mit der Benutzerfreundlichkeit verursachen.

## <a name="example"></a>Beispiel
 Die folgende Bibliothek zeigt zwei Implementierungen einer-Klasse, die Antworten auf das Feedback des Benutzers generiert. Die erste Implementierung ( `BadRefAndOut` ) zwingt den Bibliotheks Benutzer, drei Rückgabewerte zu verwalten. Die zweite Implementierung ( `RedesignedRefAndOut` ) vereinfacht die Benutzer Leistung durch die Rückgabe einer Instanz einer Container Klasse ( `ReplyData` ), die die Daten als einzelne Einheit verwaltet.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung veranschaulicht die Benutzeroberflächen Darstellung. Der-Befehl für die neu gestaltete Bibliothek ( `UseTheSimplifiedClass` -Methode) ist einfacher, und die von der-Methode zurückgegebenen Informationen können problemlos verwaltet werden. Die Ausgabe der beiden Methoden ist identisch.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Beispiel Bibliothek veranschaulicht `ref` , wie Parameter für Verweis Typen verwendet werden, und zeigt eine bessere Möglichkeit, diese Funktionalität zu implementieren.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft jede Methode in der Bibliothek auf, um das Verhalten zu veranschaulichen.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Ändern des Zeigers, der durch den Wert** 
 " **12345** 
 **12345** 
 **Ändern des Zeigers-als Verweis übermittelt:** 
 **12345** 
 **12345 ABCDE** 
 **Übergeben als Rückgabewert:** 
 **12345 ABCDE**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1021: out-Parameter vermeiden.](../code-quality/ca1021-avoid-out-parameters.md)
