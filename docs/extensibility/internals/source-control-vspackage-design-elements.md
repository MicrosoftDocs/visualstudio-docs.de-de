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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24a9b8dfa8036603c035a9112eb29688eab7ff25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852608"
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
