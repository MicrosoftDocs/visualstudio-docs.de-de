---
title: SDK-Hilfsprogramme zum Debuggen | Microsoft-Dokumentation
description: Erfahren Sie mehr über Funktionen und Deklarationen, bei denen es sich um globale Hilfsfunktionen zum Implementieren von Debug-engines, Ausdrucks Auswertung und Symbol Anbietern in C++ handelt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32d0dd7dbeee70b8c4eb566a07cf9a44d40d4f49
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606540"
---
# <a name="sdk-helpers-for-debugging"></a>SDK-Hilfsprogramme für das Debuggen
Diese Funktionen und Deklarationen sind globale Hilfsfunktionen zum Implementieren von Debug-engines, Ausdrucks Auswertung und Symbol Anbietern in C++.

> [!NOTE]
> Zurzeit gibt es keine verwalteten Versionen dieser Funktionen und Deklarationen.

## <a name="overview"></a>Übersicht
 Damit Debug-engines, Ausdrucks Auswertung und Symbol Anbieter von Visual Studio verwendet werden können, müssen Sie registriert werden. Dies erfolgt durch Festlegen der Registrierungs Unterschlüssel und-Einträge, die auch als "Festlegen von Metriken" bezeichnet werden. Die folgenden globalen Funktionen sind darauf ausgelegt, den Aktualisierungs Vorgang für diese Metriken zu vereinfachen. Weitere Informationen zum Layout der einzelnen Registrierungs Unterschlüssel, die von diesen Funktionen aktualisiert werden, finden Sie im Abschnitt zu den Registrierungs Standorten.

## <a name="general-metric-functions"></a>Allgemeine metrikfunktionen
 Dies sind allgemeine Funktionen, die von Debug-engines verwendet werden. Spezielle Funktionen für Ausdrucks Auswertung und Symbol Anbieter werden später ausführlich erläutert.

### <a name="getmetric-method"></a>Getmetric-Methode
 Ruft einen Metrikwert aus der Registrierung ab.

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszmachine|in Name eines möglicherweise Remote Computers, dessen Register geschrieben wird ( `NULL` d.h. lokaler Computer).|
|pszType|in Einer der metriktypen.|
|guidsection|in GUID eines bestimmten Moduls, Auswerters, Ausnahme, usw. Dies gibt einen unter Abschnitt unter einem Metriktyp für ein bestimmtes Element an.|
|pszmetric|in Die Metrik, die abgerufen werden soll. Dies entspricht einem bestimmten Wertnamen.|
|pdwvalue|in Der Speicherort des Werts aus der Metrik. Es gibt mehrere Arten von getmetric, die ein DWORD zurückgeben können (wie in diesem Beispiel), ein BSTR, eine GUID oder ein Array von GUIDs.|
|pszaltroot|in Ein alternativer Registrierungs Stamm, der verwendet werden soll. Legen Sie auf fest, `NULL` um den Standardwert zu verwenden.|

### <a name="setmetric-method"></a>Setmetric-Methode
 Legt den angegebenen Metrikwert in der Registrierung fest.

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszType|in Einer der metriktypen.|
|guidsection|in GUID eines bestimmten Moduls, Auswerters, Ausnahme, usw. Dies gibt einen unter Abschnitt unter einem Metriktyp für ein bestimmtes Element an.|
|pszmetric|in Die Metrik, die abgerufen werden soll. Dies entspricht einem bestimmten Wertnamen.|
|dwValue|in Der Speicherort des Werts in der Metrik. Es gibt mehrere Arten von setmetric, mit denen ein DWORD (in diesem Beispiel), ein BSTR, eine GUID oder ein Array von GUIDs gespeichert werden kann.|
|fuserspecific|in TRUE, wenn die Metrik Benutzer spezifisch ist, und wenn Sie anstelle der lokalen Computer Struktur in die Struktur des Benutzers geschrieben werden soll.|
|pszaltroot|in Ein alternativer Registrierungs Stamm, der verwendet werden soll. Legen Sie auf fest, `NULL` um den Standardwert zu verwenden.|

### <a name="removemetric-method"></a>RemoveMetric-Methode
 Entfernt die angegebene Metrik aus der Registrierung.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszType|in Einer der metriktypen.|
