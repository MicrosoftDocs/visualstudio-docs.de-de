---
title: Dienstprogramm "|" | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Dienstprogramm "depepkgdef", das eine DLL-Datei für eine Visual Studio-Erweiterung als Parameter annimmt und eine pkgdef-Datei für die DLL-Datei erstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9822319a74d1374ef2a88d4f9231e6fd86b1e5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884532"
---
# <a name="createpkgdef-utility"></a>Das Dienstprogramm "| atepkgdef"
Nimmt eine DLL-Datei für eine Visual Studio-Erweiterung als Parameter an und erstellt eine *pkgdef* -Datei für die *dll* -Datei. Die *pkgdef* -Datei enthält alle Informationen, die andernfalls bei der Installation der Erweiterung in die Systemregistrierung geschrieben werden.

> [!NOTE]
> Die meisten Projektvorlagen, die im Visual Studio SDK enthalten sind, erstellen automatisch *pkgdef* -Dateien als Teil des Buildprozesses. Dieses Dokument richtet sich an Benutzer, die Pakete manuell erstellen möchten, oder Konvertieren vorhandener Pakete, um die *pkgdef*  -Bereitstellung zu verwenden.

## <a name="syntax"></a>Syntax

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumente
**/Out = &lt; Dateiname&gt;**\
Erforderlich. Legt den Namen der *pkgdef* -Ausgabedatei auf &lt; filename fest &gt; .

**/CodeBase**\
Dies ist optional. Erzwingt die Registrierung mit dem **CodeBase** -Hilfsprogramm.

**/Assembly**\
Erzwingt **die Registrierung** mit dem Assemblydienstprogramm.

**&lt;AssemblyPath&gt;**\
Der Pfad der *dll* -Datei, aus der die *pkgdef*-Datei generiert werden soll.

## <a name="remarks"></a>Bemerkungen
Die Erweiterungs Bereitstellung mithilfe von *pkgdef* -Dateien ersetzt die Registrierungsanforderungen früherer Versionen von Visual Studio.

::: moniker range=">=vs-2019"

Die *pkgdef* -Dateien müssen an einem der folgenden Speicherorte installiert werden:

- *%LocalAppData%\microsoft\visual studio\16.0\Extensions\\*

- *%VSInstallDir%\common7\ide\Extensions\\*

Wenn der Installationsordner *%LocalAppData%\microsoft\visual studio\16.0\Extensions \\* ist, wird die Erweiterung von Visual Studio erkannt, ist aber standardmäßig deaktiviert. Der Benutzer kann die Erweiterung mithilfe von " **Erweiterungen verwalten**" aktivieren.

Wenn der Installationsordner *%VSInstallDir%\common7\ide\Extensions \\* lautet, ist die Erweiterung standardmäßig aktiviert.

> [!NOTE]
> Das Tool zum **Verwalten von Erweiterungen** kann nur verwendet werden, um auf eine Erweiterung zuzugreifen, wenn es als Teil eines VSIX-Pakets installiert ist.

::: moniker-end

::: moniker range="vs-2017"

Die *pkgdef* -Dateien müssen an einem der folgenden Speicherorte installiert werden:

- *%LocalAppData%\microsoft\visual studio\15.0\Extensions\\*

- *%VSInstallDir%\common7\ide\Extensions\\*

Wenn der Installationsordner *%LocalAppData%\microsoft\visual studio\15.0\Extensions \\* ist, wird die Erweiterung von Visual Studio erkannt, ist aber standardmäßig deaktiviert. Der Benutzer kann die Erweiterung mithilfe von **Erweiterungen und Updates** aktivieren.

Wenn der Installationsordner *%VSInstallDir%\common7\ide\Extensions \\* lautet, ist die Erweiterung standardmäßig aktiviert.

> [!NOTE]
> Das Tool " **Erweiterungen und Updates** " kann nur verwendet werden, um auf eine Erweiterung zuzugreifen, wenn Sie als Teil eines VSIX-Pakets installiert ist.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen
- [Das Hilfsprogramm "| ateexpinstance](../../extensibility/internals/createexpinstance-utility.md)
