---
title: Write-Aktivität-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4f656578526879774e698523239d5a9b2b14ccd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657531"
---
# <a name="writeline-activity-designer"></a>WriteLine-Aktivitätsdesigner
Der **beschreibbare** Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.WriteLine> .

## <a name="the-writeline-activity"></a>Die WriteLine-Aktivität
 Die <xref:System.Activities.Statements.WriteLine>-Aktivität schreibt Text in ein angegebenes <xref:System.IO.TextWriter>-Objekt. Wenn kein <xref:System.IO.TextWriter> angegeben wird, schreibt <xref:System.Activities.Statements.WriteLine> den Text in die Konsole.

### <a name="using-the-writeline-activity-designer"></a>Verwenden des WriteLine-Aktivitätsdesigners
 Der **beschreibbare** Aktivitäts Designer befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie in auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **beschreibbare** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Daraufhin wird eine <xref:System.Activities.Statements.WriteLine>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert WriteLine erstellt. Das- <xref:System.Activities.Activity.DisplayName%2A> Objekt kann in der Kopfzeile des **Write** -Aktivität-Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-writeline-properties"></a>Die WriteLine-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.WriteLine>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.WriteLine>-Aktivität. Der Standardwert lautet WriteLine. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Falsch|Der zu schreibende Text. Um die-Eigenschaft festzulegen, geben Sie im **Textfeld** im **Schreib** Weise-Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Falsch|Die <xref:System.IO.TextWriter>-Instanz, an die die <xref:System.Activities.Statements.WriteLine>-Aktivität den <xref:System.Activities.Statements.WriteLine.Text%2A>-Text ausgibt. Der Standardwert ist die Konsole.|

## <a name="see-also"></a>Weitere Informationen
 [Primitives](../workflow-designer/primitives-activity-designers.md) Die Methode " [Verzögerungs](../workflow-designer/delay-activity-designer.md) [Methode](../workflow-designer/invokemethod-activity-designer.md) [zuweisen](../workflow-designer/assign-activity-designer.md) "