|guidsection|in GUID eines bestimmten Moduls, Auswerters, Ausnahme, usw. Dies gibt einen unter Abschnitt unter einem Metriktyp für ein bestimmtes Element an.|
|pszmetric|in Die zu entfernende Metrik. Dies entspricht einem bestimmten Wertnamen.|
|pszaltroot|in Ein alternativer Registrierungs Stamm, der verwendet werden soll. Legen Sie auf fest, `NULL` um den Standardwert zu verwenden.|

### <a name="enummetricsections-method"></a>Enummetricabschnitts-Methode
 Listet die verschiedenen metrikabschnitte in der Registrierung auf.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszmachine|in Name eines möglicherweise Remote Computers, dessen Register geschrieben wird ( `NULL` d.h. lokaler Computer).|
|pszType|in Einer der metriktypen.|
|rgguidabschnitte|[in, out] Vorab zugeordneter Array von GUIDs, das ausgefüllt werden soll.|
|pdwSize|in Die maximale Anzahl von GUIDs, die im Array gespeichert werden können `rgguidSections` .|
|pszaltroot|in Ein alternativer Registrierungs Stamm, der verwendet werden soll. Legen Sie auf fest, `NULL` um den Standardwert zu verwenden.|

## <a name="expression-evaluator-functions"></a>Funktionen der Ausdrucks Auswertung

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|GetEEMetric|Ruft einen Metrikwert aus der Registrierung ab.|
|"-Metrik"|Legt den angegebenen Metrikwert in der Registrierung fest.|
|Removeeemetric|Entfernt die angegebene Metrik aus der Registrierung.|
|GetEEMetricFile|Ruft einen Dateinamen aus der angegebenen Metrik ab und lädt ihn, wobei der Inhalt der Datei als Zeichenfolge zurückgegeben wird.|

## <a name="exception-functions"></a>Ausnahme Funktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|Getexceptionmetric|Ruft einen Metrikwert aus der Registrierung ab.|
|"Abtexceptionmetric"|Legt den angegebenen Metrikwert in der Registrierung fest.|
|Removeexceptionmetric|Entfernt die angegebene Metrik aus der Registrierung.|
|Removeallexceptionmetrics|Entfernt alle ausnahmemetriken aus der Registrierung.|

## <a name="symbol-provider-functions"></a>Funktionen des Symbol Anbieters

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|Getspmetric|Ruft einen Metrikwert aus der Registrierung ab.|
|Setspmetric|Legt den angegebenen Metrikwert in der Registrierung fest.|
|Removespmetric|Entfernt die angegebene Metrik aus der Registrierung.|

## <a name="enumeration-functions"></a>Enumerationsfunktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|Enummetricabschnitte|Listet alle Metriken für einen angegebenen Metriktyp auf.|
|Enumdebugengine|Listet die registrierten Debug-engines auf.|
|EnumEEs|Listet die registrierten Ausdrucks Auswertung auf.|
|Enumexceptionmetrics|Listet alle ausnahmemetriken auf.|

## <a name="metric-definitions"></a>Metrikdefinitionen
 Diese Definitionen können für vordefinierte metriknamen verwendet werden. Die Namen entsprechen verschiedenen Registrierungs Schlüsseln und-Werten und sind alle als breit Zeichen-Zeichen folgen definiert: z `extern LPCWSTR metrictypeEngine` . b..

|Vordefinierte metriktypen|Beschreibung: der Basis Schlüssel für....|
|-----------------------------|---------------------------------------|
|metrictypeengine|Alle Debug-Engine-Metriken.|
|metrictypeportsupplier|Alle portlieferanten-Metriken.|
|metrictypeexception|Alle ausnahmemetriken.|
|metricttypeer-Erweiterung|Alle Erweiterungen der Ausdrucks Auswertung.|

