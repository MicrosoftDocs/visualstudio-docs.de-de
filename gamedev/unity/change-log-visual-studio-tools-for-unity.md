---
title: Änderungsprotokoll (Visual Studio-Tools für Unity, Windows) | Microsoft-Dokumentation
description: Zeigen Sie das Änderungsprotokoll für Visual Studio-Tools für Unity (Windows) an. Sie erhalten eine Übersicht von Version 1.0.0.0 bis 4.7.0.0 und höher.
ms.custom: ''
ms.date: 3/1/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 12a6e122d6193b7aa98cf27668dab201bbb86ce4
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683483"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Änderungsprotokoll (Visual Studio-Tools für Unity, Windows)

Visual Studio-Tools für Unity (Änderungsprotokoll)

## <a name="4910"></a>4.9.1.0
Veröffentlicht: 2. März 2021

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Zu lokalen Elementen hinzugefügt `Active Scene` , die Stamm Spielobjekte zeigen.

  - `this.gameObject`Zu den lokalen Elementen hinzugefügt, da diese häufig in Unity-Projekten verwendet werden.

  - `Children`-Und- `Components` Gruppen zu allen Instanzen hinzugefügt `GameObject` , sodass Sie problemlos alle Objekt Hierarchien anzeigen können.

  - `Scene Path`Zu allen Instanzen hinzugefügt `GameObject` , um die Position in der Szene anzuzeigen.

  - Unterstützung für `JobEntityBatch` /Lambdas bei Verwendung von Entitäten mit Quell-Generatoren hinzugefügt.

  - Verbesserte Unterstützung für das Anzeigen von großen Arrays (mithilfe von indexbucketing).
  
  - Fehlende Unity-Nachrichten für 2019,4-API hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden verschiedene Probleme mit der Benutzeroberfläche für nicht-deu Sprachen behoben.

  - Beheben von Stabilitätsproblemen bei der [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) Diagnose.
  
- **Debuggen:**

  - Beheben von Problemen bei der VM-Trennung bei der Verwendung von `Trace` Methoden.

- **Auswertung:**

  - Korrigiert: das Filtern veralteter Eigenschaften, die Ausnahmen auslösen.

## <a name="4900"></a>4.9.0.0
Veröffentlicht: 20. Januar 2021

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für `raytrace shaders` `UXML` -und-Dateien hinzugefügt `USS` .

  - Hinzugefügte `.vsconfig` Generierungs Unterstützung. Visual Studio sollte nun erkennen, welche Komponenten fehlen, und Sie auffordern, Sie bei der Verwendung von Unity-Projekten zu installieren.

  - Aktualisierte Unity-Nachrichten-API (für alle als coroutines verwendeten Methoden).

  - Aktualisierte Android SDK Erkennung.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Korrigieren der Prozess Aktualisierung bei Verwendung des Dialog Felds zur Instanzauswahl.

  - Korrigieren Sie die [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Diagnose, und geben Sie falsche Warnungen für coroutines und an `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="4820"></a>4.8.2.0
Veröffentlicht: 10. November 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Verbesserte [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) Diagnose, die auf alles trifft, das von erbt `Component` , nicht nur `MonoBehaviour` .

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Korrigiert der codelta ens-Nachrichten Invalidierung.

## <a name="4810"></a>4.8.1.0
Veröffentlicht: 13. Oktober 2020

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Unterstützung für implizite Konvertierung mit aufrufen hinzugefügt. Zuvor hat der Auswertung eine strikte Typüberprüfung erzwungen, was zu `Failed to find a match for method([parameters...])` Warnmeldungen führte.

- **Integration:**

  - [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md)-Diagnose wurde hinzugefügt. Sie sollten keine `System.Reflection` Funktionen in Leistungs kritischen Nachrichten wie `Update` , `FixedUpdate` , `LateUpdate` oder verwenden `OnGUI` .

  - Verbessert [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) und [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) unterdrückt, mit Unterstützung für alle `AssetPostprocessor` statischen Methoden.

  - [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md)-Unterdrückung für `CS8618` wurde hinzugefügt. `C# 8.0` führt Verweis Typen mit NULL-Werten und Verweis Typen auf, die keine NULL-Werte zulassen. Die Initialisierungs Erkennung von Typen, die von erben, wird `UnityEngine.Object` nicht unterstützt und führt zu Fehlern.

  - Nun verwenden Sie denselben Player und asmdef-Projekt Generierungs Mechanismus für Unity 2019. x und 2020. x +.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurde ein unerwarteter Abschluss für Meldungen in Kommentaren korrigiert.

## <a name="4800"></a>4.8.0.0 
Veröffentlicht: 14. September 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Korrigieren der Player Projektgenerierung mit Unity 2019. x.

## <a name="4710"></a>4.7.1.0
Veröffentlichung: 5. August 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Namespaceunterstützung zu Standardvorlagen hinzugefügt.
  
  - Unity-Nachrichten-API auf 2019.4 aktualisiert.

  - [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md)-Unterdrückung für `CA1823` wurde hinzugefügt. Private Felder mit dem Attribut `SerializeField` oder `SerializeReference` sollten nicht als nicht verwendet gekennzeichnet werden (FxCop).
  
  - [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md)-Unterdrückung für `CA1822` wurde hinzugefügt. Unity-Nachrichten sollten nicht als Kandidaten für den `static`-Modifizierer gekennzeichnet werden (FxCop).

  - [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md)-Unterdrückung für `CA1801` wurde hinzugefügt. Nicht verwendete Parameter sollten nicht aus Unity-Nachrichten entfernt werden (FxCop).
  
  - MenuItem-Unterstützung zum [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md)-Unterdrückungsmodul hinzugefügt.  

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Die Unterdrückungsmodule [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) und [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) wurden korrigiert, weil sie nicht mit zusätzlichen Klammern oder Methodenargumenten funktionierten.
  
  - Die obligatorische Aktualisierung der Ressourcendatenbank, auch wenn die automatische Aktualisierung in den Unity-Einstellungen deaktiviert wurde, wurde korrigiert.

## <a name="4700"></a>4.7.0.0
Veröffentlicht: 23. Juni 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Projektmappenordner können jetzt beibehalten werden, wenn Unity Projektmappen und Projekte neu generiert.

  - [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md)-Diagnose wurde hinzugefügt. Falsche Methodensignaturen mit dem Attribut `InitializeOnLoadMethod` oder `RuntimeInitializeOnLoadMethod` werden erkannt.

  - [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md)-Diagnose wurde hinzugefügt. Die Verwendung von `Invoke`, `InvokeRepeating`, `StartCoroutine` oder `StopCoroutine`, wenn das erste Argument ein Zeichenfolgenliteral ist, ist nicht typsicher.

  - [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md)-Diagnose wurde hinzugefügt. Der Aufruf von `SetPixels` ist langsam.

  - Unterstützung für Blockkommentare und Einzug für Shader-Dateien hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Setzen Sie die Auswahl nicht zurück, wenn Sie Nachrichten im Nachrichten-Assistent von Unity filtern.
  
  - Verwenden Sie zum Öffnen der Unity-API-Dokumentation immer den Standardbrowser.
  
  - Die Unterdrückungsmodule [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) und [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) wurden mit folgenden Regeln korrigiert: `IDE0044` (schreibgeschützt), `IDE0051` (nicht verwendet) und `CS0649` (nie zugewiesen) für alle Felder mit dem SerializeField-Attribut unterdrücken. `CS0649` (nie zugewiesen) wird für öffentliche Felder aller Typen unterdrückt, die `Unity.Object` erweitern.

  - Die Überprüfung auf generische Typparameter für die [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md)-Diagnose wurde korrigiert.

- **Auswertung:**

  - Der Gleichheitsvergleich mit Enumerationen wurde korrigiert.

## <a name="4610"></a>4.6.1.0
Veröffentlicht am 19. Mai 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Warnen, wenn der Messaging Server auf der Unity-Seite nicht erstellt werden kann.
  
  - Ordnungsgemäßes Ausführen von Analysetools während der Lightweight-Kompilierung.
  
  - Ein Problem wurde behoben, bei dem eine MonoBehaviour-Klasse, die aus der UPE erstellt wurde, nicht mit dem Namen der Datei übereinstimmte.

## <a name="4600"></a>4.6.0.0
Veröffentlicht: 14. April 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für CodeLens (Unity-Skripts und -Meldungen) wurde hinzugefügt.
  
  - [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md)-Diagnose wurde hinzugefügt. Erkennen und Umschließen von Aufrufen von Coroutinen in `StartCoroutine()`.

  - [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md)-Diagnose wurde hinzugefügt. Erkennen und Entfernen eines ungültigen oder redundanten `SerializeField`-Attributs.

  - [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md)-Diagnose wurde hinzugefügt. Erkennen, dass `GetComponent()` mit einem Nicht-Komponenten- oder Nicht-Schnittstellentyp aufgerufen wurde.
  
  - [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md)-Unterdrückung für `IDE0051` wurde hinzugefügt. Methoden mit dem `ContextMenu`-Attribut oder über ein Feld mit dem `ContextMenuItem`-Attribut referenziert nicht als nicht verwendet kennzeichnen.

  - [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md)-Unterdrückung für `IDE0051` wurde hinzugefügt. Methoden mit dem `ContextMenuItem`-Attribut nicht als nicht verwendet kennzeichnen.
  
  - [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md)-Unterdrückung für `IDE0044` wurde hinzugefügt. Felder mit dem `ContextMenuItem`-Attribut nicht mit Schreibschutz versehen.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) und [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) funktionieren jetzt für die `SerializeReference`- und `SerializeField`-Attribute.
  
### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Befehle zum Starten/Beenden nur an Unity senden, wenn der Editor kommunizieren kann.
  
  - QuickInfo-Dokumentation wurde mit geerbten Meldungen korrigiert.
  
  - Der Nachrichtenbereich für die `CreateInspectorGUI`-Nachricht wurde korrigiert.

  - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) nicht für Methoden mit polymorphen Modifizierern melden.

- **Auswertung:**

  - Verarbeitung von using-Direktiven mit Alias korrigiert.

## <a name="4510"></a>4.5.1.0

Veröffentlichung: 16. März 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md)-Unterdrückung für `IDE0051` wurde hinzugefügt. Private Methoden, die mit Invoke, InvokeRepeating, StartCoroutine oder StopCoroutine verwendet werden, sollten nicht als nicht verwendet gekennzeichnet werden.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Die OnDrawGizmos/OnDrawGizmosSelected-Dokumentation wurde korrigiert.

