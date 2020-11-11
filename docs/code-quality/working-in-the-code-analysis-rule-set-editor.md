---
title: Verwenden des Regelsatz-Editors für die Codeanalyse
ms.date: 04/04/2018
description: Erfahren Sie, wie Sie Regelsätze in Visual Studio bearbeiten und anzeigen. Weitere Informationen finden Sie unter Festlegen des Regel schwere Grads, angeben von Regeln in einer benutzerdefinierten Gruppe und Anpassen der Daten im Regelsatz-Raster.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d2703972658aace438ab235d469eed3e0644c06
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436822"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Verwenden des Regelsatz-Editors für die Code Analyse

Mit dem Regelsatz-Editor für die Code Analyse können Sie die Regeln angeben, die in einem benutzerdefinierten Regelsatz enthalten sind, und den Schweregrad von Regelverstößen festlegen.

In der folgenden Tabelle werden die Schweregrad Optionen angezeigt:

|Aktion (Schweregrad)|BESCHREIBUNG|
|-|-|
|Warnung|Generiert eine Warnung in der **Fehlerliste** und auch zur Buildzeit.|
|Fehler|Generiert einen Fehler in der **Fehlerliste** und auch zur Buildzeit.|
|Info|Generiert eine Meldung in der **Fehlerliste**.|
|Ausgeblendet|Der Verstoß ist für den Benutzer nicht sichtbar. Die IDE wird jedoch über den Verstoß benachrichtigt.|
|Keine|Die Regel wird unterdrückt. Das Verhalten entspricht dem, wenn die Regel aus dem Regelsatz entfernt wurde.|

Der Editor zeigt die Regeln in einer Baumstruktur an, in der die Regeln nach einem von Ihnen angegebenen Regelsatz Feld gruppiert werden. Um Regeln zu einem Regelsatz hinzuzufügen oder daraus zu entfernen, führen Sie einen oder mehrere der folgenden Schritte aus:

- Aktivieren oder deaktivieren Sie das Kontrollkästchen des Knotens Gruppe, um alle Regeln in der Gruppe hinzuzufügen oder zu entfernen. Wenn Sie eine Gruppe auswählen, werden alle Regeln auf die Aktion " **Warnung** " festgelegt.

   > [!TIP]
   > Sie können die Gruppierung von Regeln in der Dropdown- **Gruppe gruppieren nach** ändern.

- Klicken Sie auf das Feld **Aktion** einer Gruppe, und geben Sie die Aktion an, die auf alle Regeln in der Gruppe angewendet werden soll.

- Aktivieren oder deaktivieren Sie das Kontrollkästchen für eine einzelne Regel. Wenn Sie das Kontrollkästchen für eine Regel aktivieren, wird die Regel auf die **Warnungs** Aktion festgelegt.

## <a name="toolbar"></a>Symbolleiste

Mithilfe der Symbolleiste des Regelsatz-Editors können Sie die Daten gruppieren, Filtern und Durchsuchen, die im Regel Satz Raster angezeigt werden.

In der folgenden Tabelle werden die Steuerelemente auf der Symbolleiste des Regelsatz-Editors beschrieben.

|ToolBar-Steuerelement|BESCHREIBUNG|
|---------------------|-----------------|
|**Alle aufklappen**|Zeigt die Regeln in allen Gruppen an.|
|**Alle reduzieren**|Blendet die Regeln in allen Gruppen aus.|
|**Gruppieren nach**|Gibt das Feld an, nach dem Regeln gruppiert werden. Klicken Sie **\<None>** hierauf, um die Regeln ohne Gruppen anzuzeigen.|
|**Spaltenoptionen**|Gibt die anzuzeigenden Regel Felder an.|
|**Regeln ausblenden, die nicht für die aktuelle Projekt Mappe gelten**|Zeigt Regeln an, die nicht denselben Zieltyp wie die Projekt Mappe haben, oder blendet sie aus.|
|**Regeln anzeigen, die Code Analysefehler generieren können**|Blendet Regeln ein oder aus, denen die Fehler Aktion zugewiesen wird.|
|**Regeln anzeigen, die Code Analyse Warnungen generieren können**|Blendet Regeln ein oder aus, denen die Aktion "Warnung" zugewiesen ist.|
|**Nicht aktivierte Regeln anzeigen**|Blendet Regeln ein oder aus, denen die Aktion keine zugewiesen wird.|
|**Untergeordnete Regelsätze hinzufügen oder entfernen**|Fügt die Regeln in den ausgewählten Regelsätzen hinzu oder entfernt Sie.|
|**Such Regeln**|Durchsucht alle Feldwerte nach der angegebenen Zeichenfolge.|

## <a name="rule-set-fields"></a>Regelsatz-Felder

Regelsatz-Felder zeigen Informationen zu einem Regelsatz an und können verwendet werden, um die Regel Liste zu sortieren und zu gruppieren. Um Felder anzuzeigen oder auszublenden, wählen Sie auf der Symbolleiste des Regelsatz-Editors **Spaltenoptionen** aus, und aktivieren oder deaktivieren Sie dann die Kontrollkästchen der Felder, die angezeigt oder ausgeblendet werden sollen.

In der folgenden Tabelle werden die Felder eines Regelsatzes beschrieben:

|Feld|BESCHREIBUNG|
|-----------|-----------------|
|**ID**|Der Bezeichner der Regel.|
|**Kategorie**|Zusätzlich zur Mitgliedschaft in Regelsätzen werden Code Analyse Regeln auch nach Kategorie gruppiert. Weitere Informationen finden Sie unter [Code Analyse Warnungen](/dotnet/fundamentals/code-analysis/quality-rules/index).|
|**Name**|Der Titel der Regel.|
|**Namespace**|Der Namespace der Regel.|
|**Zieltyp**|Gibt an, ob die Regel für systemeigenen, verwalteten oder Datenbankcode gilt.|
|**Aktion**|Die Aktion, die ausgeführt wird, wenn die Regel in einer Code Analyse ausgeführt wird. Sie können das Feld " **Aktion** " bearbeiten.|
|**Quell Regelsätze**|Der Regelsatz, der die Regel enthält.|

## <a name="sort-and-filter-rule-sets"></a>Sortieren und Filtern von Regelsätzen

In den Spalten Headern des Regel Satz-Rasters können Sie die Regeln nach den Werten des Felds sortieren und filtern.

- Wählen Sie zum Sortieren der Regelsatz Listen die Spaltenüberschrift des Felds aus, nach dem sortiert werden soll. Wenn die Regelsätze gruppiert sind, wird jede Gruppe einzeln sortiert.

- Wenn Sie die Regelsätze nach dem Wert eines Felds filtern möchten, wählen Sie die Filter Schaltfläche in der Spaltenüberschrift des Felds aus, nach dem Sie filtern möchten. Aktivieren Sie die Kontrollkästchen der Werte, die Sie anzeigen möchten, und deaktivieren Sie die Kontrollkästchen der Werte, die Sie ausblenden möchten.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines benutzerdefinierten Regelsatzes](../code-quality/how-to-create-a-custom-rule-set.md)
