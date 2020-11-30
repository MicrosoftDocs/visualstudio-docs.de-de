---
title: Bereitstellen von Projekttypen | Microsoft-Dokumentation
description: Erfahren Sie, wie Projekttypen mit verwaltetem Code bereitgestellt werden, indem ein neuer Aggregator für den Projekttyp und Windows Installer Paket für die Weiterverteilung im Visual Studio SDK verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1b015f29b6521482013a77bbcf7c44d8a79afa6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329874"
---
# <a name="deploy-project-types"></a>Bereitstellen von Projekttypen
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installiert einen neuen Projekttyp Aggregator (*ProjectAggregator2.dll*) und auch ein Windows Installer Paket für die Weiterverteilung (*ProjectAggregator2.msi*). Sie müssen den neuen Aggregator für Projekttypen mit verwaltetem Code verwenden. ProjectAggregator2 umgeht Einschränkungen im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektaggregator, der verhindert, dass Projekttypen mit verwaltetem Code ordnungsgemäß funktionieren. In den folgenden Schritten wird beschrieben, wie Sie Ihr VSPackage für die Verwendung des neuen Aggregators ändern.

1. Entfernen Sie das nativehierarchywrapper-Projekt aus der Projekt Mappe.

2. Entfernen Sie alle nativehierarchywrapper-Binärdateien aus dem Setup.

3. Fügen Sie dem Setup *ProjectAggregator2.msi* hinzu.
