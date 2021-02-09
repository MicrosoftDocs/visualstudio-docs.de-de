---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: overview
keywords: dotfuscator, dotfuscator ce, dotfuscator community, preemptive, preemptive solutions, preemptive protection, protection, community edition, obfuskation, .NET, kostenlos, visual studio 2019, visual studio 2017, visual studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Erfahren Sie, wie Sie mit Ihrer Kopie von Dotfuscator Community, die in Visual Studio kostenlos enthalten ist, Ihre .NET-Anwendungen schützen können.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: ce0f7cb1b5f970da7b6e47797dd4c59012a46892
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924776"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection – Dotfuscator*** bietet umfassenden Schutz für .NET-Anwendungen, der problemlos in den sicheren Lebenszyklus der Softwareentwicklung passt.
Verwenden Sie die Lösung, um Desktop-, mobile, Server- und eingebettete Anwendungen zu härten, zu schützen und zu bereinigen. Dadurch können Sie Geschäftsgeheimnisse und sonstiges geistiges Eigentum sichern, Piraterie und Fälschungen reduzieren und Schutz vor Manipulationen und nicht autorisiertem Debuggen bieten.
Dotfuscator arbeitet in kompilierten Assemblys ohne zusätzliche Programmierung und sogar ohne Zugriff auf den Quellcode.

