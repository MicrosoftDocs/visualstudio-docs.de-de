---
title: Übersicht über das sprach Server Protokoll | Microsoft-Dokumentation
description: Erfahren Sie, wie das Sprachserver Protokoll ein nützliches Framework zum verfügbar machen von sprach Features für eine Vielzahl von Tools bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f9a7766d4462ffbd74073448f49457215eb79a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943282"
---
# <a name="language-server-protocol"></a>Sprachserverprotokoll

## <a name="what-is-the-language-server-protocol"></a>Was ist das sprach Server Protokoll?

Die Unterstützung umfangreicher Bearbeitungs Features wie z. b. die automatische Vervollständigung von Quellcode oder **die Definition von gehe zu Definition** für eine Programmiersprache in einem Editor oder in IDE ist bislang sehr schwierig und zeitaufwändig In der Regel ist es erforderlich, ein Domänen Modell (einen Scanner, einen Parser, eine Typüberprüfung, einen Generator usw.) in der Programmiersprache des Editors oder der IDE zu schreiben. Beispielsweise wird das Eclipse CDT-Plug-in, das C/C++ in der Eclipse-IDE unterstützt, in Java geschrieben, da die Eclipse-IDE selbst in Java geschrieben ist. Nach diesem Ansatz würde dies bedeuten, dass ein C/C++-Domänen Modell in TypeScript für Visual Studio Code implementiert wird, und ein separates Domänen Modell in c# für Visual Studio.

Das Erstellen sprachspezifischer Domänen Modelle ist auch viel einfacher, wenn ein Entwicklungs Tool vorhandene sprachspezifische Bibliotheken wieder verwenden kann. Diese Bibliotheken werden jedoch in der Regel in der Programmiersprache selbst implementiert (z. b. werden gute c/C++-Domänen Modelle in c/C++ implementiert). Das Integrieren einer C/C++-Bibliothek in einen Editor, der in typescript geschrieben wurde, ist technisch möglich, aber schwierig zu erledigen.

### <a name="language-servers"></a>Sprachserver

Ein anderer Ansatz besteht darin, die Bibliothek in einem eigenen Prozess auszuführen und die prozessübergreifende Kommunikation zu verwenden. Die zurückgesendeten Nachrichten bilden ein Protokoll. Das Sprachserver Protokoll (Language Server Protocol, LSP) ist das Produkt der Standardisierung der zwischen einem Entwicklungs Tool und einem Sprachserver Prozess ausgetauschten Nachrichten. Die Verwendung von Sprach Servern oder Dämonen ist keine neue oder neue Idee. Editoren wie vim und Emacs haben dies seit einiger Zeit getan, um Unterstützung für die automatische Vervollständigung zu bieten. Das Ziel des LSP bestand darin, diese Arten von Integrationen zu vereinfachen und ein nützliches Framework bereitzustellen, um sprach Features für eine Vielzahl von Tools verfügbar zu machen.

Ein gemeinsames Protokoll ermöglicht die Integration von Programmiersprachen Funktionen in ein Entwicklungs Tool mit minimalem Aufwand, indem eine vorhandene Implementierung des Domänen Modells der Sprache wieder verwendet wird. Ein Sprachserver-Back-End konnte in PHP, Python oder Java geschrieben werden, und das LSP ermöglicht die einfache Integration in eine Reihe von Tools. Das Protokoll arbeitet auf einer allgemeinen Abstraktions Ebene, sodass ein Tool umfangreiche Sprachdienste anbieten kann, ohne die für das zugrunde liegende Domänen modellspezifischen Besonderheiten vollständig verstehen zu müssen.

## <a name="how-work-on-the-lsp-started"></a>Starten der Arbeit am LSP

Der LSP hat sich im Laufe der Zeit weiterentwickelt und ist heute die Version 3,0. Es begann, als das Konzept eines sprach Servers von omnisharp übernommen wurde, um umfangreiche Bearbeitungsfunktionen für c# bereitzustellen. Anfänglich hat omnisharp das HTTP-Protokoll mit einer JSON-Nutzlast verwendet und wurde in mehrere Editoren integriert, einschließlich [Visual Studio Code](https://code.visualstudio.com).

