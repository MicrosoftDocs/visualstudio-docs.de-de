---
title: Problembehandlung bei der regpkg-Paket Registrierung | Microsoft-Dokumentation
description: Verwenden Sie diese Informationen zum Beheben von Problemen bei der regpkg-Paket Registrierung in Visual Studio. Verwenden Sie die für Ihr Paket geeignete Version von regpkg.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eef67b86925bc38a317196bbf00860b75a6ee15c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487711"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Problembehandlung bei der Registrierung des RegPkg-Pakets
> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio besteht darin, pkgdef-Dateien zu verwenden. Dies ermöglicht die Erweiterungs Bereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen. Pkgdef-Dateien werden mit dem [Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md)"|" erstellt.

 Zum Registrieren eines Pakets mithilfe von regpkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] müssen Sie die Version von regpkg verwenden, die für das Paket geeignet ist.

## <a name="regpkg-versions-related-to-package-versions"></a>Regpkg-Versionen im Zusammenhang mit Paketversionen
 Es gibt zwei Versionen von regpkg. Eine Version ist in enthalten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Verwenden Sie diese Version zum Registrieren von Paketen, die mit einer der folgenden Assemblys erstellt wurden:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Pakete, die mithilfe der früheren Microsoft.VisualStudio.Shell.dll Assembly erstellt wurden, können nicht registriert werden.

   Mit der früheren Version von regpkg können Pakete registriert werden, die mit der Microsoft.VisualStudio.Shell.dll-Assembly erstellt wurden. Es ist jedoch nicht möglich, Pakete zu registrieren, die mit neueren Versionen dieser Assembly erstellt wurden.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Problembehandlung für Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
