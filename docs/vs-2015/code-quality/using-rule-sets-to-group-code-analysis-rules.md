---
title: Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603480"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie die Code Analyse in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder konfigurieren [!INCLUDE[vsPro](../includes/vspro-md.md)] , können Sie eine Auswahl aus einer Liste von integrierten Microsoft- *Regelsätzen*treffen. Ein Regelsatz ist eine logische Gruppierung von Codeanalyseregeln, die gezielte Probleme und bestimmte Bedingungen identifizieren. Sie können z. B. einen Regelsatz anwenden, mit dem Code auf öffentlich verfügbare APIs überprüft wird, oder einen Regelsatz, der nur die empfohlenen Mindestregeln enthält. Sie können auch einen Regelsatz anwenden, der alle Regeln enthält.

 Sie können einen Regelsatz anpassen, indem Sie Regeln hinzufügen oder löschen, oder indem Sie Regeln so ändern, dass Sie im **Fehlerliste** Fenster als Warnungen oder Fehler angezeigt werden. Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen. Beim Anpassen eines Regelsatzes finden Sie auf der Regelsatzseite hilfreiche Such- und Filtertools.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandter Inhalt|
|----------|---------------------|
|**Praktische Übungen:** Verwenden Sie die Code Analysetools, um einen benutzerdefinierten Regelsatz anzugeben, um Probleme in einer einfachen .NET Framework Anwendung zu finden und zu beheben.|-   [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Konfigurieren Sie die Code Analyse für ein Projekt:** Wählen Sie einen vorhandenen Regelsatz für ein Projekt, eine Website oder eine Projekt Mappe aus.|-   [Gewusst wie: Konfigurieren der Code Analyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Verwenden von Regelsätzen zum Angeben der zu testenden C++-Regeln](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Gewusst wie: Konfigurieren der Code Analyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Gewusst wie: Angeben von Regelsätzen für mehrere Projekte in einer Projekt Mappe](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Anpassen eines Regelsatzes:** Regeln angeben, die auf das Projekt angewendet werden sollen.|-   [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Verstehen Sie die integrierten Regelsätze:** Anzeigen der Code Analyse Regeln, die die integrierten Regelsätze bilden.|-   [Code Analyse-Regel Satz Referenz](../code-quality/code-analysis-rule-set-reference.md)|
|**Integrieren der Code Analyse in Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] mit Eincheck Richtlinien können Entwicklungsteams sicherstellen, dass alle Code-Check-ins einem gemeinsamen Satz von Code Analyse Standards entsprechen.|-   [Gewusst wie: Synchronisieren von Code Projekt-Regelsätzen mit der Eincheck Richtlinie für Team Projekte](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
