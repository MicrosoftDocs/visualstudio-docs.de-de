---
title: Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code
ms.date: 11/04/2016
description: Erfahren Sie mehr über den Regelsatz für erweiterte Regeln für Richtigkeit in Visual Studio, der für die COM-Interoperabilität und Mobile Anwendungen nützlich ist. Siehe Regel Beschreibungen.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: a70a0315d596e4490d40db1846d7be0b6f3bf448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860372"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code

Der Regelsatz für erweiterte Richtigkeit von Regeln von Microsoft maximiert die Fehler bei der Logik-und frameworkverwendung, die von der Code Analyse gemeldet werden. Zusätzlicher Schwerpunkt liegt auf bestimmten Szenarien, wie z. b. com-Interoperabilität und mobilen Anwendungen. Sie sollten diesen Regelsatz einschließen, wenn eines dieser Szenarien auf Ihr Projekt zutrifft, oder um weitere Probleme in Ihrem Projekt zu finden.

Der Regelsatz für die erweiterten Regeln für Richtigkeit von Microsoft enthält die Regeln, die im Regelsatz [grundlegender Regeln](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) für die Richtigkeit von Regeln enthalten sind, der die Regeln im Regelsatz für [verwaltete Empfohlene Regeln](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) enthält.

In der folgenden Tabelle werden alle Regeln im Regelsatz für erweiterte Regeln für Richtigkeit von Microsoft beschrieben.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1009](../code-quality/ca1009.md)|Ereignishandler korrekt deklarieren.|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Assemblys mit AssemblyVersionAttribute markieren.|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1049](../code-quality/ca1049.md)|Typen, die native Ressourcen besitzen, müssen gelöscht werden können.|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|P/Invokes in NativeMethods-Klasse verschieben.|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Basisklassenmethoden nicht ausblenden.|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|IDisposable korrekt implementieren.|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Keine Ausnahmen an unerwarteten Speicherorten auslösen.|
|[CA1301](../code-quality/ca1301.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1400](../code-quality/ca1400.md)|Für P/Invoke müssen Einstiegspunkte vorhanden sein.|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein.|
|[CA1404](../code-quality/ca1404.md)|GetLastError unmittelbar nach P/Invoke aufrufen.|
|[CA1405](../code-quality/ca1405.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein.|
|[CA1410](../code-quality/ca1410.md)|Die COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415.md)|P/Invokes korrekt deklarieren.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Leere Finalizer entfernen.|
|[CA1900](../code-quality/ca1900.md)|Werttypfelder sollten portabel sein.|
|[CA1901](../code-quality/ca1901.md)|Deklarationen von P/Invoke müssen portabel sein.|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Auf Objekten mit schwacher Identität nicht sperren.|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
|[CA2108](../code-quality/ca2108.md)|Deklarative Sicherheit auf Werttypen überprüfen.|
|[CA2111](../code-quality/ca2111.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2116](../code-quality/ca2116.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2122](../code-quality/ca2122.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen.|
|[CA2123](../code-quality/ca2123.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124.md)|Anfällige finally-Klauseln mit äußerem try-Block umschließen.|
|[CA2126](../code-quality/ca2126.md)|Typlinkaufrufe erfordern Vererbungsanforderungen.|
|[CA2131](../code-quality/ca2131.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|
|[CA2133](../code-quality/ca2133.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.|
|[CA2134](../code-quality/ca2134.md)|Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.|
|[CA2137](../code-quality/ca2137.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2140](../code-quality/ca2140.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141.md)|Transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen.|
|[CA2146](../code-quality/ca2146.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|
|[CA2147](../code-quality/ca2147.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.|
|[CA2149](../code-quality/ca2149.md)|Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Erneut ausführen, um Stapeldetails beizubehalten.|
|[CA2202](../code-quality/ca2202.md)|Objekte nicht mehrmals verwerfen.|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Statische Felder für Werttyp inline initialisieren.|
|[CA2212](../code-quality/ca2212.md)|ServicedComponents nicht mit WebMethod markieren.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Verwerfbare Felder verwerfen.|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Überschreibbare Methoden in Konstruktoren nicht aufrufen.|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Verwerfbare Typen sollten einen Finalizer deklarieren.|
|[CA2220](../code-quality/ca2220.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Serialisierungskonstruktoren implementieren.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms-Einstiegspunkte mit STAThread markieren.|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Alle nicht serialisierbaren Felder markieren.|
|[CA2236](../code-quality/ca2236.md)|Basisklassenmethoden auf ISerializable-Typen aufrufen.|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|ISerializable-Typen mit SerializableAttribute markieren.|
|[CA2238](../code-quality/ca2238.md)|Serialisierungsmethoden korrekt implementieren.|
|[CA2240](../code-quality/ca2240.md)|ISerializable ordnungsgemäß implementieren.|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Ordnungsgemäß auf NaN testen.|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Enumerationen müssen einen Wert von 0 (null) aufweisen.|
|[CA1013](../code-quality/ca1013.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Methodenergebnisse nicht ignorieren.|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|GC.SuppressFinalize korrekt aufrufen.|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.|
|[CA1903](../code-quality/ca1903.md)|Nur API aus Zielframework verwenden.|
|[CA2004](../code-quality/ca2004.md)|Aufrufe an GC.KeepAlive entfernen.|
|[CA2006](../code-quality/ca2006.md)|SafeHandle verwenden, um native Ressourcen zu kapseln.|
|[CA2102](../code-quality/ca2102.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.|
|[CA2104](../code-quality/ca2104.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren.|
|[CA2105](../code-quality/ca2105.md)|Arrayfelder dürfen nicht schreibgeschützt sein.|
|[CA2106](../code-quality/ca2106.md)|Sichere Bestätigungen.|
|[CA2115](../code-quality/ca2115.md)|GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.|
|[CA2120](../code-quality/ca2120.md)|Sichere Serialisierungskonstruktoren.|
|[CA2121](../code-quality/ca2121.md)|Statische Konstruktoren sollten privat sein.|
|[CA2130](../code-quality/ca2130.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2205](../code-quality/ca2205.md)|Verwaltete Entsprechungen der Win32 API verwenden.|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.|
|[CA2221](../code-quality/ca2221.md)|Finalizer sollten geschützt sein.|
|[CA2222](../code-quality/ca2222.md)|Sichtbarkeit für geerbte Member nicht verringern.|
|[CA2223](../code-quality/ca2223.md)|Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224.md)|Equals beim Überladen von Gleichheitsoperatoren überschreiben.|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Sammlungseigenschaften sollten schreibgeschützt sein.|
|[CA2239](../code-quality/ca2239.md)|Deserialisierungsmethoden für optionale Felder angeben.|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Standardausnahmekonstruktoren implementieren.|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI-Parameter dürfen keine Zeichenfolgen sein.|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI-Rückgabewerte dürfen keine Zeichenfolgen sein.|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|
|[CA1057](../code-quality/ca1057.md)|URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.|
|[CA1402](../code-quality/ca1402.md)|Überladungen in für COM sichtbaren Schnittstellen vermeiden.|
|[CA1406](../code-quality/ca1406.md)|Int64-Argumente für Visual Basic 6-Clients vermeiden.|
|[CA1407](../code-quality/ca1407.md)|Statische Member in für COM sichtbaren Typen vermeiden.|
|[CA1408](../code-quality/ca1408.md)|AutoDual ClassInterfaceType nicht verwenden.|
|[CA1409](../code-quality/ca1409.md)|Für COM sichtbare Typen müssen erstellt werden können.|
|[CA1411](../code-quality/ca1411.md)|Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.|
|[CA1412](../code-quality/ca1412.md)|ComSource-Schnittstellen als IDispatch markieren.|
|[CA1413](../code-quality/ca1413.md)|Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.|
|[CA1414](../code-quality/ca1414.md)|Boolesche P/Invoke-Argumente mit MarshalAs markieren.|
|[CA1600](../code-quality/ca1600.md)|Verwenden Sie keine Prozesse mit der Priorität "idle".|
|[CA1601](../code-quality/ca1601.md)|Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern.|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Assemblys mit NeutralResourcesLanguageAttribute markieren.|
|[CA2001](../code-quality/ca2001.md)|Keine problematischen Methoden aufrufen.|
|[CA2003](../code-quality/ca2003.md)|Fibers nicht als Threads behandeln.|
|[CA2135](../code-quality/ca2135.md)|Assemblys der Stufe 2 dürfen keine LinkDemands enthalten.|
|[CA2136](../code-quality/ca2136.md)|Member dürfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen.|
|[CA2139](../code-quality/ca2139.md)|Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.|
|[CA2142](../code-quality/ca2142.md)|Transparenter Code darf nicht mit LinkDemands geschützt werden.|
|[CA2143](../code-quality/ca2143.md)|Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.|
|[CA2144](../code-quality/ca2144.md)|Transparenter Code darf keine Assemblys aus Bytearrays laden.|
|[CA2145](../code-quality/ca2145.md)|Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden.|
|[CA2204](../code-quality/ca2204.md)|Literale sollten eine korrekte Rechtschreibung aufweisen.|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Nicht konstante Felder sollten nicht sichtbar sein.|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Enumerationen nicht mit FlagsAttribute markieren.|
|[CA2218](../code-quality/ca2218.md)|GetHashCode beim Überschreiben von Equals überschreiben.|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Keine Ausnahmen in Ausnahmeklauseln auslösen.|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Operatorüberladungen weisen benannte Alternativen auf.|
|[CA2228](../code-quality/ca2228.md)|Nicht freigegebene Ressourcenformate nicht veröffentlichen.|
|[CA2230](../code-quality/ca2230.md)|params für Variablenargumente verwenden.|
|[CA2233](../code-quality/ca2233.md)|Vorgänge sollten nicht überlaufen.|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.|
