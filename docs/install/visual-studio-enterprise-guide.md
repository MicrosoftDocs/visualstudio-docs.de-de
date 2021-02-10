---
title: Leitfaden zu Visual Studio Enterprise
description: Richten Sie Visual Studio in einer Unternehmensumgebung ein, und beheben Sie mögliche Probleme.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e653d7ae5f2408fd8438cbdf69a28648c6bcc446
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967110"
---
# <a name="visual-studio-enterprise-guide"></a>Leitfaden zu Visual Studio Enterprise
Wenn Sie Zeit sparen möchten, während Sie Visual Studio für Ihr Unternehmen einrichten, sind Sie hier genau richtig. Dieser Leitfaden bietet Tipps, die Sie beim Installieren und Aktualisieren von Visual Studio in gängigen Unternehmensszenarien unterstützen. Sie erhalten auch Hinweise zur Lösung von Problemen, und Sie erfahren, wie Sie ein Problem melden, wenn Sie weitere Hilfe benötigen. 

## <a name="get-started"></a>Erste Schritte 
Erfahren Sie, wie Sie Visual Studio in Netzwerk- und Offlineumgebungen für Ihr Unternehmen bereitstellen. 

- **Grundlegendes zu den Optionen für die Unternehmensbereitstellung in Netzwerkumgebungen**. Das [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md) bietet szenariobasierte Anleitungen für Systemadministratoren. 

- **[Tipps zur Problembehandlung](troubleshooting-installation-issues.md)** . Hier erhalten Sie Hilfe beim Installieren oder Aktualisieren von Visual Studio, und Sie erfahren, wie Sie ein Problem melden, wenn Sie nicht weiterkommen. Diese Tipps enthalten Schrittanleitungen, mit denen sich die meisten Online- oder Offline-Installationsprobleme beheben lassen sollten. 

- **[Erstellen einer Offline-Installation von Visual Studio](create-an-offline-installation-of-visual-studio.md)** . Wenn Sie nicht mit dem Internet verbunden sind oder die Internetverbindung eingeschränkt ist, finden Sie hier weitere Optionen zum Installieren von Visual Studio. 

- **[Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)** . Hier erfahren Sie, wie Sie benutzerdefinierte Bootstrapperpakete erstellen, indem Sie Produkt- und Paketmanifeste erstellen. 

- **[Automatisches Anwenden von Product Keys beim Bereitstellen von Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)** . Sie können Ihren Product Key programmgesteuert als Teil eines Skripts anwenden, mit dem die Bereitstellung von Visual Studio automatisiert wird. Sie können einen Product Key während der Installation von Visual Studio oder nach Abschluss der Installation auf einem Gerät programmgesteuert festlegen. 

## <a name="install-visual-studio"></a>Installieren von Visual Studio 

Erfahren Sie, wie Sie Visual Studio in gängigen Unternehmensszenarien installieren. 

- **[Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)** . Verwenden Sie eine Vielzahl von Parametern, um Ihre Visual Studio-Installation zu steuern und anzupassen. Automatisieren Sie den Installationsprozess, oder erstellen Sie einen Cache der Installationsdateien zur späteren Verwendung. 

- **[Beispiele für Befehlszeilenparameter für die Installation von Visual Studio](command-line-parameter-examples.md)** . Zur Veranschaulichung der Verwendung von Befehlszeilenparametern zur Installation von Visual Studio sind hier einige Beispiele aufgeführt, die Sie Ihren Bedürfnissen anpassen können. 

- **[Installieren und Verwenden von Visual Studio und Azure-Diensten hinter einer Firewall oder einem Proxyserver](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)** . Wenn Ihre Organisation Sicherheitsmechanismen wie eine Firewall oder einen Proxyserver verwendet, sollten Sie einige Domänen-URLs in eine Zulassungsliste aufnehmen und verschiedene Ports und Protokolle öffnen bzw. deren Verwendung zulassen, um eine optimale Installation und Verwendung von Visual Studio und Azure-Diensten zu gewährleisten. 

- **[Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md)** . Speichern Sie die Dateien für die Erstinstallation zusammen mit allen Produktupdates in einem einzelnen Ordner zwischen.  

## <a name="update-visual-studio"></a>Aktualisieren von Visual Studio 2017 

Erfahren Sie, wie Sie Visual Studio erfolgreich aktualisieren und Probleme bei der Aktualisierung beheben. 

- **[Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)** . Aktualisieren Sie ein Layout für die Netzwerkinstallation von Visual Studio mit den neuesten Produktupdates, sodass es sowohl als Installationspfad für das neueste Update von Visual Studio als auch zum Warten von Installationen verwendet werden kann, die bereits auf Clientarbeitsstationen bereitgestellt wurden.

- **[Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung](update-servicing-baseline.md)** . Informieren Sie sich, welchen Nutzen es Ihnen bringt, wenn Sie Updates anhand einer Baseline ausführen, und lernen Sie den Unterschied zwischen Nebenversionen und Wartungsupdates kennen. 

- **[Aktualisieren von Visual Studio mit einem minimalen Offlinelayout](update-minimal-layout.md)** . Für Computer, die nicht mit dem Internet verbunden sind, ist das Erstellen eines minimalen Layouts die einfachste und schnellste Möglichkeit, Ihre Offlineinstanzen in Visual Studio zu aktualisieren.

- **[Reparieren von Visual Studio](repair-visual-studio.md) zum Beheben von Updateproblemen**. Es kann vorkommen, dass Ihre Visual Studio-Installation beschädigt wird oder fehlerhaft ist. Eine Reparatur ist nützlich, um Installationsprobleme bei allen Installationsvorgängen, einschließlich Updates, zu beheben. 

- **Befolgen von [Windows-Sicherheitsbaselines](/windows/security/threat-protection/windows-security-baselines)** . Microsoft arbeitet dediziert daran, seinen Kunden sichere Betriebssysteme wie Windows 10 und Windows Server sowie sichere Apps wie Microsoft Edge bereitzustellen. Zusätzlich zur Sicherheit der Produkte bietet Microsoft Ihnen mit verschiedenen Konfigurationsfunktionen auch eine differenzierte Kontrolle über Ihre Umgebungen. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch 

- [Produktivitätsleitfaden für Visual Studio](../ide/productivity-features.md)