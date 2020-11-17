---
title: Änderungsprotokoll (Visual Studio-Tools für Unity, Mac) | Microsoft-Dokumentation
description: Zeigen Sie das Änderungsprotokoll für Visual Studio-Tools für Unity (Mac) an. Sie erhalten eine Übersicht von Version 1.0.0.0 bis 2.7.0.0 und höher.
ms.custom: ''
ms.date: 11/13/2020
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2f026c9d33f5aa49ebb7e974a507c85b87073897
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672846"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Änderungsprotokoll (Visual Studio-Tools für Unity, Mac)

Visual Studio-Tools für Unity (Änderungsprotokoll)

## <a name="2830"></a>2.8.3.0
Veröffentlicht: 10. November 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Das Anfügen an Unity wurde korrigiert, auch wenn kein vstu-Projekt in der Projekt Mappe vorhanden ist.

## <a name="2820"></a>2.8.2.0
Veröffentlicht: 27. Oktober, 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Verbesserte [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) Diagnose, die auf alles trifft, das von erbt `Component` , nicht nur `MonoBehaviour` .

## <a name="2810"></a>2.8.1.0
Veröffentlicht: 13. Oktober 2020

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Unterstützung für implizite Konvertierung mit aufrufen hinzugefügt. Zuvor hat der Auswertung eine strikte Typüberprüfung erzwungen, was zu `Failed to find a match for method([parameters...])` Warnmeldungen führte.

- **Integration:**

  - [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md)-Diagnose wurde hinzugefügt. Sie sollten keine `System.Reflection` Funktionen in Leistungs kritischen Nachrichten wie `Update` , `FixedUpdate` , `LateUpdate` oder verwenden `OnGUI` .

  - Verbessert [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) und [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) unterdrückt, mit Unterstützung für alle `AssetPostprocessor` statischen Methoden.

  - [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md)-Unterdrückung für `CS8618` wurde hinzugefügt. `C# 8.0` führt Verweis Typen mit NULL-Werten und Verweis Typen auf, die keine NULL-Werte zulassen. Die Initialisierungs Erkennung von Typen, die von erben, wird `UnityEngine.Object` nicht unterstützt und führt zu Fehlern.

  - Nun verwenden Sie denselben Player und asmdef-Projekt Generierungs Mechanismus für Unity 2019. x und 2020. x +.
  
  - Verbesserte Benutzeroberfläche beim Erstellen von Unity-Nachrichten mit einem Assistenten.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurde ein unerwarteter Abschluss für Meldungen in Kommentaren korrigiert.

## <a name="2800"></a>2.8.0.0 
Veröffentlicht: 14. September 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Korrigieren der Player Projektgenerierung mit Unity 2019. x.

## <a name="2710"></a>2.7.1.0
Veröffentlichung: 5. August 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unity-Nachrichten-API auf 2019.4 aktualisiert.

  - [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md)-Unterdrückung für `CA1823` wurde hinzugefügt. Private Felder mit dem Attribut `SerializeField` oder `SerializeReference` sollten nicht als nicht verwendet gekennzeichnet werden (FxCop).
  
  - [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md)-Unterdrückung für `CA1822` wurde hinzugefügt. Unity-Nachrichten sollten nicht als Kandidaten für den `static`-Modifizierer gekennzeichnet werden (FxCop).

  - [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md)-Unterdrückung für `CA1801` wurde hinzugefügt. Nicht verwendete Parameter sollten nicht aus Unity-Nachrichten entfernt werden (FxCop).
  
  - `MenuItem`-Unterstützung zum [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md)-Unterdrückungsmodul hinzugefügt.  

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Die Unterdrückungsmodule [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) und [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) wurden korrigiert, weil sie nicht mit zusätzlichen Klammern oder Methodenargumenten funktionierten.
  
  - Die obligatorische Aktualisierung der Ressourcendatenbank, auch wenn die automatische Aktualisierung in den Unity-Einstellungen deaktiviert wurde, wurde korrigiert.

