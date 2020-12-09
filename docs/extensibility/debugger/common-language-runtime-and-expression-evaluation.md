---
title: Common Language Runtime und Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie, wie die Common Language Runtime mit der Debug-Engine interagiert und wie Sie eine proprietäre Programmiersprache in die Visual Studio-IDE integrieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c120ac1da59ab86e9419bcb031af46f1b3d900
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914256"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime und Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Compiler, wie z. b. Visual Basic und c# (ausgesprochen C-Sharp), die auf die Common Language Runtime (CLR) abzielen, erzeugen eine Microsoft Intermediate Language (MSIL), die später in nativem Code kompiliert wird. Die CLR stellt eine Debug-Engine (de) zum Debuggen des resultierenden Codes bereit. Wenn Sie beabsichtigen, ihre proprietäre Programmiersprache in die Visual Studio-IDE zu integrieren, können Sie die Kompilierung in MSIL durchführt, sodass Sie keine eigene de schreiben müssen. Sie müssen jedoch eine Ausdrucks Auswertung (EE) schreiben, mit der Ausdrücke im Kontext der Programmiersprache ausgewertet werden können.

## <a name="discussion"></a>Diskussion
 Computer sprach Ausdrücke werden in der Regel analysiert, um einen Satz von Datenobjekten und eine Reihe von Operatoren zu entwickeln, die zur Bearbeitung verwendet werden. Beispielsweise kann der Ausdruck "a + B" analysiert werden, um den Additions Operator (+) auf die Datenobjekte "a" und "B" anzuwenden, was möglicherweise zu einem anderen Datenobjekt führt. Der gesamte Satz von Datenobjekten, Operatoren und deren Zuordnungen wird am häufigsten in einem Programm als Struktur dargestellt, mit den Operatoren an den Knoten der Struktur und den Datenobjekten in den Verzweigungen. Ein Ausdruck, der in die Struktur Form aufgeteilt wurde, wird häufig als analysierte Struktur bezeichnet.

 Nachdem ein Ausdruck analysiert wurde, wird ein Symbol Anbieter (SP) aufgerufen, um die einzelnen Datenobjekte auszuwerten. Wenn z. b. "A" in mehr als einer Methode definiert ist, wird die Frage "welche a?" muss beantwortet werden, bevor der Wert eines ermittelt werden kann. Die Antwort, die vom SP zurückgegeben wird, ist etwa "das dritte Element im fünften Stapel Rahmen" oder "die A, die nach dem Anfang des statischen Speichers, der dieser Methode zugeordnet ist, 50 Bytes überschreitet."

 Neben der Erstellung von MSIL für das Programm selbst können CLR-Compiler auch sehr beschreibende Debuginformationen erzeugen, die in eine Programm Datenbankdatei (*. pdb*) geschrieben werden. Solange ein Compiler einer proprietären Sprache Debuginformationen im gleichen Format wie die CLR-Compiler erstellt, kann der CLR-SP die benannten Datenobjekte dieser Sprache identifizieren. Nachdem ein benanntes Datenobjekt identifiziert wurde, verwendet das EE ein Binder Objekt, um das Datenobjekt dem Speicherbereich zuzuordnen (oder zu binden), der den Wert dieses Objekts enthält. Der de kann dann einen neuen Wert für das Datenobjekt erhalten oder festlegen.

 Proprietäre Compiler können CLR-Debuginformationen bereitstellen, indem Sie die- `ISymbolWriter` Schnittstelle aufrufen (die im-.NET Framework im-Namespace definiert ist `System.Diagnostics.SymbolStore` ). Durch Kompilieren in MSIL und Schreiben von Debuginformationen über diese Schnittstellen kann ein proprietärer Compiler die CLR de und SP verwenden. Dies vereinfacht die Integration einer proprietären Sprache in die Visual Studio-IDE erheblich.

 Wenn die CLR de den proprietären EE aufruft, um einen Ausdruck auszuwerten, stellt der de den EE mit Schnittstellen an einen SP-und ein Binder Objekt bereit. Daher ist das Schreiben einer CLR-basierten Debug-Engine nur erforderlich, um die entsprechenden Ausdrucks auswerterschnitt stellen zu implementieren. die CLR kümmert sich um die Bindung und die Symbol Behandlung für Sie.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
