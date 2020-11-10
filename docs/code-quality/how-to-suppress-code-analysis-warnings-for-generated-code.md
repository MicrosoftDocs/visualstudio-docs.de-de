---
title: Code Analyse Verletzungen für generierten Code unterdrücken
ms.date: 05/13/2019
description: Erfahren Sie, wie Sie Code Analyse Warnungen für generierten Code unterdrücken. Erfahren Sie, wie Sie verhindern können, dass Visual Studio ältere Analyse Warnungen zu generiertem Code anzeigt.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e462281686236f809fbd88588df5ad8fd832dbde
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435546"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Gewusst wie: Unterdrücken von Code Analyse Warnungen für generierten Code

Generierter Code enthält Code, der von verwalteten Code Compilern oder Drittanbieter Tools zu Ihrem Projekt hinzugefügt wird. Möglicherweise möchten Sie die Regel Verletzungen sehen, die von der Code Analyse in generiertem Code erkannt werden. Da Sie jedoch den Code, der die Verstöße enthält, nicht anzeigen und verwalten können, sollten Sie ihn möglicherweise nicht sehen.

Mithilfe des Kontrollkästchens **Ergebnisse aus generiertem Code unterdrücken** der Code Analyse-Eigenschaften Seite eines Projekts können Sie auswählen, ob Code Analyse Warnungen aus Code angezeigt werden sollen, der von einem Drittanbieter Tool generiert wurde.

> [!NOTE]
> Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>So unterdrücken Sie Warnungen für generierten Code in einem Projekt

1. Klicken Sie mit der rechten Maustaste auf das Projekt in **Projektmappen-Explorer** und klicken Sie dann auf **Eigenschaften**.

2. Wählen Sie die Registerkarte **Code Analyse** aus.

3. Aktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** .

> [!IMPORTANT]
> Sie können nur Warnungen aus der Legacy Analyse unterdrücken. Die Eigenschaften Seite mit der Einstellung ist veraltet und wird in einer zukünftigen Produktversion entfernt. Derzeit können Sie keine Code Analyse Warnungen von [Analyzern](roslyn-analyzers-overview.md)unterdrücken.