- **Auswertung:**

  - Die Lambdaargumentuntersuchung wurde behoben.

## <a name="4501"></a>4.5.0.1

Veröffentlichung: 19. Februar 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Ein Fehler wurde behoben, durch den die falsche Nachrichtensignatur bei der [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md)-Diagnose überprüft wurde. Beim Untersuchen von Typen mit mehreren Vererbungsstufen kann diese Diagnose mit der folgenden Meldung fehlschlagen: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`.

## <a name="4500"></a>4.5.0.0

Veröffentlichung: 22. Januar 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Die Unterstützung für HLSL-Dateien wurde hinzugefügt.
  
  - [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)-Unterdrückung für `IDE0051` wurde hinzugefügt. Private Felder mit dem `SerializeField`-Attribut sollten nicht als nicht verwendet gekennzeichnet werden.
  
  - [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md)-Unterdrückung für `CS0649` wurde hinzugefügt. Felder mit dem `SerializeField`-Attribut sollten nicht als nicht zugewiesen gekennzeichnet werden.  

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Projektgenerierung wurde korrigiert (`GenerateTargetFrameworkMonikerAttribute`-Ziel wurde nicht immer ordnungsgemäß ermittelt).

## <a name="4420"></a>4.4.2.0

Veröffentlichung: 3. Dezember 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Diagnosen mit benutzerdefinierten Schnittstellen korrigiert.

  - QuickInfos mit falsch formatierten Ausdrücken korrigiert.

## <a name="4410"></a>4.4.1.0

Veröffentlichung: 6. November 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für Unity-Hintergrundprozesse hinzugefügt. (Der Debugger kann automatisch eine Verbindung mit dem Hauptprozess anstatt mit einem untergeordneten Prozess herstellen).
  
  - QuickInfo für Unity-Meldungen hinzugefügt, die Informationen zur zugehörigen Dokumentation anzeigt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Das Analysetool zum Vergleichen von Tags, [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md), wurde mit erweiterten Binär- und Aufrufausdrücken korrigiert.

### <a name="deprecated-features"></a>Veraltete Features

- **Integration:**

  - In Zukunft unterstützen die Visual Studio-Tools für Unity nur noch Visual Studio 2017 und höher.

## <a name="4400"></a>4.4.0.0

Veröffentlichung: 15. Oktober 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md)-Unterdrückung für `IDE0060` (nicht verwendeter Parameter) wurde für alle Unity-Meldungen hinzugefügt.
  
  - QuickInfo für mit `TooltipAttribute` markierte Felder hinzugefügt. (Dies funktioniert auch für einen einfachen get-Accessor, der dieses Feld verwendet).

## <a name="4330"></a>4.3.3.0

Veröffentlicht am 23. September 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Fehler- und Warnberichterstellung für Lightweightbuilds wurde korrigiert.

## <a name="4320"></a>4.3.2.0

Veröffentlicht am 16. September 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Wir haben das Verständnis von Visual Studio für Unity-Projekte vertieft, indem wir neue, für Unity spezifische Diagnosefunktionen hinzugefügt haben. Wir haben die IDE auch intelligenter gestaltet, indem wir allgemeine C#-Diagnosen unterdrückt haben, die nicht für Unity-Projekte gelten. Die IDE zeigt z. B. keine Schnellkorrektur zum Ändern einer Prüfungsvariablen in `readonly` an, die Sie daran hindern würde, die Variable im Unity-Editor zu ändern.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): Unity-Nachrichten werden von der Runtime auch aufgerufen, wenn sie leer sind. Deklarieren Sie sie nicht, um unnötige Verarbeitung durch die Unity-Laufzeit zu vermeiden.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): Der Tagvergleich mithilfe der Zeichenfolgengleichheit ist langsamer als die integrierte CompareTag-Methode.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Die Verwendung der generischen Form von GetComponent wird für die Typsicherheit bevorzugt.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): Die Update-Nachricht ist von der Framerate abhängig und sollte Time.deltaTime anstelle von Time.fixedDeltaTime verwenden.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): Die FixedUpdate-Nachricht ist von der Framerate abhängig und sollte Time.fixedDeltaTime anstelle von Time.deltaTime verwenden.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): Es wurde eine falsche Methodensignatur für diese Unity-Nachricht erkannt.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity überschreibt den NULL-Vergleichsoperator für Unity-Objekte, der mit der NULL-Zusammenfügung nicht kompatibel ist.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity überschreibt den NULL-Vergleichsoperator für Unity-Objekte, der mit der NULL-Verteilung nicht kompatibel ist.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): Wenn Sie das InitializeOnLoad-Attribut auf eine Klasse anwenden, müssen Sie einen statischen Konstruktor bereitstellen. Das InitializeOnLoad-Attribut stellt sicher, dass es aufgerufen wird, wenn der Editor gestartet wird.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): MonoBehaviour sollte nur mithilfe von AddComponent() erstellt werden. MonoBehaviour ist eine Komponente und muss einem GameObject angefügt werden.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject sollte nur mit CreateInstance() erstellt werden. ScriptableObject muss von der Unity-Engine zum Verarbeiten von Unity-Nachrichtenmethoden erstellt werden.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) für `IDE0029`: Unity-Objekte sollten keine NULL-Zusammenfügung verwenden.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) für `IDE0031`: Unity-Objekte sollten keine NULL-Verteilung verwenden.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) für `IDE0051`: Unity-Nachrichten werden von der Unity-Runtime aufgerufen.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) für `IDE0044`: Felder mit einem SerializeField-Attribut sollten nicht als schreibgeschützt festgelegt werden.

## <a name="4310"></a>4.3.1.0

Veröffentlicht am 4. September 2019

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Unterstützung für bessere Typanzeige wurde hinzugefügt: `List<object>` anstelle von `List'1[[System.Object, <corlib...>]]`.

  - Unterstützung für Zeigermemberzugriff wurde hinzugefügt: `p->data->member`.

  - Unterstützung für implizite Konvertierungen in Arrayinitialisierern wurde hinzugefügt: `new byte [] {1,2,3,4}`.

## <a name="4300"></a>4.3.0.0

Veröffentlicht am 13. August 2019

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Hinzugefügt: Unterstützung für das MDS-Protokoll 2.51

- **Integration:**

  - Das Fenster „An Unity-Instanz anfügen“ wurde mit Funktionen zum Sortieren, Suchen und Aktualisieren verbessert. Die PID wird jetzt auch für lokale Spieler angezeigt (durch Abfragen von lauschenden Sockets auf dem System, um den Besitzerprozess abzurufen).

  - Hinzugefügt: Unterstützung für ASMDEF-Dateien

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Behoben: Verarbeitung falsch formatierter Meldungen bei der Kommunikation mit Unity-Playern

- **Auswertung:**

  - Behoben: Verarbeitung von Namespaces in Ausdrücken

  - Behoben: Überprüfung mit IntPtr-Typen
  
  - Behoben: Probleme mit Ausnahmen bei der Einzelschrittausführung

  - Behoben: Auswertung von Pseudobezeichnen (z. B. $exception)

  - Behoben: Absturz bei Dereferenzierung ungültiger Adressen  

  - Behoben: Problem bei entladenen AppDomains

## <a name="4201"></a>4.2.0.1

Veröffentlichung: 24. Juli 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Hinzugefügt: neue Option zur Erstellung beliebiger Dateitypen über den Unity-Projekt-Explorer
  
  - Verbessert: Diagnosezwischenspeicherung bei der Verwendung schneller Builds für Unity-Projekte

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Behoben: Dateierweiterung konnte von keinem bekannten Editor verarbeitet werden

  - Behoben: Unterstützung für benutzerdefinierte Erweiterungen im Unity-Projekt-Explorer

  - Behoben: Speichern von Einstellung außerhalb des Hauptdialogfelds

  - Entfernt: veraltete Abhängigkeit „Microsoft.VisualStudio.MPF“

## <a name="4110"></a>4.1.1.0

Veröffentlicht am 24. Mai 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - MonoBehaviour-API auf 2019.1 aktualisiert.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Warnungen und Fehler bei der Berichterstellung korrigiert, die ausgegeben werden sollen, wenn der Lightweightbuild aktiviert ist.

  - Probleme mit der Leistung des Lightweightbuilds wurden behoben.

## <a name="4100"></a>4.1.0.0

Veröffentlicht am 21. Mai 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für das schnellere Laden neuer Projekte durch die neue Batch-API wurde hinzugefügt.

  - Die vollständige Builderstellung für Unity-Projekte wurde zugunsten von IntelliSense-Fehlern und -Warnungen deaktiviert. Unity erstellt eine Visual Studio-Projektmappe mit Klassenbibliotheksprojekten, die die internen Vorgänge von Unity darstellen. Das Ergebnis der Erstellung in Visual Studio wird von Unity nie verwendet oder übernommen, da die Kompilierungspipeline geschlossen ist. Die Builderstellung in Visual Studio verbraucht nur Ressourcen, führt aber zu nichts. Wenn Sie einen vollständigen Build benötigen, weil Sie über Tools oder Setups verfügen, die davon abhängig sind, können Sie diese Optimierung deaktivieren („Tools“ > „Optionen“ > „Tools für Unity“ > „Vollständigen Build von Projekten deaktivieren“).

  - Der Unity-Projekt-Explorer (UPE) wird automatisch angezeigt, wenn ein Unity-Projekt geladen wird. Der UPE wird neben dem Projektmappen-Explorer angedockt.

  - Der Mechanismus zum Extrahieren von Projektnamen wurde mit Unity 2019.x aktualisiert.

  - Unterstützung für Unity-Pakete im UPE wurde hinzugefügt. Nur referenzierte Pakete (durch Verwendung von „manifest.json“ im Ordner `Packages`) und lokale Pakete (im Ordner `Packages` integriert) werden angezeigt.

- **Project Generation:**

  - Beibehalten externer Eigenschaften bei Verarbeitung der Projektmappendatei.

