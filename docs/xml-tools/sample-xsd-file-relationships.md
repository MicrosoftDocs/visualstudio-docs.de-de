---
title: 'XSD-Beispieldatei: Beziehungen'
description: Hier erfahren Sie, wie Sie die XSD-Beispieldatei für ein Bestellungsschema mit Anmerkungen und Dokumentation anzeigen, das in verschiedenen Beispielen in der Dokumentation zum XSD-Schema-Designer verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dd4e4f3678cd59562f5945ab26f8d828210375c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398747"
---
# <a name="sample-xsd-file-relationships"></a>XSD-Beispieldatei: Beziehungen

Die folgende XSD-Datei wird in verschiedenen Beispielen in der Dokumentation zum XSD-Schema-Designer verwendet. Bei dieser Datei handelt es sich um ein Bestellungsschema mit Anmerkungen und Dokumentation.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="pet" type="PetType"/>

  <xs:attributeGroup name="NameAgeAttributes">
    <xs:attribute name="age" type="xs:integer" use="required"/>
    <xs:attribute name="name" type="xs:string" use="required"/>
  </xs:attributeGroup>

  <xs:complexType name="PetType">
    <xs:attributeGroup ref="NameAgeAttributes"/>
  </xs:complexType>

  <xs:element name="cat" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

  <xs:element name="dog" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

</xs:schema>
```

> [!NOTE]
> Die in den Beispielen genannten Unternehmen, Organisationen, Produkte, Domänennamen, E-Mail-Adressen, Logos, Personen, Orte und Ereignisse sind frei erfunden. Jede Ähnlichkeit mit bestehenden Unternehmen, Organisationen, Produkten, Domänen, E-Mail-Adressen, Logos, Personen, Orten oder Ereignissen ist rein zufällig.
