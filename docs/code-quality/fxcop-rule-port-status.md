---
title: Port Status der FxCop-Regel
ms.date: 05/21/2019
description: Erfahren Sie mehr über die statischen Code Analyse Regeln, die in .net-Analysen in Visual Studio portiert wurden. Anzeigen von portierten Regeln und Ressourcen beim Portieren von Updates.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: de23f3529cfcd321b0a7c3f9844ac69d96fed9c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860320"
---
# <a name="fxcop-rule-port-status"></a>Port Status der FxCop-Regel

Wenn Sie zuvor eine statische Code Analyse in Visual Studio verwendet haben, Fragen Sie sich vielleicht, welche dieser Regeln in der aktuellen Implementierung als [.net-Analysen](install-net-analyzers.md)verfügbar sind. Auf dieser Seite werden die Regeln aufgelistet, die portiert wurden. Weitere Informationen finden Sie unter [nicht portierte Regeln](fxcop-unported-rules.md) für diejenigen, die nicht portiert wurden, und ob Pläne zum Portieren vorhanden sind.

## <a name="ported-rules"></a>Portierte Regeln

Die [Seite für die automatisch generierte Dokumentation](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) im Repository "Roslyn-Analyzers" enthält die aktuellste Liste der Regeln, die zu Roslyn-Analyzern portiert wurden. Diese Seite verfügt auch über zusätzliche Informationen, z. b. ob die Regel standardmäßig aktiviert ist und ob Sie über eine zugeordnete *Code Korrektur* verfügt. ([Code Fehlerbehebungen](../ide/quick-actions.md) sind One-Click-Korrekturen, die im Glühbirnen-Symbolmenü in Visual Studio verfügbar sind.)

Ab dem Datum auf dieser Seite enthält die Liste der FxCop-Regeln, die zu .net- [Analysen](install-net-analyzers.md) portiert wurden, Folgendes:

