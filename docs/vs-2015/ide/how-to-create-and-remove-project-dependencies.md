---
title: 'Vorgehensweise: Erstellen und Entfernen von Projektabhängigkeiten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1403beccdb6bf9b938787f62cb3da2e5bb5c259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668122"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Gewusst wie: Erstellen und Entfernen von Projektabhängigkeiten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Erstellen einer Projektmappe, die mehrere Projekte enthält, kann es erforderlich sein, bestimmte Projekte zuerst zu erstellen, um Code zu generieren, der von anderen Projekten verwendet wird. Wenn ein Projekt ausführbaren Code verarbeitet, der von einem anderen Projekt generiert wurde, wird auf das generierende Projekt als Projektabhängigkeit des verarbeitenden Projekts verwiesen. Solche Abhängigkeitsbeziehungen können im Dialog Feld **Projekt Abhängigkeiten** definiert werden.

### <a name="to-assign-dependencies-to-projects"></a>So weisen Sie Projekten Abhängigkeiten zu

1. Wählen Sie im Projektmappen-Explorer ein Projekt aus.

2. Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.

    Das Dialogfeld **Projektabhängigkeiten** wird geöffnet.

   > [!NOTE]
   > Die Option **Projektabhängigkeiten** ist nur in einer Projektmappe mit mehr als einem Projekt verfügbar.

3. Wählen Sie auf der Registerkarte **Abhängigkeiten** ein Projekt aus dem Dropdownmenü **Projekt** aus.

4. Aktivieren Sie im Feld **Abhängigkeiten** die Kontrollkästchen für alle weiteren Projekte, die vor Erstellung dieses Projekts erstellt werden müssen.

   Die Projektmappe muss aus mehr als einem Projekt bestehen, bevor Sie Projektabhängigkeiten erstellen können.

### <a name="to-remove-dependencies-from-projects"></a>So entfernen Sie Abhängigkeiten aus Projekten

1. Wählen Sie im Projektmappen-Explorer ein Projekt aus.

2. Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.

     Das Dialogfeld **Projektabhängigkeiten** wird geöffnet.

    > [!NOTE]
    > Die Option **Projektabhängigkeiten** ist nur in einer Projektmappe mit mehr als einem Projekt verfügbar.

3. Wählen Sie auf der Registerkarte **Abhängigkeiten** ein Projekt aus dem Dropdownmenü **Projekt** aus.

4. Deaktivieren Sie im Feld **Abhängigkeiten** die Kästchen neben anderen Projekten, die keine Abhängigkeiten dieses Projekts mehr sind.

## <a name="see-also"></a>Weitere Informationen
 Erstellen [und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [Kompilieren und](../ide/compiling-and-building-in-visual-studio.md) Erstellen von Buildkonfigurationen [Understanding Build Configurations](../ide/understanding-build-configurations.md) [NIB Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
