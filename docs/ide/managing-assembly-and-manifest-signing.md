---
title: Verwalten der Signierung von Assemblys und Manifesten
description: In diesem Artikel erfahren Sie mehr über die Vorteile von Signaturen mit starkem Namen, die einer Softwarekomponente eine weltweit eindeutige Identität verleihen.
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 709a5a64164ed6c80c29a8e554d2b07050e18339
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886521"
---
# <a name="manage-assembly-and-manifest-signing"></a>Verwalten der Signierung von Assemblys und Manifesten

Durch eine Signierung mit starkem Namen erhalten Softwarekomponenten eine global eindeutige Identität. Starke Namen werden verwendet, um sicherzustellen, dass die Assembly nicht von einem anderen Entwickler manipuliert werden kann und dass Komponentenabhängigkeiten und Konfigurationsanweisungen der richtigen Komponente und Komponentenversion zugeordnet werden.

Ein starker Name setzt sich aus der Identität der Assembly – dem einfachen Textnamen, der Versionsnummer und Kulturinformationen – sowie einem öffentlichen Schlüsseltoken und einer digitalen Signatur zusammen.

Informationen zum Signieren von Assemblys in Visual Basic- und C#-Projekten finden Sie unter [Erstellen und Verwenden von Assemblys mit starkem Namen](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Informationen zum Signieren von Assemblys in C++-Projekten finden Sie unter [Assemblys mit starken Namen (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Die Signierung mit starken Namen schützt nicht gegen Reverse Engineering (Zurückentwicklung) der Assembly. Informationen zum Schutz gegen Reverse Engineering finden Sie unter [Dotfuscator Community Edition](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Objekttypen und Signierung

Sie können folgende .NET-Assemblys und Anwendungsmanifeste signieren:

- Ausführbare Dateien (*.exe*)

- Anwendungsmanifeste (*.exe.manifest*)

- Bereitstellungsmanifeste (*.application*)

- Freigegebene Komponentenassemblys (*.dll*)

Signieren Sie folgende Objekttypen:

1. Assemblys, wenn diese im globalen Assemblycache (GAC) bereitgestellt werden sollen.

2. ClickOnce-Anwendungen und Bereitstellungsmanifeste. Visual Studio aktiviert die Signierung für diese Anwendungen standardmäßig.

3. Primäre Interop-Assemblys, die für die COM-Interoperabilität verwendet werden. Durch das TLBIMP-Dienstprogramm werden primäre Interop-Assemblys mit einem starken Namen erzwungen, wenn diese aus einer COM-Typbibliothek erstellt werden.

Im Allgemeinen sollten Sie ausführbare Dateien nicht signieren. Eine Komponente mit starkem Namen kann nicht auf eine Komponente ohne starken Namen verweisen, die mit der Anwendung bereitgestellt wird. Visual Studio signiert nicht ausführbare Dateien der Anwendung, signiert jedoch stattdessen das Anwendungsmanifest, das auf die ausführbare Datei mit schwachem Namen zeigt. Vermeiden Sie das Signieren von Komponenten, die für Ihre Anwendung privat sind, da das Signieren das Verwalten von Abhängigkeiten erschweren kann.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Signieren einer Assembly in Visual Studio

Verwenden Sie zum Signieren einer Anwendung oder Komponente die Registerkarte **Signierung** des Projekteigenschaftenfensters (klicken Sie dazu zuerst im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten und anschließend mit der linken auf **Eigenschaften**). Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.

Geben Sie eine Schlüsseldatei an. Wenn Sie eine neue Schlüsseldatei erstellen, werden neue Schlüsseldateien immer im *PFX-Format* erstellt. Sie benötigen einen Namen und ein Kennwort für die neue Datei.

> [!WARNING]
> Sie sollten die Schlüsseldatei immer mit einem Kennwort schützen, damit sie von keiner anderen Person verwendet werden kann. Sie können die Schlüsseldateien auch schützen, indem Sie Schlüsselanbieter oder Zertifikatspeicher verwenden.

Außerdem können Sie auf eine Schlüsseldatei, die Sie bereits erstellt haben, zeigen. Weitere Informationen zum Erstellen eines Schlüssels finden Sie unter [Create a Public-Private Key (Erstellen eines Paars aus öffentlichem und privatem Schlüssel)](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Wenn Sie nur Zugriff auf einen öffentlichen Schlüssel haben, können Sie verzögertes Signieren verwenden, um das Zuweisen des Schlüssels zu verzögern. Sie können auch das verzögerte Signieren aktivieren, indem Sie das Kontrollkästchen **Nur verzögerte Signierung** aktivieren. Ein verzögert signiertes Projekt wird nicht ausgeführt, und Sie können es nicht debuggen. Allerdings können Sie die Überprüfung während der Entwicklung überspringen, indem Sie das Strong Name-Tool [Sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) mit der Option `-Vr` verwenden.

Weitere Informationen zum Signieren von Manifesten finden Sie unter [Vorgehensweise: Signieren von Anwendungs- und Bereitstellungsmanifesten](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Siehe auch

- [Assemblys mit starken Namen](/dotnet/framework/app-domains/strong-named-assemblies)
- [Assemblys mit starken Namen (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
