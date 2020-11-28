---
title: Ändern der Benutzeroberfläche beim Start
description: Erfahren Sie, wie Sie Ihren Startvorgang anpassen, sodass Visual Studio mit den Tools geöffnet wird, die für Sie am nützlichsten sind.
ms.custom: SEO-VS-2020
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3928ab1cad67cac26865229cbe6d317083a0a4f1
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598106"
---
# <a name="customize-startup"></a>Anpassen des Programmstarts

Sie können die Benutzeroberfläche beim Start von Visual Studio auf verschiedene Weisen anpassen. So können Sie beispielsweise festlegen, dass die zuletzt geöffnete Projektmappe oder eine leere Entwicklungsumgebung geöffnet wird.

::: moniker range="vs-2017"

Sie können eine benutzerdefinierte Startseite anzeigen. Dies ist eine Windows Presentation Foundation (WPF)-XAML-Seite, die in einem Toolfenster ausgeführt wird und Visual Studio-interne Befehle ausführen kann.

::: moniker-end

## <a name="to-change-the-startup-item"></a>So ändern Sie das Startelement

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

2. Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.

::: moniker range="vs-2017"

3. Wählen Sie in der Liste **Beim Starten** das Element aus, das nach dem Start von Visual Studio angezeigt werden soll.

::: moniker-end

::: moniker range=">=vs-2019"

3. Wählen Sie aus der Liste **On startup, open** (Beim Start öffnen) aus, was beim Starten von Visual Studio angezeigt werden soll. Sie können zwischen **Startfenster** (über das Sie ein neues oder vorhandenes Projekt öffnen können), **Letzte Projektmappe** und **Leere Umgebung** auswählen.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>So zeigen Sie eine benutzerdefinierte Startseite an

Sie können [eine eigene benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md) mit dem Visual Studio SDK erstellen oder eine Startseite verwenden, die bereits von einem anderen Benutzer erstellt wurde. Sie finden benutzerdefinierte Startseiten z.B. in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Öffnen Sie zum Installieren einer benutzerdefinierten Startseite eine *VSIX-Datei*, oder kopieren Sie die Startseitendateien, und fügen Sie sie auf dem Computer in den Ordner *%USERPROFILE%\Dokumente\Visual Studio 2017\StartPages* ein.

### <a name="to-select-which-custom-start-page-to-display"></a>So wählen Sie aus, welche benutzerdefinierte Startseite angezeigt werden soll

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

1. Erweitern Sie **Umgebung**, und wählen Sie dann **Start** aus.

1. Wählen Sie in der Liste **Startseite anpassen** die gewünschte Seite aus.

> [!TIP]
> Wenn ein Fehler in einer benutzerdefinierten Startseite einen Absturz von Visual Studio verursacht, können Sie Visual Studio im abgesicherten Modus öffnen und dann festlegen, dass die Standardstartseite verwendet wird. Weitere Informationen finden Sie unter [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Weitere Informationen

- [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
