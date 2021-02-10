---
title: ASP.NET ist nicht installiert
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 2388e59ae760e28c8f778ab8ccb15265414174b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871753"
---
# <a name="error-aspnet-not-installed"></a>Fehler: ASP.NET ist nicht installiert
Dieser Fehler tritt auf, wenn [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] auf dem zu debuggenden Computer nicht ordnungsgemäß installiert ist. Dies kann bedeuten, dass entweder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nicht installiert wurde, oder dass zuerst [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und anschließend IIS installiert wurde.

### <a name="to-reinstall-aspnet"></a>So installieren Sie ASP.NET neu

1. Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    Dabei stellt *Version* die Versionsnummer des auf dem Computer installierten .NET Framework (z. B. v1.0.370) dar. Sie können die Frameworkversion im Verzeichnis `\WINDOWS\Microsoft.NET\Framework` ermitteln.

   > [!NOTE]
   > Unter Windows Server 2003 können Sie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in der Systemsteuerung über die Option **Software** installieren.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
