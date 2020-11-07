---
title: Eincheck Richtlinien für Standard Code Analyse erstellen/aktualisieren
description: Erfahren Sie, wie Sie sicherstellen, dass die Code Analyse in allen Code Projekten in einem Azure devops-Projekt ausgeführt wird. Weitere Informationen finden Sie unter Konfigurieren einer Eincheck Richtlinie für die Projekt Code Analyse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5f03cbd78944d49301362c07d01497abb22734c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348761"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Gewusst wie: Erstellen oder Aktualisieren von Standardeincheckrichtlinien für die Codeanalyse

Mithilfe der Eincheck Richtlinie für die Code Analyse können Sie festlegen, dass die Code Analyse für alle Code Projekte in einem Azure devops-Projekt ausgeführt werden soll. Wenn Sie die Code Analyse benötigen, können Sie die Qualität des Codes verbessern, der in die Codebasis eingecheckt wird.

> [!NOTE]
> Diese Funktion ist nur verfügbar, wenn Sie Team Foundation Server verwenden.

Eincheck Richtlinien für die Code Analyse werden in den Projekteinstellungen festgelegt und gelten für jedes Code Projekt. Code Analyse Ausführungen werden für Code Projekte in der Projektdatei (. XXPROJ) für das Code Projekt konfiguriert. Code Analyse Ausführungen werden auf dem lokalen Computer ausgeführt. Wenn Sie eine Eincheck Richtlinie für die Code Analyse aktivieren, müssen die Dateien in einem Code Projekt, das eingecheckt werden soll, nach der letzten Bearbeitung kompiliert werden, und es muss eine Code Analyse ausgeführt werden, in der mindestens die Regeln in den Projekteinstellungen auf dem Computer ausgeführt werden müssen, auf dem die Änderungen vorgenommen wurden.

- Bei verwaltetem Code legen Sie die Eincheck Richtlinie durch Angabe eines *Regelsatzes* fest, der eine Teilmenge der Code Analyse Regeln enthält.

- Bei C/C++-Code in Visual Studio 2017 Version 15,6 und früher erfordert die Eincheck Richtlinie, dass alle Code Analyse Regeln ausgeführt werden. Sie können Präprozessordirektiven hinzufügen, um bestimmte Regeln für die einzelnen Code Projekte in Ihrem Azure devops-Projekt zu deaktivieren. In 15,7 und höher können Sie **/analyze: RuleSet** verwenden, um anzugeben, welche Regeln ausgeführt werden sollen. Weitere Informationen finden Sie unter [Verwenden von Regelsätzen zum Angeben der zu testenden C++-Regeln](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

Nachdem Sie eine Eincheck Richtlinie für verwalteten Code angegeben haben, können die Teammitglieder ihre Code Analyse Einstellungen für Code Projekte mit den Azure devops-Projektrichtlinien Einstellungen synchronisieren.

## <a name="to-open-the-check-in-policy-editor"></a>So öffnen Sie den Editor für Check-in-Richtlinien

1. Klicken Sie in Team Explorer mit der rechten Maustaste auf den Projektnamen, zeigen Sie auf **Projekteinstellungen** , und klicken Sie dann auf **Quell** Code Verwaltung.

1. Wählen Sie im Dialogfeld **Quell** Code Verwaltung die Registerkarte **Check-in-Richtlinie** aus.

1. Führen Sie eines der folgenden Verfahren aus:

    - Klicken Sie auf **Hinzufügen** , um eine neue Eincheck Richtlinie zu erstellen.

    - Doppelklicken Sie in der Liste **Richtlinientyp** auf das vorhandene **Code Analyse** Element, um die Richtlinie zu ändern.

## <a name="to-set-policy-options"></a>So legen Sie Richtlinien Optionen fest

Aktivieren oder deaktivieren Sie die folgenden Optionen:

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Erzwingen Sie den Eincheck Vorgang, sodass nur Dateien enthalten sind, die Teil der aktuellen Projekt Mappe sind.**|Die Code Analyse kann nur für Dateien ausgeführt werden, die in den Projektmappen-und Projekt Konfigurationsdateien Diese Richtlinie stellt sicher, dass der gesamte Code, der Teil einer Lösung ist, analysiert wird.|
|**C/C++-Code Analyse erzwingen (/analyze)**|Erfordert, dass alle C-oder C++-Projekte mit der/analyze-Compileroption erstellt werden, um die Code Analyse auszuführen, bevor Sie eingeglichen werden können.|
|**Code Analyse für verwalteten Code erzwingen**|Erfordert, dass alle verwalteten Projekte eine Code Analyse ausführen und erstellt werden, bevor Sie eingeglichen werden können.|

## <a name="to-specify-a-managed-rule-set"></a>So geben Sie einen verwalteten Regelsatz an

Verwenden Sie in der Liste **diesen Regelsatz ausführen** eine der folgenden Methoden:

- Wählen Sie einen Microsoft Standard-Regelsatz aus.

- Wählen Sie einen benutzerdefinierten Regelsatz durch Klicken aus **\<Select Rule Set from Source Control...>** . Geben Sie dann den Versions Kontroll Pfad des Regelsatzes im Quellcodeverwaltungs-Browser ein. Die Syntax eines Versions Kontroll Pfads lautet wie folgt:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Weitere Informationen zum Erstellen und Implementieren eines benutzerdefinierten Eincheck Richtlinien-Regelsatzes finden Sie unter [Implementieren von benutzerdefinierten Eincheck Richtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Weitere Informationen

- [Implementieren von benutzerdefinierten Eincheckrichtlinien für die Codeanalyse für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
