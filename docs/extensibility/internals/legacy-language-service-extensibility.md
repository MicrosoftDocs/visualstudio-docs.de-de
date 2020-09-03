---
title: Erweiterbarkeit des Legacy sprach Dienstanbieter | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707407"
---
# <a name="legacy-language-service-extensibility"></a>Erweiterbarkeit von Legacysprachdiensten
Ein Sprachdienst bietet sprachspezifische Unterstützung für das Bearbeiten von Quellcode in der IDE.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren eines sprach Dienstanbieter finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).

 In diesem Abschnitt werden die Struktur und die Implementierung eines Legacy sprach Dienstanbieter erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Migrieren eines Legacysprachdiensts](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Erläutert, wie ein Sprachdienst von Visual Studio 2008 auf die neueste Version aktualisiert wird.

- [Grundlagen zu Legacysprachdiensten](../../extensibility/internals/legacy-language-service-essentials.md)

 Enthält wichtige Informationen zum Entwickeln von Sprachdiensten, um eine Programmiersprache in Visual Studio zu integrieren.

- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)

 Enthält Links zu Themen, die Ihnen bei der Erstellung eines sprach Dienstanbieter helfen können.

- [Syntaxfarben in einem Legacysprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Stellt Informationen zur Unterstützung der Syntax Hervorhebung in einem Sprachdienst bereit.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Enthält Informationen dazu, wie Sie das Managed Package Framework (MPF) zum Implementieren eines sprach Dienstanbieter mit vollem Funktionsumfang in verwaltetem Code verwenden.

- [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Beschreibt Bibliotheken und Tools, mit denen Sie Struktur Ansichten von Symbolen in der IDE durchsuchen können.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)

 Bietet eine Übersicht über Visual Studio-Editoren.

- [Sprachdienstunterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md)

 Enthält Informationen zu und einen Link zum Visual Studio-debuggingsdk, das die Informationen enthält, die zum Erstellen und Anpassen der Debuggerkomponenten zum Debuggen von Programmen erforderlich sind.
