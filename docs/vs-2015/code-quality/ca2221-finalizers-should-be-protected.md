---
title: 'CA2221: Finalizer sollten geschützt werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e30dd2945820a61aa7c96d4e6c6fd59354e0c3ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540737"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Finalizer sollten geschützt sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ implementiert einen Finalizer, der keinen Zugriff auf die Familie (geschützter Zugriff) angibt.

## <a name="rule-description"></a>Beschreibung der Regel
 Finalizer müssen den Familienzugriffsmodifizierer verwenden. Diese Regel wird von den Compilern c#, Visual Basic und Visual C++ erzwungen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Finalizer so, dass er auf die Familie zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Diese Regel kann in keiner .NET-Sprache auf hoher Ebene verletzt werden. Sie kann verletzt werden, wenn Sie die Microsoft Intermediate Language schreiben.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Weitere Informationen
 [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
