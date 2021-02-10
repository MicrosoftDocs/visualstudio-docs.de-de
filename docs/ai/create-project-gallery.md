---
title: Erstellen eines Projekts
description: Erstellen eines Projekts mithilfe des Beispiels aus dem Azure Machine Learning-Katalog
keywords: KI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: e6c5b8201b39f82e4c4645196ca543e2567b6e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841548"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Erstellen eines KI-Projekts aus dem Azure Machine Learning-Katalog in Visual Studio

Azure Machine Learning ist in Visual Studio-Tools für KI enthalten. Sie können diesen Dienst verwenden, um Machine Learning-Aufträge an Remotecomputeziele wie virtuelle Azure-Computer, Spark-Cluster usw. zu übermitteln. 

Wenn Sie die [Visual Studio-Tools für KI](installation.md) installiert haben, lässt sich anhand der Anleitungen im Azure Machine Learning-Beispielkatalog ganz einfach ein neues Python-Projekt erstellen.

> [!NOTE]
> Azure Machine Learning Workbench muss installiert sein. 

1. Starten Sie Visual Studio. Öffnen Sie den **Server-Explorer**, indem Sie das Menü **AI Tools** (KI-Tools) öffnen und auf **Cluster auswählen** klicken.

    ![Clusterauswahl](media/create-project-gallery/select-cluster.png)

2. Melden Sie sich bei Ihrem Azure Machine Learning-Abonnement an, indem Sie mit der rechten Maustaste auf den Knoten **Azure Machine Learning** im Server-Explorer und dann auf **Anmeldung** klicken und die Anweisungen befolgen.

    ![Anmeldung](media/create-project-gallery/azureml-login.png)

3. Klicken Sie auf **AI Tools > Azure Machine Learning Sample Gallery** (KI-Tools > Azure Machine Learning-Beispielkatalog).

    ![Beispielkatalog](media/create-project-gallery/gallery.png)

4. Wählen Sie für diesen Schnellstart das Beispiel „**MNIST mit TensorFlow**“ aus, und klicken Sie auf **Installieren**. Geben Sie hierzu folgende Informationen an:

   - **Ressourcengruppe**: Die Azure-Ressourcengruppe, in der Ihre Metadaten gespeichert werden
   - **Konto**: Experimentierkonto für Azure Machine Learning
   - **Arbeitsbereich**: Azure Machine Learning-Arbeitsbereich
   - **Projekttyp**: Machine Learning-Framework Wählen Sie in diesem Fall **TensorFlow** aus.
   - **Zur Projektmappe hinzufügen**: Bestimmt, ob Ihre aktuelle Visual Studio-Projektmappe hinzugefügt oder eine neue Projektmappe erstellt und geöffnet werden soll
   - **Projektpfad**: Speicherort des Codes
   - **Projektname**: Geben Sie **TensorFlowMNIST** ein.

   ![Das resultierende Projekt, wenn die Python-Anwendungsvorlage verwendet wird](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio erstellt die Projektdatei (eine `.pyproj`-Datei auf dem Datenträger) zusammen mit anderen Dateien, die im Beispiel definiert sind. Mit der MNIST-Vorlage enthält das Projekt mehrere Dateien.

    ![Screenshot: Projektmappen-Explorer von Visual Studio mit den Dateien für das TensorFlowMNIST-Projekt und dem Code für „tf_mnist.py“ im Hauptfenster.](media/create-project-gallery/azml-mnist.png)

6. Übermitteln Sie den Auftrag an Azure Machine Learning.

    ![Screenshot: Projektmappen-Explorer von Visual Studio mit Kontextmenü für das TensorFlowMNIST-Projekt mit ausgewählter Option „Auftrag übermitteln“](media/create-project-gallery/submit-azml.png)

7. Führen Sie diesen in einem Docker-Container oder auf Ihrem lokalen virtuellen Computer aus.

    ![Screenshot: Dialogfeld „Auftrag übermitteln“ mit „azureml:/local“ für „Cluster verwenden“ und „tf_mnist.py“ für „Startskript“](media/create-project-gallery/azml-local.png)
