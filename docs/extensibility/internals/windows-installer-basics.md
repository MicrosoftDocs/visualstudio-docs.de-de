---
title: Windows Installer Grundlagen | Microsoft-Dokumentation
description: Informieren Sie sich über Windows Installer für die Installation eines VSPackages, einschließlich der Organisation der VSPackage-Funktionen in Windows Installer Komponenten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4081c79b7492e369e19187a099bf975275cb371c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869491"
---
# <a name="windows-installer-basics"></a>Grundlagen zu Windows Installer
Der Windows Installer installiert und deinstalliert Anwendungen oder Softwareprodukte auf dem Computer eines Benutzers und führt diese Aufgaben in Einheiten aus, die als Windows Installer Komponenten bezeichnet werden (manchmal als "wics" oder "nur Komponenten" bezeichnet). Eine GUID identifiziert jedes WIC, bei dem es sich um die grundlegende Einheit für die Installation und die Verweis Zählung für Setups mit Windows Installer handelt.

 Eine umfassende Dokumentation der Windows Installer finden Sie im Platform SDK-Thema [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Erstellen eines VSPackage
 In Windows Installer werden Installationspakete verwendet, die Informationen enthalten, die Windows Installer zum Installieren, deinstallieren oder Reparieren eines Produkts und zum Ausführen der Setup-Benutzeroberfläche (UI) benötigen. Jedes Installationspaket enthält eine MSI-Datei, die eine Installations Datenbank, einen Zusammenfassungs Datenstrom und Datenströme für verschiedene Teile der Installation enthält. Um das Installationsprogramm verwenden zu können, müssen Sie eine-Installation erstellen. Da das Installationsprogramm Installationen um das Konzept von Komponenten organisiert und Informationen zur Installation in einer relationalen Datenbank speichert, umfasst der Prozess der Erstellung eines Installationspakets im Allgemeinen die folgenden Schritte:

1. Planen Sie die Einrichtung Ihres Setups, um die Versionsverwaltung und parallele Strategien zu unterstützen.

2. Identifizieren Sie die Features, die Benutzern angezeigt werden sollen.

3. Organisieren Sie das VSPackage und die Abhängigkeiten in Komponenten.

4. Füllen Sie die Installations Datenbank mit Informationen auf.

5. Überprüfen Sie das Installationspaket.

   Diese Dokumentation befasst sich hauptsächlich mit dem ersten und dritten Schritt des Prozesses. Während dieser Schritte organisieren Sie Ihre VSPackage-Funktionen in wics, damit Sie Ihre Versionierung und Wartungsstrategie so Frame gestalten können, dass Sie nachfolgende Versionen von berücksichtigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die restlichen drei Schritte werden ausführlich in Windows Installer Dokumentation im Platform SDK behandelt.

## <a name="key-terms"></a>Schlüsselbegriffe
 Im folgenden finden Sie Definitionen der Schlüsselbegriffe im Zusammenhang mit der Windows Installer-Technologie.

 Ressourcen Dateien, Registrierungsschlüssel, Verknüpfungen usw., die auf einem Computer installiert werden können. Diese Ressourcen werden logisch in Windows Installer Komponenten gruppiert.

 Windows Installer Komponente (WIC) die grundlegende Einheit der Installation, die eine logische Gruppierung verwandter Ressourcen darstellt, die als Einheit installiert und deinstalliert werden. Windows Installer Komponenten werden durch eine eindeutige Komponenten-ID (GUID) identifiziert. Außerdem wird Windows Installer die Verweis Zählung auf WIC-Ebene beibehalten. Fügen Sie für eine maximale Versions Flexibilität höchstens eine primäre Ressource (z. b. eine DLL) in einem bestimmten WIC ein. Beachten Sie, dass Sie nach dem identifizieren und Auffüllen eines WIC eine GUID vergeben und bereitstellen können, um die Komposition nicht zu ändern. Weitere Informationen finden Sie unter [Organisieren von Anwendungen in Komponenten](/windows/desktop/Msi/organizing-applications-into-components).

 Paket (Redist-Paket) eine Bereitstellungs Einheit, die aus einer MSI-Datei und externen Quelldateien besteht, auf die diese Datei verweisen kann. Ein Paket enthält alle Informationen, die Windows Installer benötigt, um die Benutzeroberfläche auszuführen und die Anwendung zu installieren oder zu deinstallieren.

 MSI-Datei eine COM-strukturierte Speicherdatei, die die Anweisungen und Daten enthält, die zum Installieren einer Anwendung erforderlich sind. Jedes Paket enthält mindestens eine MSI-Datei. Die MSI-Datei enthält die Installerdatenbank, einen Zusammenfassungs Datenstrom und möglicherweise eine oder mehrere Transformationen und interne Quelldateien. Die zu installierenden Dateien können entweder in eine CAB-Datei komprimiert und in einem Stream in der MSI-Datei gespeichert werden, oder Sie können außerhalb der MSI-Datei auf dem Quell Medium gespeichert, komprimiert oder unkomprimiert werden. Weitere Informationen finden Sie unter [Windows Installer Dateierweiterungen](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Erzwingen von Windows Installer Regeln
 Zwei Sätze von Regeln bestimmen die Bereitstellung von Ressourcen über die Komponenten des Setups. Ein Regelsatz wird von der Windows Installer selbst verwaltet, während Sie den zweiten Satz als Installations Autor erzwingen sollten.

> [!NOTE]
> Die Erzwingung von Windows Installer Regeln tritt nur auf, wenn Sie eine Überprüfung der MSI-Datei ausführen. Dennoch werden Sie dazu gewarnt, diese Regeln als bewährte Methoden zu behandeln. Weitere Informationen finden Sie unter [Validieren einer Installations Datenbank](/windows/desktop/Msi/validating-an-installation-database) und [Paket](/windows/desktop/Msi/package-validation)Überprüfung.

#### <a name="installer-enforced-rules"></a>Installer-Enforced Regeln

- Alle Dateien in einer bestimmten Komponente müssen im gleichen Verzeichnis installiert sein. Im Gegensatz dazu müssen Dateien, die in separaten Ordnern installiert werden, zu separaten Komponenten gehören.

- Es darf nur ein Schlüssel Pfad pro Komponente vorhanden sein. Der Schlüssel Pfad ist einfach eine Datei oder ein Registrierungsschlüssel, der die gesamte Komponente darstellt.

#### <a name="component-provider-responsibilities"></a>Zuständigkeiten der Component-Provider

- Alle zwei Ressourcen, die möglicherweise separat in nachfolgenden Versionen ausgeliefert werden, sollten in separaten Komponenten vorhanden sein. Ressourcen sollten nur in derselben Komponente gruppiert werden, wenn Sie sicher sind, dass diese Ressourcen nie separat ausgeliefert werden. Tatsächlich wird empfohlen, dass alle primären Ressourcen (z. b. DLLs) immer in separaten wics vorhanden sind. Weitere Informationen finden Sie unter [Definieren von Installerkomponenten](/windows/desktop/Msi/defining-installer-components).

- Keine Ressource mit Versions Angabe sollte jemals in mehr als einem WIC ausgeliefert werden.

## <a name="see-also"></a>Weitere Informationen
- [Was geschieht, wenn die Komponenten Regeln beschädigt sind?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
