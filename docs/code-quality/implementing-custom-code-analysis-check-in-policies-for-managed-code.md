---
title: Eincheck Richtlinien für benutzerdefinierte Code Analyse für verwalteten Code
ms.date: 11/04/2016
description: Erfahren Sie, wie Sie eine angepasste Eincheck Richtlinie für die Code Analyse erstellen. Erfahren Sie, wie Sie sicherstellen, dass verwalteter Code von Visual Studio einer Azure devops-Projekt Richtlinie entspricht.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8e682c3d3312be5c4f4639fc2642a398e321fc78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859878"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementieren von benutzerdefinierten Eincheckrichtlinien für die Codeanalyse für verwalteten Code

Eine Eincheck Richtlinie für die Code Analyse gibt einen Satz von Regeln an, die Mitglieder eines Azure devops-Projekts im Quellcode ausführen müssen, bevor es in die Versionskontrolle eingecheckt wird. Microsoft stellt eine Reihe von Standard *Regelsätzen* bereit, die Code Analyse Regeln in Funktionsbereiche gruppieren. *Regelsätze für benutzerdefinierte Eincheck Richtlinien* geben einen Satz von Code Analyse Regeln an, die für ein projektspezifisch sind. Ein Regelsatz wird in einer RuleSet-Datei gespeichert.

Check-in-Richtlinien werden auf der Azure devops-Projektebene festgelegt und durch den Speicherort einer RuleSet-Datei in der Versions Kontrollstruktur angegeben. Es gibt keine Einschränkungen für den Speicherort der Versionskontrolle des benutzerdefinierten Regelsatzes der Team Richtlinie.

Die Code Analyse wird für die einzelnen Code Projekte im Fenster Eigenschaften für jedes Projekt konfiguriert. Ein benutzerdefinierter Regelsatz für ein Code Projekt wird vom physischen Speicherort der RuleSet-Datei auf dem lokalen Computer angegeben. Wenn eine RuleSet-Datei angegeben wird, die sich auf demselben Laufwerk wie das Code Projekt befindet, verwendet Visual Studio einen relativen Pfad zur Datei in der Projekt Konfiguration.

Eine empfohlene Vorgehensweise zum Erstellen eines benutzerdefinierten Regelsatzes für ein Azure devops-Projekt ist das Speichern der Datei "Check-in Policy. RuleSet" in einem speziellen Ordner, der kein Teil eines Code Projekts ist. Wenn Sie die Datei in einem dedizierten Ordner speichern, können Sie Berechtigungen anwenden, die einschränken, wer die Regeldatei bearbeiten kann. Außerdem können Sie die Verzeichnisstruktur, die das Projekt enthält, problemlos in ein anderes Verzeichnis oder einen anderen Computer verschieben.

## <a name="create-the-project-custom-check-in-rule-set"></a>Erstellen des benutzerdefinierten Eincheck Regelsatzes für das Projekt

Um einen benutzerdefinierten Regelsatz für ein Azure devops-Projekt zu erstellen, erstellen Sie zunächst einen speziellen Ordner für den Eincheck Richtlinien-Regelsatz in **Quellcodeverwaltungs-Explorer**. Anschließend erstellen Sie die Regel Satz Datei und fügen die Datei der Versionskontrolle hinzu. Zum Schluss geben Sie den Regelsatz als Eincheck Richtlinie für die Code Analyse für das Projekt an.

> [!NOTE]
> Zum Erstellen eines Ordners in einem Azure devops-Projekt müssen Sie zuerst das Projektstamm Verzeichnis einem Speicherort auf dem lokalen Computer zuordnen.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>So erstellen Sie den Versions Kontroll Ordner für den Eincheck Richtlinien-Regelsatz

1. Erweitern Sie in Team Explorer den Projekt Knoten, und klicken Sie dann auf **Quell** Code Verwaltung.

2. Klicken Sie im **Ordner** Bereich mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **neuer Ordner**.

3. Klicken Sie im Hauptbereich der Quell Code Verwaltung mit der rechten Maustaste auf **neuer Ordner**, klicken Sie auf **Umbenennen**, und geben Sie einen Namen für den Regelsatz Ordner ein.

### <a name="to-create-the-check-in-policy-rule-set"></a>So erstellen Sie einen Eincheck Richtlinien-Regelsatz

1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Datei**.

2. Klicken Sie in der Liste **Kategorien** auf **Allgemein**.

3. Doppelklicken Sie in der Liste **Vorlagen** auf **Code Analyse-Regelsatz**.

4. [Geben Sie die Regeln](../code-quality/how-to-create-a-custom-rule-set.md) an, die in den Regelsatz eingeschlossen werden sollen, und speichern Sie dann die Regel Satz Datei im Regel Satz Ordner, den Sie erstellt haben.

### <a name="to-add-the-rule-set-file-to-version-control"></a>So fügen Sie die Regel Satz Datei zur Versionskontrolle hinzu

