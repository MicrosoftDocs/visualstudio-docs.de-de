---
title: Glossar für Visual Studio-Debugger | Microsoft-Dokumentation
description: In diesem Artikel werden verschiedene Begriffe erläutert, die im Visual Studio-debuggingsdk verwendet werden, z. b. gebundene Haltepunkte, Kausalität und Code Kontext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0cc5a8b75fd089318434cadea185f8070616cd8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961195"
---
# <a name="visual-studio-debugger-glossary"></a>Glossar zum Visual Studio-Debugger
Im [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debuggingsdk werden die folgenden Begriffe verwendet:

## <a name="terms"></a>Begriffe
 gebundener Haltepunkt eine Abstraktion für einen Haltepunkt, der im Code festgelegt ist. Zwischen einem gebundenen Haltepunkt und einer breakpointanweisung im Codestream besteht eine eins-zu-eins-Beziehung. Wenn Code entladen wird, wird die Bindung gebundener Haltepunkte möglicherweise aufgehoben.

 Kausalität bietet die Möglichkeit, einen logischen Ausführungs Thread über mehrere physische Threads, Prozesse und Computer hinweg zu verfolgen und die aufrufsliste dieses logischen Threads an einem beliebigen Punkt in der Lebensdauer des Threads zu rekonstruieren.

 Code Kontext bietet eine Abstraktion einer Position im Code, der der Debug-Engine bekannt ist. Bei den meisten Lauf Zeit Architekturen ist ein Code Kontext eine Adresse im Anweisungs Datenstrom eines Programms. Bei nicht herkömmlichen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, kann ein Code Kontext auf andere Weise dargestellt werden.

 der Codepfad stellt einen Ausführungs Punkt im Code dar, in dem ein Branch erstellt wird, oder ein Funktions Aufrufwert. Bei einer Stapel Überwachung handelt es sich im Wesentlichen um eine Liste von Code Pfaden für Funktionsaufrufe.

 Debug-Engine (de) eine Komponente, die das Debuggen einer Lauf Zeit Architektur ermöglicht. Ein Debug-Modul funktioniert in Verbindung mit dem Interpreter oder dem Betriebssystem und stellt Debugdienste wie z. b. die Ausführungs Steuerung, Breakpoints und Ausdrucks Auswertung bereit.

 der Dokument Kontext bietet eine Abstraktion einer Position in einem Quelldatei Dokument, das der Debug-Engine bekannt ist. In den meisten Sprachen ist ein Dokument Kontext eine Position in einer Quelldatei. Bei nicht herkömmlichen Sprachen, bei denen es sich bei der Quelldatei möglicherweise nicht um Text handelt, kann ein Dokument Kontext auf andere Weise dargestellt werden. Siehe auch *Dokument Position*.

 die Dokument Position stellt eine Abstraktion einer Position in einer Quelldatei dar, die der IDE bekannt ist. In den meisten Sprachen ist eine Dokument Position eine Position in einer Quelldatei. Bei nicht herkömmlichen Sprachen kann eine Dokument Position auf andere Weise dargestellt werden. Siehe auch *Dokument Kontext*.

 Fehler breakpointpunkt eine Abstraktion zum Beschreiben eines Fehlers in einem ausstehenden Breakpoint. Ein Fehler Haltepunkt kann einen Fehler am Speicherort des ausstehenden halte Punkts, den Ausdruck, der dem ausstehenden Haltepunkt zugeordnet ist, oder andere Informationen beschreiben, die verhindern, dass der ausstehende Haltepunkt an einen Code Speicherort gebunden wird.

 der Auswertungs Kontext stellt eine Abstraktion eines Programmier Kontexts für die Ausdrucks Auswertung bereit. In der Regel ist ein Auswertungs Kontext ein Bereich. Wenn die Ausdrucks Auswertung in einem Ausdrucks Kontext durchgeführt wird, stellt der Ausdrucks Kontext Bereichs Regeln bereit, die dem Zeitpunkt der Erstellung entsprechen. Ein Ausdrucks Kontext, der in einem Stapel Rahmen erstellt wurde, stellt z. b. den Kontext zum Auswerten von lokalen Variablen, Methoden Parametern, Klassenmembern (falls zutreffend) und globalen Variablen bereit.

 abgefangene Ausnahme eine Ausnahme, die von einer Debug-Engine abgefangen wird, auch wenn im aktuellen Stapel Rahmen kein Mechanismus zur Ausnahmebehandlung vorhanden ist.

 JustMyCode: das Konzept des Debuggens von Code, der einem Benutzer angehört, und das Ignorieren des gesamten zwischen Codes, wie z. b. Systemcode – auch dann, wenn Quellcode für diesen Systemcode verfügbar ist.

 der ausstehende Haltepunkt stellt eine Abstraktion für Breakpoints vor, während und nach dem Laden von Code sowie eine Möglichkeit zum Virtualisieren von Breakpoints bereit. Ein ausstehender Haltepunkt:

- Enthält alle Informationen, die erforderlich sind, um einen Breakpoint an Code in einem oder mehreren Programmen zu binden.

- Kann an mehrere Code Speicherorte in einem oder mehreren Programmen gebunden werden.

- Bindet sich niemals an den Code.

  Jedes Mal, wenn Code geladen wird, werden alle ausstehenden Breakpoints in einem Programm geprüft, um festzustellen, ob Sie gebunden werden können. Ein ausstehender Haltepunkt enthält alle gebundenen Haltepunkte, die er bindet.

  Verarbeiten eines physischen Win32-Prozesses. Ein Prozess kann mehrere Programme enthalten. Siehe auch *Programm*.

  Programmieren Sie einen einzelnen Namespace, der innerhalb einer bestimmten Lauf Zeit Architektur ausgeführt wird. Siehe auch *Process*.

  der sitzungsdebug-Manager (SDM) verwaltet eine beliebige Anzahl von Debugmodulen, die beliebig viele Programme in mehreren Prozessen auf einer beliebigen Anzahl von Computern Debuggen. Auf der Basisebene ist SDM ein Multiplexer von Debug-engines. Außerdem bietet die SDM eine einheitliche Ansicht der Debugsitzung für die IDE.

  der Stapel Rahmen stellt den Berechnungs Zustand für einen bestimmten Frame und eine bestimmte Ebene von in der Liste von aufgerufenen Funktionsaufrufen dar.

  Thread das generalisierte Konzept der Stapel basierten Anweisungs Ausführung, das in mindestens einem Programm ausgeführt wird.

  Warnung Haltepunkt eine Abstraktion zum Beschreiben einer Warnung an einem ausstehenden Breakpoint. Ein Warnungs Haltepunkt beschreibt einen Grund, warum der ausstehende Breakpoint noch nicht an einen Code Speicherort gebunden ist. Dies kann daran liegen, dass der Code für den vom ausstehenden Breakpoint beschriebenen Speicherort noch nicht geladen wurde, oder aus einem anderen Grund.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio Debugger-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
