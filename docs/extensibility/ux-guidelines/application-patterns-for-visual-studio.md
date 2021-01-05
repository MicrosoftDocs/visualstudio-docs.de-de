---
title: Anwendungs Muster für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Unterschied zwischen Dokument Fenstern, Tool Fenstern und nicht modalem Dialogfeldern, einschließlich der Fenster Verwendungs Muster für neue Features für Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709daa641e898f9d75f4bab340c8e5fd00d28a88
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716119"
---
# <a name="application-patterns-for-visual-studio"></a>Anwendungsmuster für Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Fenster Interaktionen

### <a name="overview"></a>Übersicht
Die zwei Hauptfenster Typen, die in Visual Studio verwendet werden, sind Dokument-Editoren und Tool Fenster. Selten, aber möglich sind große Dialogfelder. Obwohl Sie alle in der Shell nicht über das Modell verfügen, sind Ihre Muster grundlegend anders. In diesem Abschnitt wird der Unterschied zwischen Dokument Fenstern, Tool Fenstern und nicht modalem Dialogfeldern behandelt. Modale Dialogfeld Muster werden [in Dialog](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)Feldern behandelt.

### <a name="comparing-window-usage-patterns"></a>Vergleichen von Fenster Verwendungs Mustern
**Dokument Fenster** werden fast immer innerhalb des Dokument Brunnens angezeigt. Dadurch erhält der Dokument-Editor eine "Mittelstufe", um ergänzende Tool Fenster anzuordnen.

Ein **Tool Fenster** wird am häufigsten als separates, kleineres Fenster angezeigt, das auf den Rand der IDE reduziert wird. Dies kann sichtbar, ausgeblendet oder automatisch ausgeblendet sein. Manchmal werden Tool Fenster aber auch im Dokument angezeigt, indem die **Fenster/Docking-** Eigenschaft im Fenster ausgecheckt wird. Dies führt zu mehr Immobilien, aber auch zu einer allgemeinen Entwurfs Entscheidung: Wenn Sie versuchen, in Visual Studio zu integrieren, müssen Sie entscheiden, ob die Funktion ein Tool Fenster oder ein Dokument Fenster anzeigen soll.

Nicht **modaldialogfelder** werden in Visual Studio nicht empfohlen. Bei den meisten nicht modalen Dialogfeldern handelt es sich um unverankerte Tool Fenster, die auf diese Weise implementiert werden müssen. Nicht modaldialogfelder sind zulässig, wenn die Größe eines normalen Tool Fensters, das an der Seite der Shell angedockt ist, zu eingeschränkt wäre. Sie sind auch in Fällen zulässig, in denen der Benutzer das Dialogfeld wahrscheinlich auf einen sekundären Monitor verschieben würde.

Überlegen Sie genau, welcher Containertyp Sie benötigen. Allgemeine Überlegungen zum Verwendungs Muster für den Benutzeroberflächen Entwurf finden Sie in der folgenden Tabelle.

||Dokument Fenster|Tool Fenster|Nicht modalem Dialogfeld|
|-|---------------------|-----------------|---------------------|
| **Position** | Ist immer innerhalb des Dokument Brunnens positioniert und wird nicht um die Ränder der IDE Andocken. Sie kann "gezogen" werden, sodass Sie getrennt von der Hauptshell schwebt. | Wird in der Regel an den Rändern der IDE angedockt, kann jedoch so angepasst werden, dass Sie unverankert, automatisch ausgeblendet (gelöst) oder innerhalb des Dokument Brunnens angedockt ist.|Großes gleitendes Fenster, getrennt von der IDE. |
| **Commit-Modell** | *Verzögerter Commit*<br /><br /> Um die Daten in einem Dokument zu speichern, muss der Benutzer den Befehl " **&gt; Speichern**", " **Speichern** unter" oder " **Alle speichern** " ausgeben. In einem Dokument Fenster ist das Konzept der darin enthaltenen Daten "dirgebunden" und dann ein Commit für einen der Save-Befehle. Beim Schließen eines Dokument Fensters werden alle Inhalte entweder auf dem Datenträger gespeichert oder gehen verloren. | *Sofortiger Commit*<br /><br /> Es ist kein Speichermodell vorhanden. Für Inspektor-Tool Fenster, die beim Bearbeiten einer Datei behilflich sind, muss die Datei im aktiven Editor oder Designer geöffnet sein, und der Editor oder Designer besitzt den Speicher. | *Verzögerter oder sofortiger Commit*<br /><br /> In den meisten Fällen erfordert ein großes, nicht modalem Dialogfeld eine Aktion, mit der Änderungen ausgeführt werden können, und ermöglicht einen "Abbrechen"-Vorgang, der alle in der Dialog Sitzung vorgenommenen Änderungen zurückführt.  Dies unterscheidet ein nicht modalem Dialogfeld in einem Tool Fenster, in dem das Tool Fenster immer über ein sofortiges Commit-Modell verfügt. |
| **Sichtbarkeit** | *Öffnen/erstellen (Datei) und schließen*<br /><br /> Das Öffnen eines Dokument Fenster erfolgt durch das Öffnen eines vorhandenen Dokuments oder das Verwenden einer Vorlage zum Erstellen eines neuen Dokuments. Es ist kein "Open \<specific editor> "-Befehl vorhanden. | *Ausblenden und anzeigen*<br /><br /> Einzel Instanz-Tool Fenster können ausgeblendet oder angezeigt werden. Inhalt und Status im Tool Fenster bleiben erhalten, wenn Sie in der Ansicht oder im verborgenen angezeigt werden. Tool Fenster mit mehreren Instanzen können geschlossen und ausgeblendet werden. Wenn ein Tool Fenster mit mehreren Instanzen geschlossen wird, werden Inhalt und Zustand innerhalb des Tool Fensters verworfen. | *Gestartet von einem Befehl*<br /><br /> Dialoge werden von einem aufgabenbasierten Befehl aus gestartet. |
| **Verein** | *Mehrere Instanzen*<br /><br /> Mehrere Editoren können gleichzeitig geöffnet sein und verschiedene Dateien bearbeiten, während einige Editoren auch zulassen, dass dieselbe Datei in mehr als einem Editor geöffnet ist (mit dem **Fenster " &gt; Neues Fenster** ").<br /><br /> Ein einzelner Editor bearbeitet möglicherweise eine oder mehrere Dateien gleichzeitig (Projekt-Designer). | *Einzelne oder mehrere Instanzen*<br /><br /> Der Inhalt wird geändert, um den Kontext (wie im Eigenschaften Browser) widerzuspiegeln oder den Fokus/Kontext auf andere Fenster (Aufgabenliste Projektmappen-Explorer) zu verschieben.<br /><br /> Die Tool Fenster Single-Instance und MultiInstance müssen mit dem aktiven Dokument Fenster verknüpft werden, es sei denn, es gibt einen überzeugenden Grund, nicht zu. | *Einzel Instanz* |
| **Beispiele** | **Text-Editoren**, wie der Code-Editor<br /><br /> **Entwurfs** Oberflächen, wie z. b. ein Formular-Designer oder eine Modellierungs Oberfläche<br /><br /> **Steuern von Layouts ähnlich** wie beim Manifest-Designer | Der **Projektmappen-Explorer** stellt eine Projekt Mappe und Projekte in der Projekt Mappe bereit.<br /><br /> Der **Server-Explorer** bietet eine hierarchische Ansicht der Server und Datenverbindungen, die der Benutzer im Fenster öffnen möchte. Wenn Sie ein Objekt aus der Daten Bank Hierarchie öffnen, wie z. b. eine Abfrage, wird ein Dokument Fenster geöffnet, und der Benutzer kann die Abfrage bearbeiten.<br /><br /> Im Eigenschaften **Browser** werden Eigenschaften für das Objekt angezeigt, das entweder in einem Dokument Fenster oder in einem anderen Tool Fenster ausgewählt ist. Die Eigenschaften werden entweder in einer hierarchischen Rasteransicht oder in komplexen Dialogfeld ähnlichen Steuerelementen angezeigt, und der Benutzer kann die Werte für diese Eigenschaften festlegen. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Tool Fenster

### <a name="overview"></a>Übersicht
Tool Fenster unterstützen die Arbeit des Benutzers, der in Dokument Fenstern ausgeführt wird. Sie können verwendet werden, um eine Hierarchie anzuzeigen, die ein grundlegendes Stamm Objekt darstellt, das von Visual Studio bereitgestellt und bearbeitet werden kann.

Wenn Sie ein neues Tool Fenster in der IDE in Erwägung ziehen, sollten Autoren folgende Aktionen ausführen:

- Verwenden Sie Aufgaben geeignete, vorhandene Tool Fenster, und erstellen Sie keine neuen mit ähnlichen Funktionen. Neue Tool Fenster sollten nur erstellt werden, wenn Sie ein erheblich anderes "Tool" oder Funktionen bieten, die nicht in ein ähnliches Fenster integriert werden können, oder indem Sie ein vorhandenes Fenster in einen pivotierungs-Hub umwandeln.

