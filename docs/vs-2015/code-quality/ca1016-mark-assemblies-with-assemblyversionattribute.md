---
title: 'CA1016: Assemblys mit AssemblyVersionAttribute markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 97bd41e51c8d6b5415ffb91c5696c7055f46cf7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545404"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Assemblys mit AssemblyVersionAttribute markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Die Assembly hat keine Versionsnummer.

## <a name="rule-description"></a>Beschreibung der Regel
 Die Identität einer Assembly besteht aus den folgenden Informationen:

- Assemblyname

- Versionsnummer

- Kultur

- Öffentlicher Schlüssel (für Assemblys mit starkem Namen).

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verwendet die Versionsnummer für die eindeutige Identifizierung einer Assembly und zum Binden an Datentypen in Assemblys mit starkem Namen. Die Versionsnummer wird zusammen mit der Versions- und Herausgeberrichtlinie verwendet. Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Assembly mithilfe des-Attributs eine Versionsnummer hinzu <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> . Siehe folgendes Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel nicht für Assemblys, die von Drittanbietern oder in einer Produktionsumgebung verwendet werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, auf die das- <xref:System.Reflection.AssemblyVersionAttribute> Attribut angewendet wurde.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Weitere Informationen
 [Assemblyversionierung](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) Gewusst [wie: Erstellen einer Herausgeber Richtlinie](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
