---
title: Erweiterbarkeit von Visual Studio-Debugger | Microsoft-Dokumentation
description: In diesem Artikel wird die Erweiterbarkeit von Visual Studio-Debugger beschrieben und Links zu Artikeln über Visual Studio-debuggen bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a072373ce0cf7633c595eb549455e6ecd62df887
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995992"
---
# <a name="visual-studio-debugger-extensibility"></a>Erweiterbarkeit von Visual Studio-Debugger
Visual Studio enthält einen vollständig interaktiven Quellcode-Debugger, der ein leistungsfähiges und einfach zu verwendende Tool zum Nachverfolgen von Fehlern in Ihrem Programm bereitstellt. Der Debugger bietet umfassende Unterstützung für Visual Basic, c#, C/C++ und JavaScript. Mit der, die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835)verfügbar ist, können jedoch andere Programmiersprachen im Debugger mit denselben umfangreichen Features unterstützt werden.

 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ist das allgemeine Front-End (d. h. die Benutzeroberfläche) für die debuggingkomponenten, die wiederum spezifisch für die zu debuggende Sprache sind. Für neue Sprachen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] müssen Sie lediglich die erforderlichen Back-End-Komponenten erstellen, z. b. eine Debug-Engine (de), um die Unterstützung durch den Debugger zu unterstützen. An diesem Punkt kommt der ins Spiel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Enthält einen vollständigen Verweis auf alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Elemente, die zum Erstellen einer neuen de erforderlich sind. Außerdem finden Sie Beispiele und Lernprogramme, die Ihnen beim Einstieg helfen.

 Ein umfassendes Beispiel eines Sprachprojekt Systems mit Debugunterstützung finden Sie im [IronPython-Beispiel](https://www.microsoft.com/download/details.aspx?id=55984).

 In den folgenden Abschnitten wird beschrieben, wie der Debugger mithilfe von erweitert wird [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>In diesem Abschnitt
 [Einstieg](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Beschreibt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , welche debugangebote und wie das SDK installiert werden soll.

 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) Dokumentiert den benutzerdefinierten de-Prozess, von der Vorbereitung des Programms bis zum Trennen der de.

 [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Erläutert, ob Sie eine Ausdrucks Auswertung schreiben müssen.

 [Auswählen einer Strategie](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) für die Debug-Engine-Implementierung Erläutert, wie Sie Ihre de implementieren.

 [Verweis](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Dokumentiert die Debug- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API.

 [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md) Enthält Links zu einem Beispiel für Common Language Runtime Ausdrucks Auswertung und eine Debug-Engine.