- Verwenden Sie bei Bedarf eine Standard Befehlsleiste am oberen Rand des Tool Fensters.

- Stimmen Sie mit Mustern überein, die bereits in anderen Tool Fenstern für die Steuerelement Präsentation und die Tastaturnavigation vorhanden sind.

- Sie sollten mit der Darstellung von Steuerelementen in anderen Tool Fenstern konsistent sein.

- Automatisches sichtbar machen Dokument spezifischer Tool Fenster, wenn möglich, sodass Sie nur angezeigt werden, wenn das übergeordnete Dokument aktiviert ist.

- Stellen Sie sicher, dass Ihr Fensterinhalt über die Tastatur navigiert wird (unterstützen Sie Pfeiltasten).

#### <a name="tool-window-states"></a>Tool Fenster Zustände
Visual Studio-Tool Fenster haben unterschiedliche Zustände, von denen einige Benutzer aktiviert sind (z. b. die Funktion zum automatischen Ausblenden). Andere Zustände, wie z. b. automatisch sichtbar, ermöglichen Tool Fenstern das Anzeigen im richtigen Kontext und das ausblenden, wenn Sie nicht benötigt werden. Insgesamt sind fünf Tool Fenster Zustände vorhanden.

- **Angedockte/angeheftete** Tool Fenster können an jede der vier Seiten des Dokument Bereichs angefügt werden. Das Symbol "PushPin" wird in der Titelleiste des Tool Fensters angezeigt. Das Tool Fenster kann horizontal oder vertikal am Rand der Shell und anderen Tool Fenstern angedockt werden und kann auch mit Tabstopps verknüpft werden.

- **Automatisch ausgeblendete** Tool Fenster werden gelöst. Das Fenster kann sich aus der Sicht auslagern, wobei eine Registerkarte (mit dem Namen des Tool Fensters und dem dazugehörigen Symbol) am Rand des Dokument Bereichs angezeigt wird. Das Tool Fenster wird heraus bewegt, wenn ein Benutzer auf die Registerkarte zeigt.

- Automatisch **sichtbare** Tool Fenster werden automatisch angezeigt, wenn ein anderer Teil der Benutzeroberfläche, wie z. b. ein Editor, gestartet wird oder den Fokus erhält.

- Unverankerte **Tool Fenster** zeigen außerhalb der IDE. Dies ist nützlich für Konfigurationen mit mehreren Monitoren.

- **Dokument** Tool Fenster im Registerkarten Format können innerhalb des Dokument Brunnens angedockt werden. Dies ist nützlich für große Tool Fenster, wie z. b. die Objektkatalog, die mehr Immobilien benötigen, als an den Rändern des Frames Andocken zu können.

