---
title: Neues in der Quell Code Verwaltung in Visual Studio 2015 SDK | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Features der Quell Code Verwaltung VSPackages, und lesen Sie eine Übersicht über die Implementierungs Schritte.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a7df9af8dbd4af708483b638c0a86470a7d2220
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940045"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Neues in der Quell Code Verwaltung für das Visual Studio 2015 SDK

In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] können Sie eine tief integrierte Quell Code Verwaltungs Lösung bereitstellen, indem Sie ein Quellcodeverwaltungs-VSPackage implementieren. In diesem Abschnitt werden die Features der Quellcodeverwaltungs-VSPackages beschrieben und eine Übersicht über die Implementierungs Schritte bereitstellt.

## <a name="the-source-control-vspackage"></a>Das VSPackage der Quell Code Verwaltung

Visual Studio unterstützt zwei Typen von Quell Code Verwaltungslösungen. In allen Versionen von Visual Studio können Sie weiterhin ein API-basiertes Plug-in für die Quellcodeverwaltungs-Plug-ins integrieren. Sie können auch ein VSPackage für die Quell Code Verwaltung erstellen, das einen Deep-Integration-Pfad bereitstellt, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] der für Quell Code Verwaltungslösungen geeignet ist, die ein hohes Maß an Komplexität und Autonomie erfordern.

Ein VSPackage kann Visual Studio nahezu jede Art von Funktionalität hinzufügen. Ein Quellcodeverwaltungs-VSPackage bietet ein vollständiges Quell Code Verwaltungs Feature für Visual Studio, von der Benutzeroberfläche, die dem Benutzer für die Back-End-Kommunikation mit dem Quell Code Verwaltungssystem angezeigt wird.

Zum Implementieren eines VSPackage für die Quell Code Verwaltung ist eine all-oder Nothing-Strategie erforderlich. Der Ersteller eines Quellcodeverwaltungs-VSPackages muss bei der Implementierung einer Reihe von Quell Code Verwaltungs Schnittstellen und neuen Benutzeroberflächen Elementen (Dialogfelder, Menüs und Symbolleisten) eine beträchtliche Menge an Aufwand investieren, um die gesamte Funktionalität der Quell Code Verwaltung sowie die Schnittstellen zu implementieren, die für die erfolgreiche Integration mit Visual Studio erforderlich sind.

Die folgenden Schritte zeigen einen allgemeinen Überblick darüber, was zum Implementieren eines Quell Code Verwaltungs Pakets erforderlich ist. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackages](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Erstellen Sie ein VSPackage, das einen privaten Quell Code Verwaltungsdienst anbietet.

2. Implementieren Sie die Schnittstellen in den in der Quell Code Verwaltung bezogenen Diensten, die von Visual Studio bereitgestellt werden (z <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . b. die-und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> Schnittstelle).

3. Registrieren Sie das VSPackage für die Quell Code Verwaltung.

4. Implementieren Sie alle Benutzeroberflächen der Quell Code Verwaltung, einschließlich Menü Elemente, Dialogfeldern, Symbolleisten und Kontextmenüs.

5. Alle Ereignisse in Zusammenhang mit der Quell Code Verwaltung werden an das vsackage der Quell Code Verwaltung übermittelt, wenn es aktiv ist und von Ihrem VSPackage behandelt werden muss.

6. Das VSPackage der Quell Code Verwaltung muss auf Ereignisse lauschen, wie z. b. die, die die-Schnittstelle implementieren, und das nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> Verfolgen von Project Document (TPD)-Ereignissen (wie von der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle implementiert) und das

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Übersicht](../../extensibility/internals/source-control-integration-overview.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
