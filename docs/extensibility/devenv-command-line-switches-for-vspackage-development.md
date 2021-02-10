---
title: Debug-Command-Line Switches für die VSPackage-Entwicklung | Microsoft-Dokumentation
description: Erfahren Sie, wie Entwickler Aufgaben über die Befehlszeile automatisieren können, wenn Sie devenv.exe ausführen, die Datei, die die Visual Studio-IDE startet.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c6b6260bad412127afe4dd9135ccf66d48e9e3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968306"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung

Visual Studio ermöglicht Entwicklern das Automatisieren von Aufgaben über die Befehlszeile bei `devenv.exe` der Ausführung, die Datei, die die Visual Studio-IDE startet.

 Zu den Tasks gehören:

- Bereitstellen von Anwendungen in vorgefertigten Konfigurationen von außerhalb der IDE.

- Automatisches Erstellen von Projekten mithilfe vordefinierter Buildeinstellungen oder Debugkonfigurationen.

- Laden der IDE in bestimmten Konfigurationen, von außerhalb der IDE. Sie können die IDE auch beim Start anpassen.

## <a name="guidelines-for-switches"></a>Richtlinien für Switches

In der Visual Studio-Dokumentation werden die `devenv` Befehls Zeilenschalter auf Benutzerebene beschrieben. Weitere Informationen finden Sie unter [devenv-Befehls Zeilenschalter](../ide/reference/devenv-command-line-switches.md). Das `devenv` Tool unterstützt auch zusätzliche Befehls Zeilenschalter, die für die Entwicklung, Bereitstellung und das Debuggen von VSPackages nützlich sind.

| Befehls Zeilenschalter | BESCHREIBUNG |
|---------------------| - |
| `/ResetSkipPkgs` | Löscht alle Skip-Lade Optionen, die von Benutzern hinzugefügt wurden, die das Laden von problematischen VSPackages vermeiden möchten, und startet dann Visual Studio. Das vorhanden sein eines SkipLoading-Tags deaktiviert das Laden eines VSPackages. Wenn Sie das Tag löschen, wird das Laden des VSPackage erneut aktiviert.<br /><br /> Der Schalter verwendet keine Argumente. |
| `/RootSuffix` | Startet Visual Studio unter Verwendung eines alternativen Speicher Orts. Der folgende Befehl wird von der Verknüpfung ausgeführt, die vom Visual Studio SDK-Installer erstellt wurde:<br /><br /> `devenv /RootSuffix exp`<br /><br /> In diesem Fall `exp` identifiziert einen Speicherort mit einem bestimmten Suffix (z. b `10.0Exp` . anstelle von `10.0` ). Die experimentelle Instanz ermöglicht Ihnen, ein VSPackage getrennt von der Instanz von Visual Studio zu debuggen, die Sie zum Schreiben von Code verwenden.<br /><br /> Dieser Schalter kann jede beliebige Zeichenfolge verwenden, die einen Speicherort identifiziert, den Sie mit VSRegEx.exe erstellt haben. Weitere Informationen finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Öffnet Visual Studio im abgesicherten Modus und lädt nur die Standard-IDE und-Dienste. Der `/SafeMode` Schalter verhindert, dass alle VSPackages von Drittanbietern geladen werden, wenn Visual Studio gestartet wird, um eine stabile Ausführung sicherzustellen.<br /><br /> Der Schalter verwendet keine Argumente. |
| `/Setup` | Erzwingt, dass Visual Studio Ressourcen Metadaten zusammenführt, mit denen Menüs, Symbolleisten und Befehls Gruppen aus allen verfügbaren VSPackages beschrieben werden. Sie können diesen Befehl nur als Administrator ausführen. <br /><br /> Der Schalter verwendet keine Argumente. Der Befehl `devenv /Setup` wird in der Regel als letzter Schritt der Installation angegeben. Durch die Verwendung des `/Setup` Schalters wird die IDE nicht gestartet.|
| `/Splash` | Zeigt den Visual Studio-Begrüßungsbildschirm wie üblich an und zeigt dann ein Meldungs Feld an, bevor die Haupt-IDE angezeigt wird. Mit dem Meldungs Feld können Sie den Begrüßungsbildschirm anzeigen (z. b., um nach einem VSPackage-Produktsymbol zu suchen).<br /><br /> Der Schalter verwendet keine Argumente. |

## <a name="see-also"></a>Weitere Informationen

- [Befehls Zeilenschalter hinzufügen](../extensibility/adding-command-line-switches.md)
- [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)
