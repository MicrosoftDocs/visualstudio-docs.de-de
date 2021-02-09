---
title: Fehler bei separaten Projekten verwenden
description: Erfahren Sie, wie Sie Datasets und TableAdapters in verschiedene Projekte aufteilen, damit Sie die Anwendungsebenen schnell trennen und N-schichtige Daten Anwendungen generieren können.
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9463fe0371ee3184fd78684e7fe0565820ab3bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866540"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Aufteilen von DataSets und TableAdapters in verschiedene Projekte
Typisierte Datasets wurden verbessert, sodass die [TableAdapters](create-and-configure-tableadapters.md) -Klasse und die DataSet-Klasse in separaten Projekten generiert werden können. Dies ermöglicht eine bequeme Trennung der Anwendungsebenen und die Erzeugung von N-Tier-Datenanwendungen.

Im folgenden Verfahren wird beschrieben, wie der **DataSet-Designer** verwendet wird, um Datasetcode in einem Projekt zu generieren, das von dem Projekt getrennt ist, das den generierten TableAdapter-Code enthält.

## <a name="separate-datasets-and-tableadapters"></a>Separate Datasets und TableAdapters
Wenn Sie Datasetcode von TableAdapter-Code trennen, muss sich das Projekt, das den Datasetcode enthält, in der aktuellen Projekt Mappe befinden. Wenn sich dieses Projekt nicht in der aktuellen Projekt Mappe befindet, ist es nicht in der **DataSet-Projekt** Liste im **Eigenschaften** Fenster verfügbar.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>So separieren Sie das DataSet in ein anderes Projekt

1. Öffnen Sie eine Projektmappe, die ein Dataset (*XSD*-Datei) enthält.

    > [!NOTE]
    > Wenn die Projekt Mappe nicht das Projekt enthält, in das Sie den Datasetcode aufteilen möchten, erstellen Sie das Projekt, oder fügen Sie der Projekt Mappe ein vorhandenes Projekt hinzu.

2. Doppelklicken Sie im **Projektmappen-Explorer** auf eine typisierte Dataset-Datei (*XSD*-Datei), um das Dataset mit dem **DataSet-Designer** zu öffnen.

3. Wählen Sie einen leeren Bereich des **DataSet-Designer** aus.

4. Suchen Sie im Fenster **Eigenschaften** den **DataSet-Projekt** Knoten.

5. Wählen Sie in der Liste **DataSet-Projekt** den Namen des Projekts aus, in das Sie den DataSet-Code generieren möchten.

     Nachdem Sie das Projekt ausgewählt haben, in das Sie den Datasetcode generieren möchten, wird die Eigenschaft **DataSet-Datei** mit einem Standard Dateinamen aufgefüllt. Sie können diesen Namen ggf. ändern. Wenn Sie den Dataset-Code in einem bestimmten Verzeichnis generieren möchten, können Sie in der **Projektordner**-Eigenschaft den Namen des Ordners angeben.

    > [!NOTE]
    > Beim Trennen von Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

6. Speichern Sie das DataSet.

     Der DataSet-Code wird in dem ausgewählten Projekt in der **DataSet-Projekt** Eigenschaft generiert, und der **TableAdapter** -Code wird im aktuellen Projekt generiert.

Nachdem Sie den DataSet-und TableAdapter-Code getrennt haben, ist das Ergebnis standardmäßig eine diskrete Klassendatei in jedem Projekt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen *DatasetName. Designer. vb* (oder *DatasetName.Designer.cs*), die den TableAdapter-Code enthält. Das Projekt, das in der **DataSet-Projekt** Eigenschaft festgelegt ist, verfügt über eine Datei namens *DatasetName. DataSet. Designer. vb* (oder *DatasetName.DataSet.Designer.cs*), die den DataSet-Code enthält.

> [!NOTE]
> Um die generierte Klassendatei anzuzeigen, wählen Sie das DataSet oder das TableAdapter-Projekt aus. Wählen Sie dann in **Projektmappen-Explorer** die Option **alle Dateien anzeigen** aus.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über n-schichtige Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
