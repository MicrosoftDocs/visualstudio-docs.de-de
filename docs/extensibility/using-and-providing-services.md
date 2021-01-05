---
title: Verwenden von und Bereitstellen von Diensten | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Dienste, die von der Visual Studio-IDE für VSPackages bereitgestellt und verwendet werden können. In diesen Artikeln wird beschrieben, wie Sie Dienste erhalten und bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a7c1d9f3632d8b710ac238c372ed4456183a8d1
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715937"
---
# <a name="using-and-providing-services"></a>Verwenden und Bereitstellen von Diensten
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet einen bestimmten Satz von Schnittstellen für ein anderes VSPackage, das verwendet werden soll. Beispielsweise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet den <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Dienst einem beliebigen VSPackage, das er lädt. Dieser Dienst stellt die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle bereit, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../extensibility/how-to-use-the-activity-log.md).

 VSPackages können eigene Dienste anbieten, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle verwenden.

 Visual Studio bietet wichtige Dienste wie die folgenden:

|IDE-Dienst|BESCHREIBUNG|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE-Dienste, die mit den grundlegenden Funktionen, VSPackages und der Registrierung in Zusammenhang stehen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende Fenster Funktionen und UI-bezogene Funktionen in der IDE, z. b. die Möglichkeit zum Erstellen von Tools und Dokument Fenstern.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet grundlegende Funktionen für die Lösung, z. b. die Möglichkeit, Projekte aufzulisten, neue Projekte zu erstellen und Projektänderungen zu überwachen.|

## <a name="in-this-section"></a>In diesem Abschnitt
- [Service Essentials](../extensibility/internals/service-essentials.md) Stellt die wichtigen Elemente eines Visual Studio-Dienstanbieter dar.

- Vorgehens [Weise: erhalten eines Dienstanbieter](../extensibility/how-to-get-a-service.md) Erläutert, wie ein Dienst angefordert (genutzt) wird.

- Vorgehens [Weise: Bereitstellen eines Dienstanbieter](../extensibility/how-to-provide-a-service.md) Erläutert, wie Sie einen Dienst bereitstellen.

- Vorgehens [Weise: Bereitstellen eines asynchronen Visual Studio-Dienstanbieter](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Erläutert, wie ein asynchroner Dienst bereitgestellt wird.

- Vorgehens [Weise: Problembehandlung bei Diensten](../extensibility/how-to-troubleshoot-services.md) Erläutert häufige Probleme und stellt Ihnen Lösungen vor.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
