---
title: Erstellen eines Quellcodeverwaltungs-VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196950"
---
# <a name="creating-a-source-control-vspackage"></a>Erstellen eines Quellcodeverwaltungs-VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Dokumentation enthält Links zu der Architektur Übersicht über ein Quell Code Verwaltungspaket [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , das in integriert ist, die API, die durch die zu implementierenden Schnittstellen definiert ist, und die zu verwendenden Dienste sowie ein Beispiel, das eine einfache Implementierung des Quell Code Verwaltungs Pakets veranschaulicht.  
  
 Mit einem Quellcodeverwaltungs-VSPackage können Sie einen Deep Integration-Pfad für die Quell Code Verwaltung für die Integration in Erstellen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Dadurch kann das Paket die von gehostete standardmäßige Quell Code Verwaltungs Benutzeroberfläche umgehen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , auf Quell Code Verwaltungsanforderungen aus dem Projekt System Antworten und mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Komponenten wie **Projektmappen-Explorer**interagieren. Ermöglicht es [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Partnern, ein VSPackage zu erstellen, das in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mithilfe eines Dienst Modells integriert werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Erläutert das Quell Code Verwaltungspaket, das eine erweiterte Alternative zum Quellcodeverwaltungs-Plug-in für die Implementierung von Quell Code Verwaltungsfunktionen in ist [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Aufbau](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Stellt ein Diagramm dar und erläutert die Komponenten eines Quell Code Verwaltungs Pakets.  
  
 [Funktionen](../../extensibility/internals/source-control-vspackage-features.md)  
 Beschreibt die verschiedenen Funktionen eines Quell Code Verwaltungs Pakets.  
  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Beschreibt die Struktur des VSPackage, das von einem Quell Code Verwaltungspaket für die umfassende Integration implementiert werden muss.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Erläutert das Erstellen eines Quellcodeverwaltungs-Plug-ins, das Quell Code Verwaltungsfunktionen in der Benutzeroberfläche der Quell Code Verwaltung bereitstellt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Quellcodeverwaltung](../../extensibility/internals/source-control.md)  
 Erläutert die Optionen zum Implementieren der Quell Code Verwaltung als integriertes Feature von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
