---
title: Allgemein, Umgebung, Dialogfeld "Optionen"
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfd1b876e58c05c668fd74087d5131bb1e9fcd40
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189783"
---
# <a name="options-dialog-box-environment--general"></a>Dialogfeld „Optionen“: Umgebung \> Allgemein

Verwenden Sie diese Seite, um Farbschemas, Statusleisteneinstellungen, Dateierweiterungszuordnungen sowie weitere Optionen für die integrierte Entwicklungsumgebung (IDE) zu ändern. Sie können das Dialogfeld **Optionen** öffnen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Allgemein** auswählen.

## <a name="visual-experience"></a>Visuelle Darstellung

**Farbdesign**

Wählen Sie **Blau**, **Hell**, **Dunkel** oder **Blau (zusätzlicher Kontrast)** als Farbdesign für die IDE aus.

Sie können auch weitere vordefinierte Farbdesigns installieren und benutzerdefinierte Designs erstellen. Dazu müssen Sie den **Visual Studio Color Theme Editor** aus dem [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) herunterladen und installieren. Nachdem Sie dieses Tool installiert haben, werden zusätzliche Farbdesigns im **Farbdesignlistenfeld** angezeigt.

**Traditionellen Menüleistenstil mit großen Anfangsbuchstaben verwenden**

Menüs verwenden diesen Stil mit großen Anfangsbuchstaben standardmäßig. Deaktivieren Sie diese Option, wenn Sie stattdessen den Stil „Alles Großbuchstaben“ verwenden möchten.

::: moniker range=">=vs-2019"

**Rendering für Bildschirme mit anderen Pixeldichten optimieren (Neustart erforderlich)**

Diese Option aktiviert oder deaktiviert den DPI-Grad (Dots Per Inch) pro Monitor (oder *PMA* (Per-Monitor Aware)). Wenn PMA aktiviert ist, wird die Visual Studio-Benutzeroberfläche in jedem Skalierungsfaktor der Monitoranzeige und jeder DPI-Konfiguration als hochauflösend angezeigt, auch wenn mehrere Monitore verwendet werden. Wenn Sie PMA aktivieren möchten, benötigen Sie das Windows-Update vom 10. April 2018 oder höhere Updates und mindestens .NET Framework 4.8. (Diese Option wird ausgeblendet, wenn diese beiden Voraussetzungen nicht erfüllt sind.)

> [!TIP]
> - Windows 10 verfügt über die Einstellung **Windows kann versuchen, Apps mit unscharfer Darstellung zu korrigieren**. Wenn Sie diese Windows-Einstellung auf **Ein** stellen, ist die Wirkung vernachlässigbar, wenn Sie die Option **Rendering für Bildschirme mit anderen Pixeldichten optimieren** aktiviert haben.
> - Windows 10 bietet außerdem eine **Problembehandlung bei der Programmkompatibilität**. Es ist nicht ratsam, die Darstellung von Visual Studio mit dieser Problembehandlung zu korrigieren.

::: moniker-end

**Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen**

Gibt an, ob Visual Studio die Anpassung der visuellen Darstellung automatisch festlegt oder Sie die Anpassung explizit festlegen. Mit dieser Anpassung können Sie die Darstellung von Farben von Farbverläufen in gleichmäßige Farben ändern oder die Verwendung von Animationen in Menüs oder Popupfenstern einschränken.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 verfügt über die Einstellung **Windows kann versuchen, Apps mit unscharfer Darstellung zu korrigieren**. Es ist empfehlenswert, diese Einstellung auf **Ein** einzustellen, wenn Visual Studio auf dem Monitor unscharf angezeigt wird. Erwägen Sie ein Upgrade auf [Visual Studio-2019](https://visualstudio.microsoft.com/downloads), das über eine erheblich verbesserte Anzeigeschärfe verfügt, da es sich um eine PMA-Anwendung (mit monitorspezifischen DPI-Werten kompatibel) handelt.

::: moniker-end

**Umfassende visuelle Clientdarstellung aktivieren**

Aktiviert die vollständige visuelle Darstellung von Visual Studio, u. a. mit Farbverläufen und Animationen. Deaktiviert diese Option bei Verwendung von Remotedesktopverbindungen oder älteren Grafikkarten, da diese Funktionen in solchen Fällen zu einer schlechteren Leistung führen können. Diese Option ist nur verfügbar, wenn Sie die Option **Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen** deaktivieren.

**Hardwaregrafikbeschleunigung verwenden, falls verfügbar**

Verwendet Hardwaregrafikbeschleunigung, sofern verfügbar, anstelle von Softwarebeschleunigung.

## <a name="other"></a>Andere

**Anzuzeigende Elemente im Windows-Menü**

Passt die Anzahl der Fenster an, die in der Fensterliste des Menüs **Fenster** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Der Standardwert ist 10.

**In den Listen der zuletzt verwendeten Elemente angezeigte Elemente**

Passt die Anzahl der zuletzt geöffneten Projekte und Dateien an, die im Menü **Datei** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Der Standardwert ist 10. Dies ist eine einfache Möglichkeit, zuletzt verwendete Projekte und Dateien abzurufen.

**Statusleiste anzeigen**

Zeigt die Statusleiste an. Die Statusleiste befindet sich am unteren Rand des IDE-Fensters und zeigt Informationen über den Fortschritt derzeit ausgeführter Vorgänge an.

**Schaltfläche „Schließen“ gilt nur für aktives Toolfenster**

Gibt an, dass beim Klicken auf die Schaltfläche **Schließen** nur das Toolfenster geschlossen wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz. Diese Option ist standardmäßig ausgewählt.

**Schaltfläche „Automatisch ausblenden“ gilt nur für aktives Toolfenster**

Gibt an, dass beim Klicken auf die Schaltfläche **Automatisch ausblenden** nur das Toolfenster automatisch ausgeblendet wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz. Diese Option ist standardmäßig nicht ausgewählt.

## <a name="see-also"></a>Weitere Informationen

- [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)
