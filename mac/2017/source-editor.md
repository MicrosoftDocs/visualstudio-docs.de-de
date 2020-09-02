---
title: Quellcode-Editor
description: Verwendung des Quellcode-Editors in Visual Studio für Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985219"
---
# <a name="source-editor"></a>Quellcode-Editor

Ein zuverlässiger Quellcode-Editor ist entscheidend für kurzen und effizienten Code. Visual Studio für Mac bietet einen anspruchsvollen Quellcode-Editor, der das Herzstück der IDE darstellt. Der Quellcode-Editor stellt Features bereit, die Sie möglicherweise erwarten und benötigen, um Ihre Arbeit mühelos durchzuführen: von den Grundlagen wie der Syntaxhervorhebung, über Codeausschnitte und der Codefaltung, bis hin zu den Vorteilen der Roslyn-Compilerintegration wie eine voll funktionale IntelliSense-Codevervollständigung.

Der Quellcode-Editor in Visual Studio für Mac funktioniert problemlos mit allen anderen Funktionen der IDE, z.B. dem Debuggen, der Umgestaltung und der Integration der Versionskontrolle.

In diesem Artikel werden die wichtigsten Funktionen des Quellcode-Editors eingeführt, und es wird erklärt, wie Sie Visual Studio für Mac so effektiv wie möglich verwenden können.

## <a name="the-source-editor-experience"></a>Benutzeroberfläche des Quellcode-Editors

Die Fähigkeit, den Code anzuzeigen und sich schnell darin bewegen zu können, ist wesentlich für den Entwicklungsworkflow. Wie Sie den Code anzeigen und verwalten, ist eine persönliche Entscheidung, die sich je nach Entwickler und Projekt unterscheidet.

Visual Studio für Mac bietet viele leistungsstarke Funktionen, mit denen die plattformübergreifende Entwicklung zugänglich und so übersichtlich wie möglich gestaltet wird. In den folgenden Abschnitten werden einige der Highlights beschrieben.

## <a name="code-folding"></a>Codefaltung

Die Codefaltung erleichtert das Verwalten großer Quellcodedateien, da Entwickler vollständige Codeabschnitte wie using-Direktiven, Codebausteine und -kommentare und #region-Anweisungen anzeigen oder ausblenden können. Codefaltung ist in Visual Studio für Mac standardmäßig deaktiviert.

Navigieren Sie zum Aktivieren der Codefaltung zu **Visual Studio > Einstellungen > Text-Editor > Allgemein > Codefaltung**:

![Optionen für die Codefaltung](media/source-editor-image1.png)

Dieses Menü enthält auch eine Option zum standardmäßigen Falten von #regions und Kommentaren, wobei ein benannter Hinweis anstelle von Code angezeigt wird.

Verwenden Sie zum Anzeigen oder Ausblenden von Abschnitten das Anzeigewidget neben der Zeilennummer:

![Ein- oder Ausblenden von Abschnitten im Code](media/source-editor-image2.png)

Sie können auch über die Menüelemente **Ansicht > Faltung > Toggle Fold (Faltung umschalten)/Toggle All Folds (Alle Faltungen umschalten)** zwischen dem Ein- und Ausblenden der Faltungen wechseln:

![Menüelement „Faltung“](media/source-editor-image19.png)

Dieses Menüelement kann auch zur Aktivierung oder Deaktivierung der Codefaltung verwendet werden.

## <a name="white-space"></a>Leerzeichen

Es kann für Sie notwendig sein, unsichtbare Zeichen im Quellcode zu sehen. So können Sie sicherstellen, dass Codierungsstandards eingehalten und Speicherplatz nicht unnötigerweise verschwendet wird. Auch beim Programmieren in F# ist dies nützlich, denn dabei kommt es bei der Bewertung von Code genau auf die eingezogenen Zeilen an.

Um Leerzeichen anzuzeigen, navigieren Sie zu **Visual Studio > Einstellungen > Text-Editor > Markierungen und Lineale**. Wenn Sie diese Option auswählen, können Sie festlegen, _wann_ unsichtbare Zeichen angezeigt werden sollen: „Never“ (Nie), „On Selection“ (Bei Auswahl) oder „Always“ (Immer):

![Optionen zum Anzeigen unsichtbarer Zeichen](media/source-editor-image3.png)

Es ist ebenfalls eine Option zum Anzeigen von Registerkarten, Leerzeichen und Zeilenenden verfügbar:

![Anzeigen von Registerkarten und Leerzeichen](media/source-editor-image4.png)

Unsichtbare Zeichen werden als graue Punkte angezeigt, wie in der folgenden Abbildung dargestellt:

![Leerzeichen angezeigt](media/source-editor-image22.png)

## <a name="ruler"></a>Lineal

Das Spaltenlineal ist sehr hilfreich für die Bestimmung von Zeilenlängen, insbesondere dann, wenn ein Team Vorgaben für die Zeilenlänge hat. Das Spaltenlineal kann aktiviert oder deaktiviert werden, indem Sie zu **Visual Studio > Einstellungen > Text-Editor > Markes and Rulers (Markierungen und Lineale)** navigieren und **Show Column ruler** (Spaltenlineal anzeigen) wie in der folgenden Abbildung gezeigt aktivieren (bzw. deaktivieren):

![Dialogfeld „Preferences“ (Einstellungen) mit aktiviertem Kontrollkästchen „Show column ruler“ (Spaltenlineal anzeigen)](media/source-editor-image5.png)

 Dadurch wird im Quellcode-Editor eine vertikale, hellgraue Linie angezeigt.

## <a name="highlight-identifier-references"></a>Hervorheben von Bezeichnerverweisen

Wenn die Option „Hervorheben von Bezeichnerverweisen“ aktiviert ist, können Sie jedes Symbol im Quellcode auswählen, und der Quellcode-Editor stellt eine visuelle Anleitung zu allen anderen Verweisen in dieser Datei bereit. Wechseln Sie zum Aktivieren dieser Option zu **Visual Studio > Einstellungen > Text-Editor > Markers and Rulers** (Markierungen und Lineale), und wählen Sie _Highlight identifier references_ (Bezeichnerverweise hervorheben) wie in der folgenden Abbildung gezeigt aus:

![Dialogfeld „Preferences“ (Einstellungen) mit markiertem Kontrollkästchen „Highlight identifier references“ (Hervorheben von Bezeichnerverweisen)](media/source-editor-image6.png)

Die Farbe der Hervorhebung ist auch hilfreich, wenn angegeben werden soll, dass etwas zugewiesen oder darauf verwiesen wird. Wenn etwas zugewiesen wird, wird es in Rot hervorgehoben. Wenn darauf verwiesen wird, ist die Hervorhebung blau:

![Beispiel für die Markierungsfarbe](media/source-editor-image7.png)

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors (Visual Studio unter Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Gliederung (Visual Studio unter Windows)](/visualstudio/ide/outlining)