---
title: Überwachen mit TensorBoard
description: Hier erfahren Sie, wie Sie Visual Studio verwenden können, um den Trainingsfortschritt Ihres Modells mit TensorBoard darzustellen.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 650189c4418355ae06b296bac7e16eece0ea88ad
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727254"
---
# <a name="monitor-with-tensorboard"></a>Überwachen mit TensorBoard

Sie können den Fortschritt des Trainings Ihres Modells mit TensorBoard verfolgen.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und klicken Sie dann auf **Run TensorBoard** (Ausführen von TensorBoard). Wählen Sie das Verzeichnis der ausgegebenen TensorBoard-Protokolle aus.

    ![Screenshot: Projektmappen-Explorer in Visual Studio mit Auswahl des MNIST-Projekts. Ein Kontextmenü ist geöffnet, und der Befehl zum Ausführen von TensorBoard ist ausgewählt.](media/monitor-tensorboard/run-tensorboard.png)

2. Beachten Sie, dass Fehler mit der Zeit abnehmen, was bedeutet, dass sich die Qualität verbessert.

    ![Screenshot: TensorBoard-Hauptfenster mit grafischen Visualisierungen der Daten aus den TensorBoard-Protokollen](media/monitor-tensorboard/tensorboard.png)
