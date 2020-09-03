---
title: Deinstallieren eines VSPackage mit Windows Installer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675230"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Deinstallieren eines VSPackage mit Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows Installer können das VSPackage zum größten Teil deinstallieren, indem Sie einfach "rückgängig machen", was für die Installation des VSPackage geschehen ist. Die benutzerdefinierten Aktionen, die in [Befehlen erläutert werden, die nach der Installation ausgeführt werden müssen,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) müssen auch nach der Deinstallation ausgeführt werden. Da die Aufrufe von devenv.exe direkt vor der InstallFinalize Standard-Aktion für die Installation und Deinstallation auftreten, dienen die Tabelleneinträge CustomAction und InstallExecuteSequence beiden Fällen.  
  
> [!NOTE]
> Führen `devenv /setup` Sie nach dem Deinstallieren eines MSI-Pakets aus.  
  
 Wenn Sie einem Windows Installer Paket benutzerdefinierte Aktionen hinzufügen, müssen Sie diese Aktionen als allgemeine Regel während der deinstalstallation und des Rollbacks behandeln. Wenn Sie benutzerdefinierte Aktionen hinzufügen, um Ihr VSPackage selbst zu registrieren, müssen Sie z. b. benutzerdefinierte Aktionen hinzufügen, um die Registrierung aufzuheben.  
  
> [!NOTE]
> Es ist möglich, dass ein Benutzer das VSPackage installiert und dann die Versionen von deinstalliert, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit denen es integriert ist. Sie können sicherstellen, dass die Deinstallation des VSPackages in diesem Szenario funktioniert, indem Sie benutzerdefinierte Aktionen eliminieren, die Code mit Abhängigkeiten von ausführen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Behandeln von Startbedingungen zum Zeitpunkt der Deinstallation  
 Mit der Standardaktion LaunchConditions werden die Zeilen der LaunchCondition-Tabelle gelesen, um Fehlermeldungen anzuzeigen, wenn die Bedingungen nicht erfüllt werden. Wenn in der Regel Startbedingungen verwendet werden, um sicherzustellen, dass die Systemanforderungen erfüllt sind, können Sie die Startbedingungen während der Deinstallation im allgemeinen überspringen, indem Sie der `NOT Installed` LaunchConditions-Zeile der LaunchCondition-Tabelle die Bedingung hinzufügen.  
  
 Eine Alternative besteht darin, `OR Installed` zu Startbedingungen hinzuzufügen, die während der Installation nicht wichtig sind. Dadurch wird sichergestellt, dass die Bedingung bei der nicht Installation immer true ist, und daher wird die Fehlermeldung der Startbedingung nicht angezeigt.  
  
> [!NOTE]
> `Installed` Gibt an, dass die-Windows Installer Eigenschaft festgelegt wird, wenn Sie erkennt, dass das VSPackage bereits auf dem System installiert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Windows Installer](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)