Zum gleichen Zeitpunkt begann Microsoft mit der Arbeit an einem typescript-Sprachserver, das Konzept der Unterstützung von typescript in Editoren wie Emacs und Sublime Text. In dieser Implementierung kommuniziert ein Editor über stdin/stdout mit dem typescript-Server Prozess und verwendet eine JSON-Nutzlast, die vom V8-Debugger-Protokoll für Anforderungen und Antworten inspiriert wird. Der typescript-Server wurde in das Sublime-Plug-in typescript integriert und vs Code für die umfassende typescript-Bearbeitung.

Nachdem zwei verschiedene Sprachserver integriert wurden, hat das vs Code Team begonnen, ein Common Language Server-Protokoll für Editoren und IDES zu untersuchen. Ein gängiges Protokoll ermöglicht einem Sprachanbieter, einen einzelnen Sprachserver zu erstellen, der von verschiedenen IDES verwendet werden kann. Ein Sprachserver Consumer muss die Clientseite des Protokolls nur einmal implementieren. Dies führt zu einer Win-Win-Situation für den Sprachanbieter und den sprach Consumer.

Das Sprachserver Protokoll wurde mit dem vom typescript-Server verwendeten Protokoll gestartet und erweitert es um mehr sprach Features, die von der vs Code Language-API inspiriert sind. Das Protokoll wird aufgrund seiner Einfachheit und vorhandener Bibliotheken mit JSON-RPC für Remote Aufrufe gesichert.

Das vs Code Team hat das Protokoll in ein prototypeingegeben, indem es mehrere Linter-Sprachserver implementiert hat, die auf Anforderungen an lint (Scan) einer Datei Antworten und eine Reihe von ermittelten Warnungen und Fehlern zurückgeben. Ziel war es, eine Datei zu bearbeiten, während der Benutzer ein Dokument bearbeitet. Dies bedeutet, dass während einer Editor-Sitzung viele linting-Anforderungen vorhanden sein werden. Es ist sinnvoll, einen Server auf dem Laufenden zu halten, damit ein neuer linting-Prozess nicht für jede Benutzer Bearbeitung gestartet werden muss. Es wurden mehrere Linter-Server implementiert, einschließlich der eslint-und tlint-Erweiterungen von vs Code. Diese beiden Linter-Server werden in typescript/JavaScript implementiert und auf Node.js ausgeführt. Sie verfügen über eine Bibliothek, die den Client-und Serverteil des Protokolls implementiert.

## <a name="how-the-lsp-works"></a>Funktionsweise des LSP

Ein Sprachserver wird in einem eigenen Prozess ausgeführt, und Tools wie Visual Studio oder vs Code kommunizieren mit dem Server über das sprach Protokoll über JSON-RPC. Ein weiterer Vorteil des sprach Servers, der in einem dedizierten Prozess betrieben wird, ist, dass Leistungsprobleme im Zusammenhang mit einem einzelnen Prozessmodell vermieden werden. Der eigentliche Transport Kanal kann entweder stdio, Sockets, Named Pipes oder Node IPC lauten, wenn sowohl der Client als auch der Server in Node.js geschrieben sind.

Im folgenden finden Sie ein Beispiel für die Kommunikation zwischen einem Tool und einem Sprachserver während einer routinemäßigen Bearbeitungs Sitzung:

![LSP-Flussdiagramm](media/lsp-flow-diagram.png)

* **Der Benutzer öffnet eine Datei (als Dokument bezeichnet) im Tool**: das Tool benachrichtigt den Sprachserver, dass ein Dokument geöffnet ist (' TextDocument/didopen '). Ab jetzt wird die Wahrheit über den Inhalt des Dokuments nicht mehr im Dateisystem, sondern vom Tool im Arbeitsspeicher beibehalten.

* **Der Benutzer nimmt Änderungen** vor: das Tool benachrichtigt den Server über die Dokument Änderung (' TextDocument/didchange '), und die semantischen Informationen des Programms werden vom Sprachserver aktualisiert. In diesem Fall analysiert der Sprachserver diese Informationen und benachrichtigt das Tool mit den erkannten Fehlern und Warnungen ("TextDocument/publishdiagnostics").

* **Der Benutzer führt "Gehe zu Definition" für ein Symbol im Editor** aus: das Tool sendet eine TextDocument/Definition-Anforderung mit zwei Parametern: (1) den Dokument-URI und (2) die Textposition, von der aus die gehe zu Definition-Anforderung an den Server initiiert wurde. Der Server antwortet mit dem Dokument-URI und der Position der Symbol Definition innerhalb des Dokuments.

