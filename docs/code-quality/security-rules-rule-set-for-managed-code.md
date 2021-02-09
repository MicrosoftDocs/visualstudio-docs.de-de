---
title: Regelsatz für Sicherheitsregeln für verwalteten Code
ms.date: 11/04/2016
description: Erfahren Sie mehr über den Regelsatz für Sicherheitsregeln für die Legacy Code Analyse von Visual Studio. Siehe Beschreibungen von Regeln, die sich auf potenzielle Sicherheitsprobleme konzentrieren.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2568137d5724613b0f5ddf801df6302c85e430f1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859683"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Regelsatz für Sicherheitsregeln für verwalteten Code

Verwenden Sie den Microsoft-Regelsatz für Sicherheitsregeln für die Legacy Code Analyse, um die Anzahl potenzieller Sicherheitsprobleme zu maximieren, die gemeldet werden.

|Regel|Beschreibung|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2102](../code-quality/ca2102.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.|
|[CA2103](../code-quality/ca2103.md)|Imperative Sicherheit überprüfen.|
|[CA2104](../code-quality/ca2104.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren.|
|[CA2105](../code-quality/ca2105.md)|Arrayfelder dürfen nicht schreibgeschützt sein.|
|[CA2106](../code-quality/ca2106.md)|Sichere Bestätigungen.|
|[CA2107](../code-quality/ca2107.md)|Verwendung von Deny und PermitOnly überprüfen.|
|[CA2108](../code-quality/ca2108.md)|Deklarative Sicherheit auf Werttypen überprüfen.|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Sichtbare Ereignishandler überprüfen.|
|[CA2111](../code-quality/ca2111.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2115](../code-quality/ca2115.md)|GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.|
|[CA2116](../code-quality/ca2116.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2118](../code-quality/ca2118.md)|Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen.|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.|
|[CA2120](../code-quality/ca2120.md)|Sichere Serialisierungskonstruktoren.|
|[CA2121](../code-quality/ca2121.md)|Statische Konstruktoren sollten privat sein.|
|[CA2122](../code-quality/ca2122.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen.|
|[CA2123](../code-quality/ca2123.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124.md)|Anfällige finally-Klauseln mit äußerem try-Block umschließen.|
|[CA2126](../code-quality/ca2126.md)|Typlinkaufrufe erfordern Vererbungsanforderungen.|
|[CA2130](../code-quality/ca2130.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2131](../code-quality/ca2131.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|
|[CA2133](../code-quality/ca2133.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.|
|[CA2134](../code-quality/ca2134.md)|Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.|
|[CA2135](../code-quality/ca2135.md)|Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.|
|[CA2136](../code-quality/ca2136.md)|Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.|
|[CA2137](../code-quality/ca2137.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2139](../code-quality/ca2139.md)|Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.|
|[CA2140](../code-quality/ca2140.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141.md)|Transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen.|
|[CA2142](../code-quality/ca2142.md)|Transparenter Code darf nicht mit LinkDemands geschützt werden.|
|[CA2143](../code-quality/ca2143.md)|Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.|
|[CA2144](../code-quality/ca2144.md)|Transparenter Code darf keine Assemblys aus Bytearrays laden.|
|[CA2145](../code-quality/ca2145.md)|Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden.|
|[CA2146](../code-quality/ca2146.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|
|[CA2147](../code-quality/ca2147.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.|
|[CA2149](../code-quality/ca2149.md)|Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.|
|[CA2210](../code-quality/ca2210.md)|Assemblys müssen gültige starke Namen aufweisen.|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|Unsicheren Deserialisierer nicht verwenden: LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|Nicht deserialisieren, ohne zuerst NetDataContractSerializer.Binder festzulegen|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|Unsicheren Deserialisierer nicht verwenden: ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|Nicht mit JavaScriptSerializer und SimpleTypeResolver deserialisieren|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Vor dem Deserialisieren sicherstellen, dass JavaScriptSerializer nicht mit SimpleTypeResolver initialisiert ist|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|Review code for SQL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von SQL-Befehlen)|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|Review code for XSS vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch XSS)|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Review code for file path injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen über einen Dateipfad)|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|Review code for LDAP injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von LDAP-Befehlen)|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|Review code for XML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XML-Befehlen)|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|Verwenden Sie keine unsicheren Verschlüsselungsmodi.|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|Keine Hartcodierung von Zertifikaten|