![PreEmptive Protection – Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Warum der Schutz von Daten wichtig ist

Es ist wichtig, **Ihr geistiges Eigentum zu schützen**.
Der Code Ihrer Anwendung enthält Entwurfs- und Implementierungsdetails, die als geistiges Eigentum angesehen werden können.
Allerdings enthalten in .NET Framework erstellte Anwendungen [wichtige Metadaten und allgemeinen Zwischencode][assemblies], und dies erleichtert das Reverse Engineering mit einem von vielen kostenlosen, automatisierten Tools.
Indem Sie das Reverse Engineering behindern und unterbinden, können Sie die nicht autorisierte Veröffentlichung von geistigem Eigentum verhindern und zeigen, dass Ihr Code Geschäftsgeheimnisse enthält.
Dotfuscator kann Ihre .NET-Assemblys [verschleiern][obfuscation], um Reverse Engineering zu verhindern. Dabei wird das ursprüngliche Verhalten der Anwendung nicht beeinträchtigt.

Es ist auch wichtig, **die Integrität der Anwendung zu schützen**.
Zusätzlich zum Reverse Engineering könnten böswillige Benutzer versuchen, illegale Kopien der Anwendung zu erstellen, das Verhalten der Anwendung zur Laufzeit zu ändern oder Daten zu manipulieren.
Mit Dotfuscator können Sie Ihrer Anwendung um eine Funktionalität erweitern, mit der Sie [eine nicht autorisierte Nutzung erkennen und auf eine solche Nutzung reagieren können][checks], einschließlich Manipulationen, Drittanbieterdebugging und Geräten mit Rootzugriff.

Weitere Informationen zum Integrieren von Dotfuscator in einen sicheren Lebenszyklus der Softwareentwicklung finden Sie auf der PreEmptive Solutions-Seite zum [SDL-App-Schutz][sdl-protection].

## <a name="about-dotfuscator-community"></a>Überblick über Dotfuscator Community

Ihre Kopie von Microsoft Visual Studio beinhaltet eine kostenlose Kopie von ***PreEmptive Protection – Dotfuscator Community*** für den Privatgebrauch.
(Diese kostenlose Version hieß früher Dotfuscator Community Edition oder Dotfuscator CE.) Anweisungen zum Installieren der Version von Dotfuscator Community, die in Visual Studio enthalten ist, finden Sie auf der [Installationsseite][install].

Dotfuscator Community bietet für Entwickler, Architekten und Tester eine Reihe von Diensten für [Softwareschutz und -härtung][software-protection].
Beispiele für Dotfuscator Community-Features für [.NET-Obfuskation][obfuscation] und sonstigen [Anwendungsschutz][app-protection]:

* *[Umbenennung][renaming]* von Bezeichnern, um das Reverse Engineering der kompilierten Assemblys zu erschweren.
* *[Manipulationsschutz][tamper]* , um die Ausführung manipulierter Anwendungen zu erkennen und manipulierte Sitzungen zu beenden oder in geeigneter Weise zu reagieren.
* *[Debugschutz][debug]* , um das Anfügen eines Debuggers an eine aktive Anwendung zu erkennen und Debugsitzungen zu beenden oder in geeigneter Weise zu reagieren.
* *[Schutz vor Geräten mit Rootzugriff][root]* , um zu ermitteln, ob die Anwendung auf einem Android-Gerät mit Rootzugriff ausgeführt wird, und um Sitzungen auf diesen Geräten zu beenden oder in geeigneter Weise zu reagieren.
* *[Verhaltensweisen beim Ablauf von Anwendungen][shelflife]* , mit denen ein Enddatum codiert wird und abgelaufene Anwendungssitzungen beendet werden.

Weitere Informationen zu diesen Funktionen und dazu, wie sie in die Strategie zum Schutz Ihrer Anwendungen passen, finden Sie auf der [Seite mit Funktionen][capabilities].

Dotfuscator Community bietet ohne zusätzliche Konfiguration grundlegenden Schutz.
Weitere Maßnahmen zum Schutz von Anwendungen stehen für registrierte Benutzer von Dotfuscator Community und für Benutzer von ***PreEmptive Protection – Dotfuscator Professional***, der weltweit führenden Lösung für [.NET-Obfuskation][net-obfuscator], zur Verfügung.
Informationen über das Erweitern von Dotfuscator finden Sie auf der [Upgradeseite][upgrades].

## <a name="getting-started"></a>Erste Schritte

::: moniker range="vs-2019"

Beginnen Sie mit der Nutzung von Dotfuscator Community in Visual Studio, indem Sie in der **Suchleiste** (STRG+Q) `dotfuscator` eingeben.

* Wenn Dotfuscator Community bereits installiert wurde, wird im **Suchfeld** die Option angezeigt, Dotfuscator Community unter der Überschrift *Menüs* zu starten. Weitere Informationen finden Sie [auf der „Erste Schritte“-Seite des vollständigen Dotfuscator Community-Benutzerhandbuchs][get-started].
* Wenn Dotfuscator Community noch nicht installiert wurde, wird im **Suchfeld** unter der Überschrift *Einzelne Komponenten* die Option **Install PreEmptive Protection – Dotfuscator** (PreEmptive Protection installieren – Dotfuscator) angezeigt. Details finden Sie auf der [Installationsseite][install].

::: moniker-end

::: moniker range="vs-2017"

Beginnen Sie mit der Nutzung von Dotfuscator Community in Visual Studio, indem Sie in der Suchleiste **Schnellstart** (STRG+Q) `dotfuscator` eingeben.

* Wenn Dotfuscator Community bereits installiert ist, wird über **Schnellstart** die Option *Menü* angezeigt, um die Benutzeroberfläche von Dotfuscator Community zu starten. Weitere Informationen finden Sie [auf der „Erste Schritte“-Seite des vollständigen Dotfuscator Community-Benutzerhandbuchs][get-started].
* Wenn Dotfuscator Community noch nicht installiert ist, wird durch den **Schnellstart** die relevante Option *Installieren* angezeigt. Details finden Sie auf der [Installationsseite][install].

::: moniker-end

Sie können auch die **neueste Version** von Dotfuscator Community von [der Seite mit Dotfuscator-Downloads auf „preemptive.com“ herunterladen][download].

## <a name="full-documentation"></a>Vollständige Dokumentation

Diese Seite und die dazugehörigen Unterseiten bieten einen allgemeinen Überblick über Dotfuscator Community-Features sowie [Anweisungen zur Installation des Tools][install].

Ausführliche Anweisungen zur Verwendung finden Sie im [vollständigen Dotfuscator Community-Benutzerhandbuch auf „preemptive.com“][full]. Dort finden Sie auch Informationen [zur Verwendung der Benutzeroberfläche von Dotfuscator Community][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
