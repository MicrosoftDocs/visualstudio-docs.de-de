---
title: Regelsatz für die erweiterten Entwurfsrichtlinienregeln für verwalteten Code
ms.date: 11/04/2016
description: Erfahren Sie mehr über den Regelsatz für erweiterte Entwurfs Richtlinien Regeln in Visual Studio, der sich auf die Verwendbarkeit und Wartbarkeit konzentriert. Siehe Regel Beschreibungen.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0da23a533ca7667ba946299a3197dd487999afec
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348982"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Regelsatz für die erweiterten Entwurfsrichtlinienregeln für verwalteten Code

Der Regelsatz für Regeln für erweiterte Entwurfs Richtlinien von Microsoft erweitert die grundlegenden Regeln für Entwurfs Richtlinien, um die gemeldeten Nutzbarkeits-und verwaltbarkeitsprobleme zu maximieren. Besonderes Augenmerk wird auf Benennungsrichtlinien gelegt. Sie sollten diesen Regelsatz einschließen, wenn Ihr Projekt Bibliotheks Code enthält, oder wenn Sie die höchsten Standards für das Schreiben von Code erzwingen möchten, der leicht zu verwalten ist.

Die Regeln für erweiterte Entwurfs Richtlinien enthalten alle Regeln im Regelsatz [grundlegender Regeln für Entwurfs Richtlinien](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , der die Regeln im Regelsatz [verwaltete Empfohlene Regeln](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) enthält.

In der folgenden Tabelle werden alle Regeln im Regelsatz Regeln für erweiterte Entwurfs Richtlinien von Microsoft beschrieben.

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
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Statische Member nicht in generischen Typen deklarieren.|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Generische Listen nicht verfügbar machen.|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Generische Ereignishandlerinstanzen verwenden.|
|[CA1004](../code-quality/ca1004.md)|Generische Methoden müssen den Typparameter angeben.|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Übermäßige Anzahl von Parametern in generischen Typen vermeiden.|
|[CA1006](../code-quality/ca1006.md)|Generische Typen in Membersignaturen nicht schachteln.|
|[CA1007](../code-quality/ca1007.md)|Nach Möglichkeit Generics verwenden.|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Enumerationen müssen einen Wert von 0 (null) aufweisen.|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Sammlungen müssen eine generische Schnittstelle implementieren.|
|[CA1011](../code-quality/ca1011.md)|Basistypen als Parameter übergeben.|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Abstrakte Typen dürfen keine Konstruktoren aufweisen.|
|[CA1013](../code-quality/ca1013.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Assemblys mit CLSCompliantAttribute markieren.|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Assemblys mit ComVisibleAttribute markieren.|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Attribute mit AttributeUsageAttribute markieren.|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Accessoren für Attributargumente definieren.|
|[CA1023](../code-quality/ca1023.md)|Indexer sollten nicht mehrdimensional sein.|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Nach Möglichkeit Eigenschaften verwenden.|
|[CA1025](../code-quality/ca1025.md)|Sich wiederholende Argumente durch ein Parameterarray ersetzen.|
|[CA1026](../code-quality/ca1026.md)|Standardparameter sollten nicht verwendet werden.|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Enumerationen mit FlagsAttribute markieren.|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Der Enumerationsspeicher sollte Int32 sein.|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Nach Möglichkeit Ereignisse verwenden.|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Allgemeine Ausnahmetypen nicht auffangen.|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Standardausnahmekonstruktoren implementieren.|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Geschachtelte Typen sollten nicht sichtbar sein.|
|[CA1035](../code-quality/ca1035.md)|ICollection-Implementierungen weisen Member mit starker Typisierung auf.|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Methoden bei vergleichbaren Typen überschreiben.|
|[CA1038](../code-quality/ca1038.md)|Enumeratoren sollten eine starke Typisierung aufweisen.|
|[CA1039](../code-quality/ca1039.md)|Listen weisen eine starke Typisierung auf.|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|ObsoleteAttribute-Meldung bereitstellen.|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Eigenschaften sollten nicht lesegeschützt sein.|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Gleichheitsoperator für Referenztypen nicht überladen.|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Geschützte Member in versiegelten Typen nicht deklarieren.|
|[CA1048](../code-quality/ca1048.md)|Virtuelle Member in versiegelten Typen nicht deklarieren.|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Typen in Namespaces deklarieren.|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Sichtbare Instanzfelder nicht deklarieren.|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Statische Haltertypen sollten versiegelt sein.|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Statische Haltertypen sollten keine Konstruktoren aufweisen.|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI-Parameter dürfen keine Zeichenfolgen sein.|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI-Rückgabewerte dürfen keine Zeichenfolgen sein.|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|
|[CA1057](../code-quality/ca1057.md)|URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Typen sollten bestimmte Basistypen nicht erweitern.|
|[CA1059](../code-quality/ca1059.md)|Member sollten bestimmte konkrete Typen nicht verfügbar machen.|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Ausnahmen sollten öffentlich sein.|
|[CA1500](../code-quality/ca1500.md)|Variablennamen sollten nicht mit Feldnamen übereinstimmen.|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Übermäßige Komplexität vermeiden.|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Nicht verwendete Parameter überprüfen.|
|[CA1804](../code-quality/ca1804.md)|Nicht verwendete lokale Variablen entfernen.|
|[CA1809](../code-quality/ca1809.md)|Übermäßige lokale Variablen vermeiden.|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Statische Felder von Referenztypen inline initialisieren.|
|[CA1811](../code-quality/ca1811.md)|Nicht aufgerufenen privaten Code vermeiden.|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Nicht instanziierte interne Klassen vermeiden.|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Nicht versiegelte Attribute vermeiden.|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Jagged Arrays mehrdimensionalen Arrays vorziehen.|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Equals und Gleichheitsoperator für Werttypen überschreiben.|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Member als statisch markieren.|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Nicht verwendete private Felder vermeiden.|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Keine reservierten Ausnahmetypen auslösen.|
|[CA2205](../code-quality/ca2205.md)|Verwaltete Entsprechungen der Win32 API verwenden.|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Argumentausnahmen korrekt instanziieren.|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Nicht konstante Felder sollten nicht sichtbar sein.|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Enumerationen nicht mit FlagsAttribute markieren.|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Keine Ausnahmen in Ausnahmeklauseln auslösen.|
|[CA2221](../code-quality/ca2221.md)|Finalizer sollten geschützt sein.|
|[CA2222](../code-quality/ca2222.md)|Sichtbarkeit für geerbte Member nicht verringern.|
|[CA2223](../code-quality/ca2223.md)|Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224.md)|Equals beim Überladen von Gleichheitsoperatoren überschreiben.|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Operatorüberladungen weisen benannte Alternativen auf.|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Sammlungseigenschaften sollten schreibgeschützt sein.|
|[CA2230](../code-quality/ca2230.md)|params für Variablenargumente verwenden.|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.|
|[CA2239](../code-quality/ca2239.md)|Deserialisierungsmethoden für optionale Felder angeben.|
|[CA1020](../code-quality/ca1020.md)|Namespaces mit wenigen Typen vermeiden.|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|out-Parameter vermeiden.|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|Leere Schnittstellen vermeiden.|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|Typen nicht als Verweis übergeben.|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|Argumente von öffentlichen Methoden validieren.|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|Übermäßige Vererbung vermeiden.|
|[CA1504](../code-quality/ca1504.md)|Irreführende Feldnamen überprüfen.|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|Nicht wartbaren Code vermeiden.|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|Übermäßige Klassenkopplungen vermeiden.|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|Enumerationswerte nicht mit "Reserviert" benennen.|
|[CA1701](../code-quality/ca1701.md)|Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden.|
|[CA1702](../code-quality/ca1702.md)|Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.|
|[CA1703](../code-quality/ca1703.md)|Ressourcenzeichenfolgen sollten korrekt geschrieben werden.|
|[CA1704](../code-quality/ca1704.md)|Bezeichner sollten korrekt geschrieben werden.|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|Bezeichner sollten keine Unterstriche enthalten.|
|[CA1709](../code-quality/ca1709.md)|Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|Bezeichner sollten ein richtiges Suffix aufweisen.|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|Bezeichner sollten kein falsches Suffix aufweisen.|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|Keine Typnamen als Präfixe für Enumerationswerte verwenden.|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|Ereignisse sollten kein Before- oder After-Präfix aufweisen.|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|Flags-Enumerationen sollten Pluralnamen aufweisen.|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|Bezeichner sollten ein korrektes Präfix aufweisen.|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.|
|[CA1719](../code-quality/ca1719.md)|Parameternamen sollten nicht mit Membernamen übereinstimmen.|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|Bezeichner dürfen keine Typnamen enthalten.|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.|
|[CA1722](../code-quality/ca1722.md)|Bezeichner sollten kein falsches Präfix aufweisen.|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|Typnamen sollten nicht mit Namespaces übereinstimmen.|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|Parameternamen sollten mit der Basisdeklaration übereinstimmen.|
|[CA1726](../code-quality/ca1726.md)|Bevorzugte Begriffe verwenden.|
|[CA2204](../code-quality/ca2204.md)|Literale sollten eine korrekte Rechtschreibung aufweisen.|
