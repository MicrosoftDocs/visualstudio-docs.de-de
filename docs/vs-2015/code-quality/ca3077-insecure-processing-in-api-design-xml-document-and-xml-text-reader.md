---
title: 'CA3077: unsichere Verarbeitung in API-Design, XML-Dokument und XML-Text Reader | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c0d6a6f6ab42d69d4503741f6625627c46d4ef77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545105"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Textreader.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Beim Entwerfen einer von XMLDocument und XMLTextReader abgeleiteten API sollten Sie <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>berücksichtigen.  Das Verwenden unsicherer DTDProcessing-Instanzen beim Verweisen auf externe Entitätsquellen bzw. bei deren Auflösung oder das Festlegen unsicherer Werte in XML-Code kann zum Offenlegen von Informationen führen.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine [Document Type Definition (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) ist eine von zwei Methoden, mit denen ein XML-Parser die Gültigkeit eines Dokuments gemäß  [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](https://www.w3.org/TR/2008/REC-xml-20081126/)bestimmen kann. Diese Regel sucht Eigenschaften und Instanzen, die nicht vertrauenswürdige Daten akzeptieren, um Entwickler vor potenziellen [Information Disclosure](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) -Bedrohungen zu warnen, die zu [Denial-of-Service-Angriffen (DoS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) führen können. Diese Regel wird  in folgenden Fällen ausgelöst:

- <xref:System.Xml.XmlDocument> -oder- <xref:System.Xml.XmlTextReader> Klassen verwenden standardresolverwerte für die DTD-Verarbeitung.

- Für die abgeleiteten XmlDocument- oder XmlTextReader-Klassen wurde kein Konstruktor definiert oder für <xref:System.Xml.XmlResolver>wird kein sicherer Wert verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Alle XmlTextReader-Ausnahmen ordnungsgemäß erfassen und verarbeiten, um die Offenlegung von Pfadinformationen zu vermeiden.

- Verwenden  <xref:System.Xml.XmlSecureResolver> Sie anstelle von XmlResolver, um die Ressourcen einzuschränken, auf die der XmlTextReader zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```
