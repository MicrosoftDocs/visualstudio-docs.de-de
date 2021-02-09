---
title: Unterstützung mehrerer Versionen von Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie verschiedene Versionen von Visual Studio unterstützen können, wobei ihre VSPackages in verschiedene Versionen geladen werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52b8bf1be57e10790d91d4712e56d707621cc7df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889940"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Unterstützen mehrerer Versionen von Visual Studio
Der Begriff *nebeneinander* bedeutet, dass Sie mehrere Versionen eines Produkts auf demselben Computer installieren und verwalten können. Für VSPackages bedeutet dies, dass ein Benutzer mehrere Visual Studio-Versionen auf demselben Computer installiert haben kann. Es ist jedoch nicht möglich, parallele Versionen ihrer VSPackages in eine einzelne Version von Visual Studio zu laden.

 Bevor Sie das VSPackage in parallele Versionen von Visual Studio laden können, berücksichtigen Sie Folgendes:

- Sie müssen bestimmen, welche parallele Implementierungsstrategie Sie befolgen möchten.

   Weitere Informationen finden Sie unter [auswählen zwischen freigegebenen und versionierten VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Ihre Projektmappen-und Projektdatei Formate müssen ihrer Implementierungsstrategie entsprechen.

   Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) und [Registrieren von Dateinamen Erweiterungen für](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)parallele bereit Stellungen.

- Das Installationsprogramm muss Ihre Implementierungsstrategie verarbeiten, damit versionierte Komponenten und auch Komponenten, die von allen Versionen gemeinsam genutzt werden, ordnungsgemäß installiert und registriert werden.

   Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und auch der [Komponenten Verwaltung](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Bei der Installation einer Version von Visual Studio wird auch eine entsprechende Version der .NET Framework installiert. Wenn Sie z. b. Visual Studio 2010 und Visual Studio 2012 auf demselben Computer installieren, werden auch die Versionen 4,0 und 4,5 der .NET Framework installiert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Auswählen zwischen freigegebenen und versionierten VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Erläutert, wie parallele Probleme in Ihrem VSPackage gelöst werden.

- [Registrieren von Dateinamen Erweiterungen für](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) parallele bereit Stellungen Beschreibt, wie das VSPackage Dateizuordnungen in einem parallelen Szenario registrieren kann.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
