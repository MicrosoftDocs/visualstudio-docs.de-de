---
title: Erstellen eines benutzerdefinierten Regelsatzes für die Code Analyse
ms.date: 11/02/2018
description: Erfahren Sie, wie Sie Code Analyse-Regelsätze in Visual Studio anpassen. Weitere Informationen finden Sie unter Erstellen neuer Sätze von Grund auf oder vorhandener Sätze. Verstehen der Regel Rangfolge.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69af1534740ddec2c804f0b7dafec61d985a4b24
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97667883"
---
# <a name="customize-a-rule-set"></a>Anpassen eines Regelsatzes

Sie können einen benutzerdefinierten Regelsatz erstellen, um bestimmte Projektanforderungen für die Code Analyse zu erfüllen.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Erstellen eines benutzerdefinierten Regelsatzes aus einem vorhandenen Regelsatz

Zum Erstellen eines benutzerdefinierten Regelsatzes können Sie einen integrierten Regelsatz im **Regelsatz-Editor** öffnen. Von dort aus können Sie bestimmte Regeln hinzufügen oder entfernen, und Sie können die Aktion ändern, die auftritt, wenn eine Regel verletzt wird &mdash; , z. b. eine Warnung oder einen Fehler.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.

2. Wählen Sie auf den **Eigenschaften** Seiten die Registerkarte **Code Analyse** aus.

::: moniker range="vs-2017"

3. Führen Sie in der Dropdown Liste **diesen Regelsatz ausführen** einen der folgenden Schritte aus:

::: moniker-end

::: moniker range=">=vs-2019"

3. Führen Sie in der Dropdown Liste **aktive Regeln** einen der folgenden Schritte aus:

::: moniker-end

   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder -

   - Wählen Sie **\<Browse>** diese Option, um einen vorhandenen Regelsatz anzugeben, der nicht in der Liste enthalten ist.

4. Wählen Sie **Öffnen** aus, um die Regeln im Regelsatz-Editor anzuzeigen.

> [!NOTE]
> Wenn Sie über ein .net Core-oder .NET Standard-Projekt verfügen, ist der Prozess ein wenig anders, da die Registerkarte **Code Analyse** in den Projekteigenschaften nicht die gleichen Optionen unterstützt. Führen Sie die Schritte zum [Kopieren eines vordefinierten Regelsatzes in das Projekt aus, und legen Sie ihn als aktiven Regelsatz fest](/dotnet/fundamentals/code-analysis/code-quality-rule-options). Nachdem Sie einen Regelsatz kopiert haben, können Sie [ihn im Visual Studio-Regelsatz-Editor bearbeiten](working-in-the-code-analysis-rule-set-editor.md) , indem Sie ihn aus **Projektmappen-Explorer** öffnen.

## <a name="create-a-new-rule-set"></a>Erstellen eines neuen Regelsatzes

Im Dialogfeld " **neue Datei** " können Sie eine neue Regel Satz Datei erstellen:

1. Wählen Sie **Datei**  >  **neue**  >  **Datei** aus, oder drücken Sie **STRG** + **N**.

2. Wählen Sie im Dialogfeld **neue Datei** auf der linken Seite die Kategorie **Allgemein** aus, und wählen Sie dann **Code Analyse-Regelsatz** aus.

3. Klicken Sie auf **Öffnen**.

   Die neue *RuleSet* -Datei wird im Regelsatz-Editor geöffnet.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Erstellen eines benutzerdefinierten Regelsatzes aus mehreren Regelsätzen

> [!NOTE]
> Das folgende Verfahren gilt nicht für .net Core-oder .NET Standard-Projekte, die die gleichen Funktionen auf der Registerkarte " **Code Analyse** Eigenschaft" nicht unterstützen.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus.

2. Wählen Sie auf den **Eigenschaften** Seiten die Registerkarte **Code Analyse** aus.

::: moniker range="vs-2017"

3. Wählen Sie **\<Choose multiple rule sets>** aus **diesen Regelsatz ausführen** aus.

::: moniker-end

::: moniker range=">=vs-2019"

3. Wählen Sie **\<Choose multiple rule sets>** aus den **aktiven Regeln** aus.

::: moniker-end

4. Wählen Sie im Dialogfeld **Regelsätze hinzufügen oder entfernen** die Regelsätze aus, die Sie in den neuen Regelsatz einschließen möchten.

   ![Dialogfeld "Regelsätze hinzufügen oder entfernen"](media/add-remove-rule-sets.png)

5. Wählen Sie **Speichern** unter aus, geben Sie einen Namen für die *RuleSet* -Datei ein, und klicken Sie dann auf **Speichern**.

   Der neue Regelsatz wird in der Liste **diesen Regelsatz ausführen** ausgewählt.

6. Wählen Sie **Öffnen** aus, um den neuen Regelsatz im Regelsatz-Editor zu öffnen.

## <a name="rule-precedence"></a>Rangfolge der Regeln

- Wenn dieselbe Regel mindestens zwei Mal in einem Regelsatz mit unterschiedlichen Schweregraden aufgeführt ist, generiert der Compiler einen Fehler. Beispiel:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Wenn dieselbe Regel mindestens zwei Mal in einem Regelsatz mit *demselben* Schweregrad aufgelistet ist, wird im **Fehlerliste** möglicherweise die folgende Warnung angezeigt:

   **CA0063: Fehler beim Laden der Regel Satz Datei " \[ your]. RuleSet" oder einer der abhängigen Regel Satz Dateien. Die Datei entspricht nicht dem Regel Satz Schema.**

- Wenn der Regelsatz mithilfe eines **include** -Tags einen untergeordneten Regelsatz enthält und die untergeordnete und übergeordnete Regel beide die gleiche Regel, aber unterschiedliche Schweregrade, enthält, hat der Schweregrad im übergeordneten Regelsatz Vorrang. Beispiel:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Name und Beschreibung

Um den anzeigen Amen eines Regelsatzes zu ändern, der im Editor geöffnet ist, öffnen Sie das **Eigenschaften** Fenster, indem Sie  >  in der Menüleiste die Option **Eigenschaften Fenster** anzeigen auswählen. Geben Sie den anzeigen Amen in das Feld **Name** ein. Sie können auch eine Beschreibung für den Regelsatz eingeben.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun über einen Regelsatz verfügen, besteht der nächste Schritt in der Anpassung der Regeln durch Hinzufügen oder Entfernen von Regeln oder durch Ändern des schwere Grads von Regelverstößen.

> [!div class="nextstepaction"]
> [Ändern von Regeln im Regelsatz-Editor](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)