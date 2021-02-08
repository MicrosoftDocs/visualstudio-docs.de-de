---
title: Implementieren eines Legacy sprach Service1 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von Managed Package Framework (MPF) einen Legacy Sprachdienst implementieren, der erweiterte Sprachdienst Features unterstützt. Teil 1 von 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2337d1ee2ac8e698e93a0d8d3d1dc9324af4f933
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839988"
---
# <a name="implementing-a-legacy-language-service-1"></a>Implementieren eines Legacy sprach Dienstanbieter 1
Sie können Klassen im Managed Package Framework (MPF) verwenden, um einen Legacy Sprachdienst zu implementieren, der eine Vielzahl von Features unterstützt, wie z. b. Syntax Hervorhebung, übereinstimmende Klammern und IntelliSense-Vervollständigung.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren eines sprach Dienstanbieter finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)

 Eine Übersicht über die Sprachdienst Features, die in MPF unterstützt werden.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Beschreibt, was zum Implementieren eines sprach Dienstanbieter mithilfe von MPF erforderlich ist.

- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Beschreibt die Schritte, die erforderlich sind, um einen MPF-basierten Sprachdienst bei zu registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Beschreibt die beiden Parser, die erforderlich sind, um alle Funktionen eines sprach Dienstanbieter mithilfe von MPF zu implementieren.

- [Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Enthält die grundlegenden Schritte, die erforderlich sind, um einen MPF-Sprachdienst in einem VSPackage zu implementieren.

- [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Veranschaulicht die Verfahren zum Abrufen einer Liste installierter Code Ausschnitte.

- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)

 Enthält Links zu Themen, in denen detailliert erläutert wird, was durchgeführt werden muss, um alle Funktionen eines sprach Dienstanbieter mithilfe von MPF zu implementieren.