## <a name="2700"></a>2.7.0.0
Veröffentlicht: 23. Juni 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Projektmappenordner können jetzt beibehalten werden, wenn Unity Projektmappen und Projekte neu generiert.

  - [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md)-Diagnose wurde hinzugefügt. Falsche Methodensignaturen mit dem Attribut `InitializeOnLoadMethod` oder `RuntimeInitializeOnLoadMethod` werden erkannt.

  - [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md)-Diagnose wurde hinzugefügt. Die Verwendung von `Invoke`, `InvokeRepeating`, `StartCoroutine` oder `StopCoroutine`, wenn das erste Argument ein Zeichenfolgenliteral ist, ist nicht typsicher.

  - [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md)-Diagnose wurde hinzugefügt. Der Aufruf von `SetPixels` ist langsam.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Das Erstellen von Breakpoints während der Ausführung des Spiels in der alten Mono-Laufzeit (Versuch, den Breakpoint direkt nach der Erstellung zu binden) wurde korrigiert. 
  
- **Integration:**

  - Setzen Sie die Auswahl nicht zurück, wenn Sie Nachrichten im Nachrichten-Assistent von Unity filtern.
  
  - Die Unterdrückungsmodule [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) und [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) wurden mit folgenden Regeln korrigiert: `IDE0044` (schreibgeschützt), `IDE0051` (nicht verwendet) und `CS0649` (nie zugewiesen) für alle Felder mit dem SerializeField-Attribut unterdrücken. `CS0649` (nie zugewiesen) wird für öffentliche Felder aller Typen unterdrückt, die `Unity.Object` erweitern.

  - Die Überprüfung auf generische Typparameter für [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) wurde korrigiert.

- **Auswertung:**

  - Der Gleichheitsvergleich mit Enumerationen wurde korrigiert.

## <a name="2610"></a>2.6.1.0
Veröffentlicht am 19. Mai 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Warnen, wenn der Messaging Server auf der Unity-Seite nicht erstellt werden kann.

  - Ordnungsgemäßes Ausführen von Analysetools während der Lightweight-Kompilierung.

  - API-Dokumentation mit Installation von Unity Hub korrigiert.
  
  - Abstürze der Debuggerschnellansicht korrigiert.

## <a name="2600"></a>2.6.0.0
Veröffentlichung: 14. April 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

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
  
  - Korrektur der Verarbeitung von Nullable-Typen.  

## <a name="2520"></a>2.5.2.0

Veröffentlichung: 23. März 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Die Registrierung von Threads bei Anfügung wurde behoben.

## <a name="2510"></a>2.5.1.0

Veröffentlichung: 3. März 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md)-Unterdrückung für `IDE0051` wurde hinzugefügt. Private Methoden, die mit Invoke, InvokeRepeating, StartCoroutine oder StopCoroutine verwendet werden, sollten nicht als nicht verwendet gekennzeichnet werden.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Die OnDrawGizmos/OnDrawGizmosSelected-Dokumentation wurde korrigiert.

- **Auswertung:**

  - Die Lambdaargumentuntersuchung wurde behoben.

## <a name="2501"></a>2.5.0.1

