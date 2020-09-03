---
title: 'CA2120: sichere Serialisierungskonstruktoren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10cfa03adb74871fb42a6e1c2ce4ab4ba6bcae75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544338"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Sichere Serialisierungskonstruktoren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|SecureSerializationConstructors|
|CheckId|CA2120|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der-Typ implementiert die- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle, ist kein Delegat oder eine Schnittstelle und wird in einer Assembly deklariert, die teilweise vertrauenswürdige Aufrufer zulässt. Der-Typ verfügt über einen Konstruktor, der ein <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> -Objekt und ein- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Objekt (die Signatur des Serialisierungskonstruktors) annimmt. Dieser Konstruktor ist nicht durch eine Sicherheitsüberprüfung gesichert, aber ein oder mehrere der regulären Konstruktoren im Typ sind gesichert.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel ist für Typen relevant, die die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, wenn die- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle implementiert wird. Der Serialisierungskonstruktor ist erforderlich und wird zum Deserialisieren oder erneuten Erstellen von Objekten verwendet, die mit der-Methode serialisiert wurden <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> . Da der Serialisierungskonstruktor Objekte zuordnet und initialisiert, müssen Sicherheitsüberprüfungen, die für reguläre Konstruktoren vorhanden sind, auch auf dem Serialisierungskonstruktor vorhanden sein. Wenn Sie gegen diese Regel verstoßen, können Aufrufer, die nicht anderweitig eine Instanz erstellen konnten, den Serialisierungskonstruktor verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, schützen Sie den Serialisierungskonstruktor mit Sicherheitsanforderungen, die mit denen identisch sind, die andere Konstruktoren schützen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keinen Verstoß gegen die Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
