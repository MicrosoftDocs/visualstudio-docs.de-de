---
title: Auswählen zwischen freigegebenen und versionierten VSPackages | Microsoft-Dokumentation
description: Erfahren Sie mehr über parallele Installationen von VSPackages über freigegebene oder versionierte Strategien mit mehreren Versionen von Visual Studio und der .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90acdde2c365effd189efe4437b5e41c39f494b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949635"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Auswählen zwischen freigegebenen und versionierten VSPackages
Verschiedene Versionen von Visual Studio können auf demselben Computer gleichzeitig vorhanden sein. VSPackages können eine beliebige Kombination von Versionen unterstützen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 Parallele Installationen von VSPackages können mithilfe von zwei Strategien, der gemeinsam genutzten Strategie oder der Strategie für die Versionsverwaltung aktiviert werden. Beide ermöglichen das vorhanden sein mehrerer Versionen von und zugeordneter [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Versionen der .NET Framework.

 In der freigegebenen Strategie wird ein VSPackage für die Verwendung in mehreren Versionen von registriert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In der versionierten Strategie werden mehrere VSPackage-DLLs installiert, eine für jede von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ihnen unterstützte Version von.

## <a name="shared-vspackages"></a>Freigegebene VSPackages
 Die Verwendung eines freigegebenen VSPackages ist geeignet, wenn Sie das gleiche VSPackage in mehreren Versionen von verwenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Zum Implementieren eines freigegebenen VSPackage müssen Sie die folgenden Schritte ausführen:

- Sorgen Sie dafür, dass das VSPackage mit mehreren Versionen von kompatibel ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Hierfür stehen zwei Möglichkeiten zur Verfügung:

  - Beschränken Sie das VSPackage auf die Verwendung der Features der frühesten Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die Sie unterstützen.

  - Program mieren Sie das VSPackage, um sich an die Version von anzupassen, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der es ausgeführt wird. Wenn Abfragen für neuere Dienste fehlschlagen, kann das VSPackage weitere Dienste anbieten, die in älteren Versionen von unterstützt werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Registrieren Sie das VSPackage entsprechend. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md) und [verwaltete VSPackage-Registrierung](/previous-versions/bb166783(v=vs.100)).

- Registrieren Sie Dateierweiterungen entsprechend. Weitere Informationen finden Sie unter [Registrieren von Dateinamen Erweiterungen für](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)parallele bereit Stellungen.

- Erstellen Sie ein Installationsprogramm, das das VSPackage für die entsprechenden Versionen von bereitstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Komponenten Verwaltung](../extensibility/internals/component-management.md).

- Beheben Sie das Problem von Registrierungs Kollisionen. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md).

- Stellen Sie sicher, dass sowohl freigegebene als auch Dateien mit Versions Angabe die Verweis Zählung beachten, um eine sichere Installation und Entfernung mehrerer Versionen zu ermöglichen Weitere Informationen finden Sie unter [Komponenten Verwaltung](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Versionierte VSPackages
 Unter der VSPackage-Strategie mit Versions Angabe erstellen Sie ein VSPackage für jede von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ihnen unterstützte Version von. Dies ist sinnvoll, wenn Sie davon ausgehen, dass die von höheren Versionen von bereitgestellten Dienste genutzt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden, da sich jedes VSPackage weiterentwickeln kann, ohne die anderen zu beeinflussen. Dennoch kann es bei der Strategie, mit der Sie mehrere Binärdateien erstellen, entweder aus einer einzelnen Codebasis oder aus mehreren unabhängigen Codebasen, eine größere anfängliche Entwicklung als bei der freigegebenen Strategie bedeuten. Außerdem sind möglicherweise zusätzliche Installationsschritte erforderlich, da Sie entweder ein separates Setup für jede Version oder eine einzelne Installation erstellen müssen, mit der die Versionen von erkannt werden, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ihrem VSPackage unterstützt werden.

## <a name="binary-compatibility"></a>Binärkompatibilität
 Im allgemeinen ermöglicht die binäre Kompatibilität das Ausführen von VSPackages mit System eigenem Code, die mit früheren Versionen von Visual Studio entwickelt wurden, in neueren Versionen von Visual Studio. Es gibt jedoch drei wichtige Ausnahmen:

- Wenn das VSPackage von einer bestimmten Version des Common Language Runtime abhängig ist, muss festgelegt werden, in welcher Version von das VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.

- Ein VSPackage kann eine Abhängigkeit von einer bestimmten Funktion eines anderen VSPackages oder eines anderen Produkts aufweisen. Folglich kann das VSPackage nur ausgeführt werden, wenn die Abhängigkeit erfüllt ist.

- Ein VSPackage ist möglicherweise von einer Sicherheitskorrektur in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Service Pack oder einer neueren Version von betroffen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In diesen Fällen wird ein VSPackage, das mit einer früheren Version von entwickelt [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] wurde, möglicherweise nicht in Versionen von ausgeführt, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nachdem die Sicherheitskorrektur angewendet wurde. Sie können das Paket jedoch mit der neueren Version neu erstellen und auch in früheren Versionen ausführen.

  Verwaltete VSPackages müssen mit einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und der erstellt werden [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] , die der Zielversion von entsprechen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  Neben der Planung der Binärkompatibilität für Ihre VSPackage-Binärdateien sollten Sie auch die Lösungs-und Projektdatei Formate berücksichtigen. Wenn das VSPackage einen neuen Projekttyp erstellt, müssen Sie entscheiden, ob es in nur einer Version oder in mehreren Versionen von ausgeführt werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Komponenten Verwaltung](../extensibility/internals/component-management.md)