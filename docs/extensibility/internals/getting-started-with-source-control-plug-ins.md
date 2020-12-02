---
title: Einstieg in die Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Erstellen eines Quellcodeverwaltungs-Plug-ins, das die in der Quellcodeverwaltungs-Plug-in-API definierten Funktionen zur Verwendung in der Quell Code Versionskontrolle implementiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1524e4c4f08b272fd17973597d558efdabec41af
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480498"
---
# <a name="get-started-with-source-control-plug-ins"></a>Einstieg in die Quellcodeverwaltungs-Plug-ins
Zum Erstellen eines Quellcodeverwaltungs-Plug-Ins müssen Sie eine DLL erstellen, die die in der Quellcodeverwaltungs-Plug-in-API definierten Funktionen implementiert, und dann die dll bei registrieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um Sie für die Verwendung in der Quell Code Versionskontrolle verfügbar zu machen.

 Für Quellcodeverwaltungs-Plug-ins sind drei Versionen der Quellcodeverwaltungs-Plug-in-API (Versionen 1,1, 1,2 und 1,3) verfügbar. Die hier dokumentierte API für das Quellcodeverwaltungs-Plug-in ist Version 1,3. Es wurde für die vollständige Kompatibilität mit Quellcodeverwaltungs-Plug-ins entwickelt, die die Versionen 1,1 und 1,2 unterstützen. Im Abschnitt Neuigkeiten im Abschnitt " [Quellcodeverwaltungs-Plug-in-API Version 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) " werden die neuen Features erläutert, die in der neuesten Version der API für Quellcodeverwaltungs-Plug-Ins unterstützt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Beschreibt, wie Sie die Registrierungseinträge erstellen, die erforderlich sind, um eine Quellcodeverwaltungs-dll zu binden.

- [Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Bietet eine kurze Übersicht über die Änderungen, die an der Quellcodeverwaltungs-Plug-in-API in Version 1,3 vorgenommen wurden.

- [Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Bietet eine kurze Übersicht über die Änderungen, die an der Quellcodeverwaltungs-Plug-in-API in Version 1,2 vorgenommen wurden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Quellcodeverwaltungs-Plug-ins](../../extensibility/source-control-plug-ins.md)

 Stellt eine vollständige Auflistung aller Elemente in der Quellcodeverwaltungs-Plug-in-API bereit.

- [Erstellen eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definiert das Quellcodeverwaltungs-Plug-in-SDK und beschreibt die enthaltenen Ressourcen.
