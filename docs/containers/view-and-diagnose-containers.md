---
title: Anzeigen und Diagnostizieren von Docker-Containern und Images
description: In diesem Artikel wird beschrieben, wie Sie Ihre Fähigkeiten zum Debuggen und Diagnostizieren Ihrer containerbasierten Apps in Visual Studio mithilfe eines Toolfensters verbessern, um zu erfahren, was innerhalb der Container geschieht, die Ihre App hosten.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: fd876e86cefcd0ce50aab02de8e7f4cf37d3ab51
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729222"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Anzeigen und Diagnostizieren von Containern und Images in Visual Studio

Mithilfe des Fensters **Container** können Sie anzeigen, was in den Containern passiert, die Ihre App hosten. Wenn Sie gewohnt sind, die Eingabeaufforderung zum Ausführen von Docker-Befehlen zu verwenden, um die Vorgänge in Ihren Containern anzuzeigen und zu diagnostizieren, wird sich dieses Fenster als praktischere Möglichkeit zum Überwachen Ihrer Container erweisen, ohne dass Sie die Visual Studio-IDE verlassen müssen.

## <a name="prerequisites"></a>Voraussetzungen

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019, Version 16.4, Vorschauversion 2](https://visualstudio.microsoft.com/downloads) oder höher. Wenn Sie eine frühere Version von Visual Studio 2019 verwenden, installieren Sie die Fenstererweiterung [Container](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Anzeigen von Informationen zu den Containern

Das Fenster **Container** wird automatisch geöffnet, wenn Sie ein .NET-Containerprojekt starten. Drücken Sie **STRG**+**Q**, um das Visual Studio-Suchfeld zu aktivieren, geben Sie `Containers` ein, und wählen Sie das erste Element aus, um Ihre Container jederzeit in Visual Studio anzuzeigen. Sie können das **Containerfenster** auch über das Hauptmenü öffnen. Verwenden Sie den Menüpfad **Ansicht** > **Weitere Fenster** > **Container**.  

![Screenshot des Fensters „Container“ in Visual Studio mit einem ausgewählten Container im linken Bereich und der ausgewählten Registerkarte „Umgebung“ im rechten Bereich.](media/view-and-diagnose-containers/container-window.png)

Auf der linken Seite wird die Liste der Container auf Ihrem lokalen Computer angezeigt. Die Container, die Ihrer Projektmappe zugeordnet sind, werden unter **Lösungscontainer** angezeigt. Auf der rechten Seite wird ein Bereich mit den Registerkarten **Umgebung**, **Ports**, **Protokolle** und **Dateien** angezeigt.

> [!TIP]
> Sie können mühelos anpassen, wo das Toolfenster **Container** in Visual Studio andocken soll. Informationen dazu finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Das Fenster **Container** ist standardmäßig an das **Überwachungsfenster** angedockt, wenn der Debugger ausgeführt wird.

## <a name="view-environment-variables"></a>Anzeigen von Umgebungsvariablen

Auf der Registerkarte **Umgebung** werden die Umgebungsvariablen im Container angezeigt. Sie können diese Variablen auf vielerlei Weisen für den Container Ihrer App festlegen, z. B. in der Dockerfile, in einer ENV-Datei oder mithilfe der Option „-e“, wenn Sie einen Container mithilfe eines Docker-Befehls starten.

![Screenshot des Fensters „Container“ in Visual Studio, in dem die Umgebungsvariablen für den Container „WebApplication11“ angezeigt werden.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Änderungen an den Umgebungsvariablen werden nicht in Echtzeit wiedergegeben. Außerdem handelt es sich bei den Umgebungsvariablen auf dieser Registerkarte um Systemumgebungsvariablen im Container, die nicht den lokalen Benutzerumgebungsvariablen der App entsprechen.

## <a name="view-port-mappings"></a>Anzeigen von Portzuordnungen

Auf der Registerkarte **Ports** können Sie die Portzuordnungen überprüfen, die für Ihren Container konfiguriert sind.

![Screenshot: Registerkarte „Ports“ im Containerfenster](media/view-and-diagnose-containers/containers-ports.png)

Bekannte Ports sind verknüpft. Wenn also Inhalt für einen Port verfügbar ist, können Sie auf den Link klicken, um den Browser zu öffnen.

## <a name="view-logs"></a>Protokoll anzeigen...

Auf der Registerkarte **Protokolle** werden die Ergebnisse des `docker logs`-Befehls angezeigt. Auf der Registerkarte werden standardmäßig die Datenströme „stdout“ und „stderr“ für einen Container angezeigt, aber Sie können die Ausgabe konfigurieren. Weitere Informationen finden Sie unter [Docker-Protokollierung](https://docs.docker.com/config/containers/logging/).  Auf der Registerkarte **Protokolle** werden die Protokolle standardmäßig in Echtzeit angezeigt. Sie können dies jedoch deaktivieren, indem Sie auf der Registerkarte auf **Stoppen** klicken.

![Screenshot: Registerkarte „Protokolle“ im Containerfenster](media/view-and-diagnose-containers/containers-logs.png)

Klicken Sie auf der Registerkarte **Protokolle** auf **Löschen**, um die Protokolle zu löschen.  Klicken Sie auf **Aktualisieren**, um alle Protokolle abzurufen.

> [!NOTE]
> Bei Ausführung mit Windows-Containern ohne Debuggen leitet Visual Studio stdout und stderr automatisch zum Fenster **Ausgabe** um. Daher zeigen Windows-Container, die in Visual Studio mit **STRG**+**F5** gestartet werden, auf dieser Registerkarte keine Protokolle an. Verwenden Sie stattdessen das Fenster **Ausgabe**.

## <a name="view-the-filesystem"></a>Anzeigen des Dateisystems

Auf der Registerkarte **Dateien** können Sie das Dateisystem des Containers sowie den App-Ordner anzeigen, der Ihr Projekt enthält.

![Screenshot: Registerkarte „Dateien“ im Containerfenster](media/view-and-diagnose-containers/container-filesystem.png)

Navigieren Sie zur Datei, und doppelklicken Sie auf diese, oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Öffnen** aus, um Dateien in Visual Studio zu öffnen. Visual Studio öffnet Dateien im schreibgeschützten Modus.

![Screenshot: Anzeige der geöffneten Datei in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Auf der Registerkarte **Dateien** können Sie Anwendungsprotokolle wie IIS-Protokolle, Konfigurationsdateien und andere Inhaltsdateien im Dateisystem Ihres Containers anzeigen.

## <a name="start-stop-and-remove-containers"></a>Starten, Stoppen und Entfernen von Containern

Im Fenster **Container** werden standardmäßig alle Container auf dem Computer angezeigt, die von Docker verwaltet werden. Sie können die Symbolleistenschaltflächen zum Starten, Stoppen und Entfernen (Löschen) eines Containers verwenden, den Sie nicht mehr benötigen.  Diese Liste wird dynamisch aktualisiert, wenn Container erstellt oder entfernt werden.

## <a name="open-a-terminal-window-in-a-running-container"></a>Öffnen eines Terminal Fensters in einem ausgeführten Container

Sie können ein Terminalfenster (Eingabeaufforderung oder interaktive Shell) im Container öffnen, indem Sie im Fenster **Container** auf die Schaltfläche **Terminalfenster öffnen** klicken.

![Screenshot von „Terminalfenster öffnen“ im Fenster „Container“](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Für Windows-Container wird die Windows-Befehlseingabeaufforderung geöffnet. Für Linux-Container wird mithilfe der bash-Shell ein Fenster geöffnet.

![Screenshot des bash-Fensters](media/view-and-diagnose-containers/container-bash-window.png)

Normalerweise wird das Terminalfenster außerhalb von Visual Studio als separates Fenster geöffnet. Wenn Sie eine Befehlszeilenumgebung als andockbares Toolfenster in die Visual Studio IDE integrieren möchten, können Sie [Whack Whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal) installieren.

## <a name="attach-the-debugger-to-a-process"></a>Anhängen des Debuggers an einen Prozess

Sie können den Debugger an einen Prozess anhängen, der im Container ausgeführt wird, indem Sie im Fenster „Container“ auf der Symbolleiste auf die Schaltfläche **An Prozess anhängen** klicken. Wenn Sie auf diese Schaltfläche klicken, wird das Dialogfeld **An Prozess anhängen** angezeigt, das die verfügbaren Prozesse anzeigt, die im Container ausgeführt werden.  

![Screenshot des Dialogfelds „An Prozess anhängen“](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Im Container ist das Anhängen an verwaltete Prozesse möglich. Um nach einem Prozess in einem anderen Container zu suchen, klicken Sie auf die Schaltfläche **Suchen**, und wählen Sie im Dialogfeld **Docker-Container auswählen** einen anderen Container aus.

## <a name="viewing-images"></a>Anzeigen von Images

Sie können Images auch auf dem lokalen Computer anzeigen, und zwar im Fenster **Container** auf der Registerkarte **Images**. Images, die aus externen Repositorys abgerufen werden, werden in einer Strukturansicht zusammengefasst. Wählen Sie ein Image aus, um dessen Details zu überprüfen.

Um ein Image zu entfernen, klicken Sie in der Strukturansicht mit der rechten Maustaste auf das Image und wählen **Entfernen** aus. Oder wählen Sie das Image aus, und klicken Sie auf der Symbolleiste auf die Schaltfläche **Entfernen**.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die Containertools in Visual Studio in der [Übersicht über Containertools](overview.md).

## <a name="see-also"></a>Siehe auch

[Containerentwicklung in Visual Studio](./index.yml)

[Marketplace für Visual Studio-Erweiterungen](https://marketplace.visualstudio.com/)