- **Auswertung:**

  - Unterstützung für aliasqualifizierte Namen wurde hinzugefügt (derzeit nur im globalen Namespace). Daher akzeptiert die Ausdrucksauswertung jetzt Typen der Form „global::namespace.type“.

  - Unterstützung für die Form `pointer[index]` wurde hinzugefügt, die semantisch identisch mit `*(pointer+index)` ist, der Form zum Dereferenzieren von Zeigern.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Abhängigkeitsprobleme mit Microsoft.VisualStudio.MPF wurden behoben.

  - Probleme mit dem Anfügen von UWP-Playern ohne geladenes Projekt wurden behoben.

  - Probleme mit der automatischen Aktualisierung von Ressourcendatenbanken, wenn Visual Studio noch nicht angefügt war, wurden behoben.

  - Themenprobleme mit Beschriftungen und Kontrollkästchen wurden behoben.

- **Debugger:**

  - Die Schrittausführung mit statischen Konstruktoren wurde korrigiert.

## <a name="4005"></a>4.0.0.5

Veröffentlichung: 27. Februar 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Visual Studio-Versionserkennung mit dem Setuppaket korrigiert.

  - Nicht verwendete Assemblys aus dem Setuppaket entfernt.

## <a name="4004"></a>4.0.0.4

Veröffentlichung: 13. Februar 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung hinzugefügt, um Unity-Prozesse während der Installation richtig zu erkennen und damit die Setup-Engine mit Dateisperren besser umgehen kann.

  - Die `ScriptableObject`-API wurde aktualisiert.

## <a name="4003"></a>4.0.0.3

Veröffentlichung: 31. Januar 2019

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Öffentliche und serialisierte Felder rufen keine Warnungen mehr hervor. Die Compilerwarnungen `CS0649` und `IDE0051` in Unity-Projekten, die diese Nachrichten erstellt haben, werden nun automatisch unterdrückt.

- **Integration:**

  - Die Benutzererfahrung bei der Anzeige von Unity-Editor- und Player-Instanzen wurde verbessert (Fenster sind nun in der Größe veränderbar, verwenden einheitliche Ränder und zeigen einen Griff zum Ändern der Größe). Prozess-ID-Informationen für Unity-Editoren hinzugefügt.

  - Die `MonoBehaviour`-API wurde aktualisiert.

- **Auswertung:**

  - Unterstützung für lokale Funktionen hinzugefügt.

  - Unterstützung für Pseudovariablen (Ausnahme und die Objekt-IDs) hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Problem mit Moniker-Images und -Designs behoben.

  - Schreiben Sie nur während des Debuggens in das Ausgabefenster, wenn Sie die Asset-Datenbank automatisch aktualisieren.

  - Verzögerungen der Benutzeroberfläche mit der MonoBehaviour-Assistentenfilterung behoben.

- **Debugger:**

  - Das Lesen von benutzerdefinierten Attributen für benannte Argumente wurde korrigiert, wenn alte Protokollversionen verwendet wurden.

## <a name="4002"></a>4.0.0.2

Veröffentlichung: 23. Januar 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Experimentelle Build-Generierung korrigiert.

  - Die Behandlung von Ereignissen in Projektdateien wurde korrigiert, um die Auslastung von UI-Threads zu minimieren.

  - Der Vervollständigungsanbieter mit gestapelten Textänderungen wurde korrigiert.

- **Debugger:**

  - Die Anzeige von Debugmeldungen für Benutzer an den angefügten Debugger wurde korrigiert.

## <a name="4001"></a>4.0.0.1

Veröffentlichung: 10. Dezember 2018

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - NRefactory zugunsten von Roslyn für die Auswertung von Ausdrücken ersetzt.

  - Unterstützung für Zeiger hinzugefügt: Dereferenzieren, Umwandeln und Zeigerarithmetik (Unity 2018.2+ und die neue Runtime sind dafür erforderlich).

  - Unterstützung für Arrayzeigeransicht (wie in C++). Nehmen Sie einen Zeigerausdruck und fügen Sie dann ein Komma und die Anzahl der Elemente hinzu, die Sie anzeigen möchten.

  - Unterstützung für asynchrone Konstrukte hinzugefügt.

- **Integration:**

  - Unterstützung für die automatische Aktualisierung der Asset-Datenbank von Unity beim Speichern hinzugefügt. Dies ist standardmäßig aktiviert und löst beim Speichern eines Skripts in Visual Studio eine Neukompilierung auf der Unity-Seite aus. Sie können dieses Feature in „Tools\Optionen\Tools für Unity\AssetDatabase von Unity beim Speichern aktualisieren“ deaktivieren.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Die Brückenaktivierung wurde korrigiert, wenn Visual Studio nicht als bevorzugter externer Editor ausgewählt wurde.

  - Auswertung von Ausdrücken mit fehlerhaften oder nicht unterstützten Ausdrücken korrigiert.

## <a name="4000"></a>4.0.0.0

Veröffentlichung: 4. Dezember 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Zusätzliche Unterstützung für Visual Studio 2019 (Sie benötigen mindestens Unity 2018.3, um Visual Studio 2019 als externen Skript-Editor verwenden zu können).

  - Übernahme des Visual Studio-Bilddienstes und -Katalogs mit voller Unterstützung für HDPI-Skalierung, pixelgenaue Bilder und Designs.

### <a name="deprecated-features"></a>Veraltete Features

- **Integration:**

  - In Zukunft wird Visual Studio-Tools für Unity nur noch Unity 5.2+ unterstützen (mit der integrierten Visual Studio-Integration von Unity).

  - In Zukunft wird Visual Studio-Tools für Unity nur noch Visual Studio 2015+ unterstützen.

  - Legacysprachendienst, Fehlerliste und Statusleiste entfernt.

  - Der Quick Monobehaviour-Assistent wurde entfernt (zugunsten der dedizierten IntelliSense-Unterstützung).

## <a name="3903"></a>3.9.0.3

am 28. November 2018 veröffentlicht

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Fehler beim erneuten Laden von Projekten sowie in IntelliSense behoben, wenn Skripts aus dem ersten Projekt hinzugefügt und entfernt wurden.

## <a name="3902"></a>3.9.0.2

am 19. November 2018 veröffentlicht

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Es wurde ein Deadlock in der Bibliothek behoben, die zur Kommunikation mit der Debuggerengine von Unity verwendet wurde, wodurch Visual Studio oder Unity nicht mehr reagiert haben (insbesondere, wenn auf „Attach to Unity“ geklickt oder das Spiel neu gestartet wurde).

## <a name="3901"></a>3.9.0.1

am 15. November 2018 veröffentlicht

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Ein Fehler bei der Aktivierung des Unity-Plug-Ins wurde behoben, der auftrat, wenn ein anderer Standard-Editor ausgewählt wurde.

## <a name="3900"></a>3.9.0.0

am 13. November 2018 veröffentlicht

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Rollback der Problemumgehung für ein Leistungsproblem von Unity, da Unity dieses behoben hat.

## <a name="3807"></a>3.8.0.7

Veröffentlichung: 20. September 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - (Aus 3.9.0.2 bereitgestellt) Es wurde ein Deadlock in der Bibliothek behoben, die zur Kommunikation mit der Debug-Engine von Unity verwendet wurde, wodurch Visual Studio oder Unity nicht mehr reagiert haben (insbesondere, wenn auf „Attach to Unity“ geklickt oder das Spiel neu gestartet wurde).

## <a name="3806"></a>3.8.0.6

Veröffentlichung: 27. August 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Fehler beim erneuten Laden von Projekten und Projektmappe wurde behoben.

## <a name="3805"></a>3.8.0.5

Veröffentlichung: 20. August 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Fehler bei der Freigabe von Projektüberwachungsabonnements behoben.

## <a name="3804"></a>3.8.0.4

Veröffentlichung: 14. August 2018

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Unterstützung für Zeigerwerte wurde hinzugefügt.

  - Unterstützung für generische Methoden wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Intelligentes erneutes Laden mit mehreren geänderten Projekten

## <a name="3803"></a>3.8.0.3

Veröffentlichung: 24. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - (Aus 3.9.0.0 bereitgestellt) Rollback der Problemumgehung für ein Leistungsproblem von Unity, da Unity dieses behoben hat.

## <a name="3802"></a>3.8.0.2

Veröffentlichung: 7. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Vorübergehende Problemumgehung für ein Leistungsproblem von Unity: Zwischenspeichern von MonoIslands beim Generieren von Projekten.

## <a name="3801"></a>3.8.0.1

Veröffentlichung: 26. Juli 2018

### <a name="new-features"></a>Neue Funktionen

- **Debuggen:**

  - Unterstützung für die Befehle „UserLog“ und „UserBreak“ wurde hinzugefügt.

  - Unterstützung für verzögerte Typlast wurde hinzugefügt (optimiert die Antwortlatenz von Netzwerklast und Debugger).

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Auswertung:**

  - Verbesserte Ausdrucksauswertung und Methodensuche von Binäroperatoren

## <a name="3800"></a>3.8.0.0

Veröffentlichung: 30. Mai 2018

### <a name="new-features"></a>Neue Funktionen

- **Debuggen:**

  - Unterstützung für die Anzeige von Variablen in asynchronen Konstrukten hinzugefügt.

  - Unterstützung für die Verarbeitung von geschachtelten Typen beim Festlegen von Haltepunkten hinzugefügt, um Warnungen mit Compilerkonstrukten zu verhindern.

- **Integration:**

  - Unterstützung für TextMate-Grammatiken für Shaders wurde hinzugefügt (die C++-Workload wird nicht länger für die Codeeinfärbung für Shader benötigt).

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Konvertieren Sie keine portablen PDB-Dateien mehr in MDB-Dateien, wenn Sie die neue Unity-Runtime verwenden.

## <a name="3701"></a>3.7.0.1

Veröffentlichung: 7. Mai 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Installer:**

  - Ein Abhängigkeitsproblem bei der Verwendung des experimentellen Builds wurde behoben.

## <a name="3700"></a>3.7.0.0

Veröffentlichung: 7. Mai 2018

### <a name="new-features"></a>Neue Funktionen

- **Debuggen:**

  - Unterstützung für orchestriertes Debuggen wurde hinzugefügt (Debuggen von mehreren Playern/Editors in derselben Visual Studio-Sitzung).

  - Unterstützung für das Debuggen von Android USB-Player wurde hinzugefügt.

  - Unterstützung für das Debuggen von UWP/IL2CPP-Player wurde hinzugefügt.

