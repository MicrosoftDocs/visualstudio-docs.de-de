---
title: Debugger-Komponenten | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Elemente, die eine Debugsitzung bilden, die vom Visual Studio-Debugger verwaltet wird und als VSPackage implementiert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2fa0a7feb85437cc8173d52695ddb1ba0d2c06b7
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914100"
---
# <a name="debugger-components"></a>Debugger-Komponenten
Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger wird als VSPackage implementiert und verwaltet die gesamte Debugsitzung. Die Debugsitzung umfasst die folgenden Elemente:

- **Paket Debuggen:** Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger stellt die gleiche Benutzeroberfläche bereit, unabhängig davon, was gerade gedebuggt wird.

- **Sitzungsdebug-Manager (SDM):** Stellt eine konsistente programmgesteuerte Schnittstelle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für den Debugger zur Verwaltung einer Vielzahl von Debug-engines bereit. Sie wird von implementiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Process Debug Manager (PDM):** Verwaltet für alle ausgelaufenden Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine Liste aller Programme, die bzw. das gedebuggt werden kann. Sie wird von implementiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Debug-Engine (de):** Ist für die Überwachung eines Programms zuständig, das gedebuggt wird, wobei der Status des ausgelaufenden Programms an SDM und PDM kommuniziert und mit der Ausdrucks Auswertung und dem Symbol Anbieter interagiert wird, um Echtzeitanalysen des Zustands des Arbeitsspeichers und der Variablen eines Programms zu ermöglichen. Sie wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die unterstützten Sprachen) und von Drittanbietern implementiert, die ihre eigene Laufzeit unterstützen möchten.

- **Ausdrucks Auswertung (EE):** Bietet Unterstützung für das dynamische Auswerten von Variablen und Ausdrücken, die vom Benutzer bereitgestellt werden, wenn ein Programm an einem bestimmten Punkt angehalten wurde. Sie wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die unterstützten Sprachen) und von Drittanbietern implementiert, die ihre eigenen Sprachen unterstützen möchten.

- **Symbol Anbieter (SP):** Wird auch als Symbol Handler bezeichnet und ordnet die Debugsymbole eines Programms einer ausgelaufenden Instanz des Programms zu, damit sinnvolle Informationen bereitgestellt werden können (z. b. Debuggen auf Quell Code Ebene und Ausdrucks Auswertung). Sie wird von implementiert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (für die CLR-Symbole (Common Language Runtime) und das Format der Programmdatenbank [PDB]-Symbol Datei) und von Drittanbietern, die über eine eigene proprietäre Methode zum Speichern von Debuginformationen verfügen.

  Das folgende Diagramm zeigt die Beziehung zwischen diesen Elementen des Visual Studio-Debuggers.

  ![Übersicht über das Debuggen von Komponenten](../../extensibility/debugger/media/dbugcompovrview.gif "Dbugcompovrview")

## <a name="in-this-section"></a>In diesem Abschnitt
 [Paket Debuggen](../../extensibility/debugger/debug-package.md) Erläutert das Debugpaket, das in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ausgeführt wird und die gesamte Benutzeroberfläche verarbeitet.

 [Process Debug Manager](../../extensibility/debugger/process-debug-manager.md) Bietet eine Übersicht über die Features des PDM, das der Manager der Prozesse ist, die gedebuggten werden können.

 [Sitzungs-Debug-Manager](../../extensibility/debugger/session-debug-manager.md) Definiert das SDM, das eine einheitliche Ansicht der Debugsitzung für die IDE bereitstellt. Der SDM verwaltet den de.

 [Debug-Engine](../../extensibility/debugger/debug-engine.md) Dokumentiert die Debugdienste, die von der de bereitstellt werden.

 [Betriebsmodi](../../extensibility/debugger/operational-modes.md) Bietet eine Übersicht über die drei Modi, in denen die IDE funktionieren kann: Entwurfs Modus, Lauf Modus und Abbruch Modus. Übergangsmechanismen werden ebenfalls erläutert.

 [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluator.md) Erläutert den Zweck der EE zur Laufzeit.

 [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md) Erläutert, wie der Symbol Anbieter bei der Implementierung Variablen und Ausdrücke auswertet.

 [Typschnell Ansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Erläutert, worum es sich bei einer typschnell Ansicht und einem benutzerdefinierten Viewer handelt und welche Rolle die Ausdrucks Auswertung bei der Unterstützung von beidem spielt.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) erläutert, wie die DE gleichzeitig innerhalb von Code-, Dokumentations- und Ausdrucksauswertungskontexten funktioniert. Es wird für jeden der drei Kontexte der Speicherort, die Position oder die Auswertung beschrieben, der bzw. die für ihn relevant ist.

 [Aufgaben Debuggen](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
