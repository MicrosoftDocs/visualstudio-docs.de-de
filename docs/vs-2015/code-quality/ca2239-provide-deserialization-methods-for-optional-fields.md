---
title: 'CA2239: Deserialisierungsmethoden für optionale Felder bereitstellen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dfbb9082d557c8e67ddebf0237293364d54a65cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545131"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Deserialisierungsmethoden für optionale Felder angeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ verfügt über ein Feld, das mit dem <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> -Attribut markiert ist, und der-Typ stellt keine deserialisierungsereignisbehandlungsmethoden bereit.

## <a name="rule-description"></a>Beschreibung der Regel
 Das- <xref:System.Runtime.Serialization.OptionalFieldAttribute> Attribut hat keine Auswirkung auf die Serialisierung. ein mit dem-Attribut gekennzeichnetes Feld wird serialisiert. Das Feld wird bei der Deserialisierung jedoch ignoriert und behält den dem Typ zugeordneten Standardwert bei. Die Deserialisierungsereignishandler müssen deklariert werden, um das Feld während des Deserialisierungsprozesses festzulegen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie dem Typ deserialisierungsereignisbehandlungsmethoden hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn das Feld während des Deserialisierungsprozesses ignoriert werden soll.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ mit optionalen Ereignis Behandlungsmethoden für Feld und Deserialisierung.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120-secure-serialization-constructors.md)
