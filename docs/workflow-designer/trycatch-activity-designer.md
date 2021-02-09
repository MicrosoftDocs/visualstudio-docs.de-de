---
title: Workflow-Designer-trycatch-Aktivitäts Designer
description: Erfahren Sie mehr über die trycatch-Aktivität und wie Sie den trycatch-Aktivitäts Designer verwenden können, um eine trycatch-Aktivität zu erstellen und zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23d9f1b0037600c6612a413cce7b089f6adbc7aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889303"
---
# <a name="trycatch-activity-designer"></a>TryCatch-Aktivitätsdesigner

Der **trycatch** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.TryCatch> .

## <a name="the-trycatch-activity"></a>Die TryCatch-Aktivität
 Die <xref:System.Activities.Statements.TryCatch> -Aktivität enthält eine <xref:System.Activities.Statements.TryCatch.Try%2A> -Aktivität, eine Auflistung von **\<TException> catch** -und eine- <xref:System.Activities.Statements.TryCatch.Finally%2A> Aktivität. Eine <xref:System.Activities.Statements.Catch%601> des Typs **TException** enthält eine <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> und eine <xref:System.Activities.Statements.Catch%601.Action%2A> . Zusammen werden diese verwendet, um einen typischen ausnahmebasierten Fehlerbehandlungsmechanismus zu implementieren. Eine <xref:System.Activities.Statements.TryCatch>-Aktivität versucht, die zugehörige <xref:System.Activities.Statements.TryCatch.Try%2A>-Aktivität auszuführen. Wenn die- <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivität eine Ausnahme auslöst, <xref:System.Activities.Statements.TryCatch> verwendet die-Aktivität die Catch- **<\> TException** -Auflistung, um die Ausnahme abzugleichen. Wenn eine Übereinstimmung vorliegt, wird die <xref:System.Activities.Statements.Catch%601.Action%2A> der entsprechenden **Catch \<TException>** -Anweisung ausgeführt, die als Fehler Behandlungs Logik für die Ausnahme fungiert. Wenn die Aktivitäten im Abschnitt <xref:System.Activities.Statements.TryCatch.Try%2A> erfolgreich abgeschlossen werden oder die Aktivitäten in <xref:System.Activities.Statements.TryCatch.Catches%2A> erfolgreich abgeschlossen werden, führt die <xref:System.Activities.Statements.TryCatch>-Aktivität die zugehörige <xref:System.Activities.Statements.TryCatch.Finally%2A>-Aktivität aus. Weitere Informationen finden Sie unter [Windows Workflow-Ausnahmen](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Verwenden des TryCatch-Aktivitätsdesigners

Greifen Sie in der Kategorie **Fehlerbehandlung** der **Toolbox** auf den **trycatch** -Aktivitäts Designer zu.

Der **trycatch** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Hierdurch erstellen Sie eine <xref:System.Activities.Statements.TryCatch>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert TryCatch. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **trycatch** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen auf der Oberfläche des **trycatch** -Aktivitäts Designers bearbeitet werden.

Klicken Sie in der rechten oberen Ecke des **trycatch** -Designers auf die Schaltfläche erweitern, um die Felder **ausprobieren**, **fängt** und **schließlich** in der erweiterten Ansicht anzuzeigen. Um einen catch hinzuzufügen, klicken Sie auf die Schaltfläche **neuen Catch hinzufügen** im **trycatch** -Designer. Die Schaltfläche nimmt die Form eines Kombinationsfelds an. Wählen Sie einen Ausnahmetyp aus, und drücken Sie die EINGABETASTE, um den Catch hinzuzufügen. Nach dem Hinzufügen eines **catch**-Blocks wird der catch-Bereich erweitert, und eine Aktivität kann im catch abgelegt werden, um die Ausführungs Logik für den catch zu definieren. Auf der rechten Seite des erweiterten Catch-Bereichs befindet sich ein Textfeld. In dieses Textfeld können Sie den Namen einer Ausnahmevariablen eingeben. Die Exception-Variable kann nur für Aktivitäten innerhalb desselben **catch** verwendet werden.

Der **trycatch** -Designer unterstützt das Bearbeiten von **catch** nicht. Wenn Sie den Ausnahmetyp ändern möchten, müssen Sie den **catch** löschen und einen neuen hinzufügen. Ein **catch** kann gelöscht werden, indem Sie ihn auswählen und löschen oder indem Sie im Kontextmenü **Löschen** auswählen, auf das Sie mit der rechten Maustaste klicken.

### <a name="the-trycatch-properties"></a>Die TryCatch-Eigenschaften

In der folgenden Tabelle sind die Eigenschaften aufgeführt, <xref:System.Activities.Statements.TryCatch> und es wird beschrieben, wie Sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.TryCatch>-Aktivität an. Der Standardwert ist TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Falsch|Die Aktivität wird erstmalig ausgeführt wird, wenn <xref:System.Activities.Statements.TryCatch> ausgeführt wird.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Falsch|Die Auflistung der **catch** -Elemente, die geprüft werden soll, wenn die <xref:System.Activities.Statements.TryCatch.Try%2A> Aktivität eine Ausnahme auslöst.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>-Block hinzufügen.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Falsch|Die Aktivität, die ausgeführt werden soll, wenn die Ausführung von <xref:System.Activities.Statements.TryCatch.Try%2A> und aller erforderlichen Aktivitäten in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung abgeschlossen wurde.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>-Block hinzufügen.|

## <a name="see-also"></a>Weitere Informationen

- [Sammlung](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
