---
title: Projekt Regelsätze mit Eincheck Richtlinie synchronisieren
ms.date: 11/04/2016
description: Erfahren Sie, wie Sie einen Visual Studio Code-Projekt Regelsatz mit einer Azure devops Project-Eincheck Richtlinie synchronisieren.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 913860538fe7f9da1514d0e51d23bb3ea48c3b66
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434687"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Vorgehensweise: Synchronisieren von Code Projekt-Regelsätzen mit einer Azure devops-Projekt Eincheck Richtlinie

Die Code Analyse Einstellungen für Code Projekte werden mit der Eincheck Richtlinie für das Azure devops-Projekt synchronisiert, indem ein Regelsatz angegeben wird, der mindestens die Regeln enthält, die im Regelsatz für die Eincheck Richtlinie angegeben sind. Ihr Entwickler Leiter kann Sie über den Namen und den Speicherort des Regelsatzes für die Eincheck Richtlinie informieren. Sie können eine der folgenden Optionen verwenden, um sicherzustellen, dass die Code Analyse für das Projekt den richtigen Regelsatz verwendet:

- Wenn die Eincheck Richtlinie einen der integrierten Microsoft-Regelsätze verwendet, öffnen Sie das Dialogfeld "Eigenschaften" für das Code Projekt, zeigen Sie die Seite "Code Analyse" an, und wählen Sie den Regelsatz aus. Die Standardregel Sätze von Microsoft werden automatisch mit Visual Studio installiert und sollten nicht bearbeitet werden. Wenn die Regelsätze nicht bearbeitet werden, entsprechen die Regeln in der Richtlinie und den lokalen Regelsätzen der Garantie.

- Wenn in der Eincheck Richtlinie ein benutzerdefinierter Regelsatz verwendet wird, führen Sie einen Get-Vorgang für die Regel Satz Datei in der Versionskontrolle aus, um eine lokale Kopie zu erstellen. Geben Sie dann den lokalen Speicherort in den Code Analyse Einstellungen für das Code Projekt an. Die Regeln entsprechen garantiert, wenn der Regelsatz für die Eincheck Richtlinie auf dem neuesten Stand ist.

     Wenn Sie den Speicherort der Versionskontrolle einem lokalen Ordner zuordnen, der sich in derselben Beziehung zum Azure devops-Projektstamm als das Code Projekt befindet, wird der Speicherort der Regel mit einem relativen Pfad festgelegt. Der relative Pfad stellt sicher, dass die Code Projekteinstellung für die Code Analyse auf andere Computer verschoben werden kann.

- Passen Sie eine Kopie des Regelsatzes für die Eincheck Richtlinie für ein Code Projekt an. Stellen Sie sicher, dass der neue Regelsatz alle Regeln in der Eincheck Richtlinie und alle anderen Regeln enthält, die Sie einschließen möchten. Sie müssen sicherstellen, dass der Regelsatz alle Regeln im Regelsatz für die Eincheck Richtlinie enthält.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>So geben Sie einen Microsoft Standard-Regelsatz an

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Code Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf **Codeanalyse**.

::: moniker range="vs-2017"

3. Wählen Sie in der Liste **diesen Regelsatz ausführen** den Regelsatz Check-in-Richtlinie aus.

::: moniker-end

::: moniker range=">=vs-2019"

3. Wählen Sie in der Liste **aktive Regeln** den Regelsatz Check-in-Richtlinie aus.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>So geben Sie einen benutzerdefinierten Eincheck Richtlinien-Regelsatz an

1. Führen Sie bei Bedarf einen Get-Vorgang für die Regel Satz Datei aus, die die Eincheck Richtlinie angibt.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Code Projekt, und klicken Sie dann auf **Eigenschaften**.

3. Klicken Sie auf **Codeanalyse**.

::: moniker range="vs-2017"

4. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf **\<Browse>** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Klicken Sie in der Liste **aktive Regeln** auf **\<Browse>** .

::: moniker-end

5. Geben Sie im Dialogfeld **Öffnen** die Regel Satz Datei für die Eincheck Richtlinie an.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>So erstellen Sie einen benutzerdefinierten Regelsatz für ein Code Projekt

Weitere Informationen zum Erstellen eines benutzerdefinierten Regelsatzes finden Sie unter [Anpassen eines Regelsatzes](how-to-create-a-custom-rule-set.md).