Veröffentlichung: 19. Februar 2020

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Ein Fehler wurde behoben, durch den die falsche Nachrichtensignatur bei der [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md)-Diagnose überprüft wurde. Beim Untersuchen von Typen mit mehreren Vererbungsstufen kann diese Diagnose mit der folgenden Meldung fehlschlagen: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`.

## <a name="2500"></a>2.5.0.0

Veröffentlichung: 22. Januar 2020

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Die Unterstützung für HLSL-Dateien wurde hinzugefügt.
  
  - In der Benutzeroberfläche wird ein neues Dialogfeld für neue Ordner verwendet.
  
  - In den Einstellungen wird ein neues zugänglicheres Eigenschaftsraster verwendet.

  - [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)-Unterdrückung für `IDE0051` wurde hinzugefügt. Private Felder mit dem `SerializeField`-Attribut sollten nicht als nicht verwendet gekennzeichnet werden.

  - [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md)-Unterdrückung für `CS0649` wurde hinzugefügt. Felder mit dem `SerializeField`-Attribut sollten nicht als nicht zugewiesen gekennzeichnet werden.  

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Die Projektgenerierung wurde behoben (`GenerateTargetFrameworkMonikerAttribute`-Ziel wurde nicht immer ordnungsgemäß ermittelt).

- **Auswertung:**

  - Die Zeichenfolgenauswertung wurde behoben (nicht mit ToString()-Aufrufen).

## <a name="2420"></a>2.4.2.0

Veröffentlichung: 3. Dezember 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Diagnosen mit benutzerdefinierten Schnittstellen korrigiert.

  - QuickInfos mit falsch formatierten Ausdrücken korrigiert.
  
## <a name="2410"></a>2.4.1.0

Veröffentlichung: 6. November 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für Unity-Hintergrundprozesse hinzugefügt. (Der Debugger kann automatisch eine Verbindung mit dem Hauptprozess anstatt mit einem untergeordneten Prozess herstellen).

  - QuickInfo für Unity-Meldungen hinzugefügt, die Informationen zur zugehörigen Dokumentation anzeigt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Analysetool für Tagvergleich, `UNT0002`, mit erweiterten Binär- und Aufrufausdrücken korrigiert.

### <a name="deprecated-features"></a>Veraltete Features

- **Integration:**

  - In Zukunft unterstützen die Visual Studio-Tools für Unity nur noch Visual Studio 2017 und höher.

## <a name="2400"></a>2.4.0.0

Veröffentlichung: 15. Oktober 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md)-Unterdrückung für `IDE0060` (nicht verwendeter Parameter) wurde für alle Unity-Meldungen hinzugefügt.

  - QuickInfo für mit `TooltipAttribute` markierte Felder hinzugefügt. (Dies funktioniert auch für einen einfachen get-Accessor, der dieses Feld verwendet).

## <a name="2330"></a>2.3.3.0

Veröffentlicht am 23. September 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Eine neue Unterdrückung für IDE0060 wurde hinzugefügt, um zu verhindern, dass die IDE eine Schnellkorrektur zum Entfernen nicht verwendeter Parameter anzeigt.
    - `USP0005` für `IDE0060`: Unity-Nachrichten werden von der Unity-Runtime aufgerufen.

## <a name="2320"></a>2.3.2.0

Veröffentlicht am 16. September 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Wir haben das Verständnis von Visual Studio für Unity-Projekte vertieft, indem wir neue, für Unity spezifische Diagnosefunktionen hinzugefügt haben. Wir haben die IDE auch intelligenter gestaltet, indem wir allgemeine C#-Diagnosen unterdrückt haben, die nicht für Unity-Projekte gelten. Die IDE zeigt z. B. keine Schnellkorrektur zum Ändern einer Prüfungsvariablen in `readonly` an, die Sie daran hindern würde, die Variable im Unity-Editor zu ändern.
    - `UNT0001`: Unity-Nachrichten werden von der Runtime auch aufgerufen, wenn sie leer sind. Deklarieren Sie sie nicht, um unnötige Verarbeitung durch die Unity-Laufzeit zu vermeiden.
    - `UNT0002`: Der Tagvergleich mithilfe der Zeichenfolgengleichheit ist langsamer als die integrierte CompareTag-Methode.
    - `UNT0003`: Die Verwendung der generischen Form von GetComponent wird für die Typsicherheit bevorzugt.
    - `UNT0004`: Die Update-Nachricht ist von der Framerate abhängig und sollte Time.deltaTime anstelle von Time.fixedDeltaTime verwenden.
    - `UNT0005`: Die FixedUpdate-Nachricht ist von der Framerate abhängig und sollte Time.fixedDeltaTime anstelle von Time.deltaTime verwenden.
    - `UNT0006`: Es wurde eine falsche Methodensignatur für diese Unity-Nachricht erkannt.
    - `UNT0007`: Unity überschreibt den NULL-Vergleichsoperator für Unity-Objekte, der mit der NULL-Zusammenfügung nicht kompatibel ist.
    - `UNT0008`: Unity überschreibt den NULL-Vergleichsoperator für Unity-Objekte, der mit der NULL-Verteilung nicht kompatibel ist.
    - `UNT0009`: Wenn Sie das InitializeOnLoad-Attribut auf eine Klasse anwenden, müssen Sie einen statischen Konstruktor bereitstellen. Das InitializeOnLoad-Attribut stellt sicher, dass es aufgerufen wird, wenn der Editor gestartet wird.
    - `UNT0010`: MonoBehaviour sollte nur mithilfe von AddComponent() erstellt werden. MonoBehaviour ist eine Komponente und muss einem GameObject angefügt werden.
    - `UNT0011`: ScriptableObject sollte nur mit CreateInstance() erstellt werden. ScriptableObject muss von der Unity-Engine zum Verarbeiten von Unity-Nachrichtenmethoden erstellt werden.
    - `USP0001` für `IDE0029`: Unity-Objekte sollten keine NULL-Zusammenfügung verwenden.
    - `USP0002` für `IDE0031`: Unity-Objekte sollten keine NULL-Verteilung verwenden.
    - `USP0003` für `IDE0051`: Unity-Nachrichten werden von der Unity-Runtime aufgerufen.
    - `USP0004` für `IDE0044`: Felder mit einem SerializeField-Attribut sollten nicht als schreibgeschützt festgelegt werden.

## <a name="2310"></a>2.3.1.0

Veröffentlicht am 4. September 2019

### <a name="new-features"></a>Neue Funktionen

- **Auswertung:**

  - Unterstützung für bessere Typanzeige wurde hinzugefügt: `List<object>` anstelle von `List'1[[System.Object, <corlib...>]]`.

  - Unterstützung für Zeigermemberzugriff wurde hinzugefügt: `p->data->member`.

  - Unterstützung für implizite Konvertierungen in Arrayinitialisierern wurde hinzugefügt: `new byte [] {1,2,3,4}`.

  - Unterstützung des Hexadezimal-Editors beim Untersuchen von Bytearrays und Zeichenfolgen wurde hinzugefügt.

