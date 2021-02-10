---
title: Schriftarten und Farben, Umgebung, Dialogfeld "Optionen"
description: Hier erfahren Sie, wie Sie über die Seite „Schriftarten und Farben“ im Abschnitt „Umgebungen“ ein benutzerdefiniertes Schriftart- und Farbschema für verschiedene Benutzeroberflächenelemente in der IDE festlegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccc2309cf3ccc51c82796816f635908b55b81901
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969749"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Schriftarten und Farben, Umgebung, Dialogfeld "Optionen"

Auf der Seite **Schriftarten und Farben** des Dialogfelds **Optionen** können Sie ein benutzerdefiniertes Schriftart- und Farbschema für verschiedene Elemente der Benutzeroberfläche in der integrierten Entwicklungsumgebung (IDE) festlegen. Sie können dieses Dialogfeld aufrufen, indem Sie auf **Extras** > **Optionen** klicken und dann **Umgebung** > **Schriftarten und Farben** auswählen.

Änderungen am Farbschema werden nicht in der Sitzung wirksam, in der Sie sie vornehmen. Sie können Farbänderungen auswerten, indem Sie eine weitere Instanz von Visual Studio öffnen und die Bedingungen erzeugen, unter denen die Änderungen gelten sollen.

**Einstellungen anzeigen für**

Zeigt eine Liste aller Elemente der Benutzeroberfläche an, für die Sie Schriftart- und Farbschemas ändern können. Nach dem Auswählen eines Elements aus der Liste können Sie die Farbeinstellungen für das ausgewählten Element unter **Elemente anzeigen** anpassen.

- **Text-Editor**

     Änderungen an den Anzeigeeinstellungen für Schriftart, Größe und Farbe für den Text-Editor wirken sich auf die Darstellung von Text in Ihrem Standard-Text-Editor aus. Dokumente, die in einem Text-Editor außerhalb der IDE geöffnet werden, sind von diesen Einstellungen nicht betroffen.

- **Drucker**

     Änderungen an den Einstellungen für den Schriftschnitt und -grad sowie die Farbwiedergabe unter „Drucker“ beeinflussen die Darstellung von Text in gedruckten Dokumenten.

    > [!NOTE]
    > Bei Bedarf können Sie für den Druck eine andere Standardschriftart als für die Anzeige im Text-Editor auswählen. Dies kann beim Drucken von Code hilfreich sein, der sowohl Einzel- als auch Doppelbytezeichen enthält.

- **Anweisungsvervollständigung**

     Ändert den Schriftschnitt und -grad für den Text, der im Popupfeld mit der Anweisungsvervollständigung im Editor angezeigt wird.

- **Editor-QuickInfo**

     Ändert den Schriftschnitt und -grad für den Text, der in QuickInfos im Editor angezeigt wird.

- **Umgebungsschriftart**

     Ändert den Schriftschnitt und -grad für alle Elemente der IDE-Benutzeroberfläche, für die keine separate Option unter **Einstellungen anzeigen für** vorhanden ist.

     ::: moniker range="vs-2017"

     Diese Option gilt beispielsweise für die **Startseite**, hat jedoch keine Auswirkung auf das Fenster **Ausgabe**.

     ::: moniker-end

- **[Alle Texttoolfenster]**

     Änderungen an den Einstellungen für den Schriftschnitt und -grad sowie die Farbwiedergabe für dieses Element betreffen die Darstellung von Text in Toolfenstern, die über Ausgabebereiche in der IDE verfügen. Beispiele: Ausgabefenster, Befehlsfenster, Direktfenster usw.

    > [!NOTE]
    > Änderungen am Text von Elementen unter **[Alle Texttoolfenster]** gelten noch nicht für die Sitzung, in der Sie sie vornehmen. Sie können diese Änderungen auswerten, indem Sie eine andere Instanz von Visual Studio öffnen.

**Standardwerte verwenden**

Setzt die Schriftart- und Farbwerte des unter **Einstellungen anzeigen für** ausgewählten Listenelements zurück. Die Schaltfläche **Verwenden** wird angezeigt, wenn auch andere Anzeigeschemas ausgewählt werden können. Sie können z. B. zwischen zwei Schemas für den Drucker wählen.

**Schriftart (Fett bedeutet mit fester Breite formatiert)**