|Debug-Engine-Eigenschaften|BESCHREIBUNG|
|-----------------------------|-----------------|
|metricaddressbp|Legen Sie ihn auf ungleich NULL fest, um die Unterstützung für Adress Haltepunkte anzugeben.|
|metricalwaysloadlocal|Legen Sie auf einen Wert ungleich 0 fest, um die Debug-Engine immer lokal zu laden.|
|metricloadindebuggeesession|nicht verwendet|
|metricloadedbydebug buggende|Legen Sie auf einen Wert ungleich 0 fest, um anzugeben, dass die Debug-Engine immer mit oder durch das Programm geladen wird, das gedebuggt wird|
|metricatcher|Legen Sie auf ungleich NULL fest, um die Unterstützung für die Anlage an vorhandene Programme anzugeben.|
|metriccallstackbp|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für Haltepunkte für die halte|
|metricconditionalbp|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für die Einstellung von bedingten Haltepunkten anzugeben.|
|metricdatabp|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für die Einstellung von Haltepunkten bei Datenänderungen anzugeben.|
|metricdisassembly|Legen Sie auf ungleich NULL fest, um die Unterstützung für die Produktion einer disassemblyauflistung anzugeben.|
|metricdumpwriting|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für das Schreiben von Schreibvorgänge (das Speichern von Speicher auf ein Ausgabegerät)|
|metricenc|Legen Sie auf ungleich NULL fest, um die Unterstützung für bearbeiten und Fortfahren anzugeben. **Hinweis:**  Eine benutzerdefinierte Debug-Engine sollte diese nie festlegen oder sollte immer auf 0 festgelegt werden.|
|metricexceptions|Legen Sie auf ungleich NULL fest, um die Unterstützung für Ausnahmen anzugeben.|
|metricfunctionbp|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für benannte Haltepunkte (Haltepunkte, die beim Aufrufen eines bestimmten Funktionsnamens unterbrochen werden) anzuzeigen.|
|metrichitrattbp|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für die Einstellung von Haltepunkten für "Treffer Punkt" (Haltepunkte, die erst ausgelöst werden, nachdem eine bestimmte Anzahl von Wiederholungen ausgelöst wird) anzugeben.|
|metricjitdebug|Legen Sie auf einen Wert ungleich 0 fest, um die Unterstützung für Just-in-Time-Debugging anzugeben (der Debugger wird gestartet, wenn eine Ausnahme in einem laufenden Prozess auftritt).|
|metricmemory|nicht verwendet|
|metricportsupplier|Legen Sie diese Einstellung auf die CLSID des Port Anbieters fest, sofern eine solche implementiert ist.|
|metricregister|nicht verwendet|
|metricsetnextstatement|Legen Sie auf ungleich NULL fest, um die Unterstützung für das Festlegen der nächsten Anweisung (die die Ausführung von zwischen Anweisungen überspringt) anzugeben.|
|metricsuspendthread|Auf ungleich NULL festlegen, um die Unterstützung für das Anhalten der Thread Ausführung anzugeben.|
|metricwarnischnosymbols|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass der Benutzer benachrichtigt werden soll, wenn keine Symbole vorhanden sind.|
|metricprogramprovider|Legen Sie diese Einstellung auf die CLSID des Programm Anbieters fest.|
|metricalwaysloadprogramproviderlocal|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass der Programmanbieter immer lokal geladen werden soll.|
|metricenginecanwatchprocess|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass die Debug-Engine anstelle des Programm Anbieters die Prozess Ereignisse überwacht.|
|metrikremotedebugging|Legen Sie diese Einstellung auf ungleich NULL fest, um die Unterstützung für Remote Debugging anzugeben.|
|metricencusenativebuilder|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass der Edit and Continue Manager den encbuild.dll der Debug-Engine zum Erstellen für "Bearbeiten und Fortfahren" verwenden soll. **Hinweis:**  Eine benutzerdefinierte Debug-Engine sollte diese nie festlegen oder sollte immer auf 0 festgelegt werden.|
|metricLoadUnderWOW64|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass die Debug-Engine beim Debuggen eines 64-Bit-Prozesses in den zu debuggenden Prozess unter wow geladen werden soll. Andernfalls wird die Debug-Engine in den Visual Studio-Prozess geladen, der unter WOW64 ausgeführt wird.|
|metricLoadProgramProviderUnderWOW64|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass der Programmanbieter beim Debuggen eines 64-Bit-Prozesses unter wow in den zu debuggenden Prozess geladen werden soll. Andernfalls wird Sie in den Visual Studio-Prozess geladen.|
|metricstoponexceptioncrossingmanagedboundary|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass der Prozess beendet werden soll, wenn eine nicht behandelte Ausnahme über verwaltete/nicht verwaltete Code Grenzen hinweg ausgelöst wird.|
|metricautoselectpriority|Legen Sie diese Option auf eine Priorität für die automatische Auswahl der Debug-Engine fest (höhere Werte sind höher als eine höhere Priorität).|
|metricautoselectincompatiblelist|Registrierungsschlüssel, der Einträge enthält, die GUIDs für Debug-engines angeben, die bei der automatischen Auswahl ignoriert werden. Diese Einträge sind eine Zahl (0, 1, 2 usw.), bei der eine GUID als Zeichenfolge ausgedrückt wird.|
|metricincompatiblelist|Registrierungsschlüssel, der Einträge enthält, die GUIDs für Debug-engines angeben, die mit dieser Debug-Engine nicht kompatibel sind.|
|metricdisablejitoptimization|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass just-in-Time-Optimierungen (für verwalteten Code) während des Debuggens deaktiviert werden sollen.|

