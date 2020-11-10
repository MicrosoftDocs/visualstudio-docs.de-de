---
title: Best Practices für MSBuild | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Best Practices zum Schreiben von MSBuild-Skripts, z. B. die Verwendung von Condition-Attributen und das Vermeiden von Platzhaltern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047663"
---
# <a name="msbuild-best-practices"></a>Best Practices für MSBuild

Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild-Skripts empfohlen:

- Standardwerte für Eigenschaften werden am besten mit dem `Condition`-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann. Verwenden Sie beispielsweise

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Im Allgemeinen sollte die Verwendung von Platzhaltern bei der Auswahl von Elementen vermieden werden. Geben Sie stattdessen Dateien explizit an. Dies wird empfohlen, weil MSBuild bei den meisten Projekttypen Platzhalter zu verschiedenen Zeitpunkten erweitert, z. B. beim Hinzufügen oder Entfernen von Elementen. Dies kann zu unerwartetem Verhalten führen. Eine Ausnahme stellen .NET Core-Projekte im SDK-Stil dar, die Platzhalter ordnungsgemäß verarbeiten.

## <a name="see-also"></a>Siehe auch

- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
