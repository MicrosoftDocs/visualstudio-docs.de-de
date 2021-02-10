---
title: Leistungsregeln für die .NET Framework-Verwendung | Microsoft-Dokumentation
description: Hier lernen Sie die Leistungsregeln in der Kategorie „.NET Framework Usage“ (.NET Framework-Nutzung) kennen. Identifizieren Sie bestimmte Methoden, die optimiert werden können, sowie allgemeinere Nutzungsmuster.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8ec2756353ac56b3b5d44e2a50c4d4f5b1c7ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955384"
---
# <a name="net-framework-usage-performance-rules"></a>Leistungsregeln für die .NET Framework-Verwendung
Leistungsregeln in der Kategorie .NET Framework-Verwendung identifizieren bestimmte Methoden, die optimiert werden können, sowie allgemeinere Verwendungsschemas, z.B. die Garbage Collection und Sperrkonflikte, die auf Leistungsprobleme überprüft werden können.

|Regel|Beschreibung|
|-|-|
|[DA0001: StringBuilder für Verkettungen verwenden](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Aufrufe von <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> machen einen großen Teil der Profilerstellungsdaten aus. Verwenden Sie ggf. die <xref:System.Text.StringBuilder>-Klasse zum Erstellen von Zeichenfolgen aus mehreren Segmenten.|
|[DA0005: Häufige Ausführung einer GC der Generation 2](../profiling/da0005-frequent-gc2-collections.md)|Bei der Garbage Collection der Generation 2 wird eine relativ hohe Anzahl von .NET-Speicherobjekten freigegeben. Wenn zu viele kurzlebige Objekte die Garbage Collection der Generation 1 überleben, kann schnell ein unverhältnismäßig hoher Aufwand für die Speicherverwaltung entstehen.|
|[DA0006: Equals() für Werttypen überschreiben](../profiling/da0006-override-equals-parens-for-value-types.md)|Aufrufe der `Equals`-Methode oder der Gleichheitsoperatoren eines öffentlichen Werttyps machen einen großen Teil der Profilerstellungsdaten aus. Implementieren Sie ggf. eine effizientere Methode.|
|[DA0007: Vermeiden der Verwendung von Ausnahmen für die Ablaufsteuerung](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|In den Profilerstellungsdaten wurde eine Vielzahl von .NET Framework-Ausnahmehandlern aufgerufen. Verwenden Sie ggf. eine andere Kontrollflusslogik, um die Anzahl der ausgelösten Ausnahmen zu verringern.|
|[DA0010: Speicherintensive GetHashCode-Funktionen](../profiling/da0010-expensive-gethashcode.md)|Aufrufe der `GetHashCode`-Methode des Typs machen einen großen Teil der Profilerstellungsdaten aus, oder die `GetHashCode`-Methode belegt Arbeitsspeicher. Verringern Sie die Komplexität der Methode.|
|[DA0011: Speicherintensive CompareTo-Funktionen](../profiling/da0011-expensive-compareto.md)|Die `CompareTo`-Methode des Typs ist aufwändig, oder die Methode belegt Arbeitsspeicher. Verringern Sie die Komplexität der `CompareTo`-Methode.|
|[DA0012: Starke Reflektion](../profiling/da0012-significant-amount-of-reflection.md)|Aufrufe der <xref:System.Reflection?displayProperty=fullName>-Methode, z.B. <xref:System.Reflection.IReflect.InvokeMember%2A> und <xref:System.Reflection.IReflect.GetMember%2A> oder der Typmethoden (beispielsweise <xref:System.Type.InvokeMember%2A>) machen einen großen Teil der Profilerstellungsdaten aus. Ersetzen Sie diese Methoden nach Möglichkeit durch eine frühe Bindung an Methoden abhängiger Assemblys.|
|[DA0013: Umfangreiche Verwendung von String.Split oder String.Substring](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Aufrufe der <xref:System.String.Split%2A?displayProperty=fullName>- oder <xref:System.String.Substring%2A>-Methode machen einen großen Teil der Profilerstellungsdaten aus. Erwägen Sie, <xref:System.String.IndexOf%2A> oder <xref:System.String.IndexOfAny%2A> zu verwenden, wenn Sie prüfen, ob eine Teilzeichenfolge in einer Zeichenfolge vorhanden ist.|
|[DA0018: 32-Bit-Anwendung wird an den vom Prozess verwalteten Speicherlimits ausgeführt](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Die bei der Profilerstellung erfassten Systemdaten deuten darauf hin, dass sich die .NET Framework-Arbeitsspeicherheaps der maximalen Größe angenähert haben, die verwaltete Heaps in einem 32-Bit-Prozess erreichen können. Wiederholen Sie die Profilerstellung mit der Methode zur .NET-Speicherprofilerstellung, und optimieren Sie die Verwendung verwalteter Ressourcen durch die Anwendung.|
|[DA0021: Hohes Maß an Garbage Collections der Generation 1](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|Bei der Garbage Collection der Generation 1 wird eine relativ hohe Anzahl von .NET-Speicherobjekten freigegeben. Wenn zu viele kurzlebige Objekte die Garbage Collection der Generation 0 überleben, kann schnell ein unverhältnismäßig hoher Aufwand für die Speicherverwaltung entstehen.|
|[DA0022: Hohes Maß an Garbage Collections der Generation 2](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Bei der Garbage Collection der Generation 2 wird eine hohe Anzahl von .NET-Speicherobjekten freigegeben. Wenn zu viele kurzlebige Objekte die Garbage Collection der Generation 1 überleben, kann schnell ein unverhältnismäßig hoher Aufwand für die Speicherverwaltung entstehen. Diese Regel wird ausgelöst, wenn die Rate von Sperrkonflikten den oberen Schwellenwert der Regel DA0005 überschreitet.|
|[DA0023: Hohe GC-CPU-Zeit](../profiling/da0023-high-gc-cpu-time.md)|Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass für die Garbage Collection im Vergleich zur gesamten Anwendungsverarbeitung viel Zeit aufgewendet wird.|
|[DA0024: Übermäßige GC-CPU-Zeit](../profiling/da0024-excessive-gc-cpu-time.md)|Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass für die Garbage Collection im Vergleich zur gesamten Anwendungsverarbeitung übermäßig viel Zeit aufgewendet wird. Diese Regel wird ausgelöst, wenn die Zeit, die für die Garbage Collection aufgewendet wurde, den oberen Schwellenwert der Regel DA0023 überschreitet.|
|[DA0038: Hohes Maß an Sperrkonflikten](../profiling/da0038-high-rate-of-lock-contentions.md)|Die zusammen mit den Profilerstellungsdaten erfassten Systemleistungsdaten deuten darauf hin, dass während der Anwendungsausführung ein überaus hohes Maß an Sperrkonflikten aufgetreten ist. Wiederholen Sie die Profilerstellung mit der Nebenläufigkeitsmethode, um die Ursache der Konflikte zu ermitteln.|
|[DA0039: Sehr hohes Maß an Sperrkonflikten](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Die zusammen mit den Profilerstellungsdaten erfassten Systemleistungsdaten deuten darauf hin, dass während der Anwendungsausführung ein übermäßig hohes Maß an Sperrkonflikten aufgetreten ist. Wiederholen Sie die Profilerstellung mit der Nebenläufigkeitsmethode, um die Ursache der Konflikte zu ermitteln. Diese Regel wird ausgelöst, wenn die Rate von Sperrkonflikten den oberen Schwellenwert der Regel DA0038 überschreitet.|
