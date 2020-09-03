---
title: Arbeiten im Regelsatz-Editor für die Code Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621506"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Arbeiten mit dem Regelsatz-Editor für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Regelsatz-Editor für die Code Analyse können Sie die Regeln angeben, die in einem benutzerdefinierten Regelsatz enthalten sind, und die Aktion angeben. Sie können auch angeben, welche Aktion ausgeführt werden soll, wenn die Code Analyse einen Verstoß gegen die Regel trifft.

|Aktion|Beschreibung|
|------------|-----------------|
|**Warning**|Generiert im **Fehlerliste** Fenster eine Warnung.|
|**Fehler**|Generiert einen Fehler im Fenster **Fehlerliste** .|
|**None**|Deaktiviert die Regel.|

 Der Editor zeigt die Regeln in einer Baumstruktur an, in der die Regeln nach einem von Ihnen angegebenen Regelsatz Feld gruppiert werden. Um Regeln zu einem Regelsatz hinzuzufügen oder daraus zu entfernen, führen Sie einen oder mehrere der folgenden Schritte aus:

- Aktivieren oder deaktivieren Sie das Kontrollkästchen des Knotens Gruppe, um alle Regeln in der Gruppe hinzuzufügen oder zu entfernen. Wenn Sie eine Gruppe auswählen, werden alle Regeln auf die Aktion " **Warnung** " festgelegt.

- Klicken Sie auf das Feld **Aktion** einer Gruppe, und geben Sie dann die Aktion an, die auf alle Regeln in der Gruppe angewendet werden soll.

- Aktivieren oder deaktivieren Sie das Kontrollkästchen für eine einzelne Regel. Wenn Sie das Kontrollkästchen für eine Regel aktivieren, wird die Regel auf die Warnungs Aktion festgelegt.

## <a name="rule-set-editor-toolbar"></a>Symbolleiste des Regelsatz-Editors
 Mithilfe der Symbolleiste des Regelsatz-Editors können Sie die Daten gruppieren, Filtern und Durchsuchen, die im Regel Satz Raster angezeigt werden.

 In der folgenden Tabelle werden die Steuerelemente auf der Symbolleiste des Regelsatz-Editors beschrieben.

|ToolBar-Steuerelement|Beschreibung|
|---------------------|-----------------|
|**Alle erweitern**|Zeigt die Regeln in allen Gruppen an.|
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
 Regelsatz-Felder zeigen Informationen zu einem Regelsatz an und können verwendet werden, um die Regel Liste zu sortieren und zu gruppieren. Um Felder anzuzeigen oder auszublenden, klicken Sie auf der Symbolleiste des Regelsatz-Editors auf **Spaltenoptionen** , und aktivieren oder deaktivieren Sie dann die Kontrollkästchen der Felder, die angezeigt oder ausgeblendet werden sollen.

 In der folgenden Tabelle werden die Felder eines Regelsatzes beschrieben.

|Feld|BESCHREIBUNG|
|-----------|-----------------|
|**ID**|Der Bezeichner der Regel.|
|**Kategorie**|Zusätzlich zur Mitgliedschaft in Regelsätzen werden Code Analyse Regeln auch nach Kategorie gruppiert. Weitere Informationen finden Sie unter [Code Analyse für Warnungen für verwalteten Code](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Der Titel der Regel.|
|**Namespace**|Der Namespace der Regel.|
|**Zieltyp**|Gibt an, ob die Regel für systemeigenen, verwalteten oder Datenbankcode gilt.|
|**Aktion**|Die Aktion, die ausgeführt wird, wenn die Regel in einer Code Analyse ausgeführt wird.<br /><br /> **Warnung** : generiert eine Warnung.<br /><br /> **Fehler** -generiert einen Fehler.<br /><br /> **Keine** : deaktiviert die Regel.<br /><br /> Sie können das Feld "Aktion" bearbeiten. Das Festlegen des Werts auf "None" entspricht dem Deaktivieren des Kontrollkästchens für die Regel.|
|**Quell Regelsätze**|Der Regelsatz, der die Regel enthält.|

## <a name="sorting-and-filtering-rule-sets"></a>Sortieren und Filtern von Regelsätzen
 In den Spalten Headern des Regel Satz-Rasters können Sie die Regeln nach den Werten des Felds sortieren und filtern.

- Um die Regelsatz Listen zu sortieren, klicken Sie auf den Spaltenheader des Felds, nach dem sortiert werden soll. Wenn die Regelsätze gruppiert sind, wird jede Gruppe einzeln sortiert.

- Wenn Sie die Regelsätze nach dem Wert eines Felds filtern möchten, klicken Sie auf die Schaltfläche Filter in der Spaltenüberschrift des Felds, nach dem Sie filtern möchten. Aktivieren Sie die Kontrollkästchen der Werte, die Sie anzeigen möchten, und deaktivieren Sie die Kontrollkästchen der Werte, die Sie ausblenden möchten.
