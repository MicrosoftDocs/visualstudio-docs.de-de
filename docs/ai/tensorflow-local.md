---
title: Lokales Trainieren eines TensorFlow-Modells
description: Lokales Ausführen eines TensorFlow-Modells in KI-Tools für Visual Studio
keywords: ki, visual studio, tensorflow, lokal
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0ceb21701958630c8b783d5b6850c5e0a0ab229a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841379"
---
# <a name="train-a-tensorflow-model-locally"></a>Lokales Trainieren eines TensorFlow-Modells

In diesem Schnellstart trainieren Sie ein TensorFlow-Modell mit einem [MNIST](http://yann.lecun.com/exdb/mnist/)-Dataset lokal in Visual Studio-Tools für KI.

Die MNIST-Datenbank enthält 60.000 Trainingsbeispiele und 10.000 Testbeispiele für handgeschriebene Ziffern.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie vor Beginn sicher, dass Sie Folgendes installiert haben:

### <a name="google-tensorflow"></a>Google TensorFlow

Führen Sie die folgenden Befehle über ein Terminal aus:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy und SciPy
Installieren Sie [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) und [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Beispielcode herunterladen
Laden Sie dieses [GitHub-Repository](https://github.com/Microsoft/samples-for-ai) herunter, das Beispiele für die ersten Schritte mit Deep Learning in TensorFlow, CNTK, Theano usw. enthält.

## <a name="open-solution-and-train-model"></a>Öffnen einer Projektmappe und Trainieren eines Modells

- Starten Sie Visual Studio, und klicken Sie auf **Datei > Öffnen> Projekt/Projektmappe**.

- Öffnen Sie den Ordner **Tensorflow Examples** (TensorFlow-Beispiele) aus dem heruntergeladenen Beispielrepository, und öffnen Sie die Datei **TensorflowExamples.sln**.

   ![Öffnen des Projekts](media/tensorflow-local/open-project.png)

   ![Projektmappe öffnen](media/tensorflow-local/open-solution.png)

- Machen Sie das MNIST-Projekt im **Projektmappen-Explorer** ausfindig, klicken Sie erst mit der rechten Maustaste auf das Projekt und anschließend mit der Linken auf **Set as StartUp Project** (Als Startprojekt festlegen).

- Klicken Sie auf **Start**.

- Die Ausgabe wird in der Konsole ausgegeben.

   ![Beispielausgabe in der Konsole](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Trainieren eines TensorFlow-Modells in der Cloud](tensorflow-vm.md)