## <a name="2300"></a>2.3.0.0

Veröffentlicht am 13. August 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Auswertung:**

  - Probleme mit Ausnahmen bei der Einzelschrittausführung wurden behoben.

  - Behoben: Auswertung von Pseudobezeichnen (z. B. $exception)

  - Behoben: Absturz bei Dereferenzierung ungültiger Adressen  

  - Ein Problem bei entladenen AppDomains wurde behoben.

## <a name="2200"></a>2.2.0.0

Veröffentlichung: 25. Juli 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Auswertung:**

  - Behoben: Überprüfung mit IntPtr-Typen

- **Debugger:**

  - Behoben: Verarbeitung von Abfangpunkten und Funktionsbreakpoints

## <a name="2130"></a>2.1.3.0

Veröffentlichung: 9. Juli 2019

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Hinzugefügt: Unterstützung für das Abfangen von Unterklassen von Ausnahmen

  - Hinzugefügt: Unterstützung für das MDS-Protokoll 2.51

- **Integration:**

  - Hinzugefügt: Unterstützung für ASMDEF-Dateien

  - Wechsel zum Umbenennungsmodus wenn eine Datei über eine Vorlage hinzugefügt wird, um das Verhalten des Unity-Editors zu imitieren

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Behoben: Verarbeitung falsch formatierter Meldungen bei der Kommunikation mit Unity-Playern

- **Auswertung:**

  - Behoben: Verarbeitung von Namespaces in Ausdrücken

## <a name="2120"></a>2.1.2.0

Veröffentlichung: 2. Juli 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Auswertung:**

  - Behoben: Fehlerberichterstattung mit nicht analysierbaren Ausdrücken

## <a name="2110"></a>2.1.1.0

Veröffentlichung: 27. Juni 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - MonoBehaviour-API auf 2019.1 aktualisiert.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Behoben: Leistung des Unity-Projekt-Explorers

  - Es wurden Warnungen und Fehler bei der Berichterstellung korrigiert, die ausgegeben werden sollen, wenn der Lightweightbuild aktiviert ist.

  - Probleme mit der Leistung des Lightweightbuilds wurden behoben.

