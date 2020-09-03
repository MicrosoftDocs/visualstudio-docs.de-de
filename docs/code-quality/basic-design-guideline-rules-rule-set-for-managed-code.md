---
title: Regelsatz für die einfachen Entwurfsrichtlinienregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cf30e3294c1a96e64efd47ffd14f03328ebec62c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75573183"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Regelsatz für die einfachen Entwurfsrichtlinienregeln für verwalteten Code

Sie können den Regelsatz Regeln für Microsoft Basic-Entwurfs Richtlinien verwenden, um sich auf das Verständnis und die Verwendung Ihres Codes zu konzentrieren. Sie sollten diesen Regelsatz einschließen, wenn Ihr Projekt Bibliotheks Code enthält, oder wenn Sie bewährte Methoden für Code erzwingen möchten, der leicht zu verwalten ist.

Die grundlegenden Regeln für Entwurfs Richtlinien enthalten alle Regeln im Regelsatz [verwaltete Empfohlene Regeln](managed-recommended-rules-rule-set-for-managed-code.md) .

In der folgenden Tabelle werden alle Regeln des Regelsatzes Microsoft Basic-Entwurfs Richtlinien Regeln beschrieben.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1000](../code-quality/ca1000.md)|Statische Member nicht in generischen Typen deklarieren.|
|[CA1001](../code-quality/ca1001.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1002](../code-quality/ca1002.md)|Generische Listen nicht verfügbar machen.|
|[CA1003](../code-quality/ca1003.md)|Generische Ereignishandlerinstanzen verwenden.|
|[CA1004](../code-quality/ca1004.md)|Generische Methoden müssen den Typparameter angeben.|
|[CA1005](../code-quality/ca1005.md)|Übermäßige Anzahl von Parametern in generischen Typen vermeiden.|
|[CA1006](../code-quality/ca1006.md)|Generische Typen in Membersignaturen nicht schachteln.|
|[CA1007](../code-quality/ca1007.md)|Nach Möglichkeit Generics verwenden.|
|[CA1008](../code-quality/ca1008.md)|Enumerationen müssen einen Wert von 0 (null) aufweisen.|
|[CA1009](../code-quality/ca1009.md)|Ereignishandler korrekt deklarieren.|
|[CA1010](../code-quality/ca1010.md)|Sammlungen müssen eine generische Schnittstelle implementieren.|
|[CA1011](../code-quality/ca1011.md)|Basistypen als Parameter übergeben.|
|[CA1012](../code-quality/ca1012.md)|Abstrakte Typen dürfen keine Konstruktoren aufweisen.|
|[CA1013](../code-quality/ca1013.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.|
|[CA1014](../code-quality/ca1014.md)|Assemblys mit CLSCompliantAttribute markieren.|
|[CA1016](../code-quality/ca1016.md)|Assemblys mit AssemblyVersionAttribute markieren.|
|[CA1017](../code-quality/ca1017.md)|Assemblys mit ComVisibleAttribute markieren.|
|[CA1018](../code-quality/ca1018.md)|Attribute mit AttributeUsageAttribute markieren.|
|[CA1019](../code-quality/ca1019.md)|Accessoren für Attributargumente definieren.|
|[CA1023](../code-quality/ca1023.md)|Indexer sollten nicht mehrdimensional sein.|
|[CA1024](../code-quality/ca1024.md)|Nach Möglichkeit Eigenschaften verwenden.|
|[CA1025](../code-quality/ca1025.md)|Sich wiederholende Argumente durch ein Parameterarray ersetzen.|
|[CA1026](../code-quality/ca1026.md)|Standardparameter sollten nicht verwendet werden.|
|[CA1027](../code-quality/ca1027.md)|Enumerationen mit FlagsAttribute markieren.|
|[CA1028](../code-quality/ca1028.md)|Der Enumerationsspeicher sollte Int32 sein.|
|[CA1030](../code-quality/ca1030.md)|Nach Möglichkeit Ereignisse verwenden.|
|[CA1031](../code-quality/ca1031.md)|Allgemeine Ausnahmetypen nicht auffangen.|
|[CA1032](../code-quality/ca1032.md)|Standardausnahmekonstruktoren implementieren.|
|[CA1033](../code-quality/ca1033.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1034](../code-quality/ca1034.md)|Geschachtelte Typen sollten nicht sichtbar sein.|
|[CA1035](../code-quality/ca1035.md)|ICollection-Implementierungen weisen Member mit starker Typisierung auf.|
|[CA1036](../code-quality/ca1036.md)|Methoden bei vergleichbaren Typen überschreiben.|
|[CA1038](../code-quality/ca1038.md)|Enumeratoren sollten eine starke Typisierung aufweisen.|
|[CA1039](../code-quality/ca1039.md)|Listen weisen eine starke Typisierung auf.|
|[CA1041](../code-quality/ca1041.md)|ObsoleteAttribute-Meldung bereitstellen.|
|[CA1043](../code-quality/ca1043.md)|Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.|
|[CA1044](../code-quality/ca1044.md)|Eigenschaften sollten nicht lesegeschützt sein.|
|[CA1046](../code-quality/ca1046.md)|Gleichheitsoperator für Referenztypen nicht überladen.|
|[CA1047](../code-quality/ca1047.md)|Geschützte Member in versiegelten Typen nicht deklarieren.|
|[CA1048](../code-quality/ca1048.md)|Virtuelle Member in versiegelten Typen nicht deklarieren.|
|[CA1049](../code-quality/ca1049.md)|Typen, die native Ressourcen besitzen, müssen gelöscht werden können.|
|[CA1050](../code-quality/ca1050.md)|Typen in Namespaces deklarieren.|
|[CA1051](../code-quality/ca1051.md)|Sichtbare Instanzfelder nicht deklarieren.|
|[CA1052](../code-quality/ca1052.md)|Statische Haltertypen sollten versiegelt sein.|
|[CA1053](../code-quality/ca1053.md)|Statische Haltertypen sollten keine Konstruktoren aufweisen.|
|[CA1054](../code-quality/ca1054.md)|URI-Parameter dürfen keine Zeichenfolgen sein.|
|[CA1055](../code-quality/ca1055.md)|URI-Rückgabewerte dürfen keine Zeichenfolgen sein.|
|[CA1056](../code-quality/ca1056.md)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|
|[CA1057](../code-quality/ca1057.md)|URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.|
|[CA1058](../code-quality/ca1058.md)|Typen sollten bestimmte Basistypen nicht erweitern.|
|[CA1059](../code-quality/ca1059.md)|Member sollten bestimmte konkrete Typen nicht verfügbar machen.|
|[CA1060](../code-quality/ca1060.md)|P/Invokes in NativeMethods-Klasse verschieben.|
|[CA1061](../code-quality/ca1061.md)|Basisklassenmethoden nicht ausblenden.|
|[CA1063](../code-quality/ca1063.md)|IDisposable korrekt implementieren.|
|[CA1064](../code-quality/ca1064.md)|Ausnahmen sollten öffentlich sein.|
|[CA1065](../code-quality/ca1065.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen.|
|[CA1301](../code-quality/ca1301.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1400](../code-quality/ca1400.md)|Für P/Invoke müssen Einstiegspunkte vorhanden sein.|
|[CA1401](../code-quality/ca1401.md)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein.|
|[CA1404](../code-quality/ca1404.md)|GetLastError unmittelbar nach P/Invoke aufrufen.|
|[CA1405](../code-quality/ca1405.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein.|
|[CA1410](../code-quality/ca1410.md)|Die COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415.md)|P/Invokes korrekt deklarieren.|
|[CA1500](../code-quality/ca1500.md)|Variablennamen sollten nicht mit Feldnamen übereinstimmen.|
|[CA1502](../code-quality/ca1502.md)|Übermäßige Komplexität vermeiden.|
|[CA1708](../code-quality/ca1708.md)|Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.|
|[CA1716](../code-quality/ca1716.md)|Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.|
|[CA1801](../code-quality/ca1801.md)|Nicht verwendete Parameter überprüfen.|
|[CA1804](../code-quality/ca1804.md)|Nicht verwendete lokale Variablen entfernen.|
|[CA1809](../code-quality/ca1809.md)|Übermäßige lokale Variablen vermeiden.|
|[CA1810](../code-quality/ca1810.md)|Statische Felder von Referenztypen inline initialisieren.|
|[CA1811](../code-quality/ca1811.md)|Nicht aufgerufenen privaten Code vermeiden.|
|[CA1812](../code-quality/ca1812.md)|Nicht instanziierte interne Klassen vermeiden.|
|[CA1813](../code-quality/ca1813.md)|Nicht versiegelte Attribute vermeiden.|
|[CA1814](../code-quality/ca1814.md)|Jagged Arrays mehrdimensionalen Arrays vorziehen.|
|[CA1815](../code-quality/ca1815.md)|Equals und Gleichheitsoperator für Werttypen überschreiben.|
|[CA1819](../code-quality/ca1819.md)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](../code-quality/ca1820.md)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.|
|[CA1821](../code-quality/ca1821.md)|Leere Finalizer entfernen.|
|[CA1822](../code-quality/ca1822.md)|Member als statisch markieren.|
|[CA1823](../code-quality/ca1823.md)|Nicht verwendete private Felder vermeiden.|
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
|[CA2201](../code-quality/ca2201.md)|Keine reservierten Ausnahmetypen auslösen.|
|[CA2202](../code-quality/ca2202.md)|Objekte nicht mehrmals verwerfen.|
|[CA2205](../code-quality/ca2205.md)|Verwaltete Entsprechungen der Win32 API verwenden.|
|[CA2207](../code-quality/ca2207.md)|Statische Felder für Werttyp inline initialisieren.|
|[CA2208](../code-quality/ca2208.md)|Argumentausnahmen korrekt instanziieren.|
|[CA2211](../code-quality/ca2211.md)|Nicht konstante Felder sollten nicht sichtbar sein.|
|[CA2212](../code-quality/ca2212.md)|ServicedComponents nicht mit WebMethod markieren.|
|[CA2213](../code-quality/ca2213.md)|Verwerfbare Felder verwerfen.|
|[CA2214](../code-quality/ca2214.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen.|
|[CA2216](../code-quality/ca2216.md)|Verwerfbare Typen sollten einen Finalizer deklarieren.|
|[CA2217](../code-quality/ca2217.md)|Enumerationen nicht mit FlagsAttribute markieren.|
|[CA2219](../code-quality/ca2219.md)|Keine Ausnahmen in Ausnahmeklauseln auslösen.|
|[CA2220](../code-quality/ca2220.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2221](../code-quality/ca2221.md)|Finalizer sollten geschützt sein.|
|[CA2222](../code-quality/ca2222.md)|Sichtbarkeit für geerbte Member nicht verringern.|
|[CA2223](../code-quality/ca2223.md)|Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224.md)|Equals beim Überladen von Gleichheitsoperatoren überschreiben.|
|[CA2225](../code-quality/ca2225.md)|Operatorüberladungen weisen benannte Alternativen auf.|
|[CA2226](../code-quality/ca2226.md)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](../code-quality/ca2227.md)|Sammlungseigenschaften sollten schreibgeschützt sein.|
|[CA2229](../code-quality/ca2229.md)|Serialisierungskonstruktoren implementieren.|
|[CA2230](../code-quality/ca2230.md)|params für Variablenargumente verwenden.|
|[CA2231](../code-quality/ca2231.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms-Einstiegspunkte mit STAThread markieren.|
|[CA2234](../code-quality/ca2234.md)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.|
|[CA2235](../code-quality/ca2235.md)|Alle nicht serialisierbaren Felder markieren.|
|[CA2236](../code-quality/ca2236.md)|Basisklassenmethoden auf ISerializable-Typen aufrufen.|
|[CA2237](../code-quality/ca2237.md)|ISerializable-Typen mit SerializableAttribute markieren.|
|[CA2238](../code-quality/ca2238.md)|Serialisierungsmethoden korrekt implementieren.|
|[CA2239](../code-quality/ca2239.md)|Deserialisierungsmethoden für optionale Felder angeben.|
|[CA2240](../code-quality/ca2240.md)|ISerializable ordnungsgemäß implementieren.|
|[CA2241](../code-quality/ca2241.md)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|
|[CA2242](../code-quality/ca2242.md)|Ordnungsgemäß auf NaN testen.|