Listet alle auf Ihrem System installierten Schriftarten auf. Wenn das Dropdownmenü zum ersten Mal angezeigt wird, ist die aktuelle Schriftart für das im Feld **Einstellungen anzeigen für** ausgewählte Element hervorgehoben. Schriftarten mit fester Breite – die im Editor einfacher ausgerichtet werden können – werden fett formatiert.

**Size**

Listet die verfügbaren Punktgrößen für die hervorgehobene Schriftart auf. Eine Änderung des Schriftgrads wirkt sich auf alle Einträge unter **Elemente anzeigen** für die Auswahl im Feld **Einstellungen anzeigen für** aus.

**Elemente anzeigen**

Listet die Elemente auf, für die Sie die Vorder- und Hintergrundfarbe ändern können.

> [!NOTE]
> Standardmäßig wird das Element **Nur-Text** angezeigt. Daher werden Eigenschaften, die **Nur-Text** zugewiesen sind, von anderen Anzeigeelementen zugewiesenen Eigenschaften überschrieben. Wenn Sie beispielsweise **Nur-Text** die Farbe Blau zuweisen und **Bezeichner** die Farbe Grün, werden alle Bezeichner in Grün angezeigt. In diesem Beispiel überschreiben die Eigenschaften für **Bezeichner** die Eigenschaften für **Nur-Text**.

Hier einige Anzeigeelemente:

