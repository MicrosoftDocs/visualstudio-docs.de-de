---
title: Übersicht über den Legacy Sprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707361"
---
# <a name="legacy-language-service-overview"></a>Übersicht über Legacysprachdienste
Ein Sprachdienst bietet Editor Unterstützung, mit der bestimmte Features implementiert werden können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die Dienst Klassen für das Managed Package Framework (MPF) bieten vollständige Unterstützung für häufig verwendete Features und partielle Unterstützung für andere Funktionen.

## <a name="fully-supported-features-in-the-mpf"></a>Vollständig unterstützte Funktionen in MPF
 Die MPF-Sprachdienst Klassen unterstützen die folgenden Funktionen:

- Syntaxhervorhebung

- Gliedern

- Kommentieren von Code Blöcken

- Klammernabgleich (zugehörige Klammer)

- Codeausschnitte

- Benutzerdefinierte Dokumenteigenschaften

- IntelliSense-Parameterinformationen

- IntelliSense-QuickInfo

- IntelliSense-Element Abschluss

- IntelliSense-Wortvervollständigung

## <a name="partially-supported-features-in-the-mpf"></a>Teilweise unterstützte Funktionen in MPF
 Der MPF bietet nur eine partielle Unterstützung für die folgenden Features. Dies bedeutet, dass Sie die Methoden implementieren müssen, die von MPF aufgerufen werden.

- Neuformatierung von Code. Sie stellen den Code bereit, der die Neuformatierung implementiert.

- Validieren von Haltepunkten durch Identifizierung gültiger Code spannen. Sie stellen den Code bereit, mit dem die Code spannen identifiziert werden.

- Unterstützen des **debuggerauto** -Fensters zum Anzeigen von Variablen. Sie stellen den Code bereit, der bestimmt, was im Fenster angezeigt werden soll.

- Unterstützen der **Navigationsleiste** für die schnelle Navigation zwischen Typen und Membern. Sie implementieren eine Hilfsklasse, die die Listen in den Kombinations Feldern der **Navigationsleiste** auffüllt, und geben Sie zurück.

## <a name="implementation"></a>Implementierung
 Sie müssen mehrere Schritte ausführen, um den Sprachdienst selbst und die Sprachdienst Funktionen zu implementieren, die Sie für Ihre Sprache unterstützen möchten. Diese Schritte werden in den folgenden Themen erläutert:

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Gliederung in einem Legacysprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Kommentieren von Code in einem Legacysprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Neuformatieren von Code in einem Legacysprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Siehe auch
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)
