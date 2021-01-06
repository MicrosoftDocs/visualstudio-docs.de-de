---
title: Regpkg-Hilfsprogramm | Microsoft-Dokumentation
description: Erfahren Sie, wie das RegPkg.exe-Hilfsprogramm ein VSPackage bei Visual Studio registriert und für die Bereitstellung vorbereitet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad66f963250dfc272506096f8932442a35d11dc7
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877325"
---
# <a name="regpkg-utility"></a>RegPkg-Hilfsprogramm
> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio besteht darin, pkgdef-Dateien zu verwenden. Dies ermöglicht die Erweiterungs Bereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen. Dies ist eine Voraussetzung für die VSIX-Bereitstellung. Pkgdef-Dateien werden mit dem [Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md)"|" erstellt. Weitere Informationen zur Bereitstellung von Visual Studio-Paketen finden Sie unter [Versand von Visual Studio-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).

 Das RegPkg.exe-Hilfsprogramm registriert ein VSPackage bei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und bereitet es für die Bereitstellung vor. Dieses Hilfsprogramm wird im Hintergrund während der VSPackage-Entwicklung verwendet. Sie wird als Teil des Buildprozesses ausgeführt, sodass Sie ein VSPackage in der experimentellen Struktur erstellen und ausführen können.

 Regpkg kann System Registrierungs Skripts in verschiedenen Formaten generieren. Sie können diese Skripts in Bereitstellungs Projekte wie MSI-Projekte oder Windows Installer XML-toolsetdateien integrieren.

 RegPkg.exe befindet sich in der Regel unter \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. Regpkg folgt der folgenden Syntax:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: root führt die Registrierung unter dem angegebenen aus.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] root

 /regfile: filename erstellt eine REG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/vrgfile oder/rgsfile oder/wixfile. verwendet werden.

 /rgsfile: filename erstellt eine RGS-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/vrgfile oder/regfile oder/wixfile. verwendet werden.

 /vrgfile: filename erstellt eine VRG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder/rgsfile oder/wixfile. verwendet werden.

 /RGM erstellt zusätzlich zur RGS-Datei eine RGM-Datei.  Muss mit/rgsfile. kombiniert werden

 /wixfile: filename erstellt eine Windows Installer XML-toolsetkompatiblen Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder/rgsfile oder/vrgfile. verwendet werden.

 /CodeBase erzwingt die Registrierung bei CodeBase anstelle der Assembly.

 /Assembly erzwingt die Registrierung bei der Assembly anstelle der Codebasis.

 /Unregister hebt die Registrierung dieses Pakets auf.  Kann nicht verwendet werden

 mit/regfile oder/vrgfile oder/rgsfile oder/wixfile.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Problembehandlung bei der Registrierung des RegPkg-Pakets](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
