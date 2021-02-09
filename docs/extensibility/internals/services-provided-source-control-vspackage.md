---
title: Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
description: Erfahren Sie, wie VSPackages Funktionen über Dienste gemeinsam nutzen, einschließlich der Interaktion mit der Visual Studio-IDE und den zugehörigen VSPackages.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 515422266ce3d719319c4ba9717106af16e84f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910999"
---
# <a name="services-provided-source-control-vspackage"></a>Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage)
Dienste sind der primäre Mechanismus, durch den die Funktionalität von VSPackages und von der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio und den installierten VSPackages gemeinsam genutzt wird. Eine ausführliche Beschreibung der Dienste und ihrer Wichtigkeit in der Visual Studio-IDE finden[Sie unter verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Der Quell Code Verwaltungsdienst
 Visual Studio bietet zwei Ebenen von Diensten, Dienste auf IDE-Ebene und Dienste auf Paketebene. Die Visual Studio-IDE bietet systemeigene Dienste auf IDE-Ebene. Das Quell Code Verwaltungspaket nutzt einige dieser Dienste. Das Quell Code Verwaltungspaket als VSPackage nutzt seine Funktionen der Quell Code Verwaltung, indem es einen eigenen privaten Quell Code Verwaltungsdienst bereitstellt. Das Quell Code Verwaltungspaket kapselt den Satz von mit der Quell Code Verwaltung implementierten Schnittstellen, der von ihm implementiert wird, in Form eines Vertrags, der von der Visual Studio-IDE verwendet werden kann.

## <a name="see-also"></a>Weitere Informationen
- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
