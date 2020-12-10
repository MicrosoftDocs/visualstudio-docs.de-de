---
title: Deaktivieren von Warnungen für Quellcodeverwaltungs-Plug-ins
description: Ein Benutzer kann bei der Verwendung der Quell Code Verwaltung in Visual Studio mehrere Kompatibilitäts Warnungen sehen. Erfahren Sie, wie Sie diese Warnungen deaktivieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5607f4a92a14b692f20d509e014991d461815bd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993548"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Gewusst wie: Deaktivieren von Kompatibilitäts Warnungen für Quellcodeverwaltungs-Plug-ins

Bei der Verwendung der Quell Code Verwaltung in werden möglicherweise mehrere Kompatibilitäts Warnungen angezeigt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Welche Warnungen angezeigt werden, hängt von den Funktionen des Quellcodeverwaltungs-Plug-ins ab und kann wie hier beschrieben deaktiviert werden.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>So deaktivieren Sie die Warnung: "so stellen Sie eine optimale Integration der Quell Code Verwaltung in Visual Studio sicher"

- Legen Sie den folgenden Registrierungs Eintrag fest (fügen Sie ggf. den Wert hinzu):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Diese Warnung wird für alle nicht- [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] Plug-Ins angezeigt.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>So deaktivieren Sie die Warnung: "der installierte Quell Code Verwaltungs Anbieter unterstützt nicht alle Funktionen"

- Legen Sie die folgenden beiden Registrierungs Werte fest (fügen Sie ggf. die Werte hinzu):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Diese Warnung wird angezeigt, wenn das Quellcodeverwaltungs-Plug-in für mehrere Projekte nicht explizit unterstützt (d. h., wenn nur eine Datei und ein Projekt gleichzeitig eingecheckt werden können).

     Es ist am besten, den erneuten eintreten ( `SCC_CAP_REENTRANT` Funktion) zu unterstützen. Dadurch wird diese Warnung entfernt. Wenn diese Unterstützung jedoch nicht möglich ist, können diese Registrierungseinträge festgelegt werden.

## <a name="see-also"></a>Weitere Informationen

- [Funktionsflags](../extensibility/capability-flags.md)