- **Auswertung:**

  - Unterstützung für hexadezimale-Spezifizierer wurden hinzugefügt.

  - Evaluierung des Überwachungsfensters wurde verbessert

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Verwendung der Ausnahmeeinstellungen wurde behoben

- **Project Generation:**

  - Der Paket-Manager wird aus der Kompilierung von Einheiten aus der Generierung ausgeschlossen.

## <a name="3605"></a>3.6.0.5

Veröffentlichung: 13. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Es wurde Unterstützung für den neuen Projektgenerator in Unity 2018.1 hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Behandlung von „Beschädigt“-Zuständen wurde mit benutzerdefinierten Projekten behoben.

- **Debugger:**

  - Festlegen der nächsten Anweisung wurde korrigiert.

## <a name="3604"></a>3.6.0.4

Veröffentlichung: 5. März 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Erkennung von Mono-Version korrigiert.

- **Integration:**

  - Probleme bei Zeitabläufen mit 2018.1 und Plug-in-Aktivierung behoben.

## <a name="3603"></a>3.6.0.3

Veröffentlichung: 23. Februar 2018

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Unterstützung für .NET Standard wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Erkennung von Unity-Zielframework korrigiert.

- **Debugger:**

  - Abbruch bei Ausnahmen, die außerhalb von Benutzercode ausgelöst werden, korrigiert.

## <a name="3602"></a>3.6.0.2

Veröffentlichung: 7. Februar 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Aktualisieren der UnityMessage-API-Oberfläche für 2017.3.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Nur Projekte bei externer Änderung neu laden (mit Einschränkungen).

## <a name="3601"></a>3.6.0.1

Veröffentlichung: 24. Januar 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Automatische Konvertierung des Debugsymbols von „pdb“ zu „mdb“ wurde behoben.

  - Indirekter Aufruf von EditorPrefs.GetBool, der den Inspektor beim Versuch beeinträchtigt, die Größe des Arrays zu ändern, korrigiert.

## <a name="3600"></a>3.6.0.0

Veröffentlichung: 10. Januar 2018

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Unterstützung für 2018.1-MonoIsland-Referenzmodell hinzugefügt.

- **Auswertung:**

  - Unterstützung für $exception-Bezeichner hinzugefügt.

- **Debugger:**

  - Unterstützung für DebuggerHidden/DebuggerStepThrough-Attribute mit der neuen Unity-Runtime hinzugefügt.

- **Assistenten:**

  - 'Latest'-Version für Assistenten eingeführt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Projekt-GUID-Berechnung für Playerprojekte korrigiert.

- **Debugger:**

  - Race bei der Behandlung von Abbruchereignissen korrigiert.

- **Assistenten:**

  - Aktualisieren des Roslyn-Kontexts vor dem Einfügen der Methode.

## <a name="3503"></a>3.5.0.3

Veröffentlichung: 9. Januar 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Automatische Konvertierung des Debugsymbols von „pdb“ zu „mdb“ wurde behoben.

## <a name="3502"></a>3.5.0.2

Veröffentlichung: 4. Dezember 2017

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unity-Projekte werden jetzt automatisch in Visual Studio neu geladen, wenn Sie ein Unity-Skript hinzufügen oder entfernen.

- **Debugger:**

  - Es wurde eine Option hinzugefügt, zum Verwenden des von Xamarin und Visual Studio für Mac gemeinsam genutzten Mono-Debuggers zum Debuggen des Unity-Editors.

  - Es wurde Unterstützung für portierbare Debugsymboldateien hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Probleme bei der Einrichtung von Abhängigkeiten behoben.

  - Korrigiert: Das API-Hilfemenü in Unity wird nicht angezeigt.

- **Project Generation:**

  - Korrigiert: Player-Projekterstellung bei der Arbeit an einem UWP-Spiel mit IL2CPP/.NET 4.6 als Back-End.

  - Korrigiert: Eine zusätzliche DLL-Erweiterung wird dem Assemblydateinamen fälschlicherweise hinzugefügt.

  - Korrigiert: Statt der globalen Kompatibilitätsebene wird eine projektspezifische API-Kompatibilitätsebene verwendet.

  - Erzwingen Sie nicht das Unity-Flag „AllowAttachedDebuggingOfEditor“, da der Standard jetzt TRUE ist.

## <a name="3402"></a>3.4.0.2

Veröffentlichung: 19. September 2017

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - assembly.json-Kompilierungseinheiten werden nun unterstützt.

  - Unity-Assemblys werden nicht mehr in den Projektordner kopiert.

- **Debugger:**

  - Festlegen der nächsten Anweisung wird nun von der neuen Unity-Laufzeit unterstützt.

  - Der Decimal-Typ wird nun von der neuen Unity-Laufzeit unterstützt.

  - Implizite/explizite Konvertierungen werden nun unterstützt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Auswertung:**

  - Fehlerhafte Arrayerstellung mit impliziter Größe wurde behoben.

  - Vom Compiler generierte fehlerhafte Elemente mit lokalen Variablen wurden behoben.

- **Project Generation:**

  - Fehlerhafter Verweis auf Microsoft.CSharp für API-Ebene wurde in Unity 4.6 behoben.

## <a name="3302"></a>3.3.0.2

Veröffentlichung: 15. August 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Korrigiert: Die Visual Studio-Projektmappengenerierung in Unity 5.5 und vorherigen Versionen.

## <a name="3300"></a>3.3.0.0

Veröffentlichung: 14. August 2017

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Erstellung von Strukturen wird nun von der neuen Unity-Laufzeit unterstützt.

  - Minimalistische Unterstützung für Zeiger wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Auswertung:**

  - Fehlerhafter Methodenaufruf für primitive Typen wurde behoben.

  - Fehlerhafte Feldauswertung mit Typen, die mit BeforeFieldInit gekennzeichnet werden, wurde behoben.

  - Nicht unterstützte Aufrufe mit binären Operatoren (Subtraktion) wurden behoben.

  - Probleme beim Hinzufügen von Elementen zu Visual Studio Watch wurden behoben.

- **Project Generation:**

  - Fehlerhafte Assembly-Namensverweise bei mcs.rsp Dateien behoben.

  - Fehlerhafte define-Anweisungen bei API-Ebenen wurden behoben.

## <a name="3200"></a>3.2.0.0

Veröffentlichung: 10. Mai 2017

### <a name="new-features"></a>Neue Funktionen

- **Installer:**

  - MEF-Cache kann nun geleert werden.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Code-Editor:**

  - Fehlerhafte Klassifizierung/Vervollständigung mit benutzerdefinierten Attributen wurde behoben.

  - Bildflimmern bei Unity-Nachrichten wurde behoben.

## <a name="3100"></a>3.1.0.0