## <a name="2100"></a>2.1.0.0

Veröffentlichung: 20. Juni 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Die vollständige Builderstellung für Unity-Projekte wurde zugunsten von IntelliSense-Fehlern und -Warnungen deaktiviert. Unity erstellt eine Visual Studio-Projektmappe mit Klassenbibliotheksprojekten, die die internen Vorgänge von Unity darstellen. Das Ergebnis der Erstellung in Visual Studio wird von Unity nie verwendet oder übernommen, da die Kompilierungspipeline geschlossen ist. Die Builderstellung in Visual Studio verbraucht nur Ressourcen, führt aber zu nichts. Wenn Sie einen vollständigen Build benötigen, weil Ihre Tools oder Setups davon abhängig sind, können Sie diese Optimierung deaktivieren (Einstellungen > Tools für Unity > Vollständigen Build von Projekten deaktivieren).
  
  - Unterstützung für Unity-Pakete im UPE wurde hinzugefügt. Nur referenzierte Pakete (durch Verwendung von „manifest.json“ im Ordner `Packages`) und lokale Pakete (im Ordner `Packages` integriert) werden angezeigt.

## <a name="2021"></a>2.0.2.1

Veröffentlichung: 30. Mai 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Hinzugefügt: benutzerdefiniertes Symbol für Unity-Ausführungsziele

## <a name="2020"></a>2.0.2.0

Veröffentlichung: 2. April 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für die automatische Aktualisierung der Asset-Datenbank von Unity beim Speichern hinzugefügt. Dies ist standardmäßig aktiviert und löst beim Speichern eines Skripts in Visual Studio eine Neukompilierung auf der Unity-Seite aus. Sie können dieses Feature in „Tools\Optionen\Tools für Unity\AssetDatabase von Unity beim Speichern aktualisieren“ deaktivieren.

  - Unterstützung für das Festlegen der bevorzugten Unity-Installation für Offlinedokumentation hinzugefügt.

  - Kontextmenü für den neuen Editor hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Fehler bei Assemblyfilterung und Frameüberprüfung mit leeren Frames behoben.

## <a name="2011"></a>2.0.1.1
 
 Veröffentlichung: 26. März 2019

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Vorübergehend ist Mono der standardmäßige und einzige verwendbare Debugger für dieses spezifische Release.

## <a name="2006"></a>2.0.0.6

Veröffentlichung: 26. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für „An Unity anfügen und wiedergeben“ hinzugefügt.

## <a name="2005"></a>2.0.0.5

Veröffentlichung: 20. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Beibehalten externer Eigenschaften bei Verarbeitung der Projektmappendatei.
  
- **Auswertung:**

  - Unterstützung für aliasqualifizierte Namen wurde hinzugefügt (derzeit nur im globalen Namespace). Daher akzeptiert die Ausdrucksauswertung jetzt Typen der Form „global::namespace.type“.

  - Unterstützung für die Form `pointer[index]` wurde hinzugefügt, die semantisch identisch mit `*(pointer+index)` ist, der Form zum Dereferenzieren von Zeigern.

## <a name="2004"></a>2.0.0.4

Veröffentlichung: 5. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Die `ScriptableObject`-API wurde aktualisiert.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Namespaces aus Vorlagen entfernt.

## <a name="2003"></a>2.0.0.3
 
 Veröffentlichung: 5. März 2019

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Öffentliche und serialisierte Felder rufen keine Warnungen mehr hervor. Die Compilerwarnungen `CS0649` und `IDE0051` in Unity-Projekten, die diese Nachrichten erstellt haben, werden nun automatisch unterdrückt.

- **Integration:**

  - Aufforderung zum Anfügen an eine bestimmte Instanz, wenn mehrere Unity-Prozesse ausgeführt werden.

- **Auswertung:**

  - Unterstützung für lokale Funktionen hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Das Lesen von benutzerdefinierten Attributen für benannte Argumente wurde korrigiert, wenn alte Protokollversionen verwendet wurden.

## <a name="2002"></a>2.0.0.2