|Eigenschaften der Ausdrucks Auswertung|BESCHREIBUNG|
|-------------------------------------|-----------------|
|metricengine|Enthält die Anzahl der Debug-engines, die die angegebene Ausdrucks Auswertung unterstützen.|
|metricpreloadmodules|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass Module vorab geladen werden sollen, wenn eine Ausdrucks Auswertung für ein Programm gestartet wird.|
|metricthisobjectname|Legen Sie diese Einstellung auf den "This"-Objektnamen fest.|

|Erweiterungs Eigenschaften der Ausdrucks Auswertung|BESCHREIBUNG|
| - |-----------------|
|metricextensiondll|Der Name der dll, die diese Erweiterung unterstützt.|
|metricextensionregisterssupported|Liste der unterstützten Register.|
|metricextensionregistersentrypoint|Einstiegspunkt für den Zugriff auf Register.|
|metricextensiontypessupported|Liste der unterstützten Typen.|
|metricextensiontypesentrypoint|Einstiegspunkt für den Zugriff auf Typen.|

|Eigenschaften von Port Lieferanten|BESCHREIBUNG|
|------------------------------|-----------------|
|metricportpickerclsid|Die CLSID der Port Auswahl (ein Dialogfeld, mit dem der Benutzer Ports auswählen und Ports für das Debuggen hinzufügen kann).|
|metricdiszuzuforderungserenteredports|Ein Wert ungleich 0 (null), wenn die vom Benutzer eingegebenen Ports nicht zum Port Lieferanten hinzugefügt werden können (Dadurch wird das Dialogfeld "Port Auswahl" im Grunde schreibgeschützt).|
|metricpidbase|Die Basis Prozess-ID, die vom Port Lieferanten beim Zuordnen von Prozess-IDs verwendet wird.|

|Vordefinierte SP-Speichertypen|BESCHREIBUNG|
|-------------------------------|-----------------|
|storetypeer-Datei|Die Symbole werden in einer separaten Datei gespeichert.|
|storetypeer Metadata|Die Symbole werden als Metadaten in einer Assembly gespeichert.|

|Sonstige Eigenschaften|BESCHREIBUNG|
|------------------------------|-----------------|
|metricshownonusercode|Legen Sie diese Einstellung auf ungleich NULL fest, um Nichtbenutzer Code anzuzeigen.|
|metricjustmycodestepping|Legen Sie diese Einstellung auf ungleich NULL fest, um anzugeben, dass die Schrittfolge nur im Benutzercode erfolgen kann.|
|metricclsid|CLSID für ein Objekt eines bestimmten metriktyps.|
|metricName|Der benutzerfreundliche Name für ein Objekt eines bestimmten metriktyps.|
|metriclanguage|Der Name der Sprache.|

## <a name="registry-locations"></a>Registrierungs Speicherorte
 Die Metriken werden aus der Registrierung gelesen und in diese geschrieben, insbesondere im `VisualStudio` Unterschlüssel.

