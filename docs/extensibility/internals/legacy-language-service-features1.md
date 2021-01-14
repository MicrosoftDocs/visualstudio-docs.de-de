---
title: Legacy Sprachdienst Features1 | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Visual Studio-Funktionen, die in einem MPF-Sprachdienst (Managed Package Framework) unterstützt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e099798ff5fcc96e798742b16ba88e522a4bc0b
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205059"
---
# <a name="legacy-language-service-features-1"></a>Funktionen von Legacy Sprachdiensten 1
Ein MPF-Sprachdienst (Managed Package Framework) kann eine oder mehrere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Funktionen unterstützen, z. b. Syntax Hervorhebung, IntelliSense und Haltepunkt Validierung. Die einzelnen Features können unabhängig von den anderen implementiert werden, aber alle erfordern einen Parser und einen Scanner, außer die Syntax Hervorhebung, die nur einen Scanner erfordert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um die Sprachpaar Übereinstimmung zu unterstützen, auch bekannt als geschweifter Klammern.

- [Kommentieren von Code in einem Legacysprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um das kommentieren und das auskommentieren des ausgewählten Codes zu unterstützen.

- [Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um Dokumenteigenschaften zu unterstützen, die in eine Quelldatei eingebettet sind.

- [Gliederung in einem Legacysprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um Gliederung durch die Implementierung ausgeblendeter Bereiche zu unterstützen

- [Neuformatieren von Code in einem Legacysprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um die Neuformatierung von Code zu unterstützen.

- [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um Code Ausschnitte zu unterstützen, bei denen es sich um Segmente von Code handelt, die eingefügt und bearbeitet werden können.

- [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Parameter Info Vorgang zum Anzeigen einer Methoden Signatur beim typisieren der Methode zu unterstützen.

- [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Quick Info-Vorgang zum Anzeigen von Informationen über einen Bezeichner zu unterstützen.

- [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Element Abschluss Vorgang zum Auswählen eines Members eines Namespace aus einer Liste zu unterstützen.

- [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um den IntelliSense-Vorgang zum Vervollständigen von Wörtern zum Abschließen teilweise typisierter Wörter zu unterstützen

- [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Beschreibt, was ein sprach **Dienst zum unterstützen des Fensters** Auto beim Debuggen tun kann.

- [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Beschreibt, wie die **Navigationsleiste** am oberen Rand der Editor-Ansicht verwendet wird, um eine schnelle Navigation zu einem beliebigen Typ oder Member in der in dieser Ansicht angezeigten Datei bereitzustellen.

- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, um die Syntax Hervorhebung von Quellcode zu unterstützen.

- [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Beschreibt, was ein Sprachdienst zur Unterstützung der Validierung von Haltepunkten außerhalb eines Debuggers ausführen kann.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Beschreibt den Parser und Scanner, die für die Implementierung aller Features eines sprach Dienstanbieter erforderlich sind, der das verwaltete Paket Framework verwendet.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Beschreibt, was zum Implementieren eines sprach Dienstanbieter mithilfe von MPF erforderlich ist.

- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Beschreibt die Schritte, die erforderlich sind, um einen MPF-basierten Sprachdienst bei zu registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Verwenden von IntelliSense](../../ide/using-intellisense.md)

 Erläutert, wie IntelliSense den Zugriff auf sprach Verweise erleichtert.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Enthält Informationen dazu, wie Sie das Managed Package Framework (MPF) zum Implementieren eines sprach Dienstanbieter mit vollem Funktionsumfang in verwaltetem Code verwenden.
