---
title: Entwurfs Elemente der Quell Code Verwaltung VSPackage | Microsoft-Dokumentation
description: Informieren Sie sich über die Struktur, die das VSPackage der Quell Code Verwaltung implementieren muss, sowie über die Schnittstellen und Dienste, die das VSPackage der Quell Code Verwaltung implementieren
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e586470208989dce070c92963fc215f1053559a4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877649"
---
# <a name="source-control-vspackage-design-elements"></a>Entwurfselemente von Quellcodeverwaltungs-VSPackages
Die Themen in diesem Abschnitt beschreiben die Struktur, die das VSPackage der Quell Code Verwaltung für die umfassende Integration implementieren muss. Außerdem werden die Schnittstellen und Dienste aufgelistet, die vom VSPackage für die Quell Code Verwaltung implementiert werden können, sowie die Schnittstellen und Dienste, die das VSPackage der Quell Code Verwaltung von anderen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten zur Unterstützung des Quell Code Verwaltungsmodells verwenden kann.

## <a name="in-this-section"></a>In diesem Abschnitt
- [VSPackage-Struktur](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Definiert die Struktur des VSPackage der Quell Code Verwaltung.

- [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Listet die auf dem Quell Code Verwaltungspaket bezogenen Schnittstellen und Dienste auf.

- [Bereitgestellte Dienste](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Beschreibt den Quell Code Verwaltungsdienst, der vom Quellcodeverwaltungs-VSPackage bereitgestellt wird.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Erläutert das Erstellen eines Quellcodeverwaltungs-VSPackages, das nicht nur Quell Code Verwaltungsfunktionen bereitstellt, sondern auch zum Anpassen der Benutzeroberfläche der Quell Code Verwaltung verwendet werden kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
