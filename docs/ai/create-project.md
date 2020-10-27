---
title: Erstellen eines KI-Projekts aus einer Vorlage
description: In diesem Artikel erfahren Sie, wie Sie Visual Studio Tools für KI verwenden, um ein KI-Projekt aus einer Vielzahl von Vorlagen zu erstellen.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 15e788cca7cb27b36e3f3567aff96cd33bf5aaae
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099231"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Erstellen eines KI-Projekts aus einer Vorlage in Visual Studio

Wenn Sie die [Visual Studio-Tools für KI installiert haben](installation.md), können Sie aus einer Vielzahl von Vorlagen ganz einfach ein neues KI-Projekt erstellen.

1. Starten Sie Visual Studio.

2. Klicken Sie auf **Datei > Neu > Projekt** (STRG+UMSCHALT+N). Suchen Sie im Dialogfeld **Neues Projekt** nach **AI Tools** (KI-Tools), und wählen Sie die gewünschte Vorlage aus. Daraufhin wird eine kurze Beschreibung des Vorlageninhalts angezeigt.

    ![Visual Studio 2017-Dialogfeld „Neues Projekt“ mit Python-Vorlage](media/create-project/new-ai-project.png)

3. Wählen Sie für diesen Schnellstart die Vorlage **TensorFlow-Anwendung** aus, benennen Sie das Projekt (z.B. „MNIST“), wählen Sie einen Speicherort aus, und klicken Sie auf **OK** .

4. Visual Studio erstellt die Projektdatei (eine `.pyproj`-Datei auf einem Datenträger) wie von der Vorlage beschrieben zusammen mit allen anderen Dateien. Mit der Vorlage „TensorFlow-Anwendung“ enthält das Projekt eine leere Datei, die den gleichen Namen wie Ihr Projekt trägt. Diese Datei ist im Visual Studio-Editor standardmäßig geöffnet.

    ![Das resultierende Projekt, wenn die Python-Anwendungsvorlage verwendet wird](media/create-project/new-tensorflowapp.png)

5. Beachten Sie, dass der Code bereits einige Bibliotheken importiert, z.B. TensorFlow, numpy, sys und os. Zusätzlich wird Ihre Anwendung bereits mit einigen Eingabeargumenten gestartet, um das einfache Wechseln des Speicherorts von Eingabetrainingsdaten, Ausgabemodellen und Protokolldateien zu ermöglichen. Diese Parameter sind nützlich, wenn Sie Ihre Aufträge an mehrere Computekontexte (d.h. verschiedene Verzeichnisse in Ihrem lokalen Entwicklungscomputer, die sich in einer Azure-Dateifreigabe befindet) übermitteln.

6. Ihr Projekt verfügt zudem über einige Eigenschaften, die erstellt wurden, um das Debuggen Ihrer App zu erleichtern, indem Befehlszeilenargumente direkt an diese Eingabeparameter übergeben werden. Klicken Sie mit der **rechten Maustaste** auf Ihr Projekt, und klicken Sie dann auf **Eigenschaften** .

    ![Eigenschaften](media/create-project/project-properties.png)

7. Klicken Sie auf die Registerkarte **Debuggen** , um die automatisch hinzugefügten Skriptargumente anzuzeigen. Sie können bei Bedarf das Verzeichnis ändern, in dem sich Ihre Eingabedaten befinden und in dem die Ausgabedaten gespeichert werden sollen.

    ![Eigenschaften](media/create-project//project-properties_1.png)

8. Drücken Sie „STRG+F5“, oder klicken Sie im Menü auf **Debuggen > Ohne Debuggen starten** , und führen Sie das Programm aus. Die Ergebnisse werden in einem Konsolenfenster angezeigt.
