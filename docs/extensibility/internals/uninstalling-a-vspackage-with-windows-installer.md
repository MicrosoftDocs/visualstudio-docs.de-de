---
title: Deinstallieren eines VSPackage mit Windows Installer | Microsoft-Dokumentation
description: Windows Installer können das VSPackage deinstallieren, indem Sie die Installation umkehren. Erfahren Sie, wie Sie benutzerdefinierte Aktionen in Ihrem Windows Installer Paket behandeln können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89a3ed681f51b392e076cff0fcb06b2f868c0aa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888991"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Deinstallieren eines VSPackage mit Windows Installer
Windows Installer können das VSPackage zum größten Teil deinstallieren, indem Sie einfach "rückgängig machen", was für die Installation des VSPackage geschehen ist. Die benutzerdefinierten Aktionen, die in [Befehlen erläutert werden, die nach der Installation ausgeführt werden müssen,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) müssen auch nach der Deinstallation ausgeführt werden. Da die Aufrufe von devenv.exe direkt vor der InstallFinalize Standard-Aktion für die Installation und Deinstallation auftreten, dienen die Tabelleneinträge CustomAction und InstallExecuteSequence beiden Fällen.

> [!NOTE]
> Führen `devenv /setup` Sie nach dem Deinstallieren eines MSI-Pakets aus.

 Wenn Sie einem Windows Installer Paket benutzerdefinierte Aktionen hinzufügen, müssen Sie diese Aktionen als allgemeine Regel während der deinstalstallation und des Rollbacks behandeln. Wenn Sie benutzerdefinierte Aktionen hinzufügen, um Ihr VSPackage selbst zu registrieren, müssen Sie z. b. benutzerdefinierte Aktionen hinzufügen, um die Registrierung aufzuheben.

> [!NOTE]
> Es ist möglich, dass ein Benutzer das VSPackage installiert und dann die Versionen von deinstalliert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit denen es integriert ist. Sie können sicherstellen, dass die Deinstallation des VSPackages in diesem Szenario funktioniert, indem Sie benutzerdefinierte Aktionen eliminieren, die Code mit Abhängigkeiten von ausführen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Behandeln von Startbedingungen zum Zeitpunkt der Deinstallation
 Mit der Standardaktion LaunchConditions werden die Zeilen der LaunchCondition-Tabelle gelesen, um Fehlermeldungen anzuzeigen, wenn die Bedingungen nicht erfüllt werden. Wenn in der Regel Startbedingungen verwendet werden, um sicherzustellen, dass die Systemanforderungen erfüllt sind, können Sie die Startbedingungen während der Deinstallation im allgemeinen überspringen, indem Sie der `NOT Installed` LaunchConditions-Zeile der LaunchCondition-Tabelle die Bedingung hinzufügen.

 Eine Alternative besteht darin, `OR Installed` zu Startbedingungen hinzuzufügen, die während der Installation nicht wichtig sind. Dadurch wird sichergestellt, dass die Bedingung bei der nicht Installation immer true ist, und daher wird die Fehlermeldung der Startbedingung nicht angezeigt.

> [!NOTE]
> `Installed` Gibt an, dass die-Windows Installer Eigenschaft festgelegt wird, wenn Sie erkennt, dass das VSPackage bereits auf dem System installiert ist.

## <a name="see-also"></a>Weitere Informationen
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)