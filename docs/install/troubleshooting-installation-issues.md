---
title: Behandlung von Installationsproblemen oder Problemen beim Upgrade
description: Manchmal kann etwas schiefgehen. Wenn die Installation oder das Upgrade von Visual Studio fehlschlägt, kann diese Seite Ihnen helfen.
ms.date: 06/24/2020
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 54bd53f5c63a2f126f4aeae264c4dff745633cf6
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668312"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Problembehandlung bei der Visual Studio-Installation und bei Upgradefehlern

> [!IMPORTANT]
> Treten bei der Installation Probleme auf? Da können wir Ihnen helfen. Wir bieten eine [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous)-Supportoption für die Installation (nur in englischer Sprache).

Dieser Leitfaden zur Problembehandlung enthält Schritt-für-Schritt-Anleitungen, mit denen sich die meisten Installationsprobleme beheben lassen sollten.

## <a name="online-installations"></a>Onlineinstallationen

Dies folgenden Schritte sind für eine typische Onlineinstallation optimiert. Informationen zum Beheben von Problemen bei Offlineinstallationen finden Sie unter [Problembehandlung bei einer Offlineinstallation](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Schritt 1: Prüfen, ob das Problem bekannt ist

::: moniker range="vs-2017"

Es gibt einige bekannte Probleme mit dem Visual Studio-Installer, an deren Behebung Microsoft arbeitet. Überprüfen Sie in den [Anmerkungen zu dieser Version den Abschnitt „Bekannte Probleme“](/visualstudio/releasenotes/vs2017-relnotes#-known-issues), um zu prüfen, ob es eine Lösung für Ihr Problem gibt.

::: moniker-end

::: moniker range="vs-2019"

Es gibt einige bekannte Probleme mit dem Visual Studio-Installer, an deren Behebung Microsoft arbeitet. Überprüfen Sie in den [Anmerkungen zu dieser Version den Abschnitt „Bekannte Probleme“](/visualstudio/releases/2019/release-notes#-known-issues), um zu prüfen, ob es eine Lösung für Ihr Problem gibt.

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Schritt 2: Reparieren von Visual Studio

Mit der Reparatur werden viele gängige Updateprobleme behoben. Weitere Informationen dazu, wann und wie Sie die Reparaturfunktion in Visual Studio verwenden, finden Sie unter [Reparieren von Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Schritt 3: Nachfragen in der Entwicklercommunity

Suchen Sie in der [Visual Studio-Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) nach der Fehlermeldung. Andere Mitglieder der Community haben ggf. eine Lösung für Ihr Problem dokumentiert.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Schritt 4: Löschen des Visual Studio-Installer-Verzeichnisses zum Beheben von Problemen mit Upgrades

Der Visual Studio-Installer-Bootstrapper ist eine kleine schlanke ausführbare Datei, mit der der Rest des Visual Studio-Installers installiert wird. Das Löschen von Visual Studio-Installer-Dateien und anschließende erneute Ausführen des Bootstrappers hilft ggf. bei der Behebung einiger Updatefehler.

> [!NOTE]
> Mithilfe der folgenden Aktionen werden die Visual Studio-Installer-Dateien neu installiert und die Installationsmetadaten zurückgesetzt.

::: moniker range="vs-2017"

1. Schließen Sie den Visual Studio-Installer.
2. Löschen Sie das Visual Studio-Installer-Verzeichnis. Das Verzeichnis ist in der Regel `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Führen Sie den Visual Studio-Installer-Bootstrapper aus. Den Bootstrapper finden Sie ggf. in Ihrem Ordner „Downloads“ mit einem Dateiname mit dem Muster `vs_[Visual Studio edition]__*.exe`. Wenn Sie die Anwendung nicht finden, können Sie den Bootstrapper herunterladen, indem Sie die [Visual Studio-Seite „Downloads“](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aufrufen und dann für Ihre Edition von Visual Studio auf **Herunterladen** klicken. Führen Sie anschließend diese ausführbare Datei aus, um die Metadaten für Ihre Installation zurückzusetzen.
4. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren. Wenn beim Installer weiterhin ein Fehler auftritt, fahren Sie mit dem nächsten Schritt fort.

::: moniker-end

::: moniker range="vs-2019"

1. Schließen Sie den Visual Studio-Installer.
2. Löschen Sie das Visual Studio-Installer-Verzeichnis. Das Verzeichnis ist in der Regel `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Führen Sie den Visual Studio-Installer-Bootstrapper aus. Den Bootstrapper finden Sie ggf. in Ihrem Ordner „Downloads“ mit einem Dateiname mit dem Muster `vs_[Visual Studio edition]__*.exe`. Wenn Sie die Anwendung nicht finden, können Sie den Bootstrapper herunterladen, indem Sie die [Visual Studio-Seite „Downloads“](https://visualstudio.microsoft.com/downloads) aufrufen und dann für Ihre Edition von Visual Studio auf **Herunterladen** klicken. Führen Sie anschließend diese ausführbare Datei aus, um die Metadaten für Ihre Installation zurückzusetzen.
4. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren. Wenn beim Installer weiterhin ein Fehler auftritt, fahren Sie mit dem nächsten Schritt fort.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Schritt 5: Melden eines Problems

In einigen Situationen, z. B. bei beschädigten Dateien, müssen die Probleme ggf. fallweise untersucht werden. Bitte gehen Sie wie folgt vor, damit wir Sie besser unterstützen können:

::: moniker range="vs-2017"

1. Sammeln Sie Ihre Setupprotokolle. Nähere Informationen finden Sie unter [Abrufen der Visual Studio-Installationsprotokolle](#installation-logs).
2. Öffnen Sie den Visual Studio-Installer, und klicken Sie dann auf **Problem melden**, um das Visual Studio-Feedbacktool zu öffnen.
![Sie können zur Schaltfläche „Feedback geben“ navigieren, um das Feedbacktool zu öffnen](media/report-a-problem.png)
3. Versehen Sie Ihren Problembericht mit einem Titel, und geben Sie relevante Details an. Klicken Sie auf **Weiter**, um zum Abschnitt **Anlagen** zu wechseln. Fügen Sie die generierte Protokolldatei an (in der Regel befindet sich die Datei unter `%TEMP%\vslogs.zip`).
4. Klicken Sie auf **Weiter**, um Ihren Problembericht zu überprüfen, und dann auf **Senden**.

::: moniker-end

::: moniker range="vs-2019"

1. Sammeln Sie Ihre Setupprotokolle. Nähere Informationen finden Sie unter [Abrufen der Visual Studio-Installationsprotokolle](#installation-logs).
2. Öffnen Sie den Visual Studio-Installer, und klicken Sie dann auf **Problem melden**, um das Visual Studio-Feedbacktool zu öffnen.
![Sie können zur Schaltfläche „Feedback geben“ navigieren, um das Feedbacktool zu öffnen](media/vs-2019/vs-installer-report-problem.png)
3. Versehen Sie Ihren Problembericht mit einem Titel, und geben Sie relevante Details an. Klicken Sie auf **Weiter**, um zum Abschnitt **Anlagen** zu wechseln. Fügen Sie die generierte Protokolldatei an (in der Regel befindet sich die Datei unter `%TEMP%\vslogs.zip`).
4. Klicken Sie auf **Weiter**, um Ihren Problembericht zu überprüfen, und dann auf **Senden**.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Schritt 6: Ausführen von „InstallCleanup.exe“ zum Entfernen der Installationsdateien

Als letzten Ausweg können Sie [Visual Studio entfernen](remove-visual-studio.md), um alle Installationsdateien und Produktinformationen zu entfernen.

1. Folgen Sie den Anweisungen unter [Entfernen von Visual Studio](remove-visual-studio.md).
2. Führen Sie den in [Schritt 4: Löschen des Visual Studio-Installer-Verzeichnisses zum Beheben von Problemen mit Upgrades](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems) beschriebenen Bootstrapper erneut aus.
3. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren.

### <a name="step-7---contact-us-optional"></a>Schritt 7: Kontaktieren Sie Microsoft (optional)

Wenn Ihnen keiner der vorherigen Schritte zu einer erfolgreichen Installation oder einem erfolgreichen Upgrade von Visual Studio verholfen hat, setzen Sie sich über unsere [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous)-Supportoption (nur englischsprachig) mit uns in Verbindung, um weitere Hilfe zu erhalten.

## <a name="offline-installations"></a>Offlineinstallationen

Es folgt eine Tabelle mit bekannten Problemen und einigen Problemumgehungen, die Sie bei der [Offlineinstallation](create-an-offline-installation-of-visual-studio.md) und der anschließenden Installation über eine lokale Umgebung unterstützen können.

| Problem       | Element                   | Lösung |
| ----------- | ---------------------- | -------- |
| Benutzer haben keinen Zugriff auf Dateien. | Berechtigungen (ACLs) | Stellen Sie sicher, dass Sie die Berechtigungen (ACLs) so anpassen, dass anderen Benutzern Lesezugriff erteilt wird, *bevor* Sie die Offlineinstallation freigeben. |
| Neue Arbeitslasten, Komponenten oder Sprachen werden nicht installiert.  | `--layout`  | Stellen Sie sicher, dass Sie über Internetzugriff verfügen, wenn Sie eine Installation aus einem partiellen Layout heraus ausführen und Arbeitsauslastungen, Komponenten oder Sprachen auswählen, die nicht zuvor in diesem partiellen Layout heruntergeladen wurden. |

Weitere Informationen zur Problembehandlung bei einer [Netzwerkinstallation](create-a-network-installation-of-visual-studio.md) finden Sie unter [Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Installationsprotokolle

Setupprotokolle sind zum Beheben der meisten Installationsprobleme nicht erforderlich. Wenn Sie ein Problem mit [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio.md) im Visual Studio-Installer melden, werden diese Protokolle automatisch in Ihren Bericht einbezogen.

Wenn Sie sich an den Microsoft-Support wenden, müssen Sie möglicherweise diese Setupprotokolle mit dem [Protokollerfassungstool für Microsoft Visual Studio und .NET Framework](https://www.microsoft.com/download/details.aspx?id=12493) bereitstellen. Das Protokollerfassungstool erfasst Setupprotokolle aller von Visual Studio installierten Komponenten einschließlich .NET Framework, Windows SDK und SQL Server. Es erfasst auch Computerinformationen, einen Windows Installer-Bestand und Windows-Ereignisprotokollinformationen für Visual Studio-Installer, Windows Installer und Systemwiederherstellung.

So erfassen Sie die Protokolle:

1. [Laden Sie das Tool herunter](https://www.microsoft.com/download/details.aspx?id=12493).
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Führen Sie `Collect.exe` aus dem Verzeichnis aus, in dem Sie das Tool gespeichert haben.
4. Suchen Sie die sich daraus ergebende `vslogs.zip`-Datei in Ihrem `%TEMP%`-Verzeichnis, z.B. `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Das Tool muss unter dem gleichen Benutzerkonto ausgeführt werden, unter dem die fehlgeschlagene Installation ausgeführt wurde. Wenn Sie das Tool in einem anderen Benutzerkonto ausführen, legen Sie die Option `–user:<name>` fest, um das Benutzerkonto anzugeben, unter dem die fehlgeschlagene Installation ausgeführt wurde. Führen Sie `Collect.exe -?` in einer Eingabeaufforderung als Administrator für zusätzliche Optionen und Nutzungsinformationen aus.

## <a name="live-help"></a>Livehilfe

Wenn die in diesem Leitfaden zur Problembehandlung aufgeführten Lösungen Ihnen nicht zu einer erfolgreichen Installation oder einem erfolgreichen Upgrade von Visual Studio verholfen haben, verwenden Sie unsere [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous)-Supportoption (nur englischsprachig), um weitere Hilfe zu erhalten.

## <a name="see-also"></a>Siehe auch

* [Reparieren von Visual Studio](repair-visual-studio.md)
* [Entfernen von Visual Studio](remove-visual-studio.md)
* [Installieren und Verwenden von Visual Studio und Azure-Diensten hinter einer Firewall oder einem Proxyserver](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
