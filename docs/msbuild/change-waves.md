---
title: Änderungswellen
description: Hier erfahren Sie, wie Sie Features in MSBuild aktivieren oder deaktivieren, die zu Störungen führen könnten.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 77f93b4741ee987bac871e619ccbe58e2d4d4000
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939525"
---
# <a name="change-waves"></a>Änderungswellen

Eine *Änderungswelle* besteht aus mehreren Behavior Changes in MSBuild, die Sie deaktivieren können, indem Sie ein bestimmtes Flag als Umgebungsvariable angeben. Der Zweck dahinter ist, Sie vor Änderungen zu warnen, die zu Störungen führen können, damit Sie über die Flexibilität verfügen, sich auf diese Änderungen vorbereiten zu können, bevor sie zu Standardfunktionen werden. Sie können keine einzelnen Features einer bestimmten Änderungswelle aktivieren oder deaktivieren, sondern sie nur insgesamt aktivieren oder deaktivieren.

Wenn Sie ein Upgrade zu einer neuen MSBuild-Version durchführen, sind Änderungen, die möglicherweise Breaking Changes sind, standardmäßig aktiviert. Wenn sich ein Feature jedoch negativ auf Ihr Build auswirkt, können Sie die entsprechende Änderungswelle problemlos deaktivieren. Jede Änderungswelle wird mit einer MSBuild-Versionsnummer gekennzeichnet (z. B. 16.8.). Bei Festlegung dieser Änderungswelle werden jedoch nur bestimmte Features gesteuert, die sich möglicherweise auf den Buildprozess auswirken können, nicht jedoch alle Änderungen der MSBuild-Version. Eine Liste der Features der verschiedenen Änderungswellen finden Sie im Abschnitt [Änderungswellen und dazugehörige Features](#change-waves-and-associated-features) in diesem Artikel. Wenn Sie eine Änderungswelle deaktivieren, werden damit auch Änderungswellen höherer Versionen deaktiviert.

## <a name="opt-out-of-change-wave-features"></a>Deaktivieren der Features von Änderungswellen

Wenn Sie die Features einer Änderungswelle deaktivieren möchten, legen Sie die Umgebungsvariable `MSBuildDisableFeaturesFromVersion` auf die Änderungswelle (oder die MSBuild-Version) fest, die die Features enthält, die Sie **deaktivieren** möchten. Hierbei handelt es sich um die MSBuild-Version, für die die Features entwickelt wurden. Unten sehen Sie eine Zuordnung von Features zu Änderungswellen.

### <a name="msbuilddisablefeaturesfromversion-values"></a>MSBuildDisableFeaturesFromVersion-Werte

Sie erhalten eine Warnung und/oder einen Standardwert für eine bestimmte Welle, wenn Sie `MSBuildDisableFeaturesFromVersion` nicht auf eine gültige Änderungswelle festlegen. In der folgenden Tabelle sind die möglichen Einstellungen aufgeführt:

| `MSBuildDisableFeaturesFromVersion`-Wert                         | Ergebnis        | Warnung erhalten? |
| :-------------                                                    | :----------   | :----------: |
| Nicht festgelegt                                                             | Hierbei sind alle Änderungswellen, d. h. alle Features einer bestimmen Änderungswelle, aktiviert.               | Nein   |
| Eine beliebige gültige und aktuelle Änderungswelle (z. B. `16.8`)                      | Hierbei werden alle Features der Änderungswelle `16.8` **und höher** deaktiviert.                                           | Nein   |
| Ungültiger Wert (z. B. `16.9`, wenn nur `16.8` und `16.10` gültige Wellen sind)| Standardmäßig wird der nächstgelegene gültige Wert in aufsteigender Reihenfolge verwendet. Wenn beispielsweise `16.9` festgelegt wird, wird standardmäßig `16.10` verwendet.               | Nein   |
| Außerhalb der Rotation (z. B. `17.1`, wenn die höchste Welle `17.0` ist)      | Hierbei wird ein Übergang zum nächstgelegenen gültigen Wert durchgeführt. Für `17.1` wird beispielsweise `17.0` verwendet, für `16.5` wird `16.8` verwendet.                    | Ja  |
| Ungültiges Format (z. B. `16x8`, `17_0`, `garbage`)                    | Hierbei sind alle Änderungswellen, d. h. alle Features einer bestimmen Änderungswelle, aktiviert.               | Ja  |

## <a name="change-waves-and-associated-features"></a>Änderungswellen und dazugehörige Features

Die Links in der Liste unten führen zum GitHub-Pull Request für dieses Feature.

### <a name="168"></a>16.8

- [Aktivieren von NoWarn](https://github.com/dotnet/msbuild/pull/5671)
- [Kürzen von Protokollmeldungen zu übersprungenen Zielen/Aufgaben auf 1.024 Zeichen](https://github.com/dotnet/msbuild/pull/5553)
- [Keine Erweiterung vollständiger Laufwerkglobs mit falscher Bedingung](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Fehler bei Leerraum einer Eigenschaftserweiterung in einer Bedingung](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Für diese Änderungswelle gibt es noch keine Einträge.

## <a name="change-waves-that-are-out-of-rotation"></a>Änderungswellen außerhalb der Rotation

Aktuell gibt es keine Änderungswellen, die sich außerhalb der Rotation befinden.

## <a name="faq"></a>Häufig gestellte Fragen

**Warum sollten andere Releases als Ziel verwendet werden, wenn Änderungswellen aussortiert werden?**

Wir sind der Meinung, es ist ausreichend Zeit, um mit Betroffenen zu sprechen und bei der Umsetzung dieser Änderungen Unterstützung zu bieten.

**Warum wird eine Umgebungsvariable und keine Projekteigenschaft verwendet?**

Es gibt Szenarios, in denen ein Feature Teil einer Änderungswelle sein soll, bevor MSBuild das Projekt geladen hat. Aus diesem Grund sind für Änderungswellen Umgebungsvariablen erforderlich.

**Die Features sind standardmäßig aktiviert und müssen bei Bedarf deaktiviert werden. Warum ist dies nicht umgekehrt?**

Dieser Ansatz eignet sich besser für uns, da wir andernfalls nur eingeschränkt Feedback erhalten würden, wenn ein Feature Builds von Kunden beeinträchtigt.

## <a name="see-also"></a>Siehe auch

- [MSBuild](msbuild.md)
- [Neuerungen in MSBuild 16.0](whats-new-msbuild-16-0.md)
