---
title: Festlegen von Standardeinstellungen für Unternehmensbereitstellungen
description: Erfahren Sie mehr über Domänenrichtlinien und andere Konfigurationsvorgänge für die Unternehmensbereitstellungen von Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8fd5e96246778e1a8fd4ec1d87221ff04e8647cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959271"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Festlegen von Standardeinstellungen für Unternehmensbereitstellungen von Visual Studio

Sie können Registrierungsrichtlinien festlegen, die sich auf die Bereitstellung von Visual Studio auswirken. Diese Richtlinien gelten global für das neue Installationsprogramm und beeinflussen Folgendes:

- Den Speicherort installierter Pakete, die mit anderen Versionen oder Instanzen gemeinsam genutzt werden
- Den Cachespeicherort von Paketen
- Ob alle Pakete zwischengespeichert werden

Sie können einige dieser Richtlinien mithilfe von [Befehlszeilenoptionen](use-command-line-parameters-to-install-visual-studio.md) festlegen, Registrierungswerte auf dem Computer festlegen oder sie mithilfe von Gruppenrichtlinien in einer Organisation verteilen.

## <a name="registry-keys"></a>Registrierungsschlüssel

Es gibt mehrere Speicherorte, an denen Sie unternehmensweite Standardwerte festlegen können, um deren Steuerung über Gruppenrichtlinien oder direkt in der Registrierung zu ermöglichen. Visual Studio prüft sequenziell, ob Unternehmensrichtlinien festgelegt wurden. Sobald ein Richtlinienwert in der nachstehenden Liste gefunden wird, werden die restlichen Schlüssel ignoriert.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (bei 64-Bit-Betriebssystemen)

> [!IMPORTANT]
> Wenn Sie den Schlüssel `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` nicht festlegen, sondern stattdessen einen der anderen Schlüssel festlegen, müssen Sie die beiden anderen Schlüssel auf 64-Bit-Betriebssystemen festlegen. Dieses Problem wir in einem kommenden Produktupdate behoben.

Einige Registrierungswerte werden bei der ersten Verwendung automatisch festgelegt, falls noch nicht geschehen. Dadurch wird sichergestellt, dass bei nachfolgenden Installationen dieselben Werte verwendet werden. Diese Werte werden im zweiten Registrierungsschlüssel `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` gespeichert.

Sie können die folgenden Registrierungswerte festlegen:

| **Name** | **Typ** | **Default** | **Beschreibung** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` oder `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Das Verzeichnis, in dem Paketmanifeste und optional Nutzlasten gespeichert werden. Weitere Informationen finden Sie unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Behalten Sie Paketnutzlasten bei, auch nachdem diese installiert wurden. Sie können den Wert jederzeit ändern. Durch Deaktivieren der Richtlinie werden alle zwischengespeicherten Paketnutzlasten für die Instanz entfernt, die Sie reparieren oder ändern. Weitere Informationen finden Sie unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` oder `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Das Verzeichnis, in dem einige Pakete installiert werden, die von Versionen oder Instanzen von Visual Studio gemeinsam genutzt werden. Sie können den Wert jederzeit ändern, jedoch wirkt sich das nur auf zukünftige Installationen aus. Produkte, die bereits am alten Speicherort installiert sind, dürfen nicht verschoben werden, da sie möglicherweise nicht mehr ordnungsgemäß funktionieren. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Verhindern, dass Setup Updates für alle installierten Visual Studio-Produkte automatisch herunterlädt. Sie können den Wert jederzeit ändern. |

> [!IMPORTANT]
> Wenn Sie die Registrierungsrichtlinie `CachePath` nach einer Installation ändern, müssen Sie den vorhandenen Paketcache an den neuen Speicherort verschieben und seinen Schutz sicherstellen, damit `SYSTEM` und `Administrators` über Vollzugriff verfügen und `Everyone` über Lesezugriff verfügt.
> Wenn der vorhandene Cache nicht verschoben oder gesichert wird, können bei zukünftigen Installationen Probleme auftreten.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

- [Installieren von Visual Studio](install-visual-studio.md)
- [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md)
- [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
