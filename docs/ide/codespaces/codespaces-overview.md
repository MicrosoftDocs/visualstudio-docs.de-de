---
title: Überblick über GitHub Codespaces (Vorschauversion)
description: Hier erfahren Sie mehr über GitHub Codespaces für Visual Studio und darüber, wie die Lösung Ihnen helfen kann, Ihre Entwicklungsumgebung auf die Cloud auszuweiten.
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 374e07735667a2a8891824b23d49b061651b3b95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911719"
---
# <a name="what-is-github-codespaces-preview"></a>Was ist GitHub Codespaces? (Vorschau)

Willkommen bei Codespaces! Vielen Dank für Ihr Interesse.

GitHub Codespaces bietet eine cloudgestützte Entwicklungsumgebung für jede beliebige Aktivität, von langfristigen Projekten bis hin zu kurzfristigen Aufgaben wie dem Überprüfen eines Pull Request. Sie können in der Vorschauversion für Visual Studio 2019 mit Codespaces arbeiten ([für die eingeschränkte öffentliche Betaversion registrieren](https://github.com/features/codespaces/signup-vs)).

Außerdem vereint GitHub Codespaces viele der DevOps-Vorteile wie Wiederholbarkeit und Zuverlässigkeit, die bisher üblicherweise für Produktionsworkloads reserviert waren, in einer einzelnen Entwicklungsumgebung. Sie können GitHub Codespaces auch personalisieren, sodass Ihre bevorzugten und bewährten Tools, Prozesse und Konfigurationen ebenfalls verfügbar sind.

In diesem Dokument werden die Schlüsselkonzepte erläutert und die Codespaces-Features vorgestellt. Wenn Sie Codespaces ausprobieren möchten, sollten Sie [Verwenden von Visual Studio mit einem Codespace](use-visual-studio-with-codespaces.md) lesen.

> [!IMPORTANT]
> Für die Verwendung von GitHub Codespaces müssen Sie sich für die eingeschränkte [öffentliche Betaversion](https://github.com/features/codespaces/signup-vs) registrieren. Während der Betaphase erteilt GitHub keine Garantien bezüglich der Verfügbarkeit von Codespaces. Weitere Informationen zur Teilnahme an der Betaphase finden Sie unter [Informationen über Codespaces](https://docs.github.com/github/developing-online-with-codespaces/about-codespaces#joining-the-beta).

## <a name="concepts-and-features"></a>Konzepte und Features

Die Features von GitHub Codespaces bauen auf einigen grundlegenden Konzepten auf. In diesem Abschnitt werden diese Konzepte behandelt und ein kurzer Überblick über die Features geboten.

### <a name="remote-development"></a>Remoteentwicklung

Viele Entwickler versuchen heutzutage, in Remotesetups oder VMs zu programmieren, die mit bestimmten Entwicklungs- und Laufzeitstapeln konfiguriert sind. Der Grund hierfür ist, dass es zu schwierig, zu disruptiv und in einigen Fällen beinahe unmöglich ist, diese Entwicklungsumgebungen lokal einzurichten. Außerdem möchten Entwickler neue Technologien oder Frameworks ausprobieren, ohne befürchten zu müssen, dass die Computer, die sie für ihre alltägliche Arbeit benötigen, in Mitleidenschaft gezogen werden.

Obwohl Remoteumgebungen und remotefähige Tools Entwicklern bereits deutlich mehr Möglichkeiten bieten, bringen sie häufig einen Mehraufwand an Computerverwaltung mit sich. Die Umgebungskonfiguration verkompliziert das Onboarding sowie den Kontextwechsel. Mit GitHub Codespaces können alle Hindernisse für ein schnelles Onboarding und Kontextwechsel überwunden werden, da mehrere Umgebungen gleichzeitig vorhanden sein können. 

GitHub Codespaces bietet verwaltete Lösungen, mit denen Sie sich auf die Produktivität anstatt auf das Setup konzentrieren können. GitHub Codespaces erweitert Visual Studio 2019 konzeptionell und technisch für die Remoteentwicklung. 

### <a name="about-codespaces"></a>Informationen zu Codespaces

Bei einem Codespace handelt es sich um das „Back-End“ von GitHub Codespaces. Dort werden alle Computeprozesse der Softwareentwicklung, also z. B. die Kompilierung, das Debuggen und die Wiederherstellung ausgeführt. Beim Erstellen eines Codespace werden alle Ressourcen vorbereitet, die Sie benötigen, um eine Aufgabe abzuschließen, einen Pull Request zu überprüfen oder ein neues Projekt zu starten. Codespaces konfiguriert die Runtime, den Compiler, den Debugger, den Editor, die benutzerdefinierten Dotfile-Konfigurationen und den Quellcode, der für die Arbeit an einem Projekt erforderlich ist.

Cloudgestützte Codespaces bieten die folgenden Vorteile:

- Sie können schnell erstellt und gelöscht werden. Sie können beliebig viele Codespaces (innerhalb der geltenden Kontogrenzwerte) erstellen und diese wieder löschen, wenn Sie sie nicht mehr benötigen.
- Codespaces werden verwaltet, wodurch sich die Gesamtwartung für Sie reduziert.
- Codespaces bieten vorhersagbare Preise, und Sie zahlen nur für die Ressourcen, die Sie nutzen. Außerdem gibt es einen integrierten Vorgang zum automatischen Unterbrechen (autosuspend), um Kostenexplosionen zu vermeiden.
- Codespaces sparen Computeressourcen. Wenn Sie Ihre Entwicklungsworkload in die Cloud verlagern, werden begrenzte Ressourcen auf Ihrem persönlichen Computer freigegeben.

## <a name="custom-configuration"></a>Benutzerdefinierte Konfiguration

GitHub Codespaces ist so aufgebaut, dass eine Vielzahl von Projekten oder Aufgaben unterstützt wird. Sie können mit intelligenten Konfigurationsfeatures beginnen, die allgemeine Standardeinstellungen bereitstellen, oder einen Codespace mit einer [benutzerdefinierten Konfiguration](customize-codespaces.md) optimieren.

Dank flexibler Konfigurationen können Entwickler schnell an Projekten mitarbeiten, die eine spezifische Konfiguration und schwer auf einem lokalen Computer umsetzbare Anforderungen aufweisen. Außerdem vermeiden reproduzierbare Codespaces computerspezifische Probleme.

## <a name="personal-configuration"></a>Persönliche Konfiguration

Es ist bekannt, dass die Beibehaltung persönlicher Einstellungen wichtig ist, damit die Entwicklung in einem in der Cloud gehosteten Codespace vertrauter erscheint. In GitHub Codespaces können zusätzlich zur Codespacekonfiguration individualisierte Anpassungen vorgenommen werden. Persönliche Einstellungen und Konfigurationen für Editoren und Terminals werden von GitHub Codespaces unterstützt.

Ein Codespace kann mit einer benutzerspezifischen Sammlung von [benutzerdefinierten Dotfiles](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) erstellt werden (z. B. `.bashrc`, `.gitconfig` usw.). Außerdem synchronisiert GitHub Codespaces automatisch Ihre Git-Identitäten, -Entwürfe und -Einstellungen, sodass jeder von Ihnen erstellte Codespace unabhängig von den projektspezifischen Umgebungsfunktionen die gewünschte Darstellung aufweist.

## <a name="see-also"></a>Weitere Informationen

* [Verwenden von Visual Studio mit einem Codespace](use-visual-studio-with-codespaces.md)
* [Anpassen eines Codespace](customize-codespaces.md)
* [Unterstützte Visual Studio-Features](supported-features-codespaces.md)