> [!NOTE]
> In den meisten Fällen werden die Metriken in den HKEY_LOCAL_MACHINE Schlüssel geschrieben. Manchmal ist HKEY_CURRENT_USER jedoch der Ziel Schlüssel. Dbgmetric. lib übernimmt beide Schlüssel. Beim erhalten einer Metrik wird zuerst HKEY_CURRENT_USER und dann HKEY_LOCAL_MACHINE durchsucht. Wenn eine Metrik festgelegt wird, gibt ein Parameter an, welcher Schlüssel der obersten Ebene verwendet werden soll.

 *[Registrierungsschlüssel]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[Version Root]*\

 *[metrikroot]*\

 *[metrikentyp]*\

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Registrierungsschlüssel]*|`HKEY_CURRENT_USER` oder `HKEY_LOCAL_MACHINE`|
|*[Version Root]*|Die Version von Visual Studio (z. b `7.0` `7.1` ., oder `8.0` ). Dieser Stamm kann jedoch auch mithilfe des **/rootsuffix** -Schalters geändert werden, um **devenv.exe**. Bei VSIP ist dieser Modifizierer in der Regel " **Exp**", sodass der Versions Stamm z. b. "8.0 Exp" lautet.|
|*[metrikroot]*|Dies ist entweder `AD7Metrics` oder `AD7Metrics(Debug)` , abhängig davon, ob die Debugversion von "dbgmetric. lib" verwendet wird. **Hinweis:**  Unabhängig davon, ob dbgmetric. lib verwendet wird, sollte diese Benennungs Konvention befolgt werden, wenn Sie Unterschiede zwischen Debug-und Releaseversionen haben, die in der Registrierung widergespiegelt werden müssen.|
|*[metrikentyp]*|Der Typ der zu schreibenden Metrik: `Engine` , `ExpressionEvaluator` , `SymbolProvider` usw. Diese werden alle als in dbgmetric. h als definiert `metricTypeXXXX` , wobei `XXXX` der spezifische Typname ist.|
|*Metrik*|Der Name eines Eintrags, dem ein Wert zugewiesen werden soll, um die Metrik festzulegen. Die tatsächliche Organisation der Metriken hängt vom Metriktyp ab.|
|*[Metrikwert]*|Der Wert, der der Metrik zugewiesen ist. Der Typ, den der Wert aufweisen sollte (Zeichenfolge, Zahl usw.), hängt von der Metrik ab.|

