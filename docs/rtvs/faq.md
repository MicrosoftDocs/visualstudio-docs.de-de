---
title: Häufig gestellte Fragen zu R Tools für Visual Studio
description: Häufig gestellte Fragen zu R in Visual Studio
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c89f1d59405fb7475e827cac9624c6623d7041e
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189094"
---
# <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

## <a name="visual-studio-support"></a>Visual Studio-Unterstützung

**F. Funktioniert RTVS unter OS X oder Linux?**

A. RTVS baut zurzeit auf Visual Studio, einer reinen Windows-Implementierung, auf. Microsoft überprüft aktuell die Unterstützung für Visual Studio Code und Visual Studio für Mac. Weiter Informationen finden Sie unter [RTVS issue #1295 (RTVS-Problem Nr. 1295)](https://github.com/Microsoft/RTVS/issues/1295).

**F. Funktioniert RTVS mit Visual Studio Express-Editionen?**

A. Nein.

**F. Kann ich Visual Studio-Erweiterungen mit RTVS verwenden?**

A. Natürlich. Die folgenden Erweiterungen beispielsweise sind bei Benutzern sehr beliebt, die mit R arbeiten.

- [VsVim für Vim-Schlüsselbindungen](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Markdown-Editor mit Livevorschau](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Noch mehr Erweiterungen finden Sie im [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**F. Bedeutet die Tatsache, dass RTVS in Visual Studio integriert ist, dass R problemlos mit C#, C++ und anderen Microsoft-Sprachen eingesetzt werden kann?**

A. Nein. RTVS ist ein Tool für die Entwicklung von R-Code und verwendet die standardmäßigen nativen R-Interpreter. Zurzeit wird die Interoperabilität zwischen R und anderen Sprachen nicht unterstützt.

**F. Funktioniert RTVS mit einem nicht englischen Gebietsschema?**

A. Release 1.0 von RTVS ist nur auf Englisch verfügbar. Release 1.1 wird in die gleichen Sprachen lokalisiert wie Visual Studio selbst. Verwenden Sie in der Zwischenzeit das [Visual Studio 2015-Sprachpaket für Englisch](https://www.microsoft.com/download/details.aspx?id=48157), oder führen Sie in Visual Studio 2017 das Installationsprogramm aus und wählen auf der Registerkarte **Sprachpakete** Englisch aus.

![Internationale Einstellungen für Visual Studio 2017](media/FAQ-international-settings.png)

**F. Ich finde meine aktuellen Visual Studio-Einstellungen super, möchte aber auch die neuen Data Science-Einstellungen ausprobieren. Wie gehe ich vor?**

A. Speichern Sie Ihre aktuellen Visual Studio-Einstellungen mithilfe von **Extras** > **Einstellungen importieren/exportieren**, und wechseln Sie dann zu den Data Science-Einstellungen. Verwenden Sie erneut den Befehl **Einstellungen importieren/exportieren**, um die gespeicherten Einstellungen wiederherzustellen.

**F. Kann ich mein Visual Studio-Projekt auf einer Netzwerkfreigabe speichern?**

A. Nein, Visual Studio unterstützt nicht das Laden von Projekten aus einer Netzwerkfreigabe.

## <a name="r-interpretersintegration"></a>R-Interpreter/-Integration

**F. Mit welchen R-Interpretern arbeitet RTVS?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client und Microsoft Machine Learning Server](/machine-learning-server/)

**F. Wo kann ich diese Interpreter herunterladen?**

A. Informationen hierzu finden Sie unter [Installation](installing-r-tools-for-visual-studio.md).

**F: Was ist Microsoft R Server?**

A. R Server ist der ehemalige Name von [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**F. Funktioniert RTVS mit 32-Bit-Editionen von R?**

A. Nein. RTVS unterstützt nur 64-Bit-Editionen von R, die auf 64-Bit-Editionen von Windows ausgeführt werden.

**F. Funktioniert RTVS mit meinem System für die Quellcodeverwaltung?**

A. Ja, Sie können jedes Quellcodeverwaltungssystem verwenden, das in Visual Studio integriert ist.

**F. Wie lauten die empfohlenen *GITIGNORE*-Einstellungen für ein RTVS-Projekt?**

A. GitHub verwaltet ein Repository mit empfohlenen *GITIGNORE*-Dateien. Dieses finden Sie hier: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore).

## <a name="remote-services"></a>Remotedienste

Q. **Was sind Remotedienste in Visual Studio?**

A. Mit den R-Remotediensten für Visual Studio können Sie Windows- oder Linux-Computer einrichten und dann über RTVS eine Verbindung zu ihnen herstellen. Siehe [Einrichten von Remotearbeitsbereichen](setting-up-remote-r-workspaces.md).

Q. **Kann RTVS eine Verbindung mit Microsoft Machine Learning Server herstellen?**

A. Nein, da es sich bei ML Server um eine andere Technologie handelt, die einen anderen Mechanismus als den für RTVS erforderlichen bereitstellt.

Q. **Kann RTVS eine Verbindung zu einer VM herstellen, die mithilfe des Images einer Data Science-VM in Azure erstellt wurde?**

A. Ja, das Image [DataScience-VM – Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) ist in Remote R Services für Visual Studio vorinstalliert.

**F: Kann RTVS eine Verbindung zu einem Remotecomputer herstellen, auf dem R installiert ist?**

Um R-Code auf einem Remotecomputer auszuführen, müssen Dienste auf Anforderungen lauschen und dabei Code empfangen und Ergebnisse an den Clientcomputer zurücksenden. Dafür sind die R-Remotedienste für Visual Studio verantwortlich. Siehe [Einrichten von Remotearbeitsbereichen](setting-up-remote-r-workspaces.md).

Q. **Was ist eine Remotesitzung?**

A. Informationen dazu finden Sie im Artikel [Execute on remote server (Ausführen auf einem Remoteserver)](/machine-learning-server/r/how-to-execute-code-remotely) in der Machine Learning Server-Dokumentation.

## <a name="rtvs-development-and-features"></a>RTVS-Entwicklung und -Funktionen

**F. Ich vermisse ein bestimmtes Feature, das in RStudio vorhanden ist!**

A. RStudio ist eine fantastische, ausgereifte IDE für R, die bereits seit vielen Jahren weiterentwickelt wird. Wir versuchen, alle wichtigen Funktionen, die Sie für eine erfolgreiche Entwicklung benötigen, in RTVS bereitzustellen. Helfen Sie bei der Priorisierung zukünftiger Aufgaben, indem Sie Probleme auf [GitHub](https://github.com/Microsoft/RTVS/issues/) einreichen.

**F. Kann ich zu RTVS beitragen?**

A. Auf jeden Fall. Der Quellcode befindet sich auf [GitHub](https://github.com/microsoft/RTVS). Unter „Issues“ können Sie Bugs melden und bereits vorhandene Dateien kommentieren.

Wir freuen uns auch, wenn Sie zur Dokumentation beitragen&mdash;wählen Sie einfach den Befehl **Edit** (Bearbeiten) rechts oben auf jeder Seite in GitHub. Kommentare zu den Dokumenten sind ebenfalls gern gesehen – diese können Sie unten auf jeder Seite einfügen.
