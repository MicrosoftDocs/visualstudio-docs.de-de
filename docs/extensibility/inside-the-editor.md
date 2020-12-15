---
title: Im Editor
description: Erfahren Sie mehr über die Subsysteme und Features des Editors. Sie können die Funktionen von Visual Studio-Editor erweitern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14193c0806c4b45f721ee97b101969de8437448d
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487529"
---
# <a name="inside-the-editor"></a>Innerhalb des Editors

Der Editor besteht aus mehreren unterschiedlichen Subsystemen, die so entworfen wurden, dass das Editor-Text Modell von der Textansicht und der Benutzeroberfläche getrennt bleibt.

In diesen Abschnitten werden verschiedene Aspekte des Editors beschrieben:

- [Übersicht über die Subsysteme](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Das Text Modell](../extensibility/inside-the-editor.md#the-text-model)

- [Die Textansicht](../extensibility/inside-the-editor.md#the-text-view)

In diesen Abschnitten werden die Funktionen des-Editors beschrieben:

- [Tags und Klassifizierungen](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Zusatzelemente](../extensibility/inside-the-editor.md#adornments)

- [Projektion](../extensibility/inside-the-editor.md#projection)

- [Gliedern](../extensibility/inside-the-editor.md#outlining)

- [Maus Bindungen](../extensibility/inside-the-editor.md#mouse-bindings)

- [Editor-Vorgänge](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Übersicht über die Subsysteme

### <a name="text-model-subsystem"></a>Text Modell Subsystem

Das Text Modell Subsystem ist für das darstellen von Text und das Aktivieren der Bearbeitung verantwortlich. Das Text Modell Subsystem enthält die- <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle, die die Zeichenfolge beschreibt, die vom Editor angezeigt werden soll. Dieser Text kann in vielerlei Hinsicht geändert, nachverfolgt und anderweitig bearbeitet werden. Das Text Modell stellt auch Typen für die folgenden Aspekte bereit:

- Ein Dienst, der Text mit Dateien verknüpft und Lese-und Schreibvorgänge im Dateisystem verwaltet.

- Ein differenzierender Dienst, der die minimalen Unterschiede zwischen zwei Sequenzen von Objekten findet.

- Ein System, mit dem der Text in einem Puffer in Bezug auf Teilmengen des Texts in anderen Puffern beschrieben wird.

Das Text Modell Subsystem ist ohne Benutzeroberflächen Konzepte verfügbar. Er ist z. b. nicht für die Textformatierung oder das Text Layout zuständig und hat keine Kenntnisse über visuelle Zusatzelemente, die möglicherweise mit dem Text verknüpft sind.

Die öffentlichen Typen des Text Modell Subsystems sind in *Microsoft.VisualStudio.Text.Data.dll* und *Microsoft.VisualStudio.CoreUtility.dll* enthalten, die nur von der .NET Framework Basisklassen Bibliothek und der Managed Extensibility Framework (MEF) abhängen.

### <a name="text-view-subsystem"></a>Text Ansichts Subsystem

Das Text Ansichts Subsystem ist für das Formatieren und Anzeigen von Text zuständig. Die Typen in diesem Subsystem sind in zwei Ebenen unterteilt, je nachdem, ob die Typen auf Windows Presentation Foundation (WPF) basieren. Die wichtigsten Typen sind <xref:Microsoft.VisualStudio.Text.Editor.ITextView> und <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , die Steuern, welche Textzeile angezeigt werden sollen, sowie die Einfügemarke, die Auswahl und die Funktionen zum aneignen des Texts mithilfe von WPF-Benutzeroberflächen Elementen. Dieses Subsystem bietet auch Ränder um den Textanzeige Bereich. Diese Ränder können erweitert werden und können unterschiedliche Arten von Inhalten und visuellen Effekten enthalten. Beispiele für Ränder sind Zeilennummern anzeigen und Bild Lauf leisten.

Die öffentlichen Typen des Text Ansichts Subsystems sind in *Microsoft.VisualStudio.Text.UI.dll* und *Microsoft.VisualStudio.Text.UI.Wpf.dll* enthalten. Die erste Assembly enthält die plattformunabhängigen Elemente, die zweite enthält die WPF-spezifischen Elemente.

### <a name="classification-subsystem"></a>Klassifizierungs Subsystem

Das Klassifizierungs Subsystem ist für die Bestimmung der Schriftart Eigenschaften für Text zuständig. Ein Klassifizierer unterteilt den Text in verschiedene Klassen, z. b. "Keyword" oder "comment". Die Klassifizierungs Format Zuordnung verknüpft diese Klassen mit tatsächlichen Schriftart Eigenschaften, z. b. "Blue Consolas 10 pt". Diese Informationen werden von der Textansicht verwendet, wenn Sie Text formatiert und rendert. Das Tagging, das weiter unten in diesem Thema ausführlich beschrieben wird, ermöglicht die Zuordnung von Daten zu Textabschnitten.

Die öffentlichen Typen des Klassifizierungs Subsystems sind in Microsoft.VisualStudio.Text.Logic.dll enthalten, und Sie interagieren mit den visuellen Aspekten der Klassifizierung, die in Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten sind.

### <a name="operations-subsystem"></a>Operations-Subsystem

Das Operations-Subsystem definiert das Editor-Verhalten. Er bietet die Implementierung für Visual Studio-Editor-Befehle und das rückgängigssystem.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Genauere Betrachtung des Text Modells und der Textansicht

### <a name="the-text-model"></a>Das Text Modell

Das Text Modell Subsystem besteht aus unterschiedlichen Gruppierungen von Text Typen. Dies schließt den Text Puffer, Text Momentaufnahmen und Text spannen ein.

#### <a name="text-buffers-and-text-snapshots"></a>Text Puffer und Text Momentaufnahmen

Die- <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle stellt eine Sequenz von Unicode-Zeichen dar, die mithilfe von UTF-16 codiert werden. Dies ist die Codierung, die vom- `String` Typ in der .NET Framework verwendet wird. Ein Text Puffer kann als Dateisystem Dokument beibehalten werden, dies ist jedoch nicht erforderlich.

Der <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> wird zum Erstellen eines leeren Text Puffers oder eines Text Puffers verwendet, der aus einer Zeichenfolge oder aus initialisiert wird <xref:System.IO.TextReader> . Der Text Puffer kann im Dateisystem als persistent gespeichert werden <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Jeder Thread kann den Text Puffer bearbeiten, bis ein Thread den Besitz des Text Puffers übernimmt, indem er aufgerufen wird <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Danach kann nur dieser Thread Änderungen ausführen.

Ein Text Puffer kann während seiner Lebensdauer viele Versionen durchlaufen. Wenn der Puffer bearbeitet wird, wird eine neue Version generiert, und ein unveränderlicher Wert <xref:Microsoft.VisualStudio.Text.ITextSnapshot> stellt den Inhalt dieser Version des Puffers dar. Da Text Momentaufnahmen unveränderlich sind, können Sie auf eine Text Momentaufnahme in einem beliebigen Thread ohne Einschränkungen zugreifen, auch wenn sich der Text Puffer, den er darstellt, weiterhin ändert.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Text Momentaufnahmen und Text momentaufnahmenzeilen

Sie können den Inhalt einer Text Momentaufnahme als Sequenz von Zeichen oder als Sequenz von Zeilen anzeigen. Zeichen und Zeilen werden beide indiziert, beginnend bei Null. Eine leere Text Momentaufnahme enthält NULL Zeichen und eine leere Zeile. Eine Zeile wird durch eine beliebige gültige Unicode-Zeilenumbruch Zeichen Sequenz oder durch den Anfang oder das Ende des Puffers getrennt. Zeilenumbruch Zeichen werden explizit in der Text Momentaufnahme dargestellt, und die Zeilenumbrüche in einer Text Momentaufnahme müssen nicht alle identisch sein.

> [!NOTE]
> Weitere Informationen zu Zeilenumbruch Zeichen im Visual Studio-Editor finden Sie unter [Codierungen und Zeilenumbrüche](../ide/encodings-and-line-breaks.md).

Eine Textzeile wird durch ein- <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> Objekt dargestellt, das aus einer Text Momentaufnahme für eine bestimmte Zeilennummer oder für eine bestimmte Zeichenposition abgerufen werden kann.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Snapshotpoints, snapshotspannen und normalizedsnapshotspancollections

Eine <xref:Microsoft.VisualStudio.Text.SnapshotPoint> stellt eine Zeichenposition in einer Momentaufnahme dar. Die Position zwischen 0 und der Länge der Momentaufnahme ist garantiert. Ein <xref:Microsoft.VisualStudio.Text.SnapshotSpan> stellt einen Textabschnitt in einer Momentaufnahme dar. Die Endposition ist garantiert zwischen null und der Länge der Momentaufnahme. Das <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> besteht aus einem Satz von- <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekten aus der gleichen Momentaufnahme.

#### <a name="spans-and-normalizedspancollections"></a>Spannen und normalizedspancollections

Ein <xref:Microsoft.VisualStudio.Text.Span> stellt ein Intervall dar, das auf einen Textabschnitt in einer Text Momentaufnahme angewendet werden kann. Momentaufnahme Positionen sind NULL basiert, sodass spannen an jeder Position beginnen können, einschließlich 0 (null). Die `End` -Eigenschaft einer Spanne ist gleich der Summe der zugehörigen `Start` -Eigenschaft und deren- `Length` Eigenschaft. Ein enthält `Span` nicht das Zeichen, das von der-Eigenschaft indiziert wird `End` . Beispielsweise weist eine Spanne, die den Wert Start = 5 und length = 3 hat, den Wert End = 8 auf, und die Zeichen an den Positionen 5, 6 und 7 sind enthalten. Die Notation für diese Spanne ist [5.. 8).

Zwei Spannen überschneiden sich, wenn Sie über gemeinsame Positionen verfügen, einschließlich der Endposition. Daher ist die Schnittmenge von [3, 5) und [2, 7) [3, 5), und die Schnittmenge von [3, 5) und [5, 7) ist [5, 5). (Beachten Sie, dass [5, 5) eine leere Spanne ist.)

Zwei Spannen überlappen sich, wenn Sie über Positionen gemeinsam sind, mit Ausnahme der Endposition. Eine leere Spanne überlappt nie alle anderen spannen, und die Überlappung zweier spannen ist nie leer.

Ein <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> ist eine Liste von spannen in der Reihenfolge der Start Eigenschaften der spannen. In der Liste werden überlappende oder überlappende spannen zusammengeführt. Wenn z. b. die Menge der spannen [5.. 9), [0.. 1), [3.. 6) und [9.. 10) ist, ist die normalisierte Liste der spannen [0.. 1), [3.. 10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Itextedit-, Textversion-und Text Änderungs Benachrichtigungen

Der Inhalt eines Text Puffers kann mithilfe eines-Objekts geändert werden <xref:Microsoft.VisualStudio.Text.ITextEdit> . Durch das Erstellen eines solchen Objekts (mit einer der- `CreateEdit()` Methoden von <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) wird eine Text Transaktion gestartet, die aus Textänderungen besteht. Jede Bearbeitung ist ein Ersatz für eine bestimmte Textzeile im Puffer durch eine Zeichenfolge. Die Koordinaten und der Inhalt jeder Bearbeitung werden relativ zur Momentaufnahme des Puffers ausgedrückt, wenn die Transaktion gestartet wurde. Das- <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt passt die Koordinaten der Änderungen an, die von anderen Änderungen in derselben Transaktion betroffen sind.

Stellen Sie sich beispielsweise einen Text Puffer vor, der diese Zeichenfolge enthält:

```
abcdefghij
```

Wenden Sie eine Transaktion an, die zwei Bearbeitungen enthält, eine Bearbeitung, die die Spanne um [2.. 4) ersetzt, indem Sie das `X` -Zeichen und eine zweite Bearbeitung verwenden, die die Spanne um [6.9) ersetzt, indem Sie das-Zeichen verwenden `Y` . Das Ergebnis ist dieser Puffer:

```
abXefYj
```

Die Koordinaten für die zweite Bearbeitung wurden in Bezug auf den Inhalt des Puffers am Anfang der Transaktion berechnet, bevor die erste Bearbeitung angewendet wurde.

Die Änderungen am Puffer treten in Kraft, wenn für das <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt ein Commit ausgeführt wird, indem seine-Methode aufgerufen wird `Apply()` . Wenn mindestens eine nicht leere Bearbeitung vorhanden ist, wird ein neuer <xref:Microsoft.VisualStudio.Text.ITextVersion> erstellt, ein neuer <xref:Microsoft.VisualStudio.Text.ITextSnapshot> erstellt und ein `Changed` Ereignis ausgelöst. Jede Textversion verfügt über eine andere Text Momentaufnahme. Eine Text Momentaufnahme stellt den vollständigen Status des Text Puffers nach einer Bearbeitungs Transaktion dar, aber eine Textversion beschreibt nur die Änderungen von einer Momentaufnahme zum nächsten. Im Allgemeinen sollen Text Momentaufnahmen einmal verwendet und dann verworfen werden, während Textversionen für einige Zeit aktiv bleiben müssen.

Eine Textversion enthält eine <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Diese Auflistung beschreibt die Änderungen, die bei der Anwendung auf die Momentaufnahme die nachfolgende Momentaufnahme erstellen. Jede <xref:Microsoft.VisualStudio.Text.ITextChange> in der Auflistung enthält die Zeichenposition der Änderung, die ersetzte Zeichenfolge und die Ersetzungs Zeichenfolge. Die ersetzte Zeichenfolge ist für eine einfache Einfügung leer, und die Ersetzungs Zeichenfolge ist für einen grundlegenden Löschvorgang leer. Die normalisierte Sammlung ist immer `null` für die aktuellste Version des Text Puffers.

Es <xref:Microsoft.VisualStudio.Text.ITextEdit> kann immer nur ein Objekt für einen Text Puffer instanziiert werden, und alle Text bearbeitvorgänge müssen für den Thread ausgeführt werden, der den Text Puffer besitzt (wenn der Besitz beansprucht wurde). Eine Textbearbeitung kann durch Aufrufen der-Methode oder der zugehörigen-Methode abgebrochen werden `Cancel` `Dispose` .

<xref:Microsoft.VisualStudio.Text.ITextBuffer> bietet auch `Insert()` `Delete()` -,-und- `Replace()` Methoden, die den in der- <xref:Microsoft.VisualStudio.Text.ITextEdit> Schnittstelle gefundenen ähneln. Das Aufrufen dieser Aufrufe hat denselben Effekt wie das Erstellen eines <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekts, das Erstellen eines ähnlichen Aufrufs und das anschließende Anwenden der Bearbeitung.

#### <a name="tracking-points-and-tracking-spans"></a>Überwachungspunkte und nach Verfolgungs spannen

Eine <xref:Microsoft.VisualStudio.Text.ITrackingPoint> stellt eine Zeichenposition in einem Text Puffer dar. Wenn der Puffer auf eine Weise bearbeitet wird, die bewirkt, dass die Position des Zeichens verschoben wird, verschiebt sich der Überwachungs Punkt damit. Wenn ein nach Verfolgungs Punkt z. b. auf Position 10 in einem Puffer verweist und fünf Zeichen am Anfang des Puffers eingefügt werden, verweist der nach Verfolgungs Punkt auf Position 15. Wenn eine Einfügung genau der durch den Verfolgungs Punkt bezeichneten Position erfolgt, wird das Verhalten durch den bestimmt <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , was entweder oder sein kann `Positive` `Negative` . Wenn der Überwachungsmodus positiv ist, verweist der nach Verfolgungs Punkt auf dasselbe Zeichen, das sich jetzt am Ende der Einfügung befindet. Wenn der Überwachungsmodus negativ ist, verweist der nach Verfolgungs Punkt auf das erste eingefügte Zeichen an der ursprünglichen Position. Wenn das Zeichen an der Position, die durch einen nach Verfolgungs Punkt dargestellt wird, gelöscht wird, wechselt der nach Verfolgungs Punkt zum ersten Zeichen, das dem gelöschten Bereich folgt. Wenn ein nach Verfolgungs Punkt z. b. auf das Zeichen an Position 5 verweist und die Zeichen an den Positionen 3 bis 6 gelöscht werden, verweist der nach Verfolgungs Punkt auf das Zeichen an Position 3.

Ein <xref:Microsoft.VisualStudio.Text.ITrackingSpan> stellt einen Bereich von Zeichen anstelle von nur einer Position dar. Das Verhalten wird durch seinen bestimmt <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Wenn der spannen Verfolgungs Modus " [spantrackingmode. edgeinclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)" ist, wird die nach Verfolgungs Spanne vergrößert, um Text einzuschließen, der an den Rändern eingefügt wurde. Wenn der spannen Verfolgungs Modus " [spantrackingmode. edgeexclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)" ist, enthält die nach Verfolgungs Spanne keinen Text, der an den Rändern eingefügt wurde. Wenn der spannen Verfolgungs Modus jedoch " [spantrackingmode. edgepositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)" ist, legt eine Einfügung die aktuelle Position auf den Start und wenn der spannen nach Verfolgungs Modus " [spantrackingmode. edgenegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)" ist, wird die aktuelle Position durch eine Einfügung auf das Ende gedrückt.

Sie können die Position eines nach Verfolgungs Punkts oder die Spanne einer nach Verfolgungs Spanne für eine beliebige Momentaufnahme des Text Puffers, zu dem Sie gehören, erhalten. Nach Verfolgungs Punkte und nach Verfolgungs spannen können von jedem Thread aus sicher referenziert werden.

#### <a name="content-types"></a>Inhaltstypen

Inhaltstypen sind ein Mechanismus zum Definieren verschiedener Arten von Inhalten. Ein Inhaltstyp kann ein Dateityp sein, z. b. "Text", "Code" oder "Binary", oder ein Technologietyp wie "XML", "vb" oder "c#". Das Wort "using" ist beispielsweise ein Schlüsselwort in c# und Visual Basic, aber nicht in anderen Programmiersprachen. Daher ist die Definition dieses Schlüssel Worts auf die Inhaltstypen "c#" und "vb" beschränkt.

Inhaltstypen werden als Filter für Zusatzelemente und andere Elemente des Editors verwendet. Viele Editor-Funktionen und Erweiterungs Punkte werden pro Inhaltstyp definiert. Beispielsweise unterscheidet sich die Text Farbgebung für nur-Text-Dateien, XML-Dateien und Visual Basic Quell Code Dateien. Text Puffern wird in der Regel ein Inhaltstyp zugewiesen, wenn Sie erstellt werden, und der Inhaltstyp eines Text Puffers kann geändert werden.

Inhaltstypen können mehrere von anderen Inhaltstypen erben. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Mit können Sie mehrere Basis Typen als übergeordnete Elemente eines bestimmten Inhaltstyps angeben.

Entwickler können Ihre eigenen Inhaltstypen definieren und mithilfe der registrieren <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Viele Editor-Funktionen können in Bezug auf einen bestimmten Inhaltstyp mithilfe von definiert werden <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Beispielsweise können Editor-Ränder, Zusatzelemente und Maus Handler so definiert werden, dass Sie nur auf Editoren angewendet werden, die bestimmte Inhaltstypen anzeigen.

### <a name="the-text-view"></a>Die Textansicht

Der Ansichts Teil des MVC-Musters (Model View Controller) definiert die Textansicht, die Formatierung der Ansicht, grafische Elemente wie die Scrollleiste und die Einfügemarke. Alle Präsentationselemente des Visual Studio-Editors basieren auf WPF.

#### <a name="text-views"></a>Text Ansichten

Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView> -Schnittstelle ist eine plattformunabhängige Darstellung einer Textansicht. Sie wird in erster Linie zum Anzeigen von Textdokumenten in einem Fenster verwendet, kann aber auch für andere Zwecke verwendet werden, z. b. in einer QuickInfo.

Die Textansicht verweist auf verschiedene Arten von Text Puffern. Die- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Eigenschaft verweist auf ein <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> Objekt, das auf diese drei verschiedenen Text Puffer zeigt: den Datenpuffer, der den obersten Puffer auf Datenebene, den Bearbeitungs Puffer, in dem die Bearbeitung erfolgt, und den visuellen Puffer, bei dem es sich um den Puffer handelt, der in der Textansicht angezeigt wird.

Der Text wird basierend auf den Klassifizierern formatiert, die an den zugrunde liegenden Text Puffer angefügt sind, und wird mit den Zusatzelement Anbietern versehen, die an die Textansicht selbst angefügt sind.

#### <a name="the-text-view-coordinate-system"></a>Das Koordinatensystem der Textansicht

Das Text Ansichts Koordinatensystem gibt Positionen in der Textansicht an. In diesem Koordinatensystem entspricht der x-Wert 0,0 dem linken Rand des angezeigten Texts, und der y-Wert 0,0 entspricht dem oberen Rand des angezeigten Texts. Die x-Koordinate wird von links nach rechts vergrößert, und die y-Koordinate wird von oben nach unten vergrößert.

Ein Viewport (der Teil des Texts, der im Textfenster sichtbar ist) kann nicht in der gleichen Weise wie ein vertikaler Bildlauf durchgeführt werden. Ein Viewport wird durch eine Änderung der linken Koordinate horizontal durch Ändern der linken Koordinate bewegt, sodass er sich in Bezug auf die Zeichen Oberfläche bewegt. Ein Viewport kann jedoch nur vertikal gescrollt werden, indem der gerenderte Text geändert wird, der bewirkt, dass ein- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Ereignis ausgelöst wird.

Entfernungen im Koordinatensystem entsprechen logischen Pixeln. Wenn die Text Rendering-Oberfläche ohne Skalierungs Transformation angezeigt wird, entspricht eine Einheit im Text Rendering-Koordinatensystem einem Pixel auf der Anzeige.

#### <a name="margins"></a>Ränder

Die <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> -Schnittstelle stellt einen Rand dar und ermöglicht die Steuerung der Sichtbarkeit des Randes und der Größe. Es gibt vier vordefinierte Ränder, die den Namen "Top", "Left", "Right" und "Bottom" haben und an den oberen, unteren, linken oder rechten Rand einer Ansicht angefügt werden. Diese Ränder sind Container, in denen andere Ränder platziert werden können. Die-Schnittstelle definiert Methoden, die die Größe des Rands und die Sichtbarkeit eines Randes zurückgeben. Ränder sind visuelle Elemente, die zusätzliche Informationen über die Textansicht bereitstellen, an die Sie angefügt sind. Der Zeilennummern Rand zeigt z. b. Zeilennummern für die Textansicht an. Der Glyphe-Rand zeigt Benutzeroberflächen Elemente an.

Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> -Schnittstelle behandelt die Erstellung und Platzierung von Rändern. Ränder können in Bezug auf andere Ränder angeordnet werden. Ränder mit höherer Priorität befinden sich näher an der Textansicht. Wenn beispielsweise zwei linke Ränder vorhanden sind, ist Rand a und Rand b und Rand b eine niedrigere Priorität als Margin a. der Rand b wird links neben Margin a angezeigt.

#### <a name="the-text-view-host"></a>Der Text Ansichts Host

Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> -Schnittstelle enthält die Textansicht und alle in die Ansicht einsetzenden Dekorationen, z. b. Scrollleisten. Der Text Ansichts Host enthält auch Ränder, die an einen Rahmen der Ansicht angefügt sind.

#### <a name="formatted-text"></a>Formatierter Text

Der in einer Textansicht angezeigte Text besteht aus- <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekten. Jede Text Ansichts Zeile entspricht einer Textzeile in der Textansicht. Lange Zeilen im zugrunde liegenden Text Puffer können entweder teilweise verdeckt werden (wenn das Umbrechen von Zeilen nicht aktiviert ist) oder in mehrere Text Ansichts Zeilen unterteilt werden. Die <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> -Schnittstelle enthält Methoden und Eigenschaften für die Zuordnung zwischen Koordinaten und Zeichen sowie für die Zusatzelemente, die der Zeile zugeordnet werden können.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> -Objekte werden mithilfe einer- <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> Schnittstelle erstellt. Wenn Sie sich nur um den derzeit in der Ansicht angezeigten Text kümmern möchten, können Sie die Formatierungs Quelle ignorieren. Wenn Sie an dem Textformat interessiert sind, das in der Ansicht nicht angezeigt wird (z. b. zur Unterstützung von Rich-Text-ausschneiden und Einfügen), können Sie verwenden, <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> um Text in einem Text Puffer zu formatieren.

Die Textansicht formatiert jeweils nacheinander <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> .

## <a name="editor-features"></a>Editor-Funktionen

Die Funktionen des Editors sind so konzipiert, dass die Definition der Funktion von ihrer Implementierung getrennt ist. Der-Editor enthält die folgenden Features:

- Tags und Klassifizierungen

- Zusatzelemente

- Projektion

- Gliedern

- Maus-und Tastenbindungen

- Vorgänge und primitive

- IntelliSense

### <a name="tags-and-classifiers"></a>Tags und Klassifizierungen

Tags sind Marker, die einem Textabschnitt zugeordnet sind. Sie können auf unterschiedliche Weise dargestellt werden, z. b. durch die Verwendung von Textfarben, unterstrichen, Grafiken oder Popups. Klassifizierer sind eine Art von Tag.

Andere Arten von Tags sind <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> zum Hervorheben von Text, zum Gliedern <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> und <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> für Kompilierungsfehler.

#### <a name="classification-types"></a>Klassifizierungs Typen

Eine <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Schnittstelle stellt eine Äquivalenzklasse dar, bei der es sich um eine abstrakte Kategorie von Text handelt. Klassifizierungs Typen können mehrfach von anderen Klassifizierungs Typen erben. Programmiersprachen Klassifizierungen können z. b. "Schlüsselwort", "Kommentar" und "Bezeichner" enthalten, die alle von "Code" erben. Zu den Klassifizierungs Typen natürlicher Sprachen zählen "noun", "Verb" und "Adjektiv", die alle von "Natural Language" erben.

#### <a name="classifications"></a>Klassifizierungen

Eine Klassifizierung ist eine Instanz eines bestimmten Klassifizierungs Typs, in der Regel über eine Textzeile. Eine <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> wird verwendet, um eine Klassifizierung darzustellen. Eine Klassifizierungs Spanne kann als Bezeichnung betrachtet werden, die einen bestimmten Textabschnitt abdeckt und dem System mitteilt, dass diese Text Spanne einen bestimmten Klassifizierungstyp hat.

#### <a name="classifiers"></a>Klassifizierern

Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ist ein Mechanismus, der Text in einen Satz von Klassifizierungen umbricht. Klassifizierungen müssen für bestimmte Inhaltstypen definiert und für bestimmte Text Puffer instanziiert werden. Clients müssen implementieren <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> , um an der Text Klassifizierung teilnehmen zu können.

#### <a name="classifier-aggregators"></a>Klassifizierungs Aggregatoren

Bei einem Klassifizierungs Aggregator handelt es sich um einen Mechanismus, der alle Klassifizierungen für einen Text Puffer in nur einem Satz von Klassifizierungen kombiniert. Beispielsweise könnten sowohl ein c#-Klassifizierer als auch ein englischer sprach Klassifizierer Klassifizierungen über einen Kommentar in einer c#-Datei erstellen. Beachten Sie diesen Kommentar:

```
// This method produces a classifier
```

Ein c#-Klassifizierer könnte die gesamte Spanne als Kommentar bezeichnen, und die englische sprach Klassifizierung kann "produziert" als "Verb" und "Methode" als "Nomen" klassifizieren. Der Aggregator erzeugt eine Reihe von nicht überlappenden Klassifizierungen, und der Typ des Satzes basiert auf allen Beiträgen.

Ein Klassifizierungs Aggregator ist auch ein Klassifizierer, da er Text in einen Satz von Klassifizierungen umbricht. Der Klassifizierungs Aggregator stellt außerdem sicher, dass keine überlappenden Klassifizierungen vorhanden sind und dass die Klassifizierungen sortiert werden. Einzelne Klassifizierer können beliebige Klassifizierungen in beliebiger Reihenfolge und in beliebiger Reihenfolge zurückgeben.

#### <a name="classification-formatting-and-text-coloring"></a>Klassifizierungs Formatierung und Text Färbung

Die Textformatierung ist ein Beispiel für eine Funktion, die auf der Text Klassifizierung basiert. Sie wird von der Text Ansichts Ebene verwendet, um die Anzeige von Text in einer Anwendung zu bestimmen. Der Text Formatierungs Bereich ist von WPF abhängig, aber von der logischen Definition der Klassifizierungen.

Ein Klassifizierungs Format ist ein Satz von Formatierungs Eigenschaften für einen bestimmten Klassifizierungstyp. Diese Formate erben vom Format des übergeordneten Elements des Klassifizierungs Typs.

Eine <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> ist eine Zuordnung von einem Klassifizierungstyp zu einem Satz von Text Formatierungs Eigenschaften. Die Implementierung der Format Map im Editor verarbeitet alle Exporte von Klassifizierungs Formaten.

### <a name="adornments"></a>Zusatzelemente

Zusatzelemente sind grafische Effekte, die nicht direkt mit der Schriftart und Farbe der Zeichen in der Textansicht verknüpft sind. Beispielsweise ist die rote Wellenlinie, die verwendet wird, um nicht Kompilier baren Code in vielen Programmiersprachen zu markieren, ein eingebettetes Zusatzelement, und Quick Infos sind Popup-Zusatzelemente. Zusatzelemente werden von abgeleitet <xref:System.Windows.UIElement> und implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Zwei spezialisierte Typen von Zusatzelement-Tags sind, für Zusatzelemente, die <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> denselben Raum wie der Text in einer Ansicht einnehmen, und <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> für die Wellenlinien Unterstreichung.

Eingebettete Zusatzelemente sind Grafiken, die einen Teil der formatierten Textansicht bilden. Sie sind in verschiedenen Z-Reihen folgen Schichten angeordnet. Es gibt drei integrierte Ebenen wie folgt: Text, die Einfügemarke und die Auswahl. Entwickler können jedoch weitere Ebenen definieren und Sie in der richtigen Reihenfolge platzieren. Die drei Arten von eingebetteten Zusatzelementen sind Text relative Zusatzelemente (die verschoben werden, wenn der Text verschoben und gelöscht wird, wenn der Text gelöscht wird), Ansichts relative Zusatzelemente (die mit nicht Textzeilen der Ansicht zu tun haben) und vom Besitzer gesteuerte Zusatzelemente (der Entwickler muss Ihre Platzierung verwalten).

Popup-Zusatzelemente sind Grafiken, die in einem kleinen Fenster oberhalb der Textansicht angezeigt werden, z. b. Quick Infos.

### <a name="projection"></a><a name="projection"></a> Projektion

Projektion ist eine Technik zum Erstellen einer anderen Art von Text Puffer, in dem Text nicht tatsächlich gespeichert wird. stattdessen wird Text aus anderen Text Puffern kombiniert. Beispielsweise kann ein Projektions Puffer verwendet werden, um den Text aus zwei anderen Puffern zu verketten und das Ergebnis so darzustellen, als ob es sich in nur einem Puffer befindet, oder Teile des Texts in einem Puffer auszublenden. Ein Projektions Puffer kann als Quell Puffer für einen anderen Projektions Puffer fungieren. Ein Satz von Puffern, die durch Projektion verknüpft sind, kann erstellt werden, um Text auf viele verschiedene Arten neu anzuordnen. (Eine solche Menge wird auch als *Puffer Diagramm* bezeichnet.) Das Visual Studio-Text Gliederungs Feature wird mithilfe eines Projektions Puffers implementiert, um den reduzierten Text auszublenden, und der Visual Studio-Editor für ASP.net Pages verwendet Projektion, um eingebettete Sprachen wie Visual Basic und c# zu unterstützen.

Eine <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> wird mithilfe von erstellt <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Ein Projektions Puffer wird durch eine geordnete Sequenz von <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Objekten dargestellt, die als *Quell spannen* bezeichnet werden. Der Inhalt dieser Spannen wird als Sequenz von Zeichen dargestellt. Die Text Puffer, aus denen die Quell spannen gezeichnet werden, werden als *Quell Puffer* bezeichnet. Clients eines Projektions Puffers müssen nicht beachten, dass Sie sich von einem normalen Text Puffer unterscheiden.

Der Projektions Puffer lauscht auf Text Änderungs Ereignisse in den Quell Puffern. Wenn der Text in einer Quell Spanne geändert wird, ordnet der Projektions Puffer die geänderten Text Koordinaten seinen eigenen Koordinaten zu und löst entsprechende Text Änderungs Ereignisse aus. Nehmen Sie beispielsweise die Quell Puffer A und B mit den folgenden Inhalten:

```
A: ABCDE
B: vwxyz
```

Wenn der Projektions Puffer P aus zwei Text spannen gebildet wird, von denen eine den gesamten Puffer a und die andere mit dem gesamten Puffer B aufweist, hat p den folgenden Inhalt:

```
P: ABCDEvwxyz
```

Wenn die Teil Zeichenfolge `xy` aus Puffer B gelöscht wird, löst Buffer P ein Ereignis aus, das angibt, dass die Zeichen an Position 7 und 8 gelöscht wurden.

Der Projektions Puffer kann auch direkt bearbeitet werden. Die Änderungen werden an die entsprechenden Quell Puffer weitergegeben. Wenn z. b. eine Zeichenfolge in buffer P an Position 6 (die ursprüngliche Position des Zeichens "v") eingefügt wird, wird die Einfügung an Position 1 an Puffer B weitergegeben.

Es gibt Einschränkungen für die Quell spannen, die zu einem Projektions Puffer beitragen. Quell spannen dürfen sich nicht überlappen. ein Speicherort in einem Projektions Puffer kann nicht mehr als einem Speicherort in einem Quell Puffer zugeordnet werden, und ein Speicherort in einem Quell Puffer kann nicht mehr als einem Speicherort in einem Projektions Puffer zugeordnet werden. In der Quell Puffer Beziehung sind keine ziritäten zulässig.

Ereignisse werden ausgelöst, wenn sich der Satz von Quell Puffern für einen Projektions Puffer ändert und wenn sich der Satz von Quell Puffern ändert.
Ein elisions Puffer ist eine besondere Art von Projektions Puffer. Es wird hauptsächlich zum Gliedern und für Vorgänge verwendet, die Textblöcke erweitern und reduzieren. Ein elisions Puffer basiert auf nur einem Quell Puffer, und die Spannen im elisions Puffer müssen so angeordnet werden, wie Sie im Quell Puffer angeordnet sind.

#### <a name="the-buffer-graph"></a>Das Puffer Diagramm

Die- <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Schnittstelle ermöglicht die Zuordnung in einem Diagramm von Projektions Puffern. Alle Text Puffer und Projektions Puffer werden in einem gerichteten azyklischen Diagramm gesammelt, ähnlich wie bei der abstrakten Syntax Struktur, die von einem sprach Compiler erzeugt wird. Das Diagramm wird durch den obersten Puffer definiert, bei dem es sich um einen beliebigen Text Puffer handeln kann. Das Puffer Diagramm kann von einem Punkt im oberen Puffer zu einem Punkt in einem Quell Puffer oder von einer Spanne im obersten Puffer zu einem Satz von spannen in einem Quell Puffer zugeordnet werden. Ebenso kann ein Punkt oder eine Spanne von einem Quell Puffer zu einem Punkt im obersten Puffer zugeordnet werden. Puffer Diagramme werden mithilfe von erstellt <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Ereignisse und Projektions Puffer

Wenn ein Projektions Puffer geändert wird, werden die Änderungen vom Projektions Puffer an die Puffer gesendet, die von ihm abhängen. Nachdem alle Puffer geändert wurden, werden Puffer Änderungs Ereignisse ausgelöst, beginnend mit dem tiefsten Puffer.

### <a name="outlining"></a>Gliedern

Gliederung ist die Möglichkeit, unterschiedliche Textblöcke in einer Textansicht zu erweitern oder zu reduzieren. Gliederung ist als Art von definiert <xref:Microsoft.VisualStudio.Text.Tagging.ITag> , und zwar auf dieselbe Weise wie Zusatzelemente definiert werden. Ein <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ist ein Tag, das einen Textbereich definiert, der erweitert oder reduziert werden kann. Wenn Sie Gliederung verwenden möchten, müssen Sie den importieren, <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> um eine zu erhalten <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Der Gliederungs-Manager listet die verschiedenen Blöcke auf, reduziert Sie und erweitert Sie, die als <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> -Objekte dargestellt werden, und löst die-Ereignisse entsprechend aus.

### <a name="mouse-bindings"></a>Maus Bindungen

Maus Bindungen verknüpfen Mausbewegungen mit verschiedenen Befehlen. Maus Bindungen werden mithilfe von definiert <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> , und Tastenbindungen werden mithilfe von definiert <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Instanziiert automatisch alle Bindungen und verbindet Sie mit Mausereignissen in der Ansicht.

Die <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> -Schnittstelle enthält Ereignisse vor und nach der Verarbeitung für verschiedene Mausereignisse. Um eines der-Ereignisse zu behandeln, können Sie einige der Methoden in überschreiben <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Editor-Vorgänge

Editor Vorgänge können verwendet werden, um die Interaktion mit dem Editor für die Skripterstellung oder andere Zwecke zu automatisieren. Sie können den <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> in den Zugriff auf Vorgänge für eine angegebene importieren <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Anschließend können Sie diese Objekte verwenden, um die Auswahl zu ändern, einen Bildlauf in der Ansicht durchführen oder die Einfügemarke in verschiedene Teile der Ansicht zu verschieben.

### <a name="intellisense"></a>IntelliSense

IntelliSense unterstützt Anweisungs Vervollständigung, Signatur Hilfe (auch als Parameter Info bezeichnet), Quick Infos und Glühbirnen.

Die Anweisungs Vervollständigung bietet Popup Listen mit möglichen Vervollständigungen für Methodennamen, XML-Elemente und andere Codierungs-oder Markup Elemente. Im allgemeinen Ruft eine Benutzer Geste eine Abschlusssitzung auf. In der Sitzung wird die Liste der möglichen Vervollständigungen angezeigt, und der Benutzer kann eine Liste auswählen oder die Liste verwerfen. Der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ist für das Erstellen und Auslösen von verantwortlich <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>Berechnet den <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> von Vervollständigungs Elementen für die Sitzung.

## <a name="see-also"></a>Weitere Informationen

- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
- [Editor Importe](../extensibility/editor-imports.md)