* **Der Benutzer schließt das Dokument (Datei)**: eine "TextDocument/didclose"-Benachrichtigung wird vom Tool gesendet, um den Sprachserver darüber zu informieren, dass das Dokument nun nicht mehr im Arbeitsspeicher vorhanden ist und dass der aktuelle Inhalt nun auf dem Dateisystem aktuell ist.

In diesem Beispiel wird veranschaulicht, wie das Protokoll mit dem Sprachserver auf der Ebene der Editor-Funktionen wie "Gehe zu Definition", "alle Verweise suchen" kommuniziert. Die vom Protokoll verwendeten Datentypen sind Editor-oder IDE-Datentypen, wie z. b. das aktuell geöffnete Textdokument und die Position des Cursors. Die Datentypen befinden sich nicht auf der Ebene eines Programmiersprachen-Domänen Modells, das normalerweise abstrakte Syntax Strukturen und compilersymbole (z. b. aufgelöste Typen, Namespaces,...) bereitstellt. Dadurch wird das Protokoll erheblich vereinfacht.

Sehen wir uns nun die TextDocument/Definition-Anforderung ausführlicher an. Im folgenden finden Sie die Nutzlasten zwischen dem Client Tool und dem Sprachserver für die Anforderung "Gehe zu Definition" in einem C++-Dokument.

Dies ist die Anforderung:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Dies ist die Antwort:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Im Nachhinein ist eine Beschreibung der Datentypen auf der Ebene des Editors anstelle der Ebene des Programmiersprachen Modells einer der Gründe für den Erfolg des Sprachserver Protokolls. Es ist wesentlich einfacher, einen Textdokument-URI oder eine Cursorposition zu standardisieren, verglichen mit der Standardisierung einer abstrakten Syntax Struktur und compilersymbolen über verschiedene Programmiersprachen.

Wenn ein Benutzer mit verschiedenen Sprachen arbeitet, wird vs Code in der Regel einen Sprachserver für jede Programmiersprache starten. Das folgende Beispiel zeigt eine Sitzung, in der der Benutzer an Java-und Sass-Dateien arbeitet.

![Java und sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funktionen

Nicht jeder Sprachserver kann alle Funktionen unterstützen, die durch das Protokoll definiert werden. Aus diesem Grund kündigen Client und Server die unterstützten Features über "Funktionen" an. Ein Server gibt beispielsweise an, dass er die Anforderung ' TextDocument/Definition ' verarbeiten kann, aber die Anforderung ' Workspace/Symbol ' möglicherweise nicht verarbeitet. Auf ähnliche Weise können Clients ankündigen, dass Sie Benachrichtigungen zu speichern bereitstellen können, bevor ein Dokument gespeichert wird, sodass ein Server Text bearbeitevorgänge berechnen kann, um das bearbeitete Dokument automatisch zu formatieren.

## <a name="integrating-a-language-server"></a>Integrieren eines sprach Servers

Die tatsächliche Integration eines sprach Servers in ein bestimmtes Tool ist nicht durch das Sprachserver Protokoll definiert und wird den Toolimplementierungen überlassen. Einige Tools integrieren Sprachserver generisch, indem Sie eine Erweiterung haben, die mit jeder beliebigen Art von Sprachserver beginnen und kommunizieren kann. Andere, wie z. b. vs Code, erstellen eine benutzerdefinierte Erweiterung pro Sprachserver, sodass eine Erweiterung weiterhin einige benutzerdefinierte sprach Features bereitstellen kann.

Um die Implementierung von Sprach Servern und Clients zu vereinfachen, sind Bibliotheken oder sdche für die Client-und Server Teile vorhanden. Diese Bibliotheken werden für verschiedene Sprachen bereitgestellt. Beispielsweise gibt es ein [NPM-Modul für den Sprachclient](https://www.npmjs.com/package/vscode-languageclient) , um die Integration eines sprach Servers in eine vs Code Erweiterung und ein weiteres [Sprachserver-NPM](https://www.npmjs.com/package/vscode-languageserver) -Modul zum Schreiben eines sprach Servers mithilfe von Node.js zu vereinfachen. Dies ist die aktuelle [Liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) der Unterstützungs Bibliotheken.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Verwenden des sprach Server Protokolls in Visual Studio

* [Hinzufügen einer Sprachserver-Protokollerweiterung](adding-an-lsp-extension.md) : Hier erfahren Sie, wie Sie einen Sprachserver in Visual Studio integrieren.