![Status für Toolfenster in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Status für Toolfenster in Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Einzel Instanz und mehrere Instanzen
Tool Fenster sind entweder eine Einzel Instanz oder eine mehrere Instanzen. Einige Einzel Instanz-Tool Fenster können dem aktiven Dokument Fenster zugeordnet werden, während das Tool Fenster mit mehreren Instanzen möglicherweise nicht. Tool Fenster mit mehreren Instanzen reagieren auf den **Fenster &gt; neuen Fenster** Befehl, indem Sie eine neue Instanz des Fensters erstellen. Die folgende Abbildung veranschaulicht ein Tool Fenster, das den Befehl Neues Fenster aktiviert, wenn eine Instanz des Fensters aktiv ist:

![Tool Fenster, das den Befehl "neuer Fenster" aktiviert, wenn eine Instanz des Fensters aktiv ist](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Tool Fenster, das den Befehl "neuer Fenster" aktiviert, wenn eine Instanz des Fensters aktiv ist

Einzel Instanz-Tool Fenster können ausgeblendet oder angezeigt werden, während Tool Fenster mit mehreren Instanzen geschlossen und ausgeblendet werden können. Alle Tool Fenster können angedockt, Tabstopps verknüpft, unverankert oder als untergeordnetes MDI-Fenster (Multiple-Document Interface) (ähnlich einem Dokument Fenster) festgelegt werden. Alle Tool Fenster sollten auf die entsprechenden Fenster Verwaltungs Befehle im Menü "Fenster" reagieren:

![Fenster Verwaltungs Befehle im Visual Studio-Menü "Fenster"](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Fenster Verwaltungs Befehle im Visual Studio-Menü "Fenster"

#### <a name="document-specific-tool-windows"></a>Dokument spezifische Tool Fenster
Einige Tool Fenster können basierend auf einem bestimmten Dokumenttyp geändert werden. Diese Windows werden fortlaufend aktualisiert, um die Funktionalität für das aktive Dokument Fenster in der IDE widerzuspiegeln.

Beispiele für Tool Fenster, deren Inhalte so geändert werden, dass Sie den ausgewählten Editor widerspiegeln, sind die Toolbox und die Dokument Gliederung. Diese Fenster zeigen ein Wasserzeichen an, wenn ein Editor den Fokus besitzt, der keinen Kontext für das Fenster bietet.

#### <a name="navigable-list-tool-windows"></a>Fenster mit navigierbaren Listen Tools
In einigen Tool Fenstern wird eine Liste der navigierbaren Elemente angezeigt, mit denen der Benutzer interagieren kann. In dieser Art von Fenster sollte für das aktuelle Element in der Liste immer Feedback vorhanden sein, auch wenn das Fenster inaktiv ist. Die Liste sollte auf die Befehle **gotonextlocation** und **gotoprevlocation** Antworten, indem auch das aktuell ausgewählte Element im Fenster geändert wird.

Beispiele für Navigier Bare Listen Tool Fenster sind die Projektmappen-Explorer und das Fenster Suchergebnisse.

### <a name="tool-window-types"></a>Tool Fenstertypen

#### <a name="common-tool-windows-and-their-functions"></a>Allgemeine Tool Fenster und ihre Funktionen

**Hierarchische Tool Fenster**

| Tool Fenster | Funktion |
| --- | --- |
| Projektmappen-Explorer | Eine hierarchische Struktur, die eine Liste von Dokumenten anzeigt, die in Projekten, verschiedenen Dateien und Projektmappenelementen enthalten sind. Die Anzeige der Elemente in Projekten wird durch das Paket definiert, das den Projekttyp besitzt (z. b. Verweis-, Verzeichnis-oder Typen mit gemischtem Modus). |
| Klassenansicht | Eine hierarchische Struktur der Klassen und verschiedener Elemente im Workingset von Dokumenten, unabhängig von den Dateien selbst. |
| Server-Explorer | Eine hierarchische Struktur, in der alle Server und Datenverbindungen in der Lösung angezeigt werden. |
| Dokumentgliederung | Die hierarchische Struktur des aktiven Dokuments. |

**Raster Tool Fenster**

| Tool Fenster | Funktion |
| --- | --- |
| Eigenschaften | Ein Raster, das eine Liste von Eigenschaften für das ausgewählte Objekt sowie Wert-Picker zum Bearbeiten dieser Eigenschaften anzeigt. |
| Aufgabenliste | Ein Raster, das es dem Benutzer ermöglicht, Aufgaben und Kommentare zu erstellen, zu bearbeiten und zu löschen. |

**Inhalts Tool Fenster**

| Tool Fenster | Funktion |
| --- | --- |
| Hilfe | Ein Fenster, in dem Benutzer auf verschiedene Methoden zum Abrufen von Hilfe zugreifen können. Videos zu MSDN-Foren. |
| Dynamische Hilfe | Ein Tool Fenster, in dem Links zu Hilfe Themen angezeigt werden, die für die aktuelle Auswahl gelten. |
| Objektkatalog | Ein zweispaltige Frameset mit einer Liste von hierarchischen Objekt Komponenten im linken Bereich und den Eigenschaften und Methoden des Objekts in der rechten Spalte. |

**Dialog Tool Fenster**

| Tool Fenster | Funktion |
| --- | --- |
| Suchen | Ein Dialogfeld, in dem der Benutzer verschiedene Dateien in der Projekt Mappe suchen und in diesen suchen und ersetzen kann. |
| Erweiterte Suche | Ein Dialogfeld, in dem der Benutzer verschiedene Dateien in der Projekt Mappe suchen und in diesen suchen und ersetzen kann. |

**Weitere Tool Fenster**

::: moniker range="vs-2017"

| Tool Fenster | Funktion |
| --- | --- |
| Werkzeugkasten | Das Tool Fenster, das zum Speichern von Elementen verwendet wird, die auf Entwurfs Oberflächen abgelegt werden, und stellt eine konsistente Zieh Quelle für alle Designer bereit. |
| Startseite | Das Portal des Benutzers zu Visual Studio mit Zugriff auf Feeds von Neuigkeiten in den Entwicklern, Visual Studio-Hilfe und zuletzt geöffnete Projekte. Benutzer können auch benutzerdefinierte Startseiten erstellen, indem Sie die Datei "StartPage. XAML" aus dem Verzeichnis "Common7\IDE\StartPages \" Visual Studio Program Files" in den StartPages-Ordner im Verzeichnis "Visual Studio-Dokumente" Kopieren und dann entweder die XAML-Datei in Visual Studio oder in einem anderen Code-Editor öffnen. |

::: moniker-end

::: moniker range=">=vs-2019"

| Tool Fenster | Funktion |
| --- | --- |
| Werkzeugkasten | Das Tool Fenster, das zum Speichern von Elementen verwendet wird, die auf Entwurfs Oberflächen abgelegt werden, und stellt eine konsistente Zieh Quelle für alle Designer bereit. |

::: moniker-end

**Debugger-Tool Fenster**

| Tool Fenster | Funktion |
| --- | --- |
| Autos ||
| Unmittelbar ||
| Ausgabe | Das Ausgabefenster kann immer dann verwendet werden, wenn Sie Text Ereignisse oder den zu deklarierenden Status aufweisen. |
| Arbeitsspeicher ||
| Haltepunkte ||
| Wird ausgeführt ||
| Dokumente ||
| Aufrufliste ||
| Locals ||
| Uhren ||
| Disassemblierung ||
| Register ||
| Threads ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Konventionen für Dokument-Editor

### <a name="document-interactions"></a>Dokument Interaktionen
Der "Dokument-Grund" ist der größte Raum innerhalb der IDE und ist der Benutzer, der sich in der Regel auf seine Aufmerksamkeit konzentriert hat, um die Aufgaben durchzuführen, die durch ergänzende Tool Fenster unterstützt werden. Dokument-Editoren stellen die grundlegenden Arbeitseinheiten dar, die der Benutzer in Visual Studio öffnet und speichert. Sie behalten einen starken Eindruck von der Auswahl, der an Projektmappen-Explorer oder andere aktive Hierarchie Fenster gebunden ist. Der Benutzer sollte auf eines dieser Hierarchie Fenster verweisen können und wissen, wo das Dokument enthalten ist, und seine Beziehung zu der Projekt Mappe, dem Projekt oder einem anderen Stamm Objekt, das von einem Visual Studio-Paket bereitgestellt wird.

Die Bearbeitung von Dokumenten erfordert eine konsistente Benutzer Leistung. Wählen Sie eine Dokument Ansichts Strategie aus, die den Benutzer Aufgaben zum Bearbeiten dieses Dokument Typs am besten entspricht, anstatt sich bei der Fensterverwaltung und beim Suchen von Befehlen auf die jeweilige Aufgabe zu konzentrieren.

#### <a name="common-interactions-for-the-document-well"></a>Allgemeine Interaktionen für die Dokument Quelle

- Behalten Sie ein konsistentes Interaktionsmodell in der allgemeinen **neuen Datei** bei, und öffnen Sie die **Datei** Erfahrung.

- Aktualisieren Sie verwandte Funktionen in verwandten Fenstern und Menüs, wenn das Dokument Fenster geöffnet wird.

- Menübefehle sind entsprechend in gängige Menüs wie **Bearbeitungs**-, **Formatierungs**-und **Anzeige** Menüs integriert. Wenn eine beträchtliche Menge spezieller Befehle verfügbar ist, kann ein neues Menü erstellt werden. Dieses neue Menü sollte nur sichtbar sein, wenn das Dokument den Fokus besitzt.

- Eine eingebettete Symbolleiste kann am oberen Rand des Editors platziert werden. Dies ist vorzuziehen, wenn eine separate Symbolleiste angezeigt wird, die außerhalb des Editors angezeigt wird.

- Behalten Sie immer eine Auswahl im Fenster Projektmappen-Explorer oder einer ähnlichen aktiven Hierarchie bei.

- Durch Doppelklicken auf ein Dokument in der Projektmappen-Explorer sollte die gleiche Aktion wie **geöffnet** ausgeführt werden.

- Wenn mehr als ein Editor für einen Dokumenttyp verwendet werden kann, muss der Benutzer in der Lage sein, die Standardaktion für einen bestimmten Dokumenttyp mithilfe des Dialog Felds **Öffnen mit** zu überschreiben oder zurückzusetzen. Klicken Sie dazu mit der rechten Maustaste auf die Datei, und wählen Sie im Kontextmenü **Öffnen mit** aus.

- Erstellen Sie keinen Assistenten in einem Dokument.

### <a name="user-expectations-for-specific-document-types"></a>Erwartungen von Benutzern für bestimmte Dokumenttypen
Es gibt mehrere verschiedene grundlegende Typen von Dokument-Editoren, die jeweils über eine Reihe von Interaktionen verfügen, die mit anderen Typen desselben Typs konsistent sind.

- **Text basierter Editor: Code-** Editor, Protokolldateien

- **Entwurfs Oberfläche:** WPF-Formular-Designer, Windows Forms

- **Dialog Feld Stil-Editor:** Manifest-Designer, Projekteigenschaften

- **Modell-Designer:** Workflow-Designer, Code Map, Architektur Diagramm, Fortschritt

Es gibt auch mehrere nicht-Editor-Typen, die das Dokument gut verwenden. Obwohl Sie Dokumente nicht selbst bearbeiten, müssen Sie die Standard Interaktionen für Dokument Fenster befolgen.

- **Berichte:** IntelliTrace-Bericht, Hyper-V-Bericht, Profiler-Bericht

- **Dashboard:** Diagnosehub

#### <a name="text-based-editors"></a>Text basierte Editoren

- Das Dokument ist am Vorschau Registerkarten Modell beteiligt und ermöglicht die Vorschau des Dokuments, ohne es zu öffnen.

- Die Struktur des Dokuments kann in einem begleitenden Tool Fenster dargestellt werden, z. b. in einer Dokument Gliederung.

- IntelliSense verhält sich ggf. konsistent mit anderen Code-Editoren.

- Popups oder hilfsbenutzer Oberflächen folgen ähnlichen Stilen und Mustern für eine vorhandene ähnliche Benutzeroberfläche, z. b. codelta ens.

- Meldungen im Zusammenhang mit dem Dokument Status werden in einem Info Leiste-Steuerelement am oberen Rand des Dokuments oder in der Statusleiste angezeigt.

- Der Benutzer muss in der Lage sein, die Darstellung von Schriftarten und Farben mithilfe der Options Seite Extras **>** , entweder der Seite freigegebene Schriftarten und Farben oder einer spezifischen Seite für den Editor.

#### <a name="design-surfaces"></a>Entwurfs Oberflächen

- Ein leerer Designer sollte über ein Wasserzeichen auf der Oberfläche verfügen, das angibt, wie der Einstieg gestartet wird.

- Optionen für die Ansichts Umstellung folgen vorhandenen Mustern, wie z. b. Doppelklicken, um einen Code-Editor zu öffnen, oder Registerkarten im Dokument Fenster, die die Interaktion mit beiden Bereichen ermöglichen.

- Das Hinzufügen von Elementen zur Entwurfs Oberfläche sollte über die Toolbox erfolgen, es sei denn, es ist ein sehr spezifisches Tool Fenster erforderlich.

- Für Elemente auf der Oberfläche wird ein konsistentes Auswahl Modell befolgt.

- Eingebettete Symbolleisten enthalten nur Dokument spezifische Befehle und keine allgemeinen Befehle wie " **Save**".

#### <a name="dialog-style-editors"></a>Editor für Dialog Feld Stil

- Das Steuerelement Layout sollte den normalen Dialogfeld Layout-Konventionen entsprechen.

- Registerkarten innerhalb des Editors sollten nicht mit der Darstellung der Dokument Registerkarten identisch sein. Sie sollten einem der beiden zulässigen inneren Registerkarten Stile entsprechen.

- Benutzer müssen in der Lage sein, mit den Steuerelementen nur über die Tastatur zu interagieren. entweder durch Aktivieren des Editors und durch Tabstopps durch Steuerelemente oder durch Verwenden von Standard-mnetmonics.

- Der Designer sollte das gängige Speichermodell verwenden. Auf der Oberfläche sollten keine allgemeinen Speicher-oder Commit-Schaltflächen platziert werden, auch wenn andere Schaltflächen geeignet sind.

#### <a name="model-designers"></a>Modell-Designer

- Ein leerer Designer sollte über ein Wasserzeichen auf der Oberfläche verfügen, das angibt, wie der Einstieg gestartet wird.

- Das Hinzufügen von Elementen zur Entwurfs Oberfläche sollte über die Toolbox erfolgen.

- Für Elemente auf der Oberfläche wird ein konsistentes Auswahl Modell befolgt.

- Eingebettete Symbolleisten enthalten nur Dokument spezifische Befehle und keine allgemeinen Befehle wie " **Save**".

- Eine Legende kann auf der-Oberfläche angezeigt werden, entweder als Hinweis oder als Wasserzeichen.

- Der Benutzer muss in der Lage sein, die Darstellung der Schriftarten/Farben auf der Seite Extras **> Optionen** zu ändern, entweder der Seite freigegebene Schriftarten und Farben oder einer spezifischen Seite für den Editor.

#### <a name="reports"></a>Berichte

- Berichte sind in der Regel nur Informationen, die nicht am Speichermodell beteiligt sind. Sie können jedoch Interaktionen wie Links zu anderen relevanten Informationen oder Abschnitten enthalten, die erweitert und reduziert werden.

- Die meisten Befehle auf der Oberfläche sollten Hyperlinks und keine Schaltflächen sein.

- Das Layout sollte einen Header enthalten und die Standardrichtlinien für das Berichtslayout einhalten.

#### <a name="dashboards"></a>Dashboards

- Dashboards haben nicht selbst ein Interaktionsmodell, sondern dienen als Mittel für eine Vielzahl anderer Tools.

- Sie sind nicht Teil des Speicher Modells.

- Benutzer müssen in der Lage sein, mit den Steuerelementen nur über die Tastatur zu interagieren, indem Sie entweder den Editor aktivieren und durch Steuerelemente oder mithilfe von Standard-mnetmonics wechseln.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Gespräche

### <a name="introduction"></a>Einführung
Dialogfelder in Visual Studio sollten in der Regel eine einzelne Einheit der Arbeit des Benutzers unterstützen und dann verworfen werden.

Wenn Sie festgestellt haben, dass Sie ein Dialogfeld benötigen, stehen Ihnen drei Optionen zur Verfügung:

1. Integrieren Sie Ihre Funktionen in eine der freigegebenen Dialogfelder in Visual Studio.

2. Erstellen Sie ein eigenes Dialogfeld mit einem Muster, das in einem vorhandenen ähnlichen Dialogfeld gefunden wurde.

3. Erstellen Sie ein neues Dialogfeld, und befolgen Sie die Anweisungen für Interaktion und Layout

In diesem Abschnitt wird beschrieben, wie Sie das richtige Dialogfeld Muster innerhalb von Visual Studio-Workflows und die allgemeinen Konventionen für den Dialog Entwurf auswählen.

### <a name="themes"></a>Designs
Dialogfelder in Visual Studio folgen einem von zwei grundlegenden Stilen:

#### <a name="standard-unthemed"></a>Standard (ohne Design)
Bei den meisten Dialogfeldern handelt es sich um Standard Dialogfelder für das Hilfsprogramm. Verwenden Sie keine neuvorlagen für allgemeine Steuerelemente, oder versuchen Sie, stilisierte "moderne" Schaltflächen oder Steuerelemente zu erstellen. Steuerelemente und die Chrome-Darstellung folgen den [standardmäßigen Windows-Desktop Interaktions Richtlinien für Dialogfelder](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Artikeln
Die speziellen "Signature"-Dialogfelder können mit Designs versehen werden. Themen Dialogfelder weisen eine unterschiedliche Darstellung auf, die auch über einige besondere Interaktionsmuster verfügt, die dem Stil zugeordnet sind. Design des Dialog Felds nur dann, wenn es die folgenden Anforderungen erfüllt:

- Das Dialogfeld ist eine gängige Benutzererfahrung, die häufig oder von vielen Benutzern (z. b. dem Dialogfeld " **Neues Projekt** ") angezeigt und verwendet wird.

- Das Dialogfeld enthält wichtige Produktmarken Elemente (z. b. das Dialogfeld " **Kontoeinstellungen** ").

- Das Dialogfeld wird als integraler Bestandteil eines größeren Flows angezeigt, der andere Themen Dialogfelder enthält (z. b. das Dialogfeld " **verbundenen Dienst hinzufügen** ").

- Das Dialogfeld ist ein wichtiger Bestandteil einer benutzerfreundlichen Rolle zum herauf Stufen oder unterscheiden einer Produktversion.

Wenn Sie ein Design Dialogfeld erstellen, verwenden Sie die entsprechenden Umgebungs Farben, und folgen Sie den richtigen Layout-und Interaktionsmustern. (Siehe [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Dialog Feld Entwurf
Gut entworfene Dialoge berücksichtigen die folgenden Elemente:

- Die unterstützte Benutzer Aufgabe

- Der Text Stil, die Sprache und die Terminologie des Dialog Felds

- Auswahl von Steuerelementen und Benutzeroberflächen Konventionen

- Spezifikation des visuellen Layouts und Steuerelement Ausrichtung

- Tastaturzugriff

#### <a name="content-organization"></a>Inhalts Organisation
Beachten Sie die Unterschiede zwischen diesen grundlegenden Dialogfeldern:

- [Einfache Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) stellen Steuerelemente in einem einzelnen modalen Fenster dar. Die Präsentation kann Variationen komplexer Steuerelement Muster enthalten, einschließlich einer Feldauswahl oder einer Symbolleiste.

- Mithilfe von [geschichteten Dialog](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) Feldern wird die Bildschirmfläche optimal genutzt, wenn eine einzelne Benutzeroberfläche mehrere Gruppen von Steuerelementen umfasst. Die Gruppierungen des Dialog Felds sind durch Registerkarten-Steuerelemente, Navigations Listen-Steuerelemente oder Schaltflächen "geschichtet", sodass der Benutzer auswählen kann, welche Gruppierung zu einem beliebigen Zeitpunkt angezeigt werden soll.

- [Assistenten](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sind hilfreich, um den Benutzer durch eine logische Abfolge von Schritten für den Abschluss einer Aufgabe zu leiten. Eine Reihe von Optionen wird in sequenziellen Bereichen angeboten, in denen manchmal verschiedene Workflows ("Branches") eingeführt werden, die von einer im vorherigen Panel getroffenen Auswahl abhängig sind.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Einfache Dialoge
Ein einfaches Dialogfeld ist eine Darstellung von Steuerelementen in einem einzelnen modalen Fenster. Diese Präsentation kann Variationen komplexer Steuerelement Muster wie z. b. eine Feldauswahl enthalten. Befolgen Sie für einfache Dialoge das allgemeine Standardlayout sowie jedes bestimmte Layout, das für komplexe Steuerelement Gruppierungen erforderlich ist.

![>Schlüssel für einen starken Namen erstellen ist ein Beispiel für ein einfaches Dialogfeld in Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Schlüssel für einen starken Namen erstellen ist ein Beispiel für ein einfaches Dialogfeld in Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Geschichtete Dialogfelder
Zu den geschichteten Dialogfeldern zählen Registerkarten, Dashboards und eingebettete Strukturen. Sie werden verwendet, um die Immobilien zu maximieren, wenn mehrere Gruppen von Steuerelementen in einer einzigen Benutzeroberfläche angeboten werden. Die Gruppierungen sind geschichtet, sodass der Benutzer auswählen kann, welche Gruppierung zu einem beliebigen Zeitpunkt angezeigt werden soll.

Im einfachsten Fall ist der Mechanismus zum Wechseln zwischen Gruppierungen ein Registerkarten-Steuerelement. Es stehen mehrere Alternativen zur Verfügung. Weitere Informationen zum Auswählen des am besten geeigneten Stils finden Sie unter priorisieren und Schichten.

Das **&gt; options** Dialogfeld Extras ist ein Beispiel für einen geschichteten Dialog mithilfe einer eingebetteten Struktur:

![Tools > Optionen ist ein Beispiel für ein geschichtetes Dialogfeld in Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Tools > Optionen ist ein Beispiel für ein geschichtetes Dialogfeld in Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> The
Assistenten sind hilfreich, um den Benutzer durch eine logische Abfolge von Schritten beim Abschluss einer Aufgabe zu leiten. Eine Reihe von Optionen wird in sequenziellen Bereichen angeboten, und der Benutzer muss die einzelnen Schritte fortsetzen, bevor er mit der nächsten fortfahren kann. Nachdem ausreichend Standardwerte verfügbar sind, ist die Schaltfläche **Fertig** stellen aktiviert.

 Modale Assistenten werden für Aufgaben verwendet, die Folgendes ausführen:

- Enthalten Verzweigungen, in denen je nach Benutzer Auswahl verschiedene Pfade angeboten werden.

- Enthalten Abhängigkeiten zwischen den Schritten, bei denen nachfolgende Schritte von Benutzereingaben aus den vorangehenden Schritten abhängig sind.

- Ausreichend komplex ist, dass die Benutzeroberfläche verwendet werden sollte, um die angebotenen Optionen und die möglichen Ergebnisse in jedem Schritt zu erläutern.

- Sind transaktional und erfordern eine Reihe von Schritten, die vollständig abgeschlossen werden müssen, bevor für Änderungen ein Commit ausgeführt wird.

### <a name="common-conventions"></a>Allgemeine Konventionen
Um ein optimales Design und Funktionen mit den Dialogfeldern zu erzielen, befolgen Sie die folgenden Konventionen für Dialog Größe, Position, Standards, Steuerelement Konfiguration und-Ausrichtung, UI-Text, Titelleisten, Steuerungs Schaltflächen und Tastenkombinationen.

Informationen zu layoutspezifischen Richtlinien finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Size
Dialoge sollten in eine Auflösung von mindestens 1024 x 768 passen, und die anfängliche Dialog Größe darf nicht länger als 900x700 Pixel sein. Die Größe von Dialogfeldern kann geändert werden, dies ist jedoch nicht zwingend erforderlich.

Es gibt zwei Empfehlungen für die Größe von Dialogfeldern mit Größenänderung:

1. Eine minimale Größe ist eine, die für das Dialogfeld definiert wird, das für die Steuerelement Gruppe ohne Clipping optimiert wird

2. Die Benutzer skalierte Größe wird von Sitzung zu Sitzung beibehalten. Wenn der Benutzer z. b. einen Dialog auf 150% skaliert, wird ein nachfolgende Start des Dialog Felds um 150% angezeigt.

#### <a name="position"></a>Position
Dialoge müssen beim ersten Start in der IDE zentriert angezeigt werden. Die letzte Position von Dialogfeldern, deren Größe nicht geändert werden kann, muss nicht persistent sein, sodass Sie bei nachfolgenden Starts zentriert angezeigt werden.

Für in der Größe zu verwendende Dialoge sollte die Größe bei nachfolgenden Starts beibehalten werden. Für modale Dialogfelder, die in der Größe geändert werden können, ist die Position nicht erforderlich. Wenn Sie in der IDE zentriert angezeigt werden, wird verhindert, dass das Dialogfeld in einer unvorhersehbaren oder nicht verwendbaren Position angezeigt wird, wenn sich die Anzeige Konfiguration des Benutzers geändert hat.

Für nicht modale Dialogfelder, die neu positioniert werden können, sollte die Position des Benutzers bei nachfolgenden Starts beibehalten werden, da das Dialogfeld häufig als integraler Bestandteil eines größeren Workflows verwendet werden kann.

Wenn Dialoge andere Dialogfelder erzeugen müssen, sollte das oberste Dialogfeld nach rechts und von der übergeordneten Seite kaskadiert werden, sodass es für den Benutzer offensichtlich ist, dass Sie zu einem neuen Ort navigiert sind.

#### <a name="modality"></a>Modalität
Das modale bedeutet, dass Benutzer den Dialog vor dem Fortsetzen des Dialogs beenden oder abbrechen müssen. Da Modale Dialoge den Benutzer daran hindern, mit anderen Teilen der Umgebung zu interagieren, sollte der Task Ablauf ihrer Funktion diese so sparsam wie möglich verwenden. Wenn ein modaler Vorgang erforderlich ist, enthält Visual Studio eine Reihe von freigegebenen Dialogfeldern, in die Sie Ihre Funktionen integrieren können. Wenn Sie ein neues Dialogfeld erstellen müssen, befolgen Sie das Interaktionsmuster eines vorhandenen Dialog Felds mit ähnlicher Funktionalität.

Wenn Benutzer gleichzeitig zwei Aktivitäten ausführen müssen, wie z. b. **Suchen** und **ersetzen** beim Schreiben von neuem Code, sollte das Dialogfeld unmodelliert sein, damit der Benutzer problemlos zwischen diesen Aktivitäten wechseln kann. Visual Studio verwendet im allgemeinen Tool Fenster für diese Art von Editor-unterstützender verknüpfter Aufgabe.

#### <a name="control-configuration"></a>Steuerelement Konfiguration
Sie müssen mit vorhandenen Steuerelement Konfigurationen konsistent sein, die das gleiche in Visual Studio erreichen.

#### <a name="title-bars"></a>Titelleisten

- Der Text in der Titelleiste muss den Namen des Befehls widerspiegeln, der ihn gestartet hat.

- In Dialog Titelleisten darf kein Symbol verwendet werden. Verwenden Sie in Fällen, in denen das System eine solche benötigt, das Visual Studio-Logo.

- Dialogfelder dürfen keine Schaltflächen zum minimieren oder maximieren aufweisen.

- Hilfe Schaltflächen in der Titelleiste sind veraltet. Fügen Sie Sie nicht zu neuen Dialogfeldern hinzu. Wenn Sie vorhanden sind, sollten Sie ein Hilfethema starten, das konzeptionell für die Aufgabe relevant ist.

  ![Richtlinien Spezifikationen für Titelleisten in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Richtlinien Spezifikationen für Titelleisten in Visual Studio-Dialogfeldern

#### <a name="control-buttons"></a>Steuerungs Schaltflächen
Im Allgemeinen sollten die Schaltflächen " **OK**", " **Abbrechen**" und " **Hilfe** " in der unteren rechten Ecke des Dialog Felds horizontal angeordnet werden. Der Alternative vertikale Stapel ist zulässig, wenn ein Dialogfeld am unteren Rand des Dialog Felds mehrere weitere Schaltflächen enthält, die visuelle Verwirrung mit den Schaltflächen des Steuer Elements darstellen.

![Akzeptable Konfigurationen für Steuerelement Schaltflächen in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Akzeptable Konfigurationen für Steuerelement Schaltflächen in Visual Studio-Dialogfeldern

Das Dialogfeld muss eine Standard-Steuerelement Schaltfläche enthalten. Zum Ermitteln des optimalen Befehls, der als Standard verwendet werden soll, wählen Sie eine der folgenden Optionen aus (in Rangfolge aufgelistet):

- Wählen Sie den sichersten und sichersten Befehl als Standard aus. Dies bedeutet, dass Sie den Befehl wahrscheinlich vermeiden, Datenverluste zu verhindern und unbeabsichtigten System Zugriff zu vermeiden.

- Wenn Datenverlust und-Sicherheit keine Faktoren sind, wählen Sie den Standardbefehl auf der Grundlage der praktische Möglichkeit aus. Wenn Sie den wahrscheinlichsten Befehl als Standardbefehl einschließen, wird der Workflow des Benutzers verbessert, wenn der Dialog häufige oder wiederkehrende Aufgaben unterstützt.

Vermeiden Sie die Auswahl einer dauerhaft destruktiven Aktion für den Standardbefehl. Wenn ein solcher Befehl vorhanden ist, wählen Sie stattdessen einen sichereren Befehl als Standard aus.

#### <a name="access-keys"></a>Zugriffstasten
Verwenden Sie keine Zugriffsschlüssel für die Schaltflächen **OK**, **Abbrechen** oder **Hilfe** . Diese Schaltflächen werden standardmäßig Tastenkombinationen zugeordnet:

| Schaltflächenname | Tastenkombinationen |
| --- | --- |
| OK | EINGABETASTE |
| Abbrechen | ESC |
| Hilfe | F1 |

#### <a name="imagery"></a>DN
Verwenden Sie Bilder in Dialogfeldern sparsam. Verwenden Sie keine großen Symbole in Dialogfeldern, sondern nur, um Speicherplatz zu verwenden. Verwenden Sie Bilder nur dann, wenn Sie ein wichtiger Bestandteil der Übermittlung der Nachricht an den Benutzer sind, wie z. b. Warn Symbole oder Status Animationen.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Priorisieren und Schichten

#### <a name="prioritizing-your-ui"></a>Priorisieren der Benutzeroberfläche
Möglicherweise ist es notwendig, bestimmte Elemente der Benutzeroberfläche in den Vordergrund zu bringen und erweiterte Verhalten und Optionen (einschließlich undurchsichtiger Befehle) in Dialogfeldern zu platzieren. Bringen Sie häufig verwendete Funktionen in den Vordergrund, indem Sie Platz dafür schaffen, und wenn Sie Sie standardmäßig in der Benutzeroberfläche mit einer Text Bezeichnung sichtbar machen, wenn das Dialogfeld angezeigt wird.

#### <a name="layering-your-ui"></a>Schichten Ihrer Benutzeroberfläche
Wenn Sie festgestellt haben, dass ein Dialogfeld erforderlich ist, aber die zugehörige Funktionalität, die Sie dem Benutzer präsentieren möchten, nicht mehr in einem einfachen Dialogfeld angezeigt werden kann, müssen Sie die Benutzeroberfläche auf eine Ebene überschreiten. Die gängigsten ebenenmethoden, die Visual Studio verwendet, sind Registerkarten und Konfigurationen oder Dashboards. In einigen Fällen sind Regionen, die erweitert und reduziert werden können, möglicherweise geeignet. Adaptive Benutzeroberfläche wird in Visual Studio in der Regel nicht empfohlen.

Es gibt vor-und Nachteile für verschiedene Methoden der ebenenschnittstelle durch Registerkarten ähnliche Steuerelemente. Überprüfen Sie die nachstehende Liste, um sicherzustellen, dass Sie ein ebenenverfahren auswählen, das für Ihre Situation geeignet ist.

##### <a name="tabbing"></a>Wechseln mit der Tabulatortaste

| Wechsel Mechanismus | Vorteile und geeignete Verwendung | Nachteile und ungeeignete Verwendung |
| --- | --- | --- |
| Registersteuerelement | Dialogseiten logisch in verknüpfte Sätze gruppieren<br /><br />Nützlich für weniger als fünf (oder die Anzahl der Registerkarten, die in einer Zeile über das Dialogfeld passen) Seiten verwandter Steuerelemente im Dialogfeld<br /><br />Registerkarten Bezeichnungen müssen kurz sein: ein oder zwei Wörter, mit denen der Inhalt leicht identifiziert werden kann<br /><br />Ein häufig verwendeter System Dialogstil<br /><br />Beispiel: **&gt; Element Eigenschaften des Datei-Explorers** | Beschreibende Kurzbezeichnungen können schwierig sein.<br /><br />Skalieren Sie im Allgemeinen nicht die letzten fünf Registerkarten in einem Dialog<br /><br />Ungeeignet, wenn Sie über zu viele Registerkarten für eine Zeile verfügen (verwenden Sie eine Alternative Schichttechnik)<br /><br />Nicht erweiterbar |
| Rand leisten Navigation | Einfaches Wechseln von Geräten, die mehr Kategorien als Registerkarten erfüllen können<br /><br />Flache Liste von Kategorien (keine Hierarchie)<br /><br />Dieser Ansatz ist erweiterbar.<br /><br />Beispiel: **anpassen... &gt; Befehl hinzufügen** | Keine gute Verwendung des horizontalen Raums, wenn weniger als drei Gruppen vorhanden sind<br /><br />Der Task eignet sich möglicherweise besser für eine Dropdown-Anwendung. |
| Baumsteuerelement | Ermöglicht unbegrenzte Kategorien<br /><br />Ermöglicht die Gruppierung und/oder die Hierarchie von Kategorien.<br /><br />Dieser Ansatz ist erweiterbar.<br /><br />Beispiel: **Tool &gt; Optionen** | Stark schastte Hierarchien können zu einem übermäßigen horizontalen Bildlauf führen<br /><br />Visual Studio verfügt über eine Vielzahl von Struktur Ansichten |
| Assistent | Hilft bei der Fertigstellung von Aufgaben, indem der Benutzer durch aufgabenbasierte, sequenzielle Schritte geleitet wird: der Assistent stellt eine allgemeine Aufgabe dar, und die einzelnen Bereiche stellen die Unteraufgaben dar, die zum Ausführen der Gesamtaufgabe erforderlich sind.<br /><br />Nützlich, wenn der Task die Benutzeroberflächen Grenzen überschreitet, als wenn der Benutzer andernfalls mehrere Editoren und Tool Fenster verwenden müsste, um die Aufgabe abzuschließen.<br /><br />Nützlich, wenn der Task Verzweigungen erfordert<br /><br />Nützlich, wenn der Task Abhängigkeiten zwischen den Schritten enthält<br /><br />Nützlich, wenn mehrere ähnliche Aufgaben mit einem Entscheidungs Verzweigungs Punkt in einem Dialog angezeigt werden können, um die Anzahl von unterschiedlichen ähnlichen Dialogfeldern zu verringern. | Ungeeignet für jeden Task, der keinen sequenziellen Workflow erfordert<br /><br />Benutzer können mit zu vielen Schritten überlastet und verwirrt werden.<br /><br />Die Assistenten verfügen über eine begrenzte Bildschirmfläche. |

##### <a name="hallways-or-dashboards"></a>Wege oder Dashboards
Bei den verschiedenen Dialogfeldern und Dashboards handelt es sich um Dialoge oder Bereiche, die als Startpunkte in anderen Dialogfeldern und Fenstern dienen. Der gut entworfene "Gang" zeigt sofort nur die gängigsten Optionen, Befehle und Einstellungen an, sodass der Benutzer häufig häufige Aufgaben ausführen kann. Genau wie ein realer Gang bietet gatewaymöglichkeiten für den Zugriff auf die dahinter liegenden Räume, hier wird die weniger häufig verwendete Benutzeroberfläche in separaten "Räumen" (oftmals in anderen Dialogfeldern) mit verwandten Funktionen gesammelt, auf die über den Hauptgang zugegriffen werden kann.

Alternativ ist eine Benutzeroberfläche, die alle verfügbaren Funktionen in einer einzelnen Sammlung bietet, anstatt die weniger häufig genutzte Funktionalität in separate Speicherorte umzugestalten, einfach ein Dashboard.

![Gang Konzept zum Bereitstellen zusätzlicher Benutzeroberflächen in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Gang Konzept zum Bereitstellen zusätzlicher Benutzeroberflächen in Outlook

##### <a name="adaptive-ui"></a>Adaptive UI
Die Anzeige oder das Ausblenden der Benutzeroberfläche basierend auf der Verwendung oder der selbst gemeldeten Benutzeroberfläche ist eine weitere Möglichkeit, die erforderliche Benutzeroberfläche beim Ausblenden anderer Teile darzustellen. Dies ist in Visual Studio nicht empfehlenswert, da die Algorithmen zur Entscheidung, wann die Benutzeroberfläche angezeigt oder ausgeblendet werden kann, knifflig sein können und die Regeln für einige Fälle immer falsch sind.

## <a name="projects"></a><a name="BKMK_Projects"></a> Kte

### <a name="projects-in-the-solution-explorer"></a>Projekte in der Projektmappen-Explorer
Die meisten Projekte werden als Verweis basiert, Verzeichnis basiert oder gemischt klassifiziert. Alle drei Projekttypen werden gleichzeitig in der Projektmappen-Explorer unterstützt. Der Stamm der Benutzererfahrung beim Arbeiten mit-Projekten findet in diesem Fenster statt. Obwohl es sich bei verschiedenen Projekt Knoten um Verweis-, Verzeichnis-oder gemischte typprojekte handelt, gibt es ein gängiges Interaktionsmuster, das als Ausgangspunkt angewendet werden sollte, bevor es in projektspezifische Benutzer Muster unterschieden wird.

Projekte sollten immer:

- Unterstützung der Möglichkeit zum Hinzufügen von Projekt Ordnern zum Organisieren von Projektinhalten

- Beibehalten eines konsistenten Modells für die Projekt Persistenz

Projekte sollten auch konsistente Interaktionsmodelle für Folgendes gewährleisten:

- Entfernen von Projekt Elementen

- Speichern von Dokumenten

- Bearbeiten von Projekteigenschaften

- Bearbeiten des Projekts in einer alternativen Ansicht

- Drag & Drop-Vorgänge

### <a name="drag-and-drop-interaction-model"></a>Interaktionsmodell für Drag & amp; Drop
Projekte werden in der Regel als Verweis basiert klassifiziert (in der Lage, nur Verweise auf Projekt Elemente im Speicher beizubehalten), Verzeichnis basiert (nur Projekt Elemente, die physisch in der Hierarchie eines Projekts gespeichert sind) oder gemischt (in der Lage, Verweise oder physische Elemente beizubehalten). Die IDE unternimmt alle drei Projekttypen gleichzeitig innerhalb der **Projektmappen-Explorer**.

Aus Drag & Drop-Sicht sollten die folgenden Eigenschaften für jeden Projekttyp innerhalb der **Projektmappen-Explorer** gelten:

- **Verweis basiertes Projekt:** Der wichtigste Punkt ist, dass das Projekt einen Verweis auf ein Element im Speicher durchläuft. Wenn ein Verweis basiertes Projekt als Quelle für einen Move-Vorgang fungiert, sollte nur der Verweis auf das Element aus dem Projekt entfernt werden. Das Element sollte nicht tatsächlich von der Festplatte gelöscht werden. Wenn ein Verweis basiertes Projekt als Ziel für einen verschiebe-oder Kopiervorgang fungiert, sollte es einen Verweis auf das ursprüngliche Quell Element hinzufügen, ohne eine private Kopie des Elements zu erstellen.

- **Verzeichnis basiertes Projekt:** Von einem Drag & Drop-Sicht wird das physische Element anstelle eines Verweises durch das Projekt gezogen. Wenn ein Verzeichnis basiertes Projekt als Quelle für einen Verschiebungs Vorgang fungiert, sollte das physische Element von der Festplatte gelöscht und aus dem Projekt entfernt werden. Wenn ein Verzeichnis basiertes Projekt als Ziel für einen verschiebe-oder Kopiervorgang fungiert, sollte es eine Kopie des Quell Elements an seinem Ziel Speicherort erstellen.

- **Projekt mit gemischtem Ziel:** Aus einer Drag & Drop-Sicht basiert das Verhalten dieses Projekt Typs auf der Art des gezogenen Elements (entweder ein Verweis auf ein Element im Speicher oder auf das Element selbst). Das richtige Verhalten für Verweise und physische Elemente werden oben beschrieben.

Wenn das **Projektmappen-Explorer** nur einen Projekttyp enthält, sind Drag & Drop-Vorgänge unkompliziert. Da jedes Projekt System in der Lage ist, ein eigenes Drag & Drop-Verhalten zu definieren, sollten bestimmte Richtlinien (basierend auf dem Drag & Drop-Verhalten von Windows-Explorer) befolgt werden, um eine vorhersagbare Benutzerfreundlichkeit zu gewährleisten:

- Ein unveränderter Zieh Vorgang im **Projektmappen-Explorer** (wenn weder STRG-Taste noch UMSCHALTTASTE gedrückt gehalten werden) sollte zu einem Verschiebungs Vorgang führen.

- Der Verschiebe Zieh Vorgang sollte auch zu einem Verschiebe Vorgang führen.

- Der STRG-Zieh Vorgang sollte zu einem Kopiervorgang führen.

- Verweis basierte und gemischte Projektsysteme unterstützen das Konzept des Hinzufügens eines Links (oder Verweises) zum Quell Element. Wenn diese Projekte das Ziel eines Drag & Drop-Vorgangs sind (wenn **STRG + UMSCHALT** gedrückt gehalten wird), sollte ein Verweis auf das Element, das dem Projekt hinzugefügt wird, entstehen.

Nicht alle Drag & Drop-Vorgänge sind in Kombinationen aus Verweis basierten, Verzeichnis basierten und gemischten Projekten sinnvoll. Vor allem ist es problematisch, eine Verschiebungs Operation zwischen einem Verzeichnis basierten Quell Projekt und einem Verweis basierten Ziel Projekt zuzulassen, da das Quellverzeichnis basierte Projekt das Quell Element nach Abschluss der Verschiebung löschen muss. Das Ziel Verweis basierte Projekt würde dann einen Verweis auf ein gelöschtes Element haben.

Es ist auch irreführend, einen Kopiervorgang zwischen diesen Typen von Projekten zuzulassen, da das Ziel Verweis basierte Projekt keine unabhängige Kopie des Quell Elements erstellen sollte. Analog dazu sollte das Ziehen von STRG + UMSCHALT auf ein Verzeichnis basiertes Ziel Projekt nicht zulässig sein, da Verweise von einem Verzeichnis basierten Projekt nicht persistent gespeichert werden können. In Fällen, in denen der Drag & Drop-Vorgang nicht unterstützt wird, sollte die IDE den Löschvorgang nicht zulassen und den Benutzer den No-Drop-Cursor anzeigen (siehe nachfolgende Tabelle).

Um Drag & Drop-Verhalten ordnungsgemäß zu implementieren, muss das Quell Projekt des Zieh Vorgangs seine Art an das Ziel Projekt übermitteln. (Ist beispielsweise Verweis-oder Verzeichnis basiert?) Diese Informationen werden durch das von der Quelle angebotene Zwischenablage Format angegeben. `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` Je nachdem, ob das Projekt Verweis basiert oder Verzeichnis basiert ist, wird als Quelle für einen Drag (oder Zwischenablage-Kopiervorgang) ein Projekt bereitstellen. Beide Formate verfügen über denselben Dateninhalt, der dem Windows-Format ähnelt, mit dem Unterschied `CF_HDROP` , dass die Liste der Zeichen folgen anstelle von Dateinamen eine doppelt `NULL` terminierte Liste von Zeichen folgen ist `Projref` (wie von oder nach Bedarf zurückgegeben `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` ).

Als Ziel eines Drop-Vorgangs (oder Zwischenablage Vorgangs) sollte ein Projekt sowohl `CF_VSREFPROJECTITEMS` als auch akzeptieren `CF_VSSTGPROJECTITEMS` , obwohl die genaue Behandlung des Drag & Drop-Vorgangs abhängig von der Art des Ziel Projekts und des Quell Projekts variiert. Das Quell Projekt deklariert seine Art, ob es `CF_VSREFPROJECTITEMS` oder bietet `CF_VSSTGPROJECTITEMS` . Das Ziel von Drop versteht seine eigene Natur und verfügt daher über ausreichend Informationen, um Entscheidungen zu treffen, ob eine Verschiebung, eine Kopie oder ein Link ausgeführt werden soll. Der Benutzer ändert auch, welcher Drag & Drop-Vorgang ausgeführt werden soll, indem er die Tasten STRG, UMSCHALT oder STRG und Umschalttaste gedrückt. Es ist wichtig, dass das Ablage Ziel ordnungsgemäß angibt, welcher Vorgang im Voraus in den `DragEnter` Methoden und ausgeführt wird `DragOver` . Der **Projektmappen-Explorer** weiß automatisch, ob das Quell Projekt und das Ziel Projekt das gleiche Projekt sind.

Das Ziehen von Projekt Elementen zwischen Instanzen von Visual Studio (z. b. von einer Instanz von devenv.exe zu einem anderen) wird nicht unterstützt. Der **Projektmappen-Explorer** wird dies ebenfalls direkt deaktivieren.

Der Benutzer sollte immer in der Lage sein, die Auswirkungen eines Drag & Drop-Vorgangs zu ermitteln, indem er ein Element auswählt, ihn an den Ziel Speicherort zieht und feststellt, welcher der folgenden Mauszeiger angezeigt wird, bevor das Element gelöscht wird:

| Mauszeiger | Get-Help | BESCHREIBUNG |
| :---: | --- | --- |
| ![Symbol „Keine Ablage“ für Maus](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Kein Drop | Das Element kann nicht am angegebenen Speicherort abgelegt werden. |
| ![Symbol "Kopieren" für Maus](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopieren | Das Element wird in den Ziel Speicherort kopiert. |
| ![Symbol "Verschieben" für Maus](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Move | Das Element wird an den Ziel Speicherort verschoben. |
| ![Symbol "Verweis hinzufügen" für Maus](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Hinzuzufügender Verweis | Dem Ziel Speicherort wird ein Verweis auf das ausgewählte Element hinzugefügt. |

#### <a name="reference-based-projects"></a>Verweis basierte Projekte
 In der folgenden Tabelle werden die Drag & amp; Drop-Vorgänge (sowie Ausschneide-, Kopier-und Einfügevorgänge) zusammengefasst, die basierend auf der Art des Quell Elements und der Modifizierertasten, die für referenzierte Ziel Projekte gedrückt wurden, ausgeführt werden sollen:

| Modifizierer | Category | Quell Element: Verweis/Link | Quell Element: physisches Element oder Dateisystem ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Kein Modifizierer | Aktion | Move | Link |
| Kein Modifizierer | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Fügt einen Verweis auf das ursprüngliche Element hinzu |
| Kein Modifizierer | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Behält das Original Element bei |
| Kein Modifizierer | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_LINK` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Umschalt + Ziehen | Aktion | Move | Kein Drop |
| Umschalt + Ziehen | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kein Drop |
| Umschalt + Ziehen | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Kein Drop |
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | Kein Drop |
| Strg + Drag | Aktion | Kopieren | Kein Drop |
| Strg + Drag | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kein Drop |
| Strg + Drag | `Source` | Behält den Verweis auf das ursprüngliche Element bei | Kein Drop |
| Strg + Drag | Ergebnis | `DROPEFFECT_COPY` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | Kein Drop |
| Strg + Umschalt + Drag | Aktion | Link | Link |
| Strg + Umschalt + Drag | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Fügt einen Verweis auf das ursprüngliche Element hinzu |
| Strg + Umschalt + Drag | `Source` | Behält den Verweis auf das ursprüngliche Element bei | Behält das Original Element bei |
| Strg + Umschalt + Drag | Ergebnis | `DROPEFFECT_LINK` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_LINK` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Strg + Umschalt + Drag | Hinweis | Identisch mit Drag & amp; Drop für Tastenkombinationen in Windows Explorer. ||
| Ausschneiden/Einfügen | Aktion | Move | Link |
| Ausschneiden/Einfügen | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Fügt einen Verweis auf das ursprüngliche Element hinzu |
| Ausschneiden/Einfügen | `Source` | Behält den Verweis auf das ursprüngliche Element bei|Behält das Original Element bei |
| Ausschneiden/Einfügen | Ergebnis | Das Element bleibt am ursprünglichen Speicherort im Speicher. | Das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Kopieren/Einfügen | Aktion | Kopieren | Link |
| Kopieren/Einfügen | `Source` | Fügt einen Verweis auf das ursprüngliche Element hinzu | Fügt einen Verweis auf das ursprüngliche Element hinzu |
| Kopieren/Einfügen | Ergebnis | Behält den Verweis auf das ursprüngliche Element bei | Behält das Original Element bei |
| Kopieren/Einfügen | Aktion | Das Element bleibt am ursprünglichen Speicherort im Speicher. | Das Element bleibt am ursprünglichen Speicherort im Speicher. |

#### <a name="directory-based-projects"></a>Verzeichnis basierte Projekte
In der folgenden Tabelle werden die Drag & amp; Drop-Vorgänge (sowie Ausschneide-, Kopier-und Einfügevorgänge) zusammengefasst, die basierend auf der Art des Quell Elements und der Modifizierertasten, die für Verzeichnis basierte Ziel Projekte gedrückt wurden, ausgeführt werden sollen:

| Modifizierer | Category | Quell Element: Verweis/Link | Quell Element: physisches Element oder Dateisystem ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Kein Modifizierer | Aktion | Move | Move |
| Kein Modifizierer | Ziel | Kopiert das Element an den Zielort. | Kopiert das Element an den Zielort. |
| Kein Modifizierer | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Löscht den Verweis auf das ursprüngliche Element. |
| Umschalt + Ziehen | Aktion | Move | Move |
| Umschalt + Ziehen | Ziel | Kopiert das Element an den Zielort. | Kopiert das Element an den Zielort. |
| Umschalt + Ziehen | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Löscht das Element am ursprünglichen Speicherort. |
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Strg + Drag | Aktion | Kopieren | Kopieren |
| Strg + Drag | Ziel | Kopiert das Element an den Zielort. | Kopiert das Element an den Zielort. |
| Strg + Drag | `Source` | Behält den Verweis auf das ursprüngliche Element bei | Behält den Verweis auf das ursprüngliche Element bei |
| Strg + Drag | Ergebnis | `DROPEFFECT_COPY` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_COPY` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Strg + Umschalt + Drag | | Kein Drop | Kein Drop |
| Ausschneiden/Einfügen | Aktion | Move | Move |
| Ausschneiden/Einfügen | Ziel | Kopiert das Element an den Zielort. | Kopiert das Element an den Zielort. |
| Ausschneiden/Einfügen | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Löscht das Element am ursprünglichen Speicherort. |
| Ausschneiden/Einfügen | Ergebnis | Das Element bleibt am ursprünglichen Speicherort im Speicher. | Das Element wird am ursprünglichen Speicherort im Speicher gelöscht. |
| Kopieren/Einfügen | Aktion | Kopieren | Kopieren |
| Kopieren/Einfügen | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kopiert das Element an den Zielort. |
| Kopieren/Einfügen | `Source` | Behält das Original Element bei | Behält das Original Element bei |
| Kopieren/Einfügen | Ergebnis | Das Element bleibt am ursprünglichen Speicherort im Speicher. | Das Element bleibt am ursprünglichen Speicherort im Speicher. |

#### <a name="mixed-target-projects"></a>Projekte mit gemischtem Ziel
In der folgenden Tabelle werden die Drag & amp; Drop-Vorgänge (sowie Ausschneide-, Kopier-und Einfügevorgänge) zusammengefasst, die auf der Grundlage der Art des Quell Elements und der Modifizierertasten ausgeführt werden sollen, die für Projekte mit gemischtem Ziel

| Modifizierer | Category | Quell Element: Verweis/Link | Quell Element: physisches Element oder Dateisystem ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Kein Modifizierer | Aktion | Move | Move |
| Kein Modifizierer | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kopiert das Element an den Zielort. |
| Kein Modifizierer | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Löscht den Verweis auf das ursprüngliche Element. |
| Kein Modifizierer | Ergebnis | `DROPEFFECT_ MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_ MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element wird am ursprünglichen Speicherort im Speicher gelöscht. |
| Umschalt + Ziehen | Aktion | Move | Move |
| Umschalt + Ziehen | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kopiert das Element an den Zielort. |
| Umschalt + Ziehen | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Löscht das Element am ursprünglichen Speicherort. |
| Umschalt + Ziehen | Ergebnis | `DROPEFFECT_ MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_ MOVE` wird als Aktion aus zurückgegeben, `::Drop` und das Element wird am ursprünglichen Speicherort im Speicher gelöscht. |
| Strg + Drag | Aktion | Kopieren | Kopieren |
| Strg + Drag | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kopiert das Element an den Zielort. |
| Strg + Drag | `Source` | Behält den Verweis auf das ursprüngliche Element bei | Behält das Original Element bei |
| Strg + Drag | Ergebnis | `DROPEFFECT_ COPY` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_ COPY` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Strg + Umschalt + Drag | Aktion | Link | Link |
| Strg + Umschalt + Drag | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Fügt einen Verweis auf das ursprüngliche Quell Element hinzu. |
| Strg + Umschalt + Drag | `Source` | Behält den Verweis auf das ursprüngliche Element bei | Behält das Original Element bei |
| Strg + Umschalt + Drag | Ergebnis | `DROPEFFECT_ LINK` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. | `DROPEFFECT_ LINK` wird als Aktion aus zurückgegeben, `::Drop` und das Element bleibt am ursprünglichen Speicherort im Speicher. |
| Ausschneiden/Einfügen | Aktion | Move | Move |
| Ausschneiden/Einfügen | Ziel | Kopiert das Element an den Zielort. | Kopiert das Element an den Zielort. |
| Ausschneiden/Einfügen | `Source` | Löscht den Verweis auf das ursprüngliche Element. | Löscht das Element am ursprünglichen Speicherort. |
| Ausschneiden/Einfügen | Ergebnis | Das Element bleibt am ursprünglichen Speicherort im Speicher. | Das Element wird am ursprünglichen Speicherort im Speicher gelöscht. |
| Kopieren/Einfügen | Aktion | Kopieren | Kopieren |
| Kopieren/Einfügen | Ziel | Fügt einen Verweis auf das ursprüngliche Element hinzu | Kopiert das Element an den Zielort. |
| Kopieren/Einfügen | `Source` | Behält das Original Element bei | Behält das Original Element bei |
| Kopieren/Einfügen | Ergebnis | Das Element bleibt am ursprünglichen Speicherort im Speicher. | Das Element bleibt am ursprünglichen Speicherort im Speicher. |

Diese Details sollten bei der Implementierung von Drag-in- **Projektmappen-Explorer** berücksichtigt werden:

- Entwurf für Szenarien mit mehreren Auswahl.

- Dateinamen (vollständiger Pfad) müssen innerhalb des Ziel Projekts eindeutig sein, oder Drop sollte nicht zulässig sein.

- Ordnernamen müssen auf der Ebene, die Sie ablegen, eindeutig sein (ohne Beachtung der Groß-/Kleinschreibung).

- Es gibt Verhaltensunterschiede zwischen Dateien, die zum Zeitpunkt des Zieh Vorgangs geöffnet oder geschlossen sind (in den obigen Szenarien nicht erwähnt).

- Dateien der obersten Ebene Verhalten sich etwas anders als Dateien in Ordnern.

Ein weiteres Problem, das Sie beachten sollten, ist die Behandlung von Verschiebungs Vorgängen für Elemente mit offenen Designern oder Editoren. Das erwartete Verhalten lautet wie folgt (gilt für alle Projekttypen):

1. Wenn im geöffneten Editor/Designer keine ungespeicherten Änderungen vorhanden sind, sollte das Editor-/Designerfenster im Hintergrund geschlossen werden.

2. Wenn der geöffnete Editor/Designer nicht gespeicherte Änderungen enthält, sollte die Quelle des Zieh Vorgangs auf den Löschvorgang warten und den Benutzer bitten, die Änderungen, für die kein Commit ausgeführt wurde, in den geöffneten Dokumenten zu speichern, bevor Sie das Fenster mit einer Eingabeaufforderung ähnlich der folgenden schließen:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Dadurch erhält der Benutzer die Möglichkeit, die Arbeit zu speichern, bevor das Ziel seine Kopien vornimmt. Eine neue Methode wurde `IVsHierarchyDropDataSource2::OnBeforeDropNotify` hinzugefügt, um diese Behandlung zu aktivieren.

Das Ziel kopiert dann den Zustand des Elements im Speicher (ohne die ungespeicherten Änderungen im Editor, wenn der Benutzer **No** ausgewählt hat). Nachdem das Ziel den Kopiervorgang (in) abgeschlossen hat `IVsHierarchyDropDataSource::Drop` , erhält die Quelle die Möglichkeit, den Löschvorgang des Verschiebungs Vorgangs (in `IVsHierarchyDropDataSource::OnDropNotify` ) abzuschließen.

Alle Editoren mit nicht gespeicherten Änderungen sollten offen bleiben. Bei Dokumenten mit nicht gespeicherten Änderungen bedeutet dies, dass der Kopiervorgang des Verschiebungs Vorgangs durchgeführt wird, der Lösch Teil aber abgebrochen wird. In einem Mehrfachauswahl Szenario, bei dem der Benutzer **Nein** auswählt, sollten diese Dokumente mit nicht gespeicherten Änderungen nicht geschlossen oder entfernt werden, aber die nicht gespeicherten Änderungen sollten geschlossen und entfernt werden.