Veröffentlichung: 4. Februar 2019

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - MonoBehaviour-API aktualisiert.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Korrektur des Festlegens primitiver Werte im Debugger.

## <a name="2001"></a>2.0.0.1

Veröffentlichung: 4. Dezember 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Korrektur der Selbstkapselung des Installationspakets.

## <a name="2000"></a>2.0.0.0
 Veröffentlichung: 4. Dezember 2018

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Der Unity-Debugger für Mac wurde durch den gleichen grundlegenden Unity-Debugger der Windows-Version ersetzt.

  - NRefactory zugunsten von Roslyn für die Auswertung von Ausdrücken ersetzt.

  - Unterstützung für Zeiger hinzugefügt: Dereferenzieren, Umwandeln und Zeigerarithmetik (Unity 2018.2+ und die neue Runtime sind dafür erforderlich).

  - Unterstützung für Arrayzeigeransicht (wie in C++). Nehmen Sie einen Zeigerausdruck und fügen Sie dann ein Komma und die Anzahl der Elemente hinzu, die Sie anzeigen möchten.

  - Unterstützung für asynchrone Konstrukte hinzugefügt.

  - Unterstützung für Pseudovariablen (Ausnahme und die Objekt-IDs) hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Auswertung von Ausdrücken mit fehlerhaften oder nicht unterstützten Ausdrücken korrigiert.

## <a name="1700"></a>1.7.0.0

Veröffentlichung: 13. November 2018

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Dem Dialogfeld „Anfügen“ wurden weitere Informationen zum Client hinzugefügt (IP-Adresse, Computername).

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Debugger:**

  - Es wurde ein Deadlock in der Bibliothek behoben, die zur Kommunikation mit der Debuggerengine von Unity verwendet wurde, wodurch Visual Studio oder Unity nicht mehr reagiert haben (insbesondere, wenn auf „Attach to Unity“ geklickt oder das Spiel neu gestartet wurde).

- **Integration:**

  - Ein Fehler bei der Aktivierung des Unity-Plug-Ins wurde behoben, der auftrat, wenn ein anderer Standard-Editor ausgewählt wurde.

  - Die Erstellung von Unity-Dateivorlagen wurde behoben.

## <a name="1602"></a>1.6.0.2

Veröffentlichung: 24. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Rollback der Problemumgehung für ein Leistungsproblem von Unity, da Unity dieses behoben hat.

## <a name="1601"></a>1.6.0.1

Veröffentlichung: 10. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Ein Problem bei der Unterstützung für die Codeeinfärbung für Shader wurde behoben.

## <a name="1600"></a>1.6.0.0

Veröffentlichung: 26. Juli 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Assistenten:**

  - Ein Schreibfehler in der OnApplicationFocus-Meldung wurde korrigiert.

- **Project Generation:**

  - Vorübergehende Problemumgehung für ein Leistungsproblem von Unity: Zwischenspeichern von MonoIslands beim Generieren von Projekten.

  - Konvertieren Sie keine portablen PDB-Dateien mehr in MDB-Dateien, wenn Sie die neue Unity-Runtime verwenden.

## <a name="1502"></a>1.5.0.2

Veröffentlichung: 18. April 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Unterstützung für die Vervollständigung von Shader-Code wurde hinzugefügt.

  - Unterstützung für das Umschalten von Kommentaren in Shader-Dateien wurde hinzugefügt.

## <a name="1501"></a>1.5.0.1

Veröffentlichung: 28. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Im Unity-Projekt-Explorer wurde die Unterstützung für zusätzliche Vorlagen hinzugefügt.

## <a name="1500"></a>1.5.0.0

Veröffentlichung: 21. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Es wurde Unterstützung für das Erkennen und Anfügen von Android-Playern hinzugefügt, die über USB verbunden sind.

## <a name="1403"></a>1.4.0.3

Veröffentlichung: 5. März 2018

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Es wurde Unterstützung für den neuen Projektgenerator in Unity 2018.1 hinzugefügt.

- **Integration:**

  - Ein Optionsbereich für dedizierte Einstellungen wurde hinzugefügt.

## <a name="1402"></a>1.4.0.2

