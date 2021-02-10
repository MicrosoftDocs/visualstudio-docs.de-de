---
title: Entfernen von Visual Studio
titleSuffix: ''
description: Erfahren Sie Schritt für Schritt, wie Sie Visual Studio vollständig von Ihrem Computer entfernen können.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 751f87075d4e9dcbb7daa94f39a2f38c5083fb3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878447"
---
# <a name="remove-visual-studio"></a>Entfernen von Visual Studio

Wenn ein schwerwiegender Fehler auftritt und Sie Visual Studio nicht reparieren können oder deinstallieren müssen, können Sie mit dem Tool `InstallCleanup.exe` Installationsdateien und Produktinformationen für alle installierten Instanzen von Visual Studio 2017 oder Visual Studio 2019 entfernen.

> [!WARNING]
> Verwenden Sie das Tool „InstallCleanup“ **nur als letzten Ausweg**, wenn die Reparatur oder Deinstallation fehlschlägt. Dieses Tool deinstalliert möglicherweise Features aus anderen Visual Studio-Installationen oder anderen Produkten, die dann möglicherweise ebenfalls repariert oder neu installiert werden müssen.

## <a name="run-installcleanupexe"></a>InstallCleanup.exe ausführen

Sie können einen der folgenden Befehlszeilenschalter mit dem Tool `InstallCleanup.exe` verwenden:

| Schalter | Verhalten |
| ------ | -------- |
| `-i`   | Dieser Schalter ist der Standardwert, wenn kein anderer Schalter übergeben wird. Es werden nur das Hauptinstallationsverzeichnis und die Produktinformationen entfernt. Verwenden Sie diesen Schalter, wenn Sie beabsichtigen, dieselbe Version von Visual Studio neu zu installieren, nachdem Sie das Tool `InstallCleanup.exe` ausgeführt haben. |
| `-f`   | Mit diesem Schalter werden das Hauptinstallationsverzeichnis, die Produktinformationen und fast alle Funktionen entfernt, die außerhalb des Installationsverzeichnisses installiert wurden und auch für andere Visual Studio-Installationen oder Produkte freigegeben werden können. Verwenden Sie diesen Schalter, wenn Sie beabsichtigen, Visual Studio zu entfernen, ohne es später neu zu installieren. |

So wird das Tool `InstallCleanup.exe` ausgeführt

1. Schließen Sie den Visual Studio-Installer.
1. Öffnen Sie eine Eingabeaufforderung als Administrator. Wenn Sie eine Eingabeaufforderung als Administrator öffnen möchten, führen Sie diese Schritte aus:
   * Geben Sie **cmd** in das Suchfeld ein.
   * Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und wählen Sie dann **Als Administrator ausführen**.
1. Geben Sie den vollständigen Pfad des Tools `InstallCleanup.exe` ein und fügen Sie den gewünschten Befehlszeilenschalter hinzu. Der Pfad des Tools lautet standardmäßig wie folgt: Die doppelten Anführungszeichen schließen einen Befehl mit Leerzeichen ein:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Wenn Sie `InstallCleanup.exe` unter dem Verzeichnis von Visual Studio-Installer, das sich immer unter `%ProgramFiles(x86)%\Microsoft Visual Studio` befindet, nicht finden können, gehen Sie wie folgt vor. Folgen Sie den Anweisungen zum [Installieren von Visual Studio](install-visual-studio.md). Wenn der Workloadauswahlbildschirm angezeigt wird, schließen Sie das Fenster und folgen Sie wieder den Schritten auf dieser Seite.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Ändern von Visual Studio](modify-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
