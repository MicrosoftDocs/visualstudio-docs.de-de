---
title: Regelsatz für verwaltete Mindestregeln für verwalteten Code
ms.date: 11/04/2016
description: Erfahren Sie mehr über den Regelsatz für verwaltete Mindestregeln in Visual Studio, der sich auf Sicherheit, Stabilität und andere kritische Probleme konzentriert. Siehe Regel Beschreibungen.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8711fd0a265618a5aaf4f84edcf7dd2b081b16a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859813"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code

Die verwalteten minimal Regeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, darunter potenzielle Sicherheitslücken, Anwendungs Abstürze und andere wichtige Logik-und Entwurfs Fehler. Fügen Sie diesen Regelsatz in einen benutzerdefinierten Regelsatz ein, den Sie für Ihre Projekte erstellen.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Leere Finalizer entfernen.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Verwerfbare Felder verwerfen.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Gleichheits Operator beim Überschreiben `ValueType.Equals`|