Veröffentlichung: 7. April 2017

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Zusätzliche Unterstützung für die neue Unity-Laufzeit (mit .NET 4.6 / C# 6-Kompatibilität).

- **Project Generation:**

  - Zusätzliche Unterstützung für .NET 4.6-Profil.

  - Zusätzliche Unterstützung für MCS.RSP-Dateien.

  - Aktivieren Sie immer den unsafe-Kompilierungsschalter, wenn Unity 5.6 verwendet wird.

  - Zusätzliche Unterstützung für die Projektgeneration „Player“ bei Verwendung der Windows Store-Plattform und il2cpp-Back-End.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Code-Editor:**

  - Feste Position der Einfügemarke nach dem Einfügen der Methode mit der automatischen Vervollständigung.

- **Project Generation:**

  - Entfernte Assemblyversion nach der Verarbeitung.

## <a name="3001"></a>3.0.0.1

Veröffentlichung: 7. März 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Diese Version enthält alle neuen Funktionen und Fehlerbehebungen, die in der Serie 2.8.x eingeführt wurden.

## <a name="2820---30-preview-3"></a>2.8.2.0–3.0 – Vorschauversion 3
Veröffentlichung: 25. Januar 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Projektgenerierung:**

  - Korrektur einer Regression, durch die zweimal auf Plug-Ins-Projekte verwiesen wurde, einmal als binäre DLL-Datei und einmal als Projektverweis.

## <a name="2810---30-preview-2"></a>2.8.1.0–3.0 – Vorschauversion 2
Veröffentlichung: 23. Januar 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Code-Editor:**

  - Korrektur eines Absturzes beim Starten einer Attributdeklaration ohne vollständige Klammern.

- **Debugger:**

  - Korrektur von Funktionshaltepunkten mit Coroutinen unter dem/der neuen Unity-Compiler/Laufzeit.

  - Hinzufügung einer Warnung für den Fall eines nicht bindbaren Haltepunkts (wenn kein zugehöriger Quellort gefunden wird).

- **Project Generation:**

  - Korrektur der csproj-Generierung mit speziellen/lokalisierten Zeichen.

  - Korrektur von Verweisen außerhalb von Objekten wie Bibliotheken (z.B. Facebook SDK).

- **Verschiedenes:**

  - Hinzufügung einer Prüfung, um zu verhindern, dass Unity während des Installierens oder Deinstallierens ausgeführt wird.

  - Umstellung auf https als Ziel für die ferne Unity-Dokumentation.

## <a name="2800---30-preview"></a>2.8.0.0–3.0 – Vorschauversion
Veröffentlichung: 17. November 2016

### <a name="new-features"></a>Neue Funktionen

- **Allgemein:**

  - Hinzufügung einer Unterstützung für das Installationsprogramm für Visual Studio 2017.

  - Hinzufügung einer Unterstützung für die Erweiterung von Visual Studio 2017.

  - Hinzufügung einer Unterstützung für die Lokalisierung.

- **Code-Editor:**

  - Hinzufügung von C# IntelliSense für Unity-Nachrichten.

  - Hinzufügung von C#-Codeeinfärbung für Unity-Nachrichten.

- **Debugger:**

  - Hinzufügung einer Unterstützung für `is`-, `as`-, Direktumwandlungs-, `default`- und `new`-Ausdrücke.

  - Hinzufügung einer Unterstützung für Zeichenfolgen-Verkettungsausdrücke.

  - Hinzufügung einer Unterstützung für die hexadezimale Anzeige ganzzahliger Werte.

  - Hinzufügung einer Unterstützung für das Erstellen neuer temporärer Variablen (Anweisungen).

  - Hinzufügung einer Unterstützung für implizite primitive Konvertierungen.

  - Hinzufügung besserer Fehlermeldungen, wenn ein Typ erwartet oder nicht gefunden wird.

- **Project Generation:**

  - Entfernung des CSharp-Suffixes aus den Projektnamen.

  - Entfernung des Verweises auf eine systemweite msbuild-Zieldatei.

- **Assistenten:**

  - Hinzufügung einer Unterstützung für Unity-Meldungen bei Nicht-Behaviour-Typen wie Editor oder EditorWindow.

  - Wechsel zu Roslyn für das Einfügen und Formatieren von Unity-Meldungen.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Korrektur eines Fehlers, der zu einem Absturz von Unity führte, wenn generische Typen ausgewertet wurden.

  - Korrektur der Verarbeitung von Nullable-Typen.

  - Korrektur der Verarbeitung von Enumerationen.

  - Korrektur der Verarbeitung geschachtelter Membertypen.

  - Korrektur des Zugriffs auf Indexer der Auflistung.

  - Korrektur der Unterstützung für das Debugging von Iteratorrahmen mit dem neuen C#-Compiler.

- **Project Generation:**

  - Behebung eines Problems, das beim Adressieren des Unity Web-Players eine Kompilierung verhinderte.

  - Behebung eines Problems, das beim Kompilieren eines Skripts mit einem webcodierten Dateinamen eine Kompilierung verhinderte.

## <a name="2300"></a>2.3.0.0

Veröffentlichung: 14. Juli 2016

### <a name="new-features"></a>Neue Funktionen

- **Allgemein:**

  - Hinzufügung einer Option, um Unity-Konsolenprotokolle in der Fehlerliste von Visual Studio zu deaktivieren.

  - Hinzufügung einer Option, mit der generierte Projekteigenschaften geändert werden können.

- **Debugger:**

  - Hinzufügung von Text-, XML-, HTML- und JSON-Zeichenfolgenschnellansichten.

- **Assistenten:**

  - Hinzufügung fehlender MonoBehaviors.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Allgemein:**

  - Behebung eines Konflikts mit ReSharper, der verhinderte, dass Steuerelemente innerhalb von Visual Studio-Einstellungen angezeigt werden.

  - Behebung eines Konflikts mit Xamarin, der in einigen Fällen das Debugging verhinderte.

- **Debugger:**

  - Es wurde ein Problem behoben, das in Visual Studio beim Debuggen zu einem Code Freeze geführt hat.

  - Behebung eines Problems mit Funktionshaltepunkten in Visual Studio 2015.

  - Behebung mehrerer Probleme bei der Ausdrucksauswertung.

## <a name="2200"></a>2.2.0.0

Veröffentlichung: 4. Februar 2016

### <a name="new-features"></a>Neue Funktionen

- **Assistenten:**

  - Intelligente Suche wurde im **"MonoBehaviours" implementieren** -Assistenten hinzugefügt.

  - Die Assistenten wurden so geändert, dass sie kontextberücksichtigend sind. Beispielsweise sind NetworkBehavior-Nachrichten nur verfügbar, wenn mit einem NetworkBehavior gearbeitet wird.

  - In den Assistenten wurde Unterstützung für NetworkBehavior-Nachrichten hinzugefügt.

- **Benutzeroberfläche:**

  - Eine Option zum Konfigurieren der Sichtbarkeit von MonoBehavior-Nachrichten wurde hinzugefügt.

  - Die Visual Studio-Eigenschaftenseiten, die für Unity-Projekte keine Bedeutung haben, wurden entfernt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Projektgenerierung:**

  - Verweise auf UnityEngine und UnityEditor für Unity 4.6 wurden korrigiert.

  - Die Generierung von Projektdateien wurde für den Fall korrigiert, dass Unity unter OS X ausgeführt wird.

  - Die Verarbeitung von Projektnamen, die Nummernzeichen (#) enthalten, wurde korrigiert.

  - Generierte Projekte wurden auf C# 4 beschränkt.

- **Debugger:**

  - Es wurde ein Problem mit der Auswertung von Ausdrücken behoben, wenn eine Unity-Koroutine debuggt wird.

  - Es wurde ein Problem behoben, das in Visual Studio beim Debuggen zu einem Code Freeze geführt hat.

- **Benutzeroberfläche:**

  - Es wurde eine Inkompatibilität behoben, die mit der Visual Studio-Erweiterung [Tabs Studio](https://tabsstudio.com/) aufgetreten ist.

- **Installer:**

  - Unterstützung für computerweite Installation von VSTU (Installation für alle Benutzer) durch Erstellen von HKLM-Registrierungseinträgen.

  - Es wurden Probleme behoben, die beim Deinstallieren von VSTU aufgetreten sind, wenn für mehrere verschiedene Versionen von Visual Studio dieselbe Version von VSTU installiert war. Zum Beispiel, wenn sowohl VSTU **2015** 2.1.0.0 als auch VSTU **2013** 2.1.0.0 installiert waren.

## <a name="2100"></a>2.1.0.0

Veröffentlichung: 8. September 2015

### <a name="new-features"></a>Neue Funktionen

- Unterstützung für Unity 5.2

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Anzeigen von Menüelementen in Unity < 4.2

- Es wird keine Fehlermeldung mehr angezeigt, wenn Intellisense-XML-Dateien von Visual Studio gesperrt werden.

- Verarbeiten bedingter <\<When Changed>>-Breakpoints, wenn das bedingte Argument kein boolescher Wert ist.

- Korrektur der Verweise auf Assemblys von UnityEngine und UnityEditor für Windows Store-Apps.

- Ein Fehler bei der schrittweisen Ausführung des Debuggers wurde behoben: schrittweise Ausführung nicht möglich, allgemeine Ausnahme.

- Korrektur der Trefferanzahl-Haltepunkte in Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Veröffentlichung: 20. Juli 2015

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Unity-Integration:**

  - Korrektur der Konvertierung von Debugsymbolen, die mit Visual Studio 2015 beim Importieren einer DLL und ihrer Debugsymbole (PDB) erstellt werden.

  - Beim Importieren einer DLL und ihrer Debugsymbole (PDB) werden immer MDB-Dateien generiert, außer wenn auch eine MDB-Datei bereitgestellt wird.

  - Korrektur der Verunreinigung des Unity-Projektverzeichnisses mit einem Verzeichnis „obj“.

  - Korrektur der Generierung von Verweisen auf „System.Xml.Link“ und „System.Runtime.Serialization“.

  - Zusätzliche Unterstützung für mehrere Abonnenten der API-Hooks zum Erstellen der Projektdatei.

  - Es wird immer eine vollständige Projektdatei erstellt, auch wenn eine der zu generierenden Dateien gesperrt ist.

  - Zusätzliche Unterstützung für *-Platzhalter im Erweiterungsfilter beim Festlegen der in das C#-Projekt einzuschließenden Dateien.

- **Visual Studio-Integration:**

  - Korrektur eines Kompatibilitätsproblems mit den Productivity Power Tools.

  - Korrektur der Generierung von MonoBehaviors im Zusammenhang mit Deklarationen von Ereignissen und Delegaten.

- **Debugger:**

  - Korrektur des potenziellen Einfrierens beim Debuggen.

  - Korrektur eines Problems, aufgrund dessen lokale Variablen in bestimmten Stapelrahmen nicht angezeigt werden.

  - Korrektur der Überprüfung leerer Arrays.

## <a name="1990---20-preview-2"></a>1.9.9.0–2.0 – Vorschauversion 2
Veröffentlichung: 2. April 2015

### <a name="new-features"></a>Neue Funktionen

- **Unity-Projekt-Explorer:**

  - Automatisches Umbenennen der Klasse beim Umbenennen einer Datei im Unity-Projekt-Explorer (siehe das Dialogfeld **Optionen** ).

  - Automatisches Auswählen neu erstellter Skripts im Unity-Projekt-Explorer.

  - Nachverfolgen des aktiven Skripts im Unity-Projekt-Explorer (siehe das Dialogfeld **Optionen** ).

  - Duale Synchronisierung des Projektmappen-Explorers von Visual Studio (siehe **Optionen** Dialogfeld).

  - Übernahme von Visual Studio-Symbolen im Unity-Projekt-Explorer.

- **Debugger:**

  - Auswählen des aktiven Debugziels in einer Liste gespeicherter oder zuletzt verwendeter Debugziele (siehe das Dialogfeld **Optionen** ).

  - Erstellen von Funktionshaltepunkten für MonoBehavior-Methoden und deren Anwendung auf mehrere MonoBehavior-Klassen.

  - Unterstützung der "Make Objekt"-ID im Debugger.

  - Unterstützung der Trefferanzahl für Haltepunkte im Debugger.

  - Unterstützung von Unterbrechung bei Ausnahme im Debugger (experimentell. Siehe das Dialogfeld **Optionen** ).

  - Unterstützung der Erstellung von Objekten und Arrays beim Auswerten von Ausdrücken im Debugger.

  - Unterstützung von NULL-Vergleichen bei der Auswertung von Ausdrücken im Debugger.

  - Herausfiltern veraltete Member im Überwachungsfenster des Debuggers.

- **Installer:**

  - Optimierte Registrierung von Visual Studio-Tools für Unity-Erweiterungen.

  - Installation des Visual Studio-Tools für Unity-Pakets für Unity 5.

- **Dokumentation:** Verbesserte Leistung bei der Dokumentationserstellung.

- **Assistenten:** Unterstützung neuer MonoBehavior-Methoden für Unity 4.6 und Unity 5.

- **Unity:** Nachschlagen unsicherer Kennzeichen und benutzerdefinierter Definitionen in RSP-Dateien während der Erstellung der Projektdatei.

- **Benutzeroberfläche:** Visual Studio-Tools für Unity-Dialogfeld **Optionen** in Visual Studio hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Unity-Projekt-Explorer:**

  - Der Unity-Projekt-Explorer wird aktualisiert, nachdem Dateien im Projektmappen-Explorer von Visual Studio verschoben oder umbenannt wurden.

  - Auswahlen werden beim Umbenennen von Dateien im Unity-Projekt-Explorer beibehalten.

  - Das automatische Erweitern und Reduzieren wird verhindert, wenn im Unity-Projekt-Explorer auf Dateien doppelgeklickt wird.

  - Es wird sichergestellt, dass neu ausgewählte Dateien im Unity-Projekt-Explorer angezeigt werden.

- **Debugger:**

  - Ein mögliches Einfrieren von Visual Studio beim Auswerten von Ausdrücken im Debugger wird verhindert.

  - Es wird sichergestellt, dass Methodenaufrufe in der richtigen Domäne im Debugger erfolgen.

- **Unity:**

  - Korrektur des Speicherorts von UnityVS.OpenFile bei Unity 5.

  - Korrektur des Speicherorts von "pdb2mdb" bei Unity 5.

  - Eine mögliche Ausnahme während der Erstellung der Projektdatei wird verhindert.

  - Ein mögliches Einfrieren bei Ausführung von Unity unter OSX wird verhindert.

  - Interne Ausnahmen werden behandelt.

  - Unity-Konsolenprotokolle werden an die Visual Studio-Fehlerliste gesendet.

- **Dokumentation:** Ordnungsgemäße Dokumentationserstellung für die neue Unity-Dokumentation.

- **Projekt:** Verschieben und Umbenennen von Unity-Dateien vom Typ „.meta“ bei Bedarf, sogar in Ordnern.

- **Assistenten:** Korrektur der Reihenfolge der Parameter der MonoBehavior-Methode beim Generieren von Code.

- **Benutzeroberfläche:** Unterstützung von Visual Studio-Designs für das Kontextmenü und Symbole.

## <a name="1980---20-preview"></a>1.9.8.0–2.0 – Vorschauversion
Veröffentlichung: 12. November 2014

### <a name="new-features"></a>Neue Funktionen

- Unterstützung für Visual Studio 2015.

- Färbung von Code für Unity-Shader in Visual Studio 2015.

- Optimierung der Darstellung von Werten beim Debuggen:

  - Bessere Visualisierung für Arraylisten, Listen, Hashtabellen und Wörterbücher.

  - Anzeigen nicht öffentlicher und statischer Member als Kategorien in Überwachungs- und lokalen Ansichten.

  - Verbesserte Anzeige der "SerializedProperty" von Unity, sodass nur das für die Eigenschaft gültige Wertfeld ausgewertet wird.

  - Unterstützung von "DebuggerDisplayAttribute" für Klassen und Strukturen.

  - Unterstützung für "DebuggerTypeProxyAttribute".

- Einfügung von MonoBehaviour-Methoden mithilfe unserer Assistenten unter Berücksichtigen der Codierkonventionen der Benutzer.

- Implementierung von Unterstützung für Textvorlagen zur Kompilierzeit in mit UnityVS generierten Projekten.

- Implementieren von Unterstützung für ResX-Ressourcen in mit UnityVS generierten Projekten.

- Unterstützung des Öffnens von Shadern in Visual Studio aus Unity.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Bereinigung von Sockets vor dem Starten des Spiels in Unity, nachdem "Anfügen" und "Wiedergeben" in Visual Studio ausgelöst wurden. Dies beseitigt einige Probleme mit der Stabilität der Verbindung zwischen Unity und VS bei Verwenden von "Anfügen" und "Wiedergeben".

- Vermeiden des Aufrufens von Methoden auf der Debuggeroberfläche der Skript-Engine von Unity, die anfällig für das Einfrieren von Unity sind. Dadurch wird das Einfrieren von Unity beim Anfügen des Debuggers behoben.

- Korrektur der Anzeige von Aufruflisten, wenn keine Symbole verfügbar sind.

- Registrierung des Rückrufprotokolls, nur wenn unbedingt erforderlich.

## <a name="1920"></a>1.9.2.0

Veröffentlichung: 9. Oktober 2014

### <a name="new-features"></a>Neue Funktionen

- Verbesserung der Erkennung von Unity-Playern.

- Bei Verwenden unserer Dateiöffnungsanwendung übergibt Unity nun die Zeilennummer und den Dateinamen.

- Standardmäßiges Zurückgreifen auf die Unity-Onlinedokumentation, wenn es keine lokale Dokumentation gibt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Beseitigung potenzieller Unity-Abstürze, wenn ein Haltepunkt nach dem Neuladen einer Domäne erreicht wird.

- Beseitigung von in der Unity-Konsole angezeigten Ausnahmen, wenn unsere Fenster "Konfiguration" oder "Info" nach dem Neuladen einer Domäne geschlossen werden.

- Korrektur der Erkennung von lokal ausgeführtem 64-Bit-Unity.

- Korrektur der Filterung von MonoBehaviour-Methoden nach Unity-Version im Assistenten.

- Korrektur eines Fehlers, bei dem alle Objekte den Projektdateien hinzugefügt wurden, wenn der Erweiterungsfilter leer war.

## <a name="1910"></a>1.9.1.0

Veröffentlichung: 22. September 2014

### <a name="new-features"></a>Neue Funktionen

- Optimierung des Bindens von Haltepunkten an Speicherorte von Quellcode.

- Unterstützung für überladene Methoden in der Ausdrucksauswertung des Debuggers.

- Unterstützung für das Boxing von Primitiven und Werttypen in der Ausdrucksauswertung des Debuggers.

- Unterstützung für das Neuerstellen der C#-Umgebung für lokale Variablen beim Debuggen anonymer Methoden.

- Löschen und Umbenennen von META-Dateien beim Löschen oder Umbenennen von Dateien in Visual Studio.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur bei der Behandlung von Visual Studio-Themen. Zuvor konnten Dialogfelder bei schwarzen Designs leer erscheinen.

- Korrektur des Einfrierens von Unity beim Verbinden des Debuggers, während Unity die Neukompilierung durchführt.

- Korrektur von Haltepunkten beim Debuggen von Remote-Editoren oder -Playern, die auf einem anderen System kompiliert wurden.

- Vermeidung eines möglichen Visual Studio-Absturzes, wenn ein Haltepunkt erreicht wird.

- Korrektur der Bindung von Haltepunkten, um zu vermeiden, dass Haltepunkte als entladen angezeigt werden.

- Korrektur der Verarbeitung des Variablenbereichs im Debugger zur Vermeidung von Livevariablen, die außerhalb des gültigen Bereichs liegen.

- Korrektur des Nachschlagens statischer Member in der Ausdrucksauswertung des Debuggers.

- Korrektur der Anzeige von Typen in der Ausdrucksauswertung des Debuggers dahingehend, dass statische Fehler und Eigenschaften angezeigt werden.

- Korrektur bei der Erstellung einer Projektmappe, wenn Unity-Projektnamen Sonderzeichen enthalten, die Visual Studio nicht zulässt (Verbindungsproblem 948666).

- Korrektur des Visual Studio Tools für Unity-Pakets dahingehend, dass das Senden von Konsolenereignissen sofort beendet wird, nachdem die Option deaktiviert wurde (Verbindungsproblem 933357).

- Korrektur der Erkennung von Verweisen, um in den von UnityVS generierten Projekten Verweise auf neue APIs wie "UnityEngine.UI" ordnungsgemäß neu zu erstellen.

- Korrektur des Installers dahingehend, dass Visual Studio vor der Installation geschlossen wird, um beschädigte Installationen zu vermeiden.

- Korrektur des Installers dahingehend, dass Unity-Verweisassemblys als ordnungsgemäße eigenständige Komponente installiert werden, die von allen Versionen von VSTU gemeinsam genutzt werden.

- Korrektur beim Öffnen von Skripts mit VSTU in 64-Bit-Versionen von Unity.

## <a name="1900"></a>1.9.0.0

Veröffentlichung: 29. Juli 2014

### <a name="new-features"></a>Neue Funktionen

- Im Fenster "Unity-Debugger anfügen" Hinzufügung der Möglichkeit zum Eingeben benutzerdefinierter Angaben für IP-Adressen und Ports für das Debugging.

- Hinzufügung der Konfigurationsoption zum Festlegen der Ausführung von Unity im Hintergrund oder nicht.

- Hinzufügung einer Konfigurationsoption zum Generieren von Projektmappen- und Projektdateien oder ausschließlich von Projektdateien.

- Startziel: Auswählen von "An Unity anfügen" oder "An Unity anfügen und wiedergeben"

- Anzeige mehrdimensionaler Arrays im Debugger.

- Behandlung neuer Debuggingports für den Unity-Player.

- Behandlung von Verweisen auf neue Unity-Assemblys wie Unity 4.6 GUI-Assemblys.

- Zerlegung von Abschlüssen zum ordnungsgemäßen Anzeigen lokaler Variablen beim Debugging.

- Zerlegung generierter Iteratorvariablen in Argumente beim Debugging.

- Beibehaltung des Zustand des Unity-Projekt-Explorers nach dem Neuladen eines Projekts.

- Hinzufügung eines Befehls zum Synchronisieren des Unity-Projekt-Explorers mit dem aktuellen Dokument.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur bedingter Haltepunkte, deren Bedingungen festgelegt werden, bevor der Debugger gestartet wird.

- Korrektur von Verweisen auf "UnityEngine", um Warnungen zu vermeiden.

- Korrektur der Analyse von Versionen für Unity-Betaversionen.

- Korrektur eines Problems, bei dem Variablen nicht im Fenster mit den lokalen Variablen angezeigt werden, wenn ein Haltepunkt erreicht oder Code schrittweise ausgeführt wird.

- Korrektur von QuickInfos für Variablen in Visual Studio 2013.

- Korrektur der Erstellung der IntelliSense-Dokumentation für Unity 4.5.

- Korrektur der Unity-/Visual Studio-Kommunikation nach dem Neuladen einer Domäne (Wiedergeben/Anhalten in Unity).

- Korrektur bei der Verarbeitung von Teilen von Visual Studio-Themen.

> [!IMPORTANT]
> C# ist die vorherrschende Sprache im Unity-Ökosystem. Die neuen Beispielobjekte sind in C# geschrieben. Die Unity-Dokumentation wurde standardmäßig auf C# umgestellt. UnityScript und Boo werden nicht mehr unterstützt, um den Schwerpunkt ganz auf die C#-Umgebung zu legen. Demzufolge basieren VSTU-Lösungen nun ausschließlich auf C# und können viel schneller geladen werden.

## <a name="1820"></a>1.8.2.0

Veröffentlichung: 7. Januar 2014

### <a name="new-features"></a>Neue Funktionen

- Umgehung eines Problems auf der Vermittlungsschicht in der Skript-Engine von Unity für Mavericks für die Remoteerkennung von Editoren.

- Behandlung neuer Ports zum Erkennen von Unity-Remoteplayern.

- Verweis der UnityEngine-Assembly spezifisch für das aktuelle Buildziel.

- Hinzufügung einer Einstellung zum Filtern von Dateien für die Einbeziehung in generierte Projekte.

- Hinzufügung einer Einstellung zum Deaktivieren des Sendens von Konsolenprotokollen an die Visual Studio-Fehlerliste. Dies ist hilfreich, wenn Sie PlayMaker oder Console Pro verwenden, da möglicherweise in Unity nur ein Rückruf für das Empfangen von Konsolenprotokollen registriert ist.

- Hinzufügung einer Einstellung zum Deaktivieren der Generierung von MDB-Debugsymbolen. Dies ist hilfreich, wenn Sie die MDB selbst generieren.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur einer Regression beim Öffnen von Dateien in Visual Studio aus Unity > = 4.2 (Verlust von IntelliSense).

- Korrektur unserer VS-Dialogfelder zur Unterstützung benutzerdefinierter Designs.

- Korrektur für das Schließen des Kontextmenüs der UPE.

- Verhinderung eines Absturzes in Unity, wenn die versionsspezifisch generierte Assembly nicht mehr synchron ist.

## <a name="1810"></a>1.8.1.0

Veröffentlichung: 21. November 2013

### <a name="new-features"></a>Neue Funktionen

- Korrektur der MonoBehaviour-Assistenten mit Unity 4.3-APIs.

- MonoBehaviour-Assistenten filtern Unity-APIs abhängig von der Version, die Sie verwenden.

- Hinzufügung eines Verweises auf "System.Xml.Linq" zu den Projekten für Unity > 4.1.

- Verbesserung unserer Aufrufe an "Debug.Log", die jetzt nicht mehr den Anfang des StackTrace in der Meldung enthalten.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur eines Fehlers, der die Standardbehandlung von JavaScript-Dateien in Visual Studio beeinträchtigen würde.

- Korrektur eines in VS angezeigten weißen Pixels (dieses Mal aber wirklich).

- Korrektur des Löschens der Assembly "UnityVS.VersionSpecific", wenn sie durch einen SCM als schreibgeschützt gekennzeichnet ist.

- Korrektur von Ausnahmen beim Erstellen von Sockets im UnityVS-Paket.

- Korrektur eines Absturzes in Visual Studio beim Laden vorhandener Bilder aus Visual Studio-Assemblys.

- Korrektur eines Fehlers bei der Generierung von "UnityVS.VersionSpecific" für Quellbuilds von Unity.

- Korrektur eines möglichen Einfrierens beim Öffnen eines Sockets im Unity-Paket.

- Korrektur der Behandlung eines Unity-Projekts mit einem Bindestrich (-) im Namen.

- Korrektur beim Öffnen von Skripts zum Vermeiden der Verwechslung der ALT+TAB-Reihenfolge für Unity 4.2 und höher.

## <a name="1800"></a>1.8.0.0

Veröffentlichung: 24. September 2013

### <a name="new-features"></a>Neue Funktionen

- Drastisch verbesserte Verbindungsgeschwindigkeit für den Debugger.

- Automatisches Behandeln der Navigation zu Datei und Zeile für Unity 4.2 und höher.

- Bedingte Haltepunkte.

- Der Projektdateigenerator verarbeitet jetzt T4-Vorlagen.

- Aktualisierung von MonoBehavior-Assistenten mit neuen APIs.

- IntelliSense-Dokumentation in C# für Unity-Typen

- Auswertung arithmetischer und logischer Ausdrücke.

- Bessere Erkennung von Remote-Editoren für die Remotedebuggingvorschau.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur eines Fehlers, der nach dem Trennen des Debuggers zu einem Threadverlust in Visual Studio führen würde.

- Korrektur eines in Visual Studio angezeigten weißen Pixels.

- Korrektur der Verarbeitung von Klicks auf das Statusleistensymbol.

- Korrektur der Generierung von Verweisen bei Assemblys im Ordner "Plug-Ins".

- Korrektur der Erstellung von Sockets aus dem UnityVS-Paket im Fall von Ausnahmen.

- Korrektur der Erkennung neuer Versionen von UnityVS.

- Korrektur der Eingabeaufforderung der Lizenzverwaltung, wenn die Lizenz abgelaufen ist.

- Korrektur eines Fehlers, der im VS-Fenster " Debugger an Prozess anfügen" eine leere Prozessliste verursachen würde.

- Korrektur der Änderung boolescher Werte in der lokalen Ansicht.

## <a name="1220"></a>1.2.2.0

Veröffentlichung: 9. Juli 2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Verarbeitung vollständig qualifizierter Namen in der Ausdrucksauswertung.

- Korrektur des Einfrierens im Zusammenhang mit der Ausnahmebehandlung, bei der die Unity-Skript-Engine uns falsche StackFrame-Daten sendet.

- Korrektur des Buildprozesses für Webziele.

- Korrektur eines Fehlers, der auftreten kann, wenn Visual Studio gestartet wird und sich eine gelöschte Datei in der Liste der Dateien befindet, die beim Start geöffnet werden sollen.

- Korrektur von "UnityVS.OpenFile" für die Verarbeitung von Nicht-Skriptdateien, wie z. B. kompilierte Shader.

- Wir verweisen jetzt aus allen C#-Projekten auf "Boo.Lang" und "UnityScript.Lang".

- Korrektur der Generierung von Verweisen in Projekten, wenn das Projekt Sonderzeichen enthält.

- Umgehung eines VS-Problems, bei dem Methodenaufrufe an verworfene Projekte mehrere Meldungen vom Typ "NullReferenceException" auslösen.

- Korrektur der Verarbeitung von Unity 4.2 Beta-Assemblys.

## <a name="1210"></a>1.2.1.0

Veröffentlichung: 9. April 2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur der lokalen Bereitstellung von Unity-Assemblys für die Codevervollständigung bei einem E/A-Fehler (z. B. schreibgeschützte oder von Visual Studio gesperrte Dateien).

- Korrektur einer Regression, bei der beim Öffnen eines Skripts in Unity der Fokus nicht auf der Datei liegt, die bereits in Visual Studio geöffnet wurde.

- Korrektur eines Leistungsproblems bei der neuen Ausnahmebehandlung.

- Korrektur der Bindung von Haltepunkten in einigen externen DLLs.

## <a name="1200"></a>1.2.0.0

Veröffentlichung: 25. März 2013

### <a name="new-features"></a>Neue Funktionen

- Drastisch verbesserte Verbindungsgeschwindigkeit für den Debugger.

- Optimierter Unity-Projekt-Explorer für größere Projekte.

- Berücksichtigung der Visual Studio-Einstellungen für das Unterbrechen (oder nicht) bei behandelten und nicht behandelten Ausnahmen.

- Berücksichtigung der Visual Studio-Einstellung für das Aufrufen von "ToString" für lokale Variablen.

- Hinzufügung des neuen Menüs "Debug -> Unity-Debugger anfügen", mit dem Sie Unity-Player debuggen können.

- Beibehalten benutzerdefinierter Projekte, die der UnityVS-Projektmappe bei Generierung der Projektmappendatei hinzugefügt werden.

- Hinzufügung der neuen Tastenkombination STRG+ALT+M -> STRG+H, um die Unity-Dokumentation für den Unity-Funktion oder den Unity-Member an der Position der Einfügemarke anzuzeigen.

- Berücksichtigung von Compilerantwortdateien (.rsp) beim Kompilieren von Visual Studio aus.

- Zerlegung vom Compiler generierter Typen, um Variablen anzuzeigen, wenn Generatormethoden dem Debugging unterzogen werden.

- Vereinfachung des Remotedebuggens, da für Unity kein freigegebener Ordner mehr konfiguriert werden muss. Sie können jetzt aus Windows auf das Unity-Projekt zugreifen.

- Installation eines benutzerdefinierten Unity-Profils als .NET-Standardzielprofil. Dies behebt alle falsch positiven Ergebnisse, die ReSharper anzeigen könnte.

- Umgehung eines Unity-Skript-Engine-Fehlers, damit der Debugger bei nicht ordnungsgemäß registrierten Threads nicht unterbricht.

- Überarbeitung der Dateiöffnungsfunktion zum Vermeiden einer Racebedingung, bei der VS vorgab, eine Datei öffnen zu können, es aber bei der Anforderung zum Öffnen der Datei zu einem Absturz kam.

- UnityVS fordert nun das Aktualisieren des Builds an, wenn VS den Build für das Projekt erstellt, und nicht mehr beim Speichern der Datei.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur des benutzerdefinierten .NET-Profils

- Korrektur der Designintegration, wodurch unsere Probleme mit dem dunklen Visual Studio 2012-Design behoben werden.

- Korrektur der Quick Behavior-Verknüpfung in Visual Studio 2012.

- Korrektur eines Steppingproblems, das beim Debuggen und dann auftreten kann, wenn ein Nicht-Hauptthread auf einen Haltepunkt trifft.

- Korrektur der UnityScript- und Boo-Vervollständigung von Typaliasnamen wie z. B. "int".

- Korrektur einer Ausnahme beim Schreiben einer neuen UnityScript- oder Boo-Zeichenfolge.

- Korrektur von Ausnahmen in Unity-Menüs, wenn eine Projektmappe nicht geladen wurde.

- Korrektur von Bug UVS-48: Bei der Eingabe doppelter Anführungszeichen wird manchmal ein Fehler erzeugt, durch den alle Funktionen unterbrochen werden (Codevervollständigung, Syntaxhervorhebung usw.).

- Fehler UVS-46 behoben: Doppelt geöffnete Skriptdatei (UnityScript) beim Klicken auf die Fehlerliste von Visual Studio.

- Fehler UVS-42 behoben: Unity-Konnektivitätslogo in der Statusleiste verarbeitet keine Mausereignisse in VS 2012.

- Fehler UVS-44 behoben: STRG+UMSCHALT+Q in VS 2012 für Quick MonoBehaviours nicht verfügbar.

- Fehler UVS-40 behoben: Im Unity-Projekt-Explorer ausgewählte Elemente sind unlesbar, wenn das Fenster im „dunklen“ VS2012-Design inaktiv ist.

- Fehler UVS-39 behoben: Fehler beim Ausstellen von Token für Escapezeichenfolgen.

- Fehler UVS-35 behoben: Aufrufen von „ToString“ für Objekte beim Untersuchen von Variablen.

- Fehler UVS-27 behoben: Inkonsistenz beim Fenster „Gehe zu Symbol“ mit „dunklem“ Design in VS2012.

- Fehler UVS-11 behoben: Lokale Elemente in Coroutinen.

## <a name="1100---beta-release"></a>1.1.0.0 – Betarelease
Veröffentlichung: 9. März 2013

## <a name="10130"></a>1.0.13.0
Veröffentlichung: 21. Januar 2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur einer Visual Studio-Blockade, die auftreten kann, wenn die zu debuggende Komponente ungültige Threadereignisse sendet. Dies passiert meist beim Debuggen einer Unity-Remoteprojekts unter OSX.

- Korrektur einer Visual Studio-Blockade, die auftreten kann, wenn der Debugger aufgrund einer Ausnahme heruntergefahren wird.

- Korrektur unserer MonoBehavior-Hilfsprogramme, wenn sich ein C#-MonoBehavior in einem Namespace befindet.

- Korrektur von QuickInfos für den Debugger für UnityScript in Visual Studio 2012.

- Korrektur der Projekterstellung, wenn von Unity aus nur Debugkonstanten geändert werden.

- Korrektur der Tastaturnavigation im Unity-Projekt-Explorer.

- Korrektur der farbigen UnityScript-Kennzeichnung für mit Escapezeichen versehene Zeichenfolgen.

- Korrektur unserer Dateiöffnungsfunktion zur besseren Ermittlung des Projektnamens bei Verwendung außerhalb von Unity. Dies ist erforderlich, wenn der Benutzer in Unity eine Dateiöffnungsfunktion eines Drittanbieters verwendet, die an UnityVS delegiert.

- Korrektur der Verarbeitung langer Meldungen, die von Unity an UnityVS gesendet werden. Zuvor konnten lange Meldungen unseren Meldungsteil von UnityVS zum Absturz bringen. Die Folge war, dass UnityVS manchmal eine Datei aus Unity nicht öffnen konnte.

## <a name="10120"></a>1.0.12.0
Veröffentlichung: 3. Januar 2013

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur einer Visual Studio-Blockade, die erfolgen kann, wenn Visual Studio einen Haltepunkt gelöscht hat.

- Korrektur eines Fehlers, bei dem einige Haltepunkte nicht getroffen werden, nachdem Unity Spielskripts neu kompiliert hat.

- Korrektur des Debuggers dahingehend, dass Visual Studio ordnungsgemäß benachrichtigt wird, wenn Haltepunkte aufgehoben wurden.

- Korrektur eines Registrierungsproblems, das den Visual Studio-Debugger am Debuggen systemeigener Programme hindern könnte.

- Korrektur einer Ausnahme, die auftreten könnte, wenn UnityScript- und Boo-Ausdrücke ausgewertet werden.

- Korrektur einer Regression, bei der beim Ändern der .NET-API-Ebene in Unity keine Aktualisierung der Projektdateien ausgelöst wurde

- Korrektur eines API-Fehlers, bei dem Benutzercode nicht am Handler des Protokollrückrufs teilnehmen kann.

## <a name="10110"></a>1.0.11.0
Veröffentlichung: 28. November 2012

### <a name="new-features"></a>Neue Funktionen

- Offizielle Unterstützung von Unity 4.

- Bearbeitung von Skripts im Unity-Projekt-Explorer.

- Integration in das Visual Studio-Fenster "Navigieren zu".

- Analyse der Info-Konsolenmeldung, damit Sie beim Klicken auf die Fehlerliste zum ersten Stackframe mit Symbolen gelangen.

- Hinzufügung einer [API](extensibility/customize-project-files-created-by-vstu.md) , damit Benutzer an der Projekterstellung teilnehmen können.

- Hinzufügung einer [API](extensibility/share-the-unity-log-callback-with-vstu.md) , damit Benutzer am Protokollrückruf teilnehmen können.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur einer Regression im Hintergrund von Unity-Projekt-Explorer in Visual Studio 2012.

- Korrektur der Projekterstellung für Benutzer des vollständigen .NET-Profils

- Korrektur der Projekterstellung für Benutzer des Ziels "Web".

- Korrektur der Projekterstellung, indem die Kompilierungssymbole DEBUG und TRACE wie bei Unity einbezogen werden.

- Korrektur eines Absturzes bei Verwendung von Sonderzeichen in unserem Symbolfenster "Gehe zu".

- Korrektur eines Absturzes, wenn wir unser Symbol nicht in die Statusleiste von Visual Studio einfügen können.

## <a name="10100"></a>1.0.10.0
Veröffentlichung: 9. Oktober 2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur des Hintergrunds von Unity-Projekt-Explorer in Visual Studio 2010.

- Korrektur eines Einfrierens von Visual Studio, das auftreten konnte, wenn UnityVS versuchte, den Debugger an ein Unity-Projekt anzufügen, dessen Debuggeroberfläche zuvor abgestürzt war.

- Korrektur eines Einfrierens von Visual Studio, das auftreten konnte, wenn ein Haltepunkt festgelegt wurde und das Neuladen einer AppDomain erfolgte.

- Korrektur, wie Assemblys aus Unity abgerufen werden, um das Sperren von Dateien und Verwechseln des Unity-Buildprozesses zu vermeiden.

## <a name="1090"></a>1.0.9.0

Veröffentlichung: 3. Oktober 2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur der Projekterstellung, wenn das Unity-Projekt tatsächliche JavaScript-Objekte enthält.

- Korrektur der Fehlerbehandlung bei der Ausdrucksauswertung.

- Korrektur beim Festlegen neuer Werte für Felder von Werttypen.

- Korrektur möglicher Nebeneffekte bei Bewegen des Mauszeigers über Ausdrücke im Code-Editor.

- Korrektur, wie Typen in geladenen Assemblys für die Ausdrucksauswertung durchsucht werden.

- Fehler UVS-21 behoben: Auswertung der Zuweisung zu Unity-Objekten hat keine Auswirkung.

- Fehler UVS-21 behoben: Ungültiger Zeiger beim Auswerten eines Methodenaufrufs in der Unity-Math-API.

## <a name="1080"></a>1.0.8.0

Veröffentlichung: 26. September 2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur des Abrufs des Pfads durch unsere Skriptöffnungsfunktion, um sicherzustellen, dass sie sowohl Visual Studio als auch die Skripts öffnen kann.

- Korrektur eines Fehlers mit Haltepunkten, die während der aktiven Debugsitzung erstellt wurden und eine Blockade von Visual Studio verursachen konnten.

- Korrektur, wie UnityVS in Visual Studio 2010 registriert wird.

## <a name="1070"></a>1.0.7.0

Veröffentlichung: 14. September 2012

### <a name="new-features"></a>Neue Funktionen

- Unterstützung von Visual Studio 2012.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur der Erstellung von Editor- und Plug-In-Projektdateien entsprechend dem Unity-Verhalten.

- Korrektur der Übersetzung von PDB-Symbolen für Unity 4.

> [!IMPORTANT]
> Durch die Unterstützung für Visual Studio 2012 mussten wir einige Dateien umbenennen und andere verschieben. Das UnityVS-Paket zum Importieren von Unity heißt jetzt für Visual Studio 2010 bzw. Visual Studio 2012 entweder UnityVS 2010 oder UnityVS 2012. Diese Version erfordert auch, dass die UnityVS-Projektdateien neu generiert werden.

## <a name="1060---internal-build"></a>1.0.6.0 – Interner Build
Veröffentlichung: 12. September 2012

## <a name="1050"></a>1.0.5.0

Veröffentlichung: 10. September 2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur der Erstellung von Projektdateien, wenn Skripts oder Shader ein ungültiges XML-Zeichen enthielten.

- Korrektur der Erkennung von Unity-Instanzen, wenn Unity mit dem Asset-Server verbunden war. Dadurch wurden Fehler beim Öffnen von Dateien aus Unity und bei der automatischen Verbindung von Visual Studio-Debuggers ausgelöst.

## <a name="1040"></a>1.0.4.0

Veröffentlichung: 5. September 2012

### <a name="new-features"></a>Neue Funktionen

- Automatische Konvertierung von Debugsymbolen in Unity.

    Wenn sich in Ihrem Ordner "Asset" eine .NET-DLL-Assembly mit der zugehörigen PDB-Datei befindet, müssen Sie die Assembly einfach erneut importieren. Daraufhin konvertiert UnityVS die PDB-Datei in eine Debugsymboldatei, die die Unity-Skript-Engine versteht. Sie können anschließend Ihre .NET-Assemblys aus UnityVS schrittweise ausführen.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur eines UnityVS-Absturzes während des Debuggens, der von Unity-internen Methoden oder Eigenschaften ausgelöst wurde.

## <a name="1030"></a>1.0.3.0

Veröffentlichung: 4. September 2012

### <a name="new-features"></a>Neue Funktionen

- Neue Konfigurationsoption zum Deaktivieren der Verwendung von UnityVS zum Öffnen von Dateien aus Unity.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur der Erstellung von Verweisen auf den UnityEditor für Nicht-Editor-Projekte.

- Korrektur der Definition des UNITY_EDITOR-Symbols für Nicht-Editor-Projekte.

- Korrektur eines zufälligen VS-Absturzes, der durch unsere benutzerdefinierte Statusleiste verursacht wurde.

## <a name="1020"></a>1.0.2.0

Veröffentlichung: 30. August 2012

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur eines Konflikts mit dem PythonTools-Debugger.

- Korrektur von Verweisen auf Mono.Cecil.

- Korrektur eines Bugs dahingehend, wie Skriptassemblys mit Unity 4 b7 aus Unity abgerufen werden.

## <a name="1010"></a>1.0.1.0

Veröffentlichung: 28. August 2012

### <a name="new-features"></a>Neue Funktionen

- Unterstützung der Vorschau auf Unity 4.0 Beta.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- Korrektur der Überprüfung der Eigenschaften, die Ausnahmen auslösen.

- Korrektur beim Wechsel zu Basisobjekten bei der Überprüfung von Objekten.

- Korrektur einer leeren Dropdownliste für die Einfügemarke im MonoBehavior-Assistenten.

- Korrektur der Vervollständigung für DLL-Dateien im Ordner "Asset" für UnityScript und Boo.

## <a name="1000---initial-release"></a>1.0.0.0 – Erstrelease
Veröffentlichung: 22. August 2012
