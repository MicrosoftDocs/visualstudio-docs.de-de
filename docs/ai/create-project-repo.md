---
title: Klonen eines Repositorys
description: Hier erfahren Sie, wie Sie mit Visual Studio Tools für KI ein Repository mit Python-Code klonen und ein Projekt daraus erstellen.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 58e6bdae7ef85545d0790782f5ad825b8f27659c
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099244"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonen eines Repositorys in Python-Code in Visual Studio

Sobald Sie [die Visual Studio-Tools für KI installiert haben](installation.md), können Sie ganz leicht ein Repository mit Python-Code klonen und daraus ein Projekt erstellen.

1. Um die Verbindung mit GitHub-Repositorys herzustellen, führen Sie den Visual Studio-Installer aus. Klicken Sie auf **Ändern** , und wählen Sie dann die Registerkarte **Einzelne Komponenten** aus. Scrollen Sie runter zum Bereich **Codetools** , klicken Sie auf **GitHub-Erweiterung für Visual Studio** und dann auf **Ändern** .

    ![Auswählen der GitHub-Erweiterung im Visual Studio-Installer](media/create-project-repo/installation-github-extension.png)

2. Starten Sie Visual Studio.

3. Klicken Sie auf **Ansicht > Team Explorer** , um das Fenster **Team Explorer** zu öffnen. Dort können Sie eine Verbindung zu GitHub oder Azure DevOps herstellen oder ein Repository klonen.

    ![Das Team Explorer-Fenster zeigt Azure DevOps, GitHub und das Klonen eines Repositorys an.](media/create-project-repo/team-explorer-devops.png)

4. Geben Sie `https://github.com/Microsoft/samples-for-ai` im Feld „URL“ unter **Lokale Git-Repositorys** ein. Geben Sie einen Ordner für die geklonten Dateien an, und klicken Sie auf **Klonen** .

    > [!Tip]
    > Der Ordner, den Sie in Team Explorer angeben, empfängt die geklonten Dateien. Im Gegensatz zum Befehl `git clone` wird beim Erstellen eines Klons in Team Explorer nicht automatisch ein Unterordner mit dem Namen des Repositorys erstellt.

5. Wenn der Klonvorgang abgeschlossen ist, doppelklicken Sie auf den Repositoryordner im unteren Bereich von Team Explorer, um zum Repositorydashboard zu navigieren. Klicken Sie unter **Projektmappen** auf **Neu** .

    ![Das Fenster „Team Explorer“, in dem ein neues Projekt aus einem Klon erstellt wird](media/create-project-repo/team-explorer-new-project.png)

6. Klicken Sie in dem Dialogfeld **Neues Projekt** auf **Aus vorhandenem Python-Code** . Geben Sie einen Namen für das Projekt an, legen Sie für **Speicherort** denselben Ordner fest, in dem auch das Repository gespeichert ist, und klicken Sie auf **OK** . Klicken Sie in dem sich öffnenden Assistenten auf **Fertig stellen** .

7. Klicken Sie im Menü auf **Ansicht > Projektmappen-Explorer** .

8. Erweitern Sie im Projektmappen-Explorer den Knoten `TensorFlow Examples> MNIST`. Klicken Sie mit der rechten Maustaste zunächst auf `convolutional.py`, und klicken Sie anschließend auf **Als Startdatei festlegen** . In diesem Schritt meldet Visual Studio, welche Datei beim Ausführen des Projekts verwendet werden soll.

9. Drücken Sie **STRG**+**F5** , oder klicken Sie auf **Debuggen > Ohne Debuggen starten** , um das Programm auszuführen. Wenn Ihnen ein Fehler angezeigt wird, überprüfen Sie die Einstellungen für das Arbeitsverzeichnis im vorherigen Schritt erneut.

10. Wenn das Programm erfolgreich ausgeführt wird, beginnt es mit dem Herunterladen des Trainings- und Testdatasets. Anschließend wird das Modell trainiert und die Fehlerquote ausgegeben. Sie möchten, dass die Fehlerquote mit der Zeit abnimmt.

    ![Erste Ausgabe des Python MNIST-Programms](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Wenn Sie Anaconda verwenden und eine Fehlermeldung über das Fehlen von „numpy“ erhalten, müssen Sie möglicherweise [Ihre Python-Umgebung auf die Verwendung von Anaconda umstellen](../python/selecting-a-python-environment-for-a-project.md).

11. Sie können den Fortschritt mit TensorBoard verfolgen. Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und klicken Sie dann auf **Run TensorBoard** . Wählen Sie das Verzeichnis der ausgegebenen TensorBoard-Protokolle aus.

   ![Ausführen von TensorBoard](media/create-project-repo/run-tensorboard.png)

12. Beachten Sie, dass die Anzahl der Fehler mit der Zeit abnehmen, was bedeutet, dass sich die Qualität verbessert.

   ![Ausführen von TensorBoard](media/create-project-repo/tensorboard.png)
