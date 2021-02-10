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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83527ac4b7d16d2cb06c797924c18f2567f12350
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919191"
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
