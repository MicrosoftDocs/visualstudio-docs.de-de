---
title: Regelsatz für die grundlegenden Regeln für Richtigkeit für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c38d8bc2eefe9c6116f9bde93e475cf332591471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75573234"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Regelsatz für die grundlegenden Regeln für Richtigkeit für verwalteten Code

Der Regelsatz für die grundlegenden Regeln für Richtigkeit konzentriert sich auf logische Fehler und häufige Fehler bei der Verwendung von Framework-APIs. Die grundlegenden Regeln für Richtigkeit enthalten die Regeln im Regelsatz [verwaltete Empfohlene Regeln](managed-recommended-rules-rule-set-for-managed-code.md) .

In der folgenden Tabelle werden alle Regeln im Regelsatz für Microsoft Basic-Regeln für Richtigkeit beschrieben.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1009](../code-quality/ca1009.md)|Ereignishandler korrekt deklarieren.|
|[CA1016](../code-quality/ca1016.md)|Assemblys mit AssemblyVersionAttribute markieren.|
|[CA1033](../code-quality/ca1033.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1049](../code-quality/ca1049.md)|Typen, die native Ressourcen besitzen, müssen gelöscht werden können.|
|[CA1060](../code-quality/ca1060.md)|P/Invokes in NativeMethods-Klasse verschieben.|
|[CA1061](../code-quality/ca1061.md)|Basisklassenmethoden nicht ausblenden.|
|[CA1063](../code-quality/ca1063.md)|IDisposable korrekt implementieren.|
|[CA1065](../code-quality/ca1065.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen.|
|[CA1301](../code-quality/ca1301.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1400](../code-quality/ca1400.md)|Für P/Invoke müssen Einstiegspunkte vorhanden sein.|
|[CA1401](../code-quality/ca1401.md)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein.|
|[CA1404](../code-quality/ca1404.md)|GetLastError unmittelbar nach P/Invoke aufrufen.|
|[CA1405](../code-quality/ca1405.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein.|
|[CA1410](../code-quality/ca1410.md)|Die COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415.md)|P/Invokes korrekt deklarieren.|
|[CA1821](../code-quality/ca1821.md)|Leere Finalizer entfernen.|
|[CA1900](../code-quality/ca1900.md)|Werttypfelder sollten portabel sein.|
|[CA1901](../code-quality/ca1901.md)|Deklarationen von P/Invoke müssen portabel sein.|
|[CA2002](../code-quality/ca2002.md)|Auf Objekten mit schwacher Identität nicht sperren.|
|[CA2100](../code-quality/ca2100.md)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2101](../code-quality/ca2101.md)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
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
|[CA2200](../code-quality/ca2200.md)|Erneut ausführen, um Stapeldetails beizubehalten.|
|[CA2202](../code-quality/ca2202.md)|Objekte nicht mehrmals verwerfen.|
|[CA2207](../code-quality/ca2207.md)|Statische Felder für Werttyp inline initialisieren.|
|[CA2212](../code-quality/ca2212.md)|ServicedComponents nicht mit WebMethod markieren.|
|[CA2213](../code-quality/ca2213.md)|Verwerfbare Felder verwerfen.|
|[CA2214](../code-quality/ca2214.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen.|
|[CA2216](../code-quality/ca2216.md)|Verwerfbare Typen sollten einen Finalizer deklarieren.|
|[CA2220](../code-quality/ca2220.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2229](../code-quality/ca2229.md)|Serialisierungskonstruktoren implementieren.|
|[CA2231](../code-quality/ca2231.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms-Einstiegspunkte mit STAThread markieren.|
|[CA2235](../code-quality/ca2235.md)|Alle nicht serialisierbaren Felder markieren.|
|[CA2236](../code-quality/ca2236.md)|Basisklassenmethoden auf ISerializable-Typen aufrufen.|
|[CA2237](../code-quality/ca2237.md)|ISerializable-Typen mit SerializableAttribute markieren.|
|[CA2238](../code-quality/ca2238.md)|Serialisierungsmethoden korrekt implementieren.|
|[CA2240](../code-quality/ca2240.md)|ISerializable ordnungsgemäß implementieren.|
|[CA2241](../code-quality/ca2241.md)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|
|[CA2242](../code-quality/ca2242.md)|Ordnungsgemäß auf NaN testen.|
|[CA1008](../code-quality/ca1008.md)|Enumerationen müssen einen Wert von 0 (null) aufweisen.|
|[CA1013](../code-quality/ca1013.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.|
|[CA1303](../code-quality/ca1303.md)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1308](../code-quality/ca1308.md)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1806](../code-quality/ca1806.md)|Methodenergebnisse nicht ignorieren.|
|[CA1816](../code-quality/ca1816.md)|GC.SuppressFinalize korrekt aufrufen.|
|[CA1819](../code-quality/ca1819.md)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](../code-quality/ca1820.md)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.|
|[CA1903](../code-quality/ca1903.md)|Nur API aus Zielframework verwenden.|
|[CA2004](../code-quality/ca2004.md)|Aufrufe an GC.KeepAlive entfernen.|
|[CA2006](../code-quality/ca2006.md)|SafeHandle verwenden, um native Ressourcen zu kapseln.|
|[CA2102](../code-quality/ca2102.md)|Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.|
|[CA2104](../code-quality/ca2104.md)|Schreibgeschützte änderbare Referenztypen nicht deklarieren.|
|[CA2105](../code-quality/ca2105.md)|Arrayfelder dürfen nicht schreibgeschützt sein.|
|[CA2106](../code-quality/ca2106.md)|Sichere Bestätigungen.|
|[CA2115](../code-quality/ca2115.md)|GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.|
|[CA2119](../code-quality/ca2119.md)|Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.|
|[CA2120](../code-quality/ca2120.md)|Sichere Serialisierungskonstruktoren.|
|[CA2121](../code-quality/ca2121.md)|Statische Konstruktoren sollten privat sein.|
|[CA2130](../code-quality/ca2130.md)|Sicherheitskritische Konstanten sollten transparent sein.|
|[CA2205](../code-quality/ca2205.md)|Verwaltete Entsprechungen der Win32 API verwenden.|
|[CA2215](../code-quality/ca2215.md)|Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.|
|[CA2221](../code-quality/ca2221.md)|Finalizer sollten geschützt sein.|
|[CA2222](../code-quality/ca2222.md)|Sichtbarkeit für geerbte Member nicht verringern.|
|[CA2223](../code-quality/ca2223.md)|Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224.md)|Equals beim Überladen von Gleichheitsoperatoren überschreiben.|
|[CA2226](../code-quality/ca2226.md)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](../code-quality/ca2227.md)|Sammlungseigenschaften sollten schreibgeschützt sein.|
|[CA2239](../code-quality/ca2239.md)|Deserialisierungsmethoden für optionale Felder angeben.|
