---
title: Regelsatz für Globalisierungsregeln für verwalteten Code
ms.date: 11/04/2016
description: Erfahren Sie mehr über den Regelsatz für Globalisierungsregeln in Visual Studio, der sich auf Probleme im Zusammenhang mit Sprachen, Gebiets Schemas und Kulturen konzentriert. Siehe Regel Beschreibungen.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: fdf816b978aac5d22b1750eeabe3737f1eb64085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867931"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Regelsatz für Globalisierungsregeln für verwalteten Code

Verwenden Sie den Regelsatz Microsoft-Globalisierungsregeln, um sich auf Probleme zu konzentrieren, die möglicherweise verhindern, dass Daten in Ihrer Anwendung in verschiedenen Sprachen, Gebiets Schemata und Kulturen ordnungsgemäß angezeigt werden. Sie sollten diesen Regelsatz einschließen, wenn Ihre Anwendung lokalisiert, globalisiert oder beides ist.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|CultureInfo angeben.|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|IFormatProvider angeben.|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|StringComparison zur Übersichtlichkeit angeben|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Ordinal-StringComparison verwenden.|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|StringComparison für Richtigkeit angeben|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