|Anzeigeelement|Beschreibung|
|------------------|-----------------|
|**Nur-Text**|Text im Editor.|
|**Markierter Text**|Text, der in der aktuellen Auswahl enthalten ist, wenn der Editor den Fokus besitzt.|
|**Inaktiver ausgewählter Text**|Text, der in der aktuellen Auswahl enthalten ist, wenn der Editor nicht mehr den Fokus besitzt.|
|**Indikatorrand**|Der Rand auf der linken Seite des Code-Editors, in dem Haltepunkte und Lesezeichensymbole angezeigt werden.|
|**Zeilennummern**|Optionale Zahlen, die neben den einzelnen Codezeilen angezeigt werden.|
|**Sichtbare Leerstellen**|Leerzeichen, Tabulatoren und Zeilenumbruchindikatoren|
|**Textmarke**|Zeilen mit Lesezeichen. **Textmarke** ist nur bei deaktiviertem Indikatorrand sichtbar.|
|**Zugehörige Klammer (Hervorhebung)**|Hervorhebung, i. d. R. Fettformatierung zugehöriger geschweifter Klammern.|
|**Zugehörige Klammer (Rechteck)**|Hervorhebung, i. d. R. ein graues Rechteck im Hintergrund.|
|**Haltepunkt (deaktiviert)**|Wird nicht verwendet.|
|**Haltepunkt (aktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit einfachen Haltepunkten an. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt (Fehler)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit Haltepunkten an, die einen Fehlerzustand aufweisen. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt (Warnung)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit Haltepunkten an, die einen Warnungszustand aufweisen. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Erweitert (Deaktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit deaktivierten bedingten Haltepunkten oder Haltepunkten mit Trefferzähler an. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Erweitert (Aktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit bedingten Haltepunkten oder Haltepunkten mit Trefferzähler an. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Erweitert (Fehler)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit bedingten Haltepunkten oder Haltepunkten mit Trefferzähler an, die einen Fehlerzustand aufweisen. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Erweitert (Warnung)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit bedingten Haltepunkten oder Haltepunkten mit Trefferzähler an, die einen Warnzustand aufweisen. Diese Option ist nur anwendbar, wenn Haltepunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Zugeordnet (Deaktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit deaktivierten zugeordneten Haltepunkten an. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Zugeordnet (Aktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit zugeordneten Haltepunkten an. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Zugeordnet (Fehler)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit zugeordneten Haltepunkten an, die einen Fehlerzustand aufweisen. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Haltepunkt - Zugeordnet (Warnung)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit zugeordneten Haltepunkten an, die einen Warnzustand aufweisen. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**C/C++-Benutzerschlüsselwörter**|Eine Konstante innerhalb einer bestimmten Codedatei, die durch die `#define`-Direktive definiert wird.|
|**Aufrufrückgabe**|Gibt die Hervorhebungsfarbe für Quellanweisungen oder Zeilen an, die Aufrufrückgabepunkte angeben, wenn beim Debuggen der Kontext in einen Stapelrahmen geändert wird, der nicht auf der obersten Ebene liegt.|
|**Abhängiges Codeausschnittfeld**|Ein Feld, das aktualisiert wird, wenn das aktuelle bearbeitbare Feld geändert wird.|
|**Codeausschnittfeld**|Bearbeitbares Feld, wenn ein Codeausschnitt aktiv ist.|
|**Reduzierbarer Text**|Ein Block mit Text oder Code, der innerhalb des Code-Editors ein- und ausgeblendet werden kann.|
|**Kommentar**|Codekommentare.|
|**Compilerfehler**|Blaue Wellenlinien im Editor, die einen Compilerfehler anzeigen.|
|**Von Codeabdeckung nicht verwendeter Bereich**|Code, der nicht von einem Komponententest abgedeckt wurde.|
|**Von Codeabdeckung teilweise verwendeter Bereich**|Code, der teilweise von einem Komponententest abgedeckt wurde.|
|**Von Codeabdeckung verwendeter Bereich**|Code, der vollständig von einem Komponententest abgedeckt wurde.|
|**CSS-Kommentar**|Ein Kommentar in Cascading Stylesheets (CSS). Beispiel:<br /><br /> /* comment \*/|
|**CSS-Schlüsselwort**|Schlüsselwörter im Cascading Style Sheet (CSS).|
|**CSS-Eigenschaftenname**|Der Name einer Eigenschaft, z. B. „Background“.|
|**CSS-Eigenschaftenwert**|Der einer Eigenschaft zugewiesene Wert, z. B. „blue“.|
|**CSS-Auswahl**|Eine Zeichenfolge, die die Elemente identifiziert, für die die entsprechende Regel gilt. Eine Auswahl kann eine einfache Auswahl wie z. B. „H1“ sein oder eine kontextabhängige Auswahl wie z. B. „H1 B“, die aus mehreren einfachen Auswahlen besteht.|
|**CSS-Zeichenfolgenwert**|Eine Zeichenfolge in Cascading Stylesheets (CSS).|
|**Aktueller Listenspeicherort**|Aktuelle Zeile, zu der in einem Toolfenster im Listenformat navigiert wird, z. B. im Ausgabe- oder Suchergebnisfenster.|
|**Aktuelle Anweisung**|Gibt die Hervorhebungsfarbe für die Quellanweisung oder Zeile an, die die aktuelle Schrittposition beim Debuggen kennzeichnet.|
|**Debuggerdaten wurden geändert**|Die Textfarbe, die zum Anzeigen von geänderten Daten in den Fenstern **Register** und **Arbeitsspeicher** verwendet wird.|
|**Hintergrund für das Definitionsfenster**|Die Hintergrundfarbe des Fensters **Codedefinition**|
|**Definitionsfenster: Aktuelle Übereinstimmung**|Die aktuelle Definition im Fenster **Codedefinition**|
|**Disassemblydateiname**|Die Textfarbe, die zum Anzeigen von Dateinamenunterbrechungen im Fenster **Disassembly** verwendet wird|
|**Disassemblyquelle**|Die Textfarbe, die zum Anzeigen von Quellzeilen im Fenster **Disassembly** verwendet wird|
|**Disassemblysymbol**|Die Textfarbe, die zum Anzeigen von Symbolnamen im Fenster **Disassembly** verwendet wird|
|**Disassemblytext**|Die Textfarbe, die zum Anzeigen von Op-Code und Daten im Fenster **Disassembly** verwendet wird|
|**Ausgeschlossener Code**|Code, der gemäß einer bedingten Präprozessordirektive wie z. B. `#if` nicht kompiliert werden soll.|
|**Bezeichner**|Bezeichner in Code, z. B. Klassennamen, Methodennamen und Variablennamen.|
|**Schlüsselwort**|Schlüsselwörter für die angegebene Sprache, die reserviert sind. Beispiel: Klasse und Namespace.|
|**Speicheradresse**|Die Textfarbe, die zum Anzeigen der Adressspalte im Fenster **Arbeitsspeicher** verwendet wird|
|**Speicheränderung**|Die Textfarbe, die zum Anzeigen von geänderten Daten im Fenster **Arbeitsspeicher** verwendet wird|
|**Speicherdaten**|Die Textfarbe, die zum Anzeigen von Daten im Fenster **Arbeitsspeicher** verwendet wird|
|**Speicher unlesbar**|Die Textfarbe, die zum Anzeigen von unlesbaren Speicherbereichen im Fenster **Arbeitsspeicher** verwendet wird|
|**Zahl**|Eine Zahl im Code, die einen tatsächlichen numerischen Wert darstellt.|
|**Operator**|Operatoren wie „+“, „-“ und „!=“.|
|**Anderer Fehler**|Andere Fehlertypen, die nicht von anderen Fehlerwellenlinien abgedeckt sind. Momentan zählen hierzu grobe Bearbeitungen beim Bearbeiten und Fortfahren.|
|**Präprozessor-Schlüsselwort**|Schlüsselwörter, die vom Präprozessor verwendet werden, z. B. #include.|
|**Schreibgeschützter Bereich**|Code, der nicht bearbeitet werden kann. Beispielsweise Code, der im Fenster mit der Codedefinition angezeigt wird, oder Code, der beim Bearbeiten und Fortfahren nicht geändert werden kann.|
|**Umgestaltungshintergrund**|Hintergrundfarbe des Dialogfelds **Vorschau der Änderungen**|
|**Das aktuelle Feld wird umgestaltet.**|Hintergrundfarbe des aktuellen Elements, das umgestaltet werden soll, im Dialogfeld **Vorschau der Änderungen**|
|**Das abhängige Feld wird umgestaltet.**|Farbe von Verweisen auf das aktuelle Element, das umgestaltet werden soll, im Dialogfeld **Vorschau der Änderungen**|
|**Registrierungsdaten**|Die Textfarbe, die zum Anzeigen von Daten im Fenster **Register** verwendet wird|
|**NAT registrieren**|Die Textfarbe, die zum Anzeigen von nicht erkannten Daten und Objekten im Fenster **Register** verwendet wird|
|**Smarttag**|Wird zur Bezeichnung der Gliederung verwendet, wenn Smarttags aufgerufen werden.|
|**SQL-DML-Marker**|Gilt für den Transact-SQL-Editor. DML-Anweisungen in diesem Editor werden standardmäßig mit einem blauen Rahmen gekennzeichnet.|
|**Veralteter Code**|Abgelöster Code, für den ein Update erwartet wird. In einigen Fällen können Codeänderungen beim Bearbeiten und Fortfahren nicht sofort angewendet werden; sie werden später angewendet, wenn Sie mit dem Debuggen fortfahren. Dies geschieht, wenn Sie eine Funktion bearbeiten, die die aktuell ausgeführte Funktion aufrufen muss, oder wenn Sie einer in der Aufrufliste wartenden Funktion neue Variablen mit einer Größe von mehr als 64 Bytes hinzufügen. In diesem Fall zeigt der Debugger das Dialogfeld „Warnung: Veralteter Code“ an, und der abgelöste Code wird weiterhin ausgeführt, bis die betreffende Funktion beendet und erneut aufgerufen wird. Bearbeiten und Fortfahren wendet die Codeänderungen zu diesem Zeitpunkt an.|
|**String**|Zeichenfolgenliterale.|
|**Zeichenfolge (C# @ Verbatim)**|Zeichenfolgenliterale in C#, die wörtlich interpretiert werden. Beispiel:<br /><br /> @"x"|
|**Syntaxfehler**|Analysefehler.|
|**Verknüpfung für Aufgabenliste**|Wenn einer Zeile eine Verknüpfung zu einer **Aufgabenliste** hinzugefügt wird und der Indikatorrand deaktiviert ist, wird die Zeile hervorgehoben.|
|**Ablaufverfolgungspunkt (Deaktiviert)**|Wird nicht verwendet.|
|**Ablaufverfolgungspunkt (Aktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit einfachen Ablaufverfolgungspunkten an. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt (Fehler)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit Ablaufverfolgungspunkten an, die einen Fehlerzustand aufweisen. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt (Warnung)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit Ablaufverfolgungspunkten an, die einen Warnzustand aufweisen. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Erweitert (Deaktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit deaktivierten bedingten Ablaufverfolgungspunkten oder Ablaufverfolgungspunkten mit Trefferzähler an. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Erweitert (Aktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit bedingten Ablaufverfolgungspunkten oder Ablaufverfolgungspunkten mit Trefferzähler an. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Erweitert (Fehler)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit bedingten Ablaufverfolgungspunkten oder Ablaufverfolgungspunkten mit Trefferzähler an, die einen Fehlerzustand aufweisen. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Erweitert (Warnung)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit bedingten Ablaufverfolgungspunkten oder Ablaufverfolgungspunkten mit Trefferzähler an, die einen Warnzustand aufweisen. Diese Option ist nur anwendbar, wenn Ablaufverfolgungspunkte auf Anweisungsebene aktiv sind, oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Zugeordnet (Deaktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit deaktivierten zugeordneten Ablaufverfolgungspunkten an. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Zugeordnet (Aktiviert)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit zugeordneten Ablaufverfolgungspunkten an. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Zugeordnet (Fehler)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit zugeordneten Ablaufverfolgungspunkten an, die einen Fehlerzustand aufweisen. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Ablaufverfolgungspunkt - Zugeordnet (Warnung)**|Gibt die Hervorhebungsfarbe für Anweisungen oder Zeilen mit zugeordneten Ablaufverfolgungspunkten an, die einen Warnzustand aufweisen. Gilt für das ASP- oder ASP.NET-Debuggen, wenn Haltepunkte auf Anweisungsebene aktiv sind oder wenn die Option **Bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren** im [Dialogfeld „Optionen“ unter „Allgemein“, „Debuggen“](../../debugger/general-debugging-options-dialog-box.md) aktiviert ist.|
|**Änderungen nachverfolgen nach dem Speichern**|Codezeilen, die seit dem Öffnen der Datei geändert wurden, aber auf einem Datenträger gespeichert sind.|
|**Änderungen nachverfolgen vor dem Speichern**|Codezeilen, die seit dem Öffnen der Datei geändert wurden, aber nicht auf einem Datenträger gespeichert sind.|
|**Benutzertypen**|Von Benutzern definierte Typen.|
|**Benutzertypen (Delegate)**|Typfarbe für Delegaten.|
|**Benutzertypen (Enumerationen)**|Typfarbe für Enumerationen.|
|**Benutzertypen (Schnittstellen)**|Typfarbe für Schnittstellen.|
|**Benutzertypen (Werttypen)**|Typfarbe für Werttypen wie z. B. Strukturen in C#.|
|**Visual Basic-Schreibschutzmarker**|Ein für Visual Basic spezifischer Marker zum Kennzeichnen von EnC wie z. B. Ausnahmebereiche, eine Methodendefinition und innere Knotenaufrufframes.|
|**Warnung**|Compilerwarnungen.|
|**Pfad für Warnmeldungen**|Wird für Warnungszeilen in der statischen Analyse verwendet.|
|**XML-Attribut**|Attributnamen.|
|**XML-Attributanführungszeichen**|Die Anführungszeichen für XML-Attribute.|
|**XML-Attributwert**|Der Inhalt von XML-Attributen.|
|**XML-CData-Abschnitt**|Inhalt von \<![CDATA[...]]>.|
|**XML-Kommentar**|Der Inhalt von \<!-- -->.|
|**XML-Trennzeichen**|XML-Syntaxtrennzeichen, z. B. <, <?, <!, \<!--, -->, ?\>, \<![, ]]> und [, ].|
|**XML-Dokumentattribut**|Der Wert eines XML-Dokumentationsattributs wie z.B. \<param name="I">, wobei das „I“ farbig hervorgehoben ist|
|**XML-Dokumentkommentar**|Die in den XML-Dokumentationskommentaren eingeschlossenen Kommentare.|
|**XML-Dokumenttag**|Die Tags in XML-Dokumentkommentaren, z. B.<br /><br /> /// \<summary>.|
|**XML-Schlüsselwort**|DTD-Schlüsselwörter wie CDATA, IDREF und NDATA.|
|**XML-Name**|Elementnamen und der Zielname von Verarbeitungsanweisungen.|
|**XML-Verarbeitungsanweisung**|Der Inhalt von Verarbeitungsanweisungen ohne Zielname.|
|**XML-Text**|Nur-Text-Elementinhalt.|
|**XSLT-Schlüsselwort**|XSLT-Elementnamen.|

**Elementvordergrund**

Führt die verfügbaren Farben auf, die Sie für den Vordergrund des unter **Elemente anzeigen** ausgewählten Elements auswählen können. Da einige Elemente verwandt sind und daher ein einheitliches Anzeigeschema beibehalten sollten, werden beim Ändern der Vordergrundfarbe des Texts auch die Standardwerte für Elemente wie Compilerfehler, Schlüsselwort oder Operator geändert.

**Automatisch**

Elemente können die Vordergrundfarbe von anderen Anzeigeelementen wie z.B. **Nur-Text** erben. Wenn Sie diese Option beim Ändern der Farbe eines geerbten Anzeigeelements verwenden, wird die Farbe der zugehörigen Anzeigeelemente ebenfalls automatisch geändert. Wenn Sie beispielsweise den Wert **Automatisch** für **Compilerfehler** ausgewählt und später die Farbe von **Nur Text** in Rot geändert haben, erbt **Compilerfehler** ebenfalls automatisch die Farbe Rot.

**Default**

Die Farbe, die für das Element angezeigt wird, wenn Sie Visual Studio das erste Mal öffnen. Durch Klicken auf die Schaltfläche **Standardwerte verwenden** wird diese Farbe wiederhergestellt.

**Benutzerdefiniert**

Zeigt das Dialogfeld „Farbe“ an, in dem Sie eine benutzerdefinierte Farbe für das in der Liste „Elemente anzeigen“ ausgewählte Element festlegen können.

> [!NOTE]
> Die Möglichkeit zum Definieren benutzerdefinierter Farben kann durch die Farbeinstellungen des Bildschirms eingeschränkt sein. Wenn Ihr Computer beispielsweise auf 256 Farben festgelegt ist und Sie eine benutzerdefinierte Farbe im Dialogfeld **Farbe** auswählen, verwendet die IDE standardmäßig die ähnlichste verfügbare **Grundfarbe** und zeigt die Farbe Schwarz im Vorschaufeld **Farbe** an.

**Elementhintergrund**

Stellt eine Farbpalette bereit, aus der Sie für das in der Liste **Elemente anzeigen** ausgewählte Element eine Hintergrundfarbe auswählen können. Da einige Elemente verwandt sind und daher ein einheitliches Anzeigeschema beibehalten sollten, werden beim Ändern der Hintergrundfarbe des Texts auch die Standardwerte für Elemente wie Compilerfehler, Schlüsselwort oder Operator geändert.

**Automatisch**

Elemente können die Hintergrundfarbe von anderen Anzeigeelementen wie z.B. **Nur-Text** erben. Wenn Sie diese Option beim Ändern der Farbe eines geerbten Anzeigeelements verwenden, wird die Farbe der zugehörigen Anzeigeelemente ebenfalls automatisch geändert. Wenn Sie beispielsweise den Wert **Automatisch** für **Compilerfehler** ausgewählt und später die Farbe von **Nur Text** in Rot geändert haben, erbt **Compilerfehler** ebenfalls automatisch die Farbe Rot.

**Default**

Die Farbe, die für das Element angezeigt wird, wenn Sie Visual Studio das erste Mal öffnen. Durch Klicken auf die Schaltfläche **Standardwerte verwenden** wird diese Farbe wiederhergestellt.

**Benutzerdefiniert**

Zeigt das Dialogfeld „Farbe“ an, in dem Sie eine benutzerdefinierte Farbe für das in der Liste „Elemente anzeigen“ ausgewählte Element festlegen können.

**Fett**

Wählen Sie diese Option aus, um den Text von im Feld **Elemente anzeigen** ausgewählten Elementen fett formatiert anzuzeigen. Fett formatierter Text ist im Editor leichter zu identifizieren.

**Beispiel**

Zeigt ein Beispiel für den Schriftschnitt und -grad sowie das Farbschema für die in den Feldern **Einstellungen anzeigen für** und **Elemente anzeigen** ausgewählten Elemente an. Sie können dieses Feld verwenden, um eine Vorschau der Ergebnisse anzuzeigen, während Sie mit verschiedenen Formatierungsoptionen experimentieren.

## <a name="see-also"></a>Weitere Informationen

- [Optionen (Dialogfeld)](../../ide/reference/options-dialog-box-visual-studio.md)
- [Vorgehensweise: Ändern von Schriftarten und Farben](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
