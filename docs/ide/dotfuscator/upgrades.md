---
title: Upgraden von Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: dotfuscator, dotfuscator community, dotfuscator ce, preemptive, preemptive solutions, preemptive protection, protection, community edition, obfuskation, .NET, kostenlos, visual studio 2019, visual studio 2017, visual studio, upgrade, befehlszeile
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Erfahren Sie, wie Sie die in Visual Studio enthaltene, kostenlose Dotfuscator Community-Kopie upgraden können.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: a0e3ad3e5f6afbd6675f8e65c918b4a5d7c66dd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922786"
---
# <a name="upgrade-dotfuscator-community"></a>Upgraden von Dotfuscator Community

Dotfuscator Community bietet viele Funktionen für sofortigen Anwendungsschutz und sofortige Anwendungshärtung für alle Entwickler, die mit Microsoft Visual Studio arbeiten.
Für Benutzer, die Ihre Version von Dotfuscator upgraden, sind jedoch mehr Funktionen verfügbar.

## <a name="registering-dotfuscator-community"></a>Registrieren von Dotfuscator Community

Als registrierte Benutzer von Dotfuscator Community erhalten Sie Zugriff auf zusätzliche Features wie der [Befehlszeilenunterstützung][cli], sodass Sie Dotfuscator Community mühelos in Ihren automatisierten Buildprozess integrieren können. Darüber hinaus gewährt die Registrierung Zugriff auf ein integriertes Tool, das für die [Decodierung verschleierter Stapelüberwachungen][decode-obfuscated] verwendet wird.

Die Registrierung ist schnell, einfach und kostenlos.
Wenn Sie Dotfuscator Community registrieren möchten, finden Sie die [Anleitungen im vollständigen Dotfuscator Community-Benutzerhandbuch][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Während die Dotfuscator Community ein grundlegendes Schutzlevel bietet, enthält ***PreEmptive Protection – Dotfuscator Professional*** erweiterte Obfuskationstransformationen und Schutzfunktionen, z.B.:

* *Schutz geistigen Eigentums*
  * Zusätzliche Umbenennungsoptionen einschließlich Enhanced Overload Induction™ sowie zufällige Auswahl von Bezeichnern.
  * Zugriff auf Obfuskationstransformationen auf Unternehmensebene einschließlich [Transformationen zur Vereitelung von automatisierter Code-Dekompilierung][control-flow].
  * Die Möglichkeit zum [Verbergen vertraulicher Zeichenfolgen][string-encryption], die eine einfache Suche im dekompilierten Code unmöglich macht.
  * Die Möglichkeit zur [diskreten Einbettung von Besitz und Verteilungszeichenfolgen in Ihre Assemblys][watermarking], mit der Sie die Quelle nicht autorisierter Softwareleaks finden können.
  * Die Möglichkeit, [mehrere Assemblys in einer zu kombinieren][linking] und damit Angreifern das Bestimmen der Rollen von Codeelementen weiter zu erschweren, wurde als Trennung der Belange entfernt.
  * Die Möglichkeit, [nicht verwendeten Code automatisch aus der Anwendung zu entfernen][pruning] und so die Menge an vertraulichem Code, der implementiert wird, zu reduzieren.
* *Schutz der Anwendungsintegrität*
  * Zusätzliche [Abwehrverhalten der Anwendung][check-actions].
  * Die Möglichkeit, einen Warnungszeitraum vor der End-of-Life-Deadline einer Anwendung anzugeben.
  * Die Möglichkeit, Anwendungscode während eines End-of-Life-Warnungszeitraums oder nach Ablauf der Deadline anzuzeigen.

Dotfuscator Professional ist der [.NET Obfuscator][net-obfuscator]-Industriestandard und eignet sich für Enterprise-Entwickler, die fortlaufende Unterstützung, Wartung und Produkt-Updates benötigen.
Darüber hinaus bietet Dotfuscator Professional eine engere Integration mit Visual Studio und ist für die gewerbliche Verwendung lizenziert.

Weitere Informationen zu den erweiterten Features von Dotfuscator Professional zum Anwendungsschutz erhalten Sie auf der [Seite Dotfuscator Overview (Übersicht über Dotfuscator)][product-about] von PreEmptive Solutions und [im Vergleich mit Dotfuscator Community][product-compare].
[Vollständig unterstützte Testversionen sind unter preemptive.com erhältlich][eval].

## <a name="see-also"></a>Weitere Informationen

[Dieser Artikel im vollständigen Dotfuscator Community-Benutzerhandbuch][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
