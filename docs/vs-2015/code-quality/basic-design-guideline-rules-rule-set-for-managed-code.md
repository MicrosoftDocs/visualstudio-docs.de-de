---
title: Regelsatz für die grundlegenden Regeln für Entwurfs Richtlinien für verwalteten Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cefe4864db8455ba6712dc728b342f49b6c7d5d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655122"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Regelsatz für die einfachen Entwurfsrichtlinienregeln für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Regelsatz Regeln für Microsoft Basic-Entwurfs Richtlinien verwenden, um sich auf das Verständnis und die Verwendung Ihres Codes zu konzentrieren. Sie sollten diesen Regelsatz einschließen, wenn Ihr Projekt Bibliotheks Code enthält, oder wenn Sie bewährte Methoden für Code erzwingen möchten, der leicht zu verwalten ist.

 Die grundlegenden Regeln für Entwurfs Richtlinien enthalten alle Regeln im Regelsatz für die Mindestanzahl von Microsoft-Regeln. Eine Liste der minimal Regeln finden Sie unter [Regelsatz für verwaltete Empfohlene Regeln für verwalteten Code](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).

 In der folgenden Tabelle werden alle Regeln des Regelsatzes Microsoft Basic-Entwurfs Richtlinien Regeln beschrieben.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Ereignishandler korrekt deklarieren.|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Assemblys mit AssemblyVersionAttribute markieren.|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können.|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typen, die native Ressourcen besitzen, müssen gelöscht werden können.|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invokes in NativeMethods-Klasse verschieben.|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Basisklassenmethoden nicht ausblenden.|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable korrekt implementieren.|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen.|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Für P/Invoke müssen Einstiegspunkte vorhanden sein.|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes dürfen nicht sichtbar sein.|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein.|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|GetLastError unmittelbar nach P/Invoke aufrufen.|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein.|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Die COM-Registrierungsmethoden müssen übereinstimmen.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes korrekt deklarieren.|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen.|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Werttypfelder sollten portabel sein.|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarationen von P/Invoke müssen portabel sein.|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Auf Objekten mit schwacher Identität nicht sperren.|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL-Abfragen auf Sicherheitsrisiken überprüfen.|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen.|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein.|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-Methoden sollten nur APTCA-Methoden aufrufen.|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-Typen sollten nur APTCA-Basistypen erweitern.|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen.|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten mit der Basis identisch sein.|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Anfällige finally-Klauseln mit äußerem try-Block umschließen.|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern Vererbungsanforderungen.|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden dürfen nur überprüfbare IL enthalten.|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen.|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen.|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden dürfen keine LinkDemand-Anforderungen erfüllen.|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden dürfen keine Sicherheitsassertionen verwenden.|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen keine Aufrufe in nativen Code durchführen.|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Erneut ausführen, um Stapeldetails beizubehalten.|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Objekte nicht mehrmals verwerfen.|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Statische Felder für Werttyp inline initialisieren.|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|ServicedComponents nicht mit WebMethod markieren.|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen.|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Verwerfbare Typen sollten einen Finalizer deklarieren.|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizer sollten Basisklassen-Finalizer aufrufen.|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serialisierungskonstruktoren implementieren.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows Forms-Einstiegspunkte mit STAThread markieren.|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Alle nicht serialisierbaren Felder markieren.|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Basisklassenmethoden auf ISerializable-Typen aufrufen.|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable-Typen mit SerializableAttribute markieren.|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serialisierungsmethoden korrekt implementieren.|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable ordnungsgemäß implementieren.|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Ordnungsgemäß auf NaN testen.|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Statische Member nicht in generischen Typen deklarieren.|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Generische Listen nicht verfügbar machen.|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Generische Ereignishandlerinstanzen verwenden.|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Generische Methoden müssen den Typparameter angeben.|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Übermäßige Anzahl von Parametern in generischen Typen vermeiden.|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Generische Typen in Membersignaturen nicht schachteln.|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Nach Möglichkeit Generics verwenden.|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Enumerationen müssen einen Wert von 0 (null) aufweisen.|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Sammlungen müssen eine generische Schnittstelle implementieren.|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Basistypen als Parameter übergeben.|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Abstrakte Typen dürfen keine Konstruktoren aufweisen.|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Assemblys mit CLSCompliantAttribute markieren.|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Assemblys mit ComVisibleAttribute markieren.|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Attribute mit AttributeUsageAttribute markieren.|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Accessoren für Attributargumente definieren.|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indexer sollten nicht mehrdimensional sein.|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Nach Möglichkeit Eigenschaften verwenden.|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Sich wiederholende Argumente durch ein Parameterarray ersetzen.|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Standardparameter sollten nicht verwendet werden.|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Enumerationen mit FlagsAttribute markieren.|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Der Enumerationsspeicher sollte Int32 sein.|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Nach Möglichkeit Ereignisse verwenden.|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Allgemeine Ausnahmetypen nicht auffangen.|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standardausnahmekonstruktoren implementieren.|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Geschachtelte Typen sollten nicht sichtbar sein.|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection-Implementierungen weisen Member mit starker Typisierung auf.|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Methoden bei vergleichbaren Typen überschreiben.|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Enumeratoren sollten eine starke Typisierung aufweisen.|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listen weisen eine starke Typisierung auf.|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute-Meldung bereitstellen.|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Eigenschaften sollten nicht lesegeschützt sein.|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Gleichheitsoperator für Referenztypen nicht überladen.|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Geschützte Member in versiegelten Typen nicht deklarieren.|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Virtuelle Member in versiegelten Typen nicht deklarieren.|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Typen in Namespaces deklarieren.|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Sichtbare Instanzfelder nicht deklarieren.|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Statische Haltertypen sollten versiegelt sein.|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Statische Haltertypen sollten keine Konstruktoren aufweisen.|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI-Parameter dürfen keine Zeichenfolgen sein.|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI-Rückgabewerte dürfen keine Zeichenfolgen sein.|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI-Eigenschaften dürfen keine Zeichenfolgen sein.|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Typen sollten bestimmte Basistypen nicht erweitern.|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Member sollten bestimmte konkrete Typen nicht verfügbar machen.|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Ausnahmen sollten öffentlich sein.|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Variablennamen sollten nicht mit Feldnamen übereinstimmen.|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Übermäßige Komplexität vermeiden.|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Nicht verwendete Parameter überprüfen.|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Nicht verwendete lokale Variablen entfernen.|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Übermäßige lokale Variablen vermeiden.|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Statische Felder von Referenztypen inline initialisieren.|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Nicht aufgerufenen privaten Code vermeiden.|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Nicht instanziierte interne Klassen vermeiden.|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Nicht versiegelte Attribute vermeiden.|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Jagged Arrays mehrdimensionalen Arrays vorziehen.|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Equals und Gleichheitsoperator für Werttypen überschreiben.|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Eigenschaften sollten keine Arrays zurückgeben.|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Member als statisch markieren.|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Nicht verwendete private Felder vermeiden.|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Keine reservierten Ausnahmetypen auslösen.|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Verwaltete Entsprechungen der Win32 API verwenden.|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Argumentausnahmen korrekt instanziieren.|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Nicht konstante Felder sollten nicht sichtbar sein.|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Enumerationen nicht mit FlagsAttribute markieren.|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Keine Ausnahmen in Ausnahmeklauseln auslösen.|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizer sollten geschützt sein.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Sichtbarkeit für geerbte Member nicht verringern.|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden.|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Equals beim Überladen von Gleichheitsoperatoren überschreiben.|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Operatorüberladungen weisen benannte Alternativen auf.|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatoren sollten symmetrische Überladungen aufweisen.|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Sammlungseigenschaften sollten schreibgeschützt sein.|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|params für Variablenargumente verwenden.|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Deserialisierungsmethoden für optionale Felder angeben.|