1. Klicken Sie in **Quellcodeverwaltungs-Explorer** mit der rechten Maustaste auf den neuen Ordner, und klicken Sie dann **auf Elemente zum Ordner hinzufügen**.

     Weitere Informationen finden Sie unter [git und Azure Repos](/azure/devops/repos/git/overview?view=vsts&preserve-view=true).

2. Klicken Sie auf die Regel Satz Datei, die Sie erstellt haben, und klicken Sie auf **Fertig** stellen.

     Die Datei wird der Quell Code Verwaltung hinzugefügt und an Sie ausgecheckt.

3. Klicken Sie im Fenster **Quellcodeverwaltungs-Explorer** Details mit der rechten Maustaste auf den Dateinamen, und klicken Sie dann auf **Ausstehende Änderungen einchecken**.

4. Im Dialogfeld **Einchecken** haben Sie die Möglichkeit, einen Kommentar hinzuzufügen, und klicken Sie dann auf **Einchecken**.

    > [!NOTE]
    > Wenn Sie bereits eine Eincheck Richtlinie für die Code Analyse für das Azure devops-Projekt konfiguriert haben und das Eincheck Element erzwingen ausgewählt haben, **um nur Dateien zu enthalten, die Teil der aktuellen** Projekt Mappe sind, wird eine Warnung zu einem Richtlinien Fehler ausgegeben. Wählen Sie im Dialogfeld Richtlinien Fehler die Option **Richtlinien Fehler außer Kraft setzen und Eincheck Vorgang fortsetzen aus**. Fügen Sie einen erforderlichen Kommentar hinzu, und klicken Sie dann auf **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>So geben Sie die Regel Satz Datei als Check-in-Richtlinie an

1. Zeigen Sie im Menü **Team** auf **Projekteinstellungen**, und klicken Sie dann auf **Quell** Code Verwaltung.

2. Klicken Sie auf **Eincheck Richtlinie**, und klicken Sie dann auf **Hinzufügen**.

3. Doppelklicken Sie in der Liste **Eincheck Richtlinie** auf **Code Analyse**, und stellen Sie sicher, dass das Kontrollkästchen **Code Analyse für verwalteten Code erzwingen** aktiviert ist.

4. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf **\<Select Rule Set from Source Control>** .

5. Geben Sie den Pfad der Regel Satz Datei der Eincheck Richtlinie in der Versionskontrolle ein.

     Der Pfad muss mit der folgenden Syntax übereinstimmen:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Sie können den Pfad mithilfe eines der folgenden Verfahren in **Quellcodeverwaltungs-Explorer** kopieren:

    - Klicken Sie im **Ordner** Bereich auf den Ordner, der die Regel Satz Datei enthält. Kopieren Sie den Versions Kontroll Pfad des Ordners, der im Feld **Quelle** angezeigt wird, und geben Sie den Namen der Regel Satz Datei manuell ein.

    - Klicken Sie im Detailfenster mit der rechten Maustaste auf die Regel Satz Datei, und klicken Sie dann auf **Eigenschaften**. Kopieren Sie auf der Registerkarte **Allgemein** den Wert unter **Server Name**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchronisieren von Code Projekten mit dem Eincheck Richtlinien-Regelsatz

Sie geben eine Richtlinien Regel für den Projekt Eincheck Vorgang als Code Analyse-Regelsatz einer Code Projekt Konfiguration im Eigenschaften Dialogfeld des Code Projekts an. Wenn sich der Regelsatz auf dem gleichen Laufwerk wie das Code Projekt befindet, wird ein relativer Pfad verwendet, um den Regelsatz anzugeben, wenn der Pfad aus dem Datei Dialogfeld ausgewählt wird. Der relative Pfad ermöglicht, dass die Projekteigenschaften Einstellungen auf andere Computer übertragbar sind, die ähnliche lokale Versions Kontrollstrukturen verwenden.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>So geben Sie einen Projekt Regelsatz als Regelsatz eines Code Projekts an

1. Rufen Sie ggf. den Regel Satz Ordner und die Datei der Check-in-Richtlinie aus der Versionskontrolle ab.

   Sie können diesen Schritt in **Quellcodeverwaltungs-Explorer** ausführen, indem Sie mit der rechten Maustaste auf den Ordner Regel Satz und dann auf **neueste Version erhalten** klicken.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Code Projekt, und klicken Sie dann auf **Eigenschaften**.

3. **Klicken Sie auf Code Analyse**.

4. Klicken Sie ggf. auf die entsprechenden Optionen in den Listen **Konfiguration** und **Plattform** .

::: moniker range="vs-2017"

5. Wenn Sie die Code Analyse bei jedem Erstellen des Code Projekts mithilfe der angegebenen Konfiguration ausführen möchten, wählen Sie **Code Analyse beim Build aktivieren aus**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Um die Code Analyse jedes Mal auszuführen, wenn das Code Projekt mithilfe der angegebenen Konfiguration erstellt wird, wählen Sie im Abschnitt **binäre Analysen** die Option **im Build ausführen** aus.

::: moniker-end

6. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf **\<Browse>** .

8. Wählen Sie die lokale Version der Regel Satz Datei für die Eincheck Richtlinie aus.
