---
title: 'CA2116: APTCA-Methoden sollten nur APTCA-Methoden abrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 115c0e733716994ba463eada938f8ff908612d0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547757"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einer Assembly mit dem- <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> Attribut ruft eine Methode in einer Assembly auf, die nicht über das-Attribut verfügt.

## <a name="rule-description"></a>Beschreibung der Regel
 Standardmäßig werden öffentliche oder geschützte Methoden in Assemblys mit starken Namen implizit durch einen [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) Aufruf für volle Vertrauenswürdigkeit geschützt. nur voll vertrauenswürdige Aufrufer können auf eine Assembly mit starkem Namen zugreifen. Assemblys mit starkem Namen, die mit dem- <xref:System.Security.AllowPartiallyTrustedCallersAttribute> Attribut (APTCA) gekennzeichnet sind, verfügen nicht über diesen Schutz. Das-Attribut deaktiviert den Link Aufruf, sodass Aufrufer, die nicht voll vertrauenswürdig sind, wie z. b. Code, der über ein Intranet oder das Internet ausgeführt wird, auf die Assembly zugreifen können.

 Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und die Assembly Code in einer anderen Assembly ausführt, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann eine Sicherheitslücke ausgenutzt werden. Wenn zwei Methoden `M1` und `M2` die folgenden Bedingungen erfüllen, können böswillige Aufrufer die-Methode verwenden, `M1` um den impliziten voll vertrauenswürdigen Link Bedarf zu umgehen, der schützt `M2` :

- `M1` ist eine öffentliche Methode, die in einer voll vertrauenswürdigen Assembly mit dem APTCA-Attribut deklariert ist.

- `M1` Ruft eine Methode `M2` außerhalb `M1` der Assembly auf.

- `M2`die Assembly verfügt nicht über das APTCA-Attribut und sollte daher nicht von oder im Auftrag von Aufrufern ausgeführt werden, die teilweise vertrauenswürdig sind.

  Ein teilweise vertrauenswürdiger `X` Aufrufer kann die-Methode aufzurufen `M1` , wodurch `M1` aufgerufen wird `M2` . Da `M2` nicht über das APTCA-Attribut verfügt, muss der unmittelbare Aufrufer ( `M1` ) einen Link Aufruf für volle Vertrauenswürdigkeit erfüllen; `M1` hat volle Vertrauenswürdigkeit und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko besteht darin `X` , dass nicht an der Erfüllung des Link Bedarfs teilnimmt, der `M2` vor nicht vertrauenswürdigen Aufrufern schützt. Daher dürfen Methoden mit dem APTCA-Attribut keine Methoden aufzurufen, die nicht über das-Attribut verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn das apcta-Attribut erforderlich ist, verwenden Sie eine Anforderung, um die Methode zu schützen, die die voll vertrauenswürdige Assembly aufruft. Welche Berechtigungen Sie benötigen, hängt von der Funktionalität ab, die von der-Methode verfügbar gemacht wird. Wenn dies möglich ist, schützen Sie die Methode mit einer Anforderung für vollständige Vertrauenswürdigkeit, um sicherzustellen, dass die zugrunde liegende Funktionalität nicht teilweise vertrauenswürdigen Aufrufern ausgesetzt ist. Wenn dies nicht möglich ist, wählen Sie einen Berechtigungs Satz aus, der die verfügbaren Funktionen effektiv schützt. Weitere Informationen zu den Anforderungen finden Sie unter [Anforderungen](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass die von der-Methode verfügbar gemachten Funktionen nicht direkt oder indirekt Aufrufern Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen ermöglichen, die auf zerstörerische Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden zwei Assemblys und eine Testanwendung verwendet, um das Sicherheitsrisiko zu veranschaulichen, das von dieser Regel erkannt wird. Die erste Assembly verfügt nicht über das APTCA-Attribut und sollte nicht für teilweise vertrauenswürdige Aufrufer (dargestellt durch `M2` in der vorherigen Diskussion) verfügbar sein.

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Beispiel
 Die zweite Assembly ist voll vertrauenswürdig und ermöglicht teilweise vertrauenswürdige Aufrufer ( `M1` in der vorherigen Diskussion dargestellt).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Beispiel
 Die Testanwendung (dargestellt durch `X` in der vorherigen Diskussion) ist teilweise vertrauenswürdig.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Anforderung für vollständige Vertrauenswürdigkeit: Fehler bei der Anforderung.** 
 **Classrequensingfulltrust. DoWork wurde aufgerufen.**
## <a name="related-rules"></a>Verwandte Regeln
 [CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Weitere Informationen
 [Sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) .NET Framework Assemblys, die [von teilweise vertrauenswürdigem Code mithilfe von](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [Bibliotheken aus teilweise vertrauenswürdigem Code](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [benötigt](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) werden [, erfordern Verknüpfungs](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