Veröffentlichung: 24. Januar 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Erkennung von Mono-Version korrigiert.

- **Integration:**

  - Probleme bei Zeitabläufen mit 2018.1 und Plug-in-Aktivierung behoben.

  - Es wurden Probleme mit Benachrichtigungen behoben, die beim Erkennen eines neuen Players angezeigt werden.

## <a name="1401"></a>1.4.0.1

Veröffentlichung: 23. Januar 2018

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Probleme mit dem Erweitern und Reduzieren von Ordnern durch Doppelklicken behoben.

## <a name="1400"></a>1.4.0.0

Veröffentlichung: 13. Dezember 2017

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Unterstützung für .NET Standard wurde hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Automatische Konvertierung des Debugsymbols von „pdb“ zu „mdb“ wurde behoben.

## <a name="1301"></a>1.3.0.1

Veröffentlichung: 12. Dezember 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Indirekter Aufruf von EditorPrefs.GetBool, der den Inspektor beim Versuch beeinträchtigt, die Größe des Arrays zu ändern, korrigiert.

- **Assistenten:**

  - Aktualisieren des Roslyn-Kontexts vor dem Einfügen der Methode.

## <a name="1300"></a>1.3.0.0

Veröffentlichung: 20. November 2017

### <a name="new-features"></a>Neue Funktionen

- **Assistenten:**

  - Der Assistent für das Implementieren von Unity-Meldungen wurde hinzugefügt.

  - Es wurde Unterstützung für die neue Abschluss-API in Visual Studio für Mac 7.4 hinzugefügt.

## <a name="1200"></a>1.2.0.0

Veröffentlichung: 23. Oktober 2017

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Es wurde Unterstützung für portierbare Debugsymboldateien hinzugefügt.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Project Generation:**

  - Korrigiert: Eine zusätzliche DLL-Erweiterung wird dem Assemblydateinamen fälschlicherweise hinzugefügt.

  - Erzwingen Sie nicht das Unity-Flag „AllowAttachedDebuggingOfEditor“, da der Standard jetzt TRUE ist.

## <a name="1103"></a>1.1.0.3

Veröffentlichung: 23. Oktober 2017

### <a name="new-features"></a>Neue Funktionen

- **Project Generation:**

  - Zusätzliche Unterstützung für .NET 4.6-Profil.

## <a name="1102"></a>1.1.0.2

Veröffentlichung: 8. August 2017

### <a name="new-features"></a>Neue Funktionen

- **Debugger:**

  - Starten Sie das Dialogfeld „An den Prozess anhängen“, wenn Sie nicht sicher sind, an welche Unity-Version angehängt werden soll.

- **Project Generation:**

  - Aktivieren Sie immer den unsafe-Kompilierungsschalter, wenn Unity 5.6 verwendet wird.

## <a name="1101"></a>1.1.0.1

Veröffentlichung: 20. Juli 2017

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Es wurde Unterstützung für lokalisierte Ressourcen hinzugefügt.

## <a name="1100"></a>1.1.0.0

Veröffentlichung: 12. Juli 2017

### <a name="new-features"></a>Neue Funktionen

- **Integration:**

  - Es wurde Unterstützung für das Anhängen an Player und Editors über das Fenster „An den Prozess anhängen“ hinzugefügt.

- **Project Generation:**

  - Fehlerhafte Assembly-Namensverweise bei mcs.rsp Dateien behoben.

  - assembly.json-Kompilierungseinheiten werden nun unterstützt.

  - Fehlerhafte define-Anweisungen bei API-Ebenen wurden behoben.

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Eine auf Shader bezogene Fehlermeldung bei der Kompilierung wurde entfernt.

## <a name="1001"></a>1.0.0.1

Veröffentlichung: 4. Mai 2017

### <a name="bug-fixes"></a>Fehlerkorrekturen

- **Integration:**

  - Es wurden Probleme bei der aktiven Nachverfolgung von Dokumenten bei hybriden und regulären Projekten behoben.

## <a name="1000"></a>1.0.0.0

Veröffentlichung: 3. Mai 2017
