---
title: Dekompilieren von .NET-Code beim Debuggen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Quellcode aus .NET-Assemblys während des Debuggens in Visual Studio generieren und einbetten. Hierzu müssen Sie den eingebetteten Quellcode extrahieren und anzeigen.
ms.custom: SEO-VS-2020
ms.date: 2/2/2020
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 8ad919b14642dff98746c194ad8c05bbb3aea529
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726734"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generieren von Quellcode aus .NET-Assemblys beim Debuggen

Wenn Sie eine .NET-Anwendung debuggen, möchten Sie möglicherweise Quellcode anzeigen, über den Sie nicht verfügen. Dies kann z. B. der Fall sein, um die Ausführung bei einer Ausnahme zu unterbrechen oder mithilfe der Aufrufliste zu einer Position im Quellcode zu navigieren.

> [!NOTE]
> * Die Quellcodegenerierung (Dekompilierung) ist nur für .NET-Anwendungen verfügbar und basiert auf dem [ILSpy](https://github.com/icsharpcode/ILSpy)-Open Source-Projekt.
> * Dekompilierung ist nur in Visual Studio 2019 16.5 und höher verfügbar.
> * Durch Anwenden des [SuppressIldasmAttribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) auf eine Assembly oder ein Modul wird die Kompilierung in Visual Studio verhindert.

## <a name="generate-source-code"></a>Generieren von Quellcode

Wenn Sie debuggen und kein Quellcode verfügbar ist, wird in Visual Studio das Dokument **Quelle nicht gefunden** angezeigt. Wenn keine Symbole für die Assembly vorhanden sind, wird das Dokument **Keine Symbole geladen** angezeigt. Beide Dokumente verfügen über die Option **Quellcode dekompilieren**, mit der C#-Code für die aktuelle Position generiert wird. Der generierte C#-Code kann dann wie jeder andere Quellcode verwendet werden. Sie können den Code anzeigen, Variablen überprüfen, Haltepunkte festlegen usw.

### <a name="no-symbols-loaded"></a>Keine Symbole geladen

In der folgenden Abbildung wird die Meldung **Keine Symbole geladen** gezeigt.

![Screenshot des Dokuments „Keine Symbole geladen“](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Quelle nicht gefunden

In der folgenden Abbildung wird die Meldung **Quelle nicht gefunden** gezeigt.

![Screenshot des Dokuments „Quelle nicht gefunden“](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generieren und Einbetten von Quellcode für eine Assembly

Zusätzlich zum Generieren von Quellcode für eine bestimmte Position können Sie den gesamten Quellcode für eine angegebene .NET-Assembly generieren. Wechseln Sie zu diesem Zweck zum Fenster **Module**, und wählen Sie dann im Kontextmenü einer .NET-Assembly den Befehl **Quellcode dekompilieren** aus. Visual Studio generiert eine Symboldatei für die Assembly und bettet dann den Quellcode in die Symboldatei ein. In einem späteren Schritt können Sie den eingebetteten Quellcode [extrahieren](#extract-and-view-the-embedded-source-code).

![Screenshot des Kontextmenüs der Assembly im Fenster „Module“ mit dem Befehl „Quellcode dekompilieren“](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrahieren und Anzeigen des eingebetteten Quellcodes

Sie können Quelldateien extrahieren, die in eine Symboldatei eingebettet sind. Verwenden Sie dazu den Befehl **Extract Source Code** (Quellcode extrahieren) im Kontextmenü des Fensters **Module**.

![Screenshot des Kontextmenüs der Assembly im Fenster „Module“ mit dem Befehl zum Extrahieren des Quellcodes](media/decompilation-extract-source-code.png)

Die extrahierten Quelldateien werden der Projektmappe als [Sonstige Dateien](../ide/reference/miscellaneous-files.md) hinzugefügt. Das Feature „Sonstige Dateien“ ist in Visual Studio standardmäßig deaktiviert. Sie können dieses Feature mit dem Kontrollkästchen **Extras** > **Optionen** > **Umgebung** > **Dokumente** > **Sonstige Dateien im Projektmappen-Explorer anzeigen** aktivieren. Wenn Sie dieses Feature nicht aktivieren, können Sie den extrahierten Quellcode nicht öffnen.

![Screenshot der Seite „Optionen“ unter „Extras“ mit aktivierter Option für sonstige Dateien](media/decompilation-tools-options-misc-files.png)

Extrahierte Quelldateien werden in den sonstigen Dateien im **Projektmappen-Explorer** angezeigt.

![Screenshot des Projektmappen-Explorers mit sonstigen Dateien](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="requires-break-mode"></a>Unterbrechungsmodus erforderlich

Das Generieren von Quellcode durch Dekompilierung ist nur möglich, wenn sich der Debugger im Unterbrechungsmodus befindet und die Anwendung angehalten wurde. Beispielsweise wechselt Visual Studio in den Unterbrechungsmodus, wenn ein Haltepunkt oder eine Ausnahme erreicht wird. Mit dem Befehl **Alle unterbrechen** (![Symbol „Alle unterbrechen“](media/decompilation-break-all.png)) können Sie bei der nächsten Ausführung des Codes in Visual Studio den Unterbrechungsmodus aktivieren.

### <a name="decompilation-limitations"></a>Einschränkungen bei der Dekompilierung

Das Erzeugen von Quellcode aus dem Zwischenformat (IL), das in .NET-Assemblys verwendet wird, ist mit einigen Einschränkungen verbunden. Der generierte Quellcode sieht nicht wie der ursprüngliche Quellcode aus. Die meisten Unterschiede bestehen an Stellen, an denen die Informationen im ursprünglichen Quellcode zur Laufzeit nicht benötigt werden. Beispielsweise werden Informationen wie Leerzeichen, Kommentare und die Namen lokaler Variablen zur Laufzeit nicht benötigt. Es wird empfohlen, den generierten Quellcode zum besseren Verständnis der Programmausführung und nicht als Ersatz für den ursprünglichen Quellcode zu verwenden.

### <a name="debug-optimized-or-release-assemblies"></a>Debuggen von optimierten oder Releaseassemblys

Beim Debuggen von Code, der aus einer mit Compileroptimierungen kompilierten Assembly dekompiliert wurde, können die folgenden Probleme auftreten:
- Haltepunkte werden möglicherweise nicht immer an die entsprechende Quellcodeposition gebunden.
- Die schrittweise Ausführung endet möglicherweise nicht immer an der richtigen Position.
- Lokale Variablen weisen möglicherweise keine korrekten Namen auf.
- Einige Variablen können möglicherweise nicht ausgewertet werden.

Weitere Informationen finden Sie im GitHub-Problem: [ICSharpCode.Decompiler integration into VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901) (Integration von ICSharpCode.Decompiler in den VS-Debugger, in englischer Sprache).

### <a name="decompilation-reliability"></a>Zuverlässigkeit der Dekompilierung

Ein relativ kleiner Prozentsatz der Dekompilierungen führt möglicherweise zu einem Fehler. Die Ursache ist ein Fehler aufgrund eines Sequenzpunkt-Nullverweises in ILSpy.  Wir haben den Fehler abgeschwächt, indem diese Probleme abgefangen werden und die Dekompilierung ordnungsgemäß abgebrochen wird.

Weitere Informationen finden Sie im GitHub-Problem: [ICSharpCode.Decompiler integration into VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901) (Integration von ICSharpCode.Decompiler in den VS-Debugger, in englischer Sprache).

### <a name="limitations-with-async-code"></a>Einschränkungen bei asynchronem Code

Die Ergebnisse der Dekompilierung von Modulen mit async/await-Codemustern sind möglicherweise unvollständig, oder die Dekompilierung schlägt vollständig fehl. Die ILSpy-Implementierung von async/await- und yield-Zustandsautomaten ist unvollständig. 

Weitere Informationen finden Sie im GitHub-Problem: [PDB Generator Status](https://github.com/icsharpcode/ILSpy/issues/1422) (PDB-Generator-Status, in englischer Sprache).

### <a name="just-my-code"></a>Nur eigenen Code

Mit den Einstellungen für [Nur eigenen Code (Just My Code, JMC)](./just-my-code.md) können System-, Framework-, Bibliotheks- und andere nicht benutzerseitige Aufrufe in Visual Studio übersprungen werden. Während einer Debugsitzung wird im Fenster **Module** angezeigt, welche Codemodule vom Debugger als eigener Code (Benutzercode) behandelt werden.

Bei der Dekompilierung von optimierten oder Releasemodulen wird Nichtbenutzercode erzeugt. Wenn der Debugger beispielsweise die Ausführung von dekompiliertem Nichtbenutzercode unterbricht, wird das Fenster **Keine Quelle** angezeigt. Um „Nur eigenen Code“ zu deaktivieren, navigieren Sie zu **Extras** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debugging** > **Allgemein**, und deaktivieren Sie dann **Nur meinen Code aktivieren**.

### <a name="extracted-sources"></a>Extrahierter Quellcode

Aus einer Assembly extrahierter Quellcode weist die folgenden Einschränkungen auf:
- Der Name und der Speicherort der generierten Dateien sind nicht konfigurierbar.
- Die Dateien sind temporär und werden von Visual Studio gelöscht.
- Die Dateien werden in einem einzelnen Ordner abgelegt, und die ggf. vorhandene Ordnerhierarchie der ursprünglichen Quellcodedateien wird nicht verwendet.
- Der Dateiname für jede Datei enthält einen Prüfsummenhash der Datei.

### <a name="generated-code-is-c-only"></a>Es wird nur C#-Code generiert
Bei der Dekompilierung werden nur Quellcodedateien in C# generiert. Es gibt keine Option zum Generieren von Dateien in einer anderen Sprache.