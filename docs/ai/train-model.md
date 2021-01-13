---
title: Senden eines Auftrags zum Trainieren eines Modells
description: Senden eines Auftrags zum Trainieren eines Modells mit Azure Batch AI
ms.custom: SEO-VS-2020
keywords: KI, Visual Studio, Modell trainieren, Cloud
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 72f5fa5aab9f9afa6268f8acd737430af0568928
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727358"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Trainieren von KI-Modellen in Azure Batch AI

Azure Batch AI ist ein verwalteter Dienst, mit dem Datenanalysten und KI-Forscher KI und andere Machine Learning-Modelle in Clustern von virtuellen Azure-Computern trainieren können (inkl. VMs mit GPU-Unterstützung). Sie müssen nur beschreiben, welche Anforderungen für den Auftrag bestehen und wo die Eingaben zu finden sind sowie die Ausgaben speichern, und Batch AI übernimmt den Rest. [Weitere Informationen zu Azure Batch AI](/azure/batch-ai/overview)

Da Batch AI mit den Visual Studio-Tools für KI integriert wird, können Sie Trainingsmodelle in Azure dynamisch horizontal hochskalieren.  Wenn Sie die [Visual Studio-Tools für KI](installation.md) installiert haben, lässt sich anhand der Anleitungen im Azure Machine Learning-Beispielkatalog ganz einfach ein neues Python-Projekt erstellen.

1. Starten Sie Visual Studio. Öffnen Sie den **Server-Explorer**, indem Sie das Menü **AI Tools** (KI-Tools) öffnen und auf **Cluster auswählen** klicken.

    ![Clusterauswahl](media/train-model/select-cluster.png)

2. Erweitern Sie **AI Tools** (KI-Tools). Jede Ihrer Batch AI-Ressourcen wird automatisch erkannt und im Server-Explorer angezeigt.

    ![Screenshot der erweiterten Ordnerstruktur für KI-Tools im Server-Explorer, in der erweiterte Unterordner für Azure Batch KI und Azure Machine Learning angezeigt werden.](media/train-model/batchai.png)

3. Klicken Sie auf **Ansicht > Team Explorer...** , um das Fenster **Team Explorer** zu öffnen. Dort können Sie eine Verbindung zu GitHub oder Azure DevOps herstellen oder ein Repository klonen.

    ![Das Team Explorer-Fenster zeigt Azure DevOps, GitHub und das Klonen eines Repositorys an.](media/train-model/team-explorer-devops.png)

4. Geben Sie `https://github.com/Microsoft/samples-for-ai` im Feld „URL“ unter **Lokale Git-Repositorys** ein. Geben Sie einen Ordner für die geklonten Dateien an, und klicken Sie auf **Klonen**.

    > [!Tip]
    > Der Ordner, den Sie in Team Explorer angeben, empfängt die geklonten Dateien. Im Gegensatz zum Befehl `git clone` wird beim Erstellen eines Klons in Team Explorer nicht automatisch ein Unterordner mit dem Namen des Repositorys erstellt.

5. Wenn das Klonen abgeschlossen ist, klicken Sie auf **Datei > Projektmappe öffnen > Projekt/Projektmappe**.

    ![Screenshot, der einen Teil des Menüs „Datei“ im Server-Explorer mit ausgewähltem Befehl „Öffnen“ und im Kontextmenü ausgewähltem „Projekt/Projektmappe“ zeigt.](media/train-model/open-solution.png)

6. Öffnen Sie **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** im Verzeichnis, das Sie im Repository geklont haben.

    ![Screenshot, der die Projektmappendatei „TensorflowExamples.sln“ zeigt, die im Inhalt des Ordners „TensorflowExamples“ im Repository „samples-for-ai“ aufgeführt ist.](media/train-model/tensorflowexamples.png)

7. Legen Sie das MNIST-Projekt als **Startprojekt** fest.

    ![Screenshot, der für das MNIST-Projekt im Projektmappen-Explorer die im Kontextmenü ausgewählte Option „Als Startprojekt festlegen“ zeigt.](media/train-model/mnist-startup.png)

8. <strong>Klicken Sie mit der rechten Maustaste auf das **MNIST-Projekt** und dann auf **Auftrag übermitteln**</strong>.

    ![Screenshot, der für das MNIST-Projekt im Projektmappen-Explorer die im Kontextmenü ausgewählte Option „Auftrag übermitteln“ zeigt.](media/train-model/submit-job.png)
9. Wählen Sie Ihr **Azure Batch AI**-Cluster aus, und klicken Sie auf **Importieren**. Wählen Sie die Datei `AzureBatchAI_TF_MNIST.json` aus, um schnell einige Standardwerte wie das zu verwendende Docker-Image aufzufüllen. Klicken Sie dann auf **Senden**.

    ![Screenshot des Dialogfelds „Auftrag übermitteln“ mit aufgefüllten Werten für „Cluster verwenden“, Startskript, Auftragsname, Imagename, StdOutErr-Pfadpräfix und CLI-Parameter.](media/train-model/submit-batch.png)
