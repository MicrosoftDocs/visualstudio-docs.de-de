---
title: Erstellen eines Quellcodeverwaltungs-VSPackages | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Quellcodeverwaltungs-VSPackage erstellen, das einen Deep Integration-Pfad zum Integrieren der Quell Code Verwaltung in Visual Studio erstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9be8b97b3e37a224b12781e66543f7ab126f2c6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958530"
---
# <a name="create-a-source-control-vspackage"></a>Quellcodeverwaltungs-VSPackage erstellen
Diese Dokumentation enthält Links zu der Architektur Übersicht über ein Quell Code Verwaltungspaket [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , das in integriert ist, die API, die durch die zu implementierenden Schnittstellen definiert ist, und die zu verwendenden Dienste sowie ein Beispiel, das eine einfache Implementierung des Quell Code Verwaltungs Pakets veranschaulicht.

 Mit einem Quellcodeverwaltungs-VSPackage können Sie einen Deep Integration-Pfad für die Quell Code Verwaltung für die Integration in Erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Dadurch kann das Paket die von gehostete standardmäßige Quell Code Verwaltungs Benutzeroberfläche umgehen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , auf Quell Code Verwaltungsanforderungen aus dem Projekt System Antworten und mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten wie **Projektmappen-Explorer** interagieren. Ermöglicht es [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Partnern, ein VSPackage zu erstellen, das in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe eines Dienst Modells integriert werden kann.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Erläutert das Quell Code Verwaltungspaket, das eine erweiterte Alternative zum Quellcodeverwaltungs-Plug-in für die Implementierung von Quell Code Verwaltungsfunktionen in ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Aufbau](../../extensibility/internals/source-control-vspackage-architecture.md)

 Stellt ein Diagramm dar und erläutert die Komponenten eines Quell Code Verwaltungs Pakets.

- [Funktionen](../../extensibility/internals/source-control-vspackage-features.md)

 Beschreibt die verschiedenen Funktionen eines Quell Code Verwaltungs Pakets.

- [Design Elemente](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Beschreibt die Struktur des VSPackage, das von einem Quell Code Verwaltungspaket für die umfassende Integration implementiert werden muss.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Erläutert das Erstellen eines Quellcodeverwaltungs-Plug-ins, das Quell Code Verwaltungsfunktionen in der Benutzeroberfläche der Quell Code Verwaltung bereitstellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Quellcodeverwaltung](../../extensibility/internals/source-control.md)

 Erläutert die Optionen zum Implementieren der Quell Code Verwaltung als integriertes Feature von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