Regel-ID | Titel
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Statische Member nicht in generischen Typen deklarieren.
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Typen, die löschbare Felder besitzen, müssen gelöscht werden können.
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Generische Listen nicht verfügbar machen.
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Generische Ereignishandlerinstanzen verwenden.
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Übermäßige Anzahl von Parametern in generischen Typen vermeiden.
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Enumerationen müssen einen Wert von 0 (null) aufweisen.
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Sammlungen müssen eine generische Schnittstelle implementieren.
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Abstrakte Typen dürfen keine Konstruktoren aufweisen.
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Assemblys mit clscompliance markieren
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Assemblys mit Assembly-Version markieren
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Assemblys mit ComVisible markieren
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Attribute mit AttributeUsageAttribute markieren.
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Accessoren für Attributargumente definieren.
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | out-Parameter vermeiden.
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Nach Möglichkeit Eigenschaften verwenden.
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Enumerationen mit FlagsAttribute markieren.
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Der Aufzählungs Speicher muss Int32 lauten.
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Nach Möglichkeit Ereignisse verwenden.
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Allgemeine Ausnahmetypen nicht auffangen.
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Standardausnahmekonstruktoren implementieren.
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Geschachtelte Typen sollten nicht sichtbar sein.
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Methoden bei vergleichbaren Typen überschreiben.
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Leere Schnittstellen vermeiden.
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | ObsoleteAttribute-Meldung bereitstellen.
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Ganzzahliges Argument oder Zeichen folgen Argument für Indexer verwenden
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Eigenschaften sollten nicht lesegeschützt sein.
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Typen nicht als Verweis übergeben.
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Gleichheitsoperator für Referenztypen nicht überladen.
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Geschützte Member in versiegelten Typen nicht deklarieren.
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Typen in Namespaces deklarieren.
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Sichtbare Instanzfelder nicht deklarieren.
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Statische Halter Typen sollten statisch oder notgeerbt sein.
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Statische Halter Typen sollten keine Konstruktoren aufweisen (CA1053 ist Teil von [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) für .net-Analyzers).
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | URI-Parameter dürfen keine Zeichen folgen sein.
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | URI-Rückgabewerte dürfen keine Zeichen folgen sein.
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Uri-Eigenschaften dürfen keine Zeichen folgen sein.
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Typen sollten bestimmte Basistypen nicht erweitern.
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | PInvokes in systemeigene Methoden Klasse verschieben
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Basisklassenmethoden nicht ausblenden.
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Argumente von öffentlichen Methoden validieren.
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Ordnungsgemäße Implementierung von iverwerf
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Ausnahmen sollten öffentlich sein.
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Keine Ausnahmen an unerwarteten Speicherorten auslösen.
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | Der Typ {0} muss "IEquatable" implementieren, \<T> da er "ist mit"
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Überschreiben Sie Object. Gleichheits (Objekt), wenn Sie IEquatable implementieren.\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Literale nicht als lokalisierte Parameter übergeben.
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | CultureInfo angeben.
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | IFormatProvider angeben.
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | StringComparison zur Übersichtlichkeit angeben
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Zeichenfolgen in Großbuchstaben normalisieren.
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Ordinalzeichenfolgen-Vergleich verwenden
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | P/Invokes dürfen nicht sichtbar sein.
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Übermäßige Vererbung vermeiden.
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Übermäßige Komplexität vermeiden.
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Nicht wartbaren Code vermeiden.
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Übermäßige Klassenkopplungen vermeiden.
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Enumerationswerte nicht mit "Reserviert" benennen.
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Bezeichner sollten keine Unterstriche enthalten.
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Bezeichner sollten ein richtiges Suffix aufweisen.
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Bezeichner sollten kein falsches Suffix aufweisen.
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Keine Typnamen als Präfixe für Enumerationswerte verwenden.
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Ereignisse sollten kein Before- oder After-Präfix aufweisen.
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Flags-Enumerationen sollten Pluralnamen aufweisen.
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Bezeichner sollten ein korrektes Präfix aufweisen.
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | Bezeichner enthält Typnamen
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Typnamen sollten nicht mit Namespaces identisch sein.
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Parameternamen sollten mit der Basisdeklaration übereinstimmen.
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Nicht verwendete Parameter überprüfen.
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Verwenden Sie nach Bedarf Literale.
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Nicht unnötig initialisieren
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Methodenergebnisse nicht ignorieren.
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Statische Felder von Referenztypen inline initialisieren.
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Nicht instanziierte interne Klassen vermeiden.
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Nicht versiegelte Attribute vermeiden.
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Jagged Arrays mehrdimensionalen Arrays vorziehen.
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Equals und Gleichheitsoperator für Werttypen überschreiben.
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Verwerfen von Methoden sollten SuppressFinalize aufgerufen werden.
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Eigenschaften sollten keine Arrays zurückgeben.
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Leere Finalizer entfernen
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Member als statisch markieren.
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Nicht verwendete private Felder vermeiden.
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Assemblys mit NeutralResourcesLanguageAttribute markieren.
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Vermeiden Sie Array Belegungen der Länge 0 (null).
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Objekte verwerfen, bevor Bereich verloren geht.
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Auf Objekten mit schwacher Identität nicht sperren.
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | SQL-Abfragen auf Sicherheitsrisiken überprüfen.
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Sichtbare Ereignishandler überprüfen.
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen.
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Beschädigte Zustands Ausnahmen nicht erfassen
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Erneut auslösen, um Stapel Details beizubehalten.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Keine reservierten Ausnahmetypen auslösen.
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Statische Felder für Werttyp inline initialisieren.
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Argumentausnahmen korrekt instanziieren.
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Nicht konstante Felder sollten nicht sichtbar sein.
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Verwerfbare Felder verwerfen.
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Überschreibbare Methoden in Konstruktoren nicht aufrufen.
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Verwerfbare Typen sollten einen Finalizer deklarieren.
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Enumerationen nicht mit FlagsAttribute markieren.
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Keine Ausnahmen in den Schluss Klauseln
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Operatorüberladungen weisen benannte Alternativen auf.
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Operatoren sollten symmetrische Überladungen aufweisen.
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Sammlungseigenschaften sollten schreibgeschützt sein.
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Serialisierungskonstruktoren implementieren.
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Gleichheits Operator beim Überschreiben des Werttyps
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Übergeben von System-Uri-Objekten anstelle von Zeichen folgen
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Alle nicht serialisierbaren Felder markieren.
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | ISerializable-Typen als serialisierbar markieren
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Geben Sie die korrekte Anzahl für Formatierungsmethoden an.
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Ordnungsgemäß auf NaN testen.
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Nicht den unsicheren BinaryFormatter zur Deserialisierung verwenden
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | BinaryFormatter.Deserialize nicht ohne Festlegung von BinaryFormatter.Binder aufrufen
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Festlegung von BinaryFormatter.Binder vor dem Aufruf von BinaryFormatter.Deserialize sicherstellen
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Unsicheren Deserialisierer nicht verwenden: LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Unsicheren Deserialisierer nicht verwenden: NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Nicht deserialisieren, ohne zuerst NetDataContractSerializer.Binder festzulegen
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Vor dem Deserialisieren sicherstellen, dass NetDataContractSerializer.Binder festgelegt ist
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Unsicheren Deserialisierer nicht verwenden: ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Nicht mit JavaScriptSerializer und SimpleTypeResolver deserialisieren
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Vor dem Deserialisieren sicherstellen, dass JavaScriptSerializer nicht mit SimpleTypeResolver initialisiert ist
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Review code for SQL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von SQL-Befehlen)
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Review code for XSS vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch XSS)
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Review code for file path injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen über einen Dateipfad)
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Review code for information disclosure vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken bei der Veröffentlichung von Informationen)
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Review code for LDAP injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von LDAP-Befehlen)
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Review code for process command injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von Prozessbefehlen)
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Review code for open redirect vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch offene Umleitungen)
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Review code for XPath injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XPath-Befehlen)
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Review code for XML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XML-Befehlen)
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Review code for XAML injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von XAML-Befehlen)
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Review code for DLL injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von DLL)
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Review code for regex injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusungen von RegEx)
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Schema nicht nach URL hinzufügen
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Unsichere DTD-Verarbeitung in XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Unsichere XSLT-Skript Verarbeitung.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Unsichere Verarbeitung in API-Design, XmlDocument und XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Markieren von Verb Handlern mit Token zum Überprüfen der Antifälschung
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Keine schwachen Kryptografiealgorithmen verwenden.
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Verwenden Sie keine unterbrochenen Kryptografiealgorithmen.
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Verwenden Sie keine unsicheren Verschlüsselungsmodi.
CA5359 | Zertifikat Überprüfung nicht deaktivieren
CA5360 | Keine gefährlichen Methoden bei der Deserialisierung aufzurufen
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Die SChannel-Verwendung der starken Kryptografie nicht deaktivieren
CA5362 | In der serialisierbaren Klasse nicht auf sich selbst verweisen
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Anforderungs Validierung nicht deaktivieren
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Veraltete Sicherheitsprotokolle nicht verwenden
CA5365 | HTTP-Header Überprüfung nicht deaktivieren
CA5366 | Verwenden von XmlReader für DataSet-Lese-XML
CA5367 | Typen mit Zeiger Feldern nicht serialisieren
CA5368 | Festlegen von "VIEWSTATUS User Key" für von der Seite abgeleitete Klassen
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | XmlReader für die Deserialisierung verwenden
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Verwenden von XmlReader zum Überprüfen des Readers
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Verwenden von XmlReader für Schema Lesevorgänge
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | XmlReader für XPathDocument verwenden
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Verwenden Sie keine veraltete Schlüsselableitungsfunktion.
CA5374 | XslTransform nicht verwenden
CA5375 | Konto Shared Access Signature nicht verwenden
CA5376 | Verwenden von sharedaccessproycol httpsonly
CA5377 | Zugriffs Richtlinie auf Container Ebene verwenden
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Deaktivieren Sie ServicePointManagerSecurityProtocols nicht.
CA5379 | Algorithmus für schwache Schlüssel abderivations Funktion nicht verwenden
CA9999 | Konflikt bei der Analyzer-Version

## <a name="see-also"></a>Weitere Informationen

- [.NET Analyzer-Regeln](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