> [!NOTE]
> Alle GUIDs werden im Format gespeichert `{GUID}` . Beispiel: `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Debug-engines
 Im folgenden finden Sie die Organisation der Debug-Engine-Metriken in der Registrierung. `Engine` der metriktypname für eine Debug-Engine, der in der obigen Registrierungs Unterstruktur *[metric Type]* entspricht.

 `Engine`\

 *[Engine-GUID]*\

 `CLSID` = *[Klassen-GUID]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

 `PortSupplier`\

 `0` = *[Port Lieferanten-GUID]*

 `1` = *[Port Lieferanten-GUID]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Engine-GUID]*|Der GUID der Debug-Engine.|
|*[Klassen-GUID]*|Der GUID der Klasse, die diese Debug-Engine implementiert.|
|*[Port Lieferanten-GUID]*|Die GUID des Port Anbieters (sofern vorhanden). Viele debugengines verwenden den Standardport Lieferant und geben daher keinen eigenen Lieferanten an. In diesem Fall ist der Unterschlüssel nicht `PortSupplier` vorhanden.|

### <a name="port-suppliers"></a>Portanbieter
 Im folgenden finden Sie die Organisation der portlieferanten-Metriken in der Registrierung. `PortSupplier` der metriktypname für einen Port Lieferanten, der *[Metriktyp]* entspricht.

 `PortSupplier`\

 *[Port Lieferanten-GUID]*\

 `CLSID` = *[Klassen-GUID]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Port Lieferanten-GUID]*|Die GUID des Port Anbieters|
|*[Klassen-GUID]*|Der GUID der Klasse, die diesen Port Lieferanten implementiert.|

### <a name="symbol-providers"></a>Symbol Anbieter
 Im folgenden finden Sie die Organisation der symbollieferanten-Metriken in der Registrierung. `SymbolProvider` der metriktypname für den Symbol Anbieter und entspricht *[Metriktyp]*.

 `SymbolProvider`\

 *[Symbol Anbieter-GUID]*\

 `file`\

 `CLSID` = *[Klassen-GUID]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

 `metadata`\

 `CLSID` = *[Klassen-GUID]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Symbol Anbieter-GUID]*|Der GUID des Symbol Anbieters.|
|*[Klassen-GUID]*|Der GUID der Klasse, die diesen Symbol Anbieter implementiert.|

### <a name="expression-evaluators"></a>Ausdrucks Auswertung
 Im folgenden finden Sie die Organisation der Ausdrucks auswertungsmetriken in der Registrierung. `ExpressionEvaluator` der metriktypname für die Ausdrucks Auswertung, der *[Metriktyp]* entspricht.

> [!NOTE]
> Der Metriktyp für `ExpressionEvaluator` ist nicht in dbgmetric. h definiert, da davon ausgegangen wird, dass alle Metrikänderungen für Ausdrucksauswertungen die entsprechenden metrikfunktionen der Ausdrucks Auswertung durchlaufen (das Layout des `ExpressionEvaluator` unter Schlüssels ist etwas kompliziert, sodass die Details in dbgmetric. lib ausgeblendet werden).

 `ExpressionEvaluator`\

 *[sprach-GUID]*\

 *[Hersteller-GUID]*\

 `CLSID` = *[Klassen-GUID]*

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

 `Engine`\

 `0` = *[Debug-Engine-GUID]*

 `1` = *[Debug-Engine-GUID]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[sprach-GUID]*|Die GUID einer Sprache|
|*[Hersteller-GUID]*|Die GUID eines Anbieters|
|*[Klassen-GUID]*|Der GUID der Klasse, die diese Ausdrucks Auswertung implementiert.|
|*[Debug-Engine-GUID]*|Die GUID einer Debug-Engine, mit der diese Ausdrucks Auswertung arbeitet.|

### <a name="expression-evaluator-extensions"></a>Ausdrucks auswerterweiterungen
 Im folgenden finden Sie die Organisation der Ausdrucks Auswertung-erweiterungsmetriken in der Registrierung. `EEExtensions` der metriktypname für die Ausdrucks auswertungserweiterungen und entspricht *[metric Type]*.

 `EEExtensions`\

 *[Erweiterungs-GUID]*\

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Erweiterungs-GUID]*|Die GUID einer Ausdrucks auswerterweiterung|

### <a name="exceptions"></a>Ausnahmen
 Im folgenden finden Sie die Organisation der Ausnahmen Metriken in der Registrierung. `Exception` der metriktypname für die Ausnahmen, der *[Metriktyp]* entspricht.

 `Exception`\

 *[Debug-Engine-GUID]*\

 *[Ausnahme Typen]*\

 *distanzieren*\

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

 *distanzieren*\

 *[Metrik] = [Metrikwert]*

 *[Metrik] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Debug-Engine-GUID]*|Die GUID einer Debug-Engine, die Ausnahmen unterstützt.|
|*[Ausnahme Typen]*|Ein allgemeiner Titel für den Unterschlüssel, der die Klasse von Ausnahmen identifiziert, die behandelt werden können. Typische Namen sind **C++-Ausnahmen**, **Win32-Ausnahmen**, **Common Language Runtime-Ausnahmen** und **Native Run-Time Überprüfungen**. Diese Namen werden auch verwendet, um eine bestimmte Ausnahme Klasse für den Benutzer zu identifizieren.|
|*distanzieren*|Ein Name für eine Ausnahme, z. b. **_com_error** oder **Steuerelement Umbruch**. Diese Namen werden auch verwendet, um eine bestimmte Ausnahme für den Benutzer zu identifizieren.|

## <a name="requirements"></a>Anforderungen
 Diese Dateien befinden sich im [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK-Installationsverzeichnis (standardmäßig *[Laufwerk]* \Programme\Microsoft Visual Studio 2010 SDK \\ ).

 Header: includes\dbgmetric.h

 Bibliothek: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
