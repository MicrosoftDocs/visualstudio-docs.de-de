---
title: Optionen, Text-Editor, C/C++, Erweitert
description: Hier erfahren Sie, wie Sie über die Seite „Erweitert“ im C/C++-Abschnitt die Verhaltensweisen im Zusammenhang mit IntelliSense und der Suchdatenbank ändern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: fe69471d231599c6e3eece0b56ff70fca5b6afab
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040341"
---
# <a name="options-text-editor-cc-advanced"></a>Optionen, Text-Editor, C/C++, Erweitert

Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt.

Klicken Sie zum Öffnen dieser Seite im linken Fenster auf das Dialogfeld **Optionen**, erweitern Sie **Text-Editor** und **C/C++**, und klicken Sie dann auf **Erweitert**.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="browsingnavigation"></a>Durchsuchen/Navigation

Diese Optionen sollten nur in dem seltenen Fall ausgewählt werden, wenn eine Projektmappe so groß ist, dass die Datenbankaktivität einen unzulässigen Anteil der Systemressourcen beansprucht.

**Datenbank deaktivieren**

Die gesamte Codesuchdatenbank (SDF), alle anderen Optionen zum Durchsuchen und zur Navigation sowie alle IntelliSense-Funktionen (außer #include-AutoVervollständigen) werden deaktiviert.

**Datenbankupdates deaktivieren**

Die Datenbank wird schreibgeschützt geöffnet, und während der Bearbeitung der Dateien werden keine Updates ausgeführt. Die meisten Funktionen können weiterhin verwendet werden. Bei Vornahme von Änderungen veralten die Daten jedoch, und Sie erhalten falsche Ergebnisse.

**Automatische Datenbankupdates deaktivieren**

Die Codesuchdatenbank wird bei Änderung der Quelldateien nicht automatisch aktualisiert. Wenn Sie jedoch den **Projektmappen-Explorer** und das Kontextmenü für das Projekt öffnen und dann **Projektmappe neu prüfen** auswählen, werden alle veralteten Dateien überprüft, und die Datenbank wird aktualisiert.

**Implizite Dateien deaktivieren**

Die Codesuchdatenbank erfasst keine Daten für Dateien, die nicht in einem Projekt angegeben wurden. Ein Projekt enthält Quelldateien und Headerdateien, die explizit angegeben werden. Implizite Dateien sind in expliziten Dateien enthalten (beispielsweise afxwin.h, windows.h und atlbase.h). Normalerweise findet das System diese Dateien und indiziert sie auch für unterschiedliche Suchfunktionen (einschließlich "Navigieren zu"). Wenn Sie diese Option auswählen, werden diese Dateien nicht indiziert, und einige Funktionen stehen ihnen nicht zur Verfügung. Wenn Sie diese Option auswählen, werden „Implizites Bereinigen deaktivieren“ und „Ordner für externe Abhängigkeiten deaktivieren“ ebenfalls implizit ausgewählt.

**Implizites Bereinigen deaktivieren**

Die Codesuchdatenbank bereinigt keine impliziten Dateien, auf die nicht mehr verwiesen wird. Diese Option verhindert, dass implizite Dateien aus der Datenbank entfernt werden, wenn sie nicht mehr verwendet werden. Wenn Sie beispielsweise eine `#include`-Direktive hinzufügen, die festlegt, dass mapi.h auf eine der Quelldateien verweist, wird mapi.h gefunden und indiziert. Wenn Sie #include anschließend entfernen und von keinem anderen Ort auf die Datei verwiesen wird, werden die Informationen über die Datei schließlich entfernt, es sei denn, Sie wählen diese Option aus. (Weitere Informationen finden Sie in der Option **Intervall für das erneute Prüfen der Projektmappe**.) Diese Option wird ignoriert, wenn Sie die Projektmappe explizit neu prüfen.

**Ordner für externe Abhängigkeiten deaktivieren**

Die Ordner für externe Abhängigkeiten der einzelnen Projekte werden nicht erstellt oder aktualisiert. Im **Projektmappen-Explorer** enthält jedes Projekt einen Ordner für externe Abhängigkeiten mit allen impliziten Dateien für dieses Projekt. Wenn Sie diese Option auswählen, wird dieser Ordner nicht angezeigt.

**Datenbank neu erstellen**

Die Codesuchdatenbank wird beim nächsten Laden der Projektmappe vollständig neu erstellt. Wenn Sie diese Option auswählen, wird die SDF-Datenbankdatei beim nächsten Laden der Projektmappe gelöscht, was zur Folge hat, dass die Datenbank neu erstellt wird und alle Dateien indiziert werden.

**Intervall für das erneute Prüfen der Projektmappe**

Ein „Projektmappe jetzt prüfen“-Auftrag ist für das angegebene Intervall geplant. Sie müssen einen Wert zwischen 0 und 5000 Minuten angeben. Der Standardwert beträgt 60 Minuten. Beim erneuten Durchsuchen der Projektmappe werden die Zeitstempel der Dateien überprüft, um zu bestimmen, ob eine Datei außerhalb der IDE geändert wurde. (Änderungen in der IDE werden automatisch nachverfolgt, und die Dateien werden aktualisiert.) Implizit eingeschlossene Dateien werden überprüft, um zu ermitteln, ob auf sie noch Verweise vorhanden sind.

## <a name="diagnostic-logging"></a>Diagnoseprotokollierung

Diese Optionen stehen zur Verfügung, falls Sie von Microsoft gebeten werden, weitere Informationen zur Diagnose eines Problems zu sammeln. Da die Protokollierungsinformationen für Benutzer nicht hilfreich sind, empfehlen wir, sie deaktiviert zu belassen.

**Protokollierung aktivieren**

Aktiviert die Diagnoseprotokollierung an das Ausgabefenster.

**Protokolliergrad**

Legt die Ausführlichkeit des Protokolls von 0 bis 5 fest.

**Protokollierungsfilter**

Filtert angezeigte Ereignistypen mit einer Bitmaske.

Wird durch eine Summe aus den folgenden Optionen festgelegt:

- 0 – Keine

- 1 – Allgemein

- 2 – Leerlauf

- 4 – WorkItem

- 8 – IntelliSense

- 16 – ACPerf

- 32 – ClassView

## <a name="fallback-location"></a>Ausweichpfad

Der Ausweichpfad gibt an, wo die SDF- und IntelliSense-Unterstützungsdateien (beispielsweise iPCH) abgelegt werden, wenn der primäre Speicherort (dasselbe Verzeichnis wie die Projektmappe) nicht verwendet wird. Diese Situation kann auftreten, wenn der Benutzer keine Schreibberechtigungen für das Projektmappenverzeichnis hat, oder wenn sich das Projektmappenverzeichnis auf einem langsamen Gerät befindet. Der Standardausweichpfad befindet sich im temporären Verzeichnis des Benutzers.

**Immer Ausweichpfad verwenden**

Gibt an, dass die Codesuchdatenbank und IntelliSense-Dateien immer in einem Ordner, den Sie als „Ausweichpfad“ festlegen, und nicht neben der SLN-Datei gespeichert werden müssen. Die IDE legt die SDF- oder iPCH-Dateien nie neben dem Projektmappenverzeichnis ab und verwendet immer den Ausweichpfad.

**Nicht warnen, wenn Ausweichpfad verwendet wird**

Sie werden nicht informiert oder gewarnt, wenn ein Ausweichpfad verwendet wird. Normalerweise werden Sie von der IDE informiert, wenn der Ausweichpfad verwendet wurde. Mit dieser Option wird diese Warnung deaktiviert.

**Ausweichpfad**

Dieser Wert wird als sekundärer Speicherort zum Speichern der Codesuchdatenbank oder IntelliSense-Dateien verwendet. Das temporäre Verzeichnis ist standardmäßig der Ausweichpfad. Die IDE erstellt ein Unterverzeichnis unter dem angegebenen Pfad (oder im temporären Verzeichnis), das den Namen der Projektmappe zusammen mit einem Hash des vollständigen Pfads zur Projektmappe enthält. Dadurch werden Probleme mit identischen Projektmappennamen vermieden.

## <a name="intellisense"></a>IntelliSense

**Automatische QuickInfo**

Aktiviert QuickInfos, wenn Sie den Zeiger über Text bewegen.

**IntelliSense deaktivieren**

Deaktiviert alle IntelliSense-Funktionen. Die IDE erstellt keine VCPkgSrv.exe-Prozesse für IntelliSense-Anforderungen, und die IntelliSense-Funktionen werden nicht ausgeführt (QuickInfo, Memberliste, AutoVervollständigen, Parameterhilfe). Semantische Einfärbung und Verweishervorhebung sind ebenfalls deaktiviert. Diese Option deaktiviert keine Browserfunktionen, die ausschließlich von der Datenbank abhängen (einschließlich Navigationsleiste, ClassView und Eigenschaftenfenster).

**Automatisches Aktualisieren deaktivieren**

Das Aktualisieren von IntelliSense wird verzögert, bis eine tatsächliche Anforderung für IntelliSense vorliegt. Diese Verzögerung kann zu einer längeren Ausführungszeit des ersten IntelliSense-Vorgangs für eine Datei führen. Es kann jedoch hilfreich sein, diese Option auf sehr langsamen oder ressourcenbeschränkten Geräten festzulegen. Wenn Sie diese Option auswählen, wählen Sie auch implizit die Optionen „Fehlerberichterstellung deaktivieren“ und „Wellenlinien deaktivieren“.

**Fehlerberichterstellung deaktivieren**

Deaktiviert die Kennzeichnung von IntelliSense-Fehlern durch Wellenlinien und im Fenster "Fehlerliste". Außerdem wird das Analysieren im Hintergrund deaktiviert, das mit der Fehlerberichterstellung zusammenhängt. Wenn Sie diese Option auswählen, wählen Sie auch implizit die Option „Wellenlinien deaktivieren“ aus.

**Wellenlinien deaktivieren**

Deaktiviert IntelliSense-Fehlerwellenlinien. Die roten Wellenlinien werden nicht im Editorfenster, der Fehler jedoch weiterhin im Fenster „Fehlerliste“ angezeigt.

**Maximale Anzahl zwischengespeicherter Übersetzungseinheiten automatisch anpassen**

Die maximale Anzahl von Übersetzungseinheiten, die zu einem beliebigen Zeitpunkt für IntelliSense-Anforderungen aktiv gehalten werden. Sie müssen einen Wert zwischen 2 und 15 angeben. Diese Zahl bezieht sich direkt auf die maximale Anzahl von ausgeführten VCPkgSrv.exe-Prozessen (für eine angegebene Instanz von Visual Studio). Der Standardwert ist 2. Wenn Sie jedoch verfügbaren Arbeitsspeicher haben, können Sie diesen Wert erhöhen und erzielen möglicherweise eine bessere IntelliSense-Leistung.

Weitere Informationen zu Übersetzungseinheiten finden Sie unter [Phasen der Übersetzung](/cpp/preprocessor/phases-of-translation).

**#include-AutoVervollständigen deaktivieren**

Deaktiviert die automatische Vervollständigung von `#include`-Anweisungen.

**In #include-AutoVervollständigen einen Schrägstrich verwenden**

Löst die automatische Vervollständigung von `#include`-Anweisungen aus, wenn "/" verwendet wird. Das Standardtrennzeichen ist der umgekehrte Schrägstrich \'. Der Compiler akzeptiert beide. Geben Sie daher mit dieser Option an, welches Zeichen in Ihrer Codebasis verwendet wird.

**Aggressive Memberliste deaktivieren**

Die Memberliste wird nicht angezeigt, während Sie den Namen eines Typs oder einer Variablen eingeben. Die Liste wird nur nach Eingabe eines der Commitzeichen angezeigt, die in der Option **Commitzeichen der Memberliste** definiert wurden.

**Memberlisten-Schlüsselwörter deaktivieren**

Schlüsselwörter wie `void`, `class` und `switch` werden nicht in den Memberlistenvorschlägen angezeigt.

**Memberlisten-Codeausschnitte deaktivieren**

Codeausschnitte werden nicht in den Memberlistenvorschlägen angezeigt.

**Memberlistenfilter-Modus**

Legt den Typ des Übereinstimmungsalgorithmus fest. **Fuzzy** sucht die meisten möglichen Übereinstimmungen, da ein Algorithmus zur Suche von ähnlichen, jedoch nicht identischen Übereinstimmungen verwendet wird, der einer Rechtschreibprüfung ähnelt. **Intelligentes Filtern** sucht Übereinstimmungen in Teilzeichenfolgen, auch wenn sie nicht am Anfang eines Worts stehen. **Präfix** sucht nur Übereinstimmungen in identischen Teilzeichenfolgen am Wortanfang.

**Semantische Farbgebung deaktivieren**

Deaktiviert sämtliche farblichen Kennzeichnungen von Code, außer Schlüsselwörter, Zeichenfolgen und Kommentare.

**Commitzeichen der Memberliste**

Legt Zeichen fest, die bewirken, dass der derzeit markierte Memberlistenvorschlag übernommen wird. Sie können Zeichen zu dieser Liste hinzufügen oder aus der Liste entfernen.

**Intelligentes Commit der Memberliste**

Fügt eine Zeile hinzu, wenn Sie nach Eingabe eines ganzen Worts die EINGABETASTE drücken.

**Punkt in Pfeil in der Memberliste aktivieren**

Ersetzt „.“ durch „->“, sofern dies für die Memberliste anwendbar ist.

## <a name="references"></a>Referenzen

**Auflösen deaktivieren**

Standardmäßig zeigt „Alle Verweise suchen“ reine Textsuchergebnisse an, anstatt IntelliSense zur Überprüfung der einzelnen Kandidaten zu verwenden. Sie können dieses Kontrollkästchen deaktivieren, um genauere Ergebnisse aus sämtlichen Suchoperationen zu erhalten. Öffnen Sie zum Filtern pro Suche das Kontextmenü für die Ergebnisliste, und wählen Sie dann "Ergebnisse auflösen" aus.

**Unbestätigte ausblenden**

Blendet alle nicht bestätigten Elemente in den Ergebnissen von „Alle Verweise suchen“ aus. Wenn Sie die Option „Auflösen deaktiveren“ löschen, können Sie mit dieser Option unbestätigte Elemente in den Ergebnissen ausblenden.

**Markieren von Verweisen deaktivieren**

Bei Auswahl von Text werden standardmäßig alle Vorkommen desselben Texts im aktuellen Dokument hervorgehoben. Sie können dieses Feature deaktivieren, indem Sie **Hervorheben von Verweisen** auf **True** festlegen.

## <a name="text-editor"></a>Text-Editor

**Einschluss in geschweifte Klammern aktivieren**

Ist diese Option aktiviert, können Sie markierten Text in geschweifte Klammern setzen, indem Sie '{' im Text-Editor eingeben.

**Einschluss in runde Klammern aktivieren**

Ist diese Option aktiviert, können Sie markierten Text in runde Klammern setzen, indem Sie '(' im Text-Editor eingeben.

## <a name="see-also"></a>Siehe auch

- [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)
