---
title: Dialog Feld "Auflistungs-Editor für Workflow-Designer"
description: Erfahren Sie, wie Sie das Dialogfeld typauflistungs-Editor verwenden können, um den Sende-und Empfangs Aktivitäten bekannte Typen hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8f194ee792f2a60df71a78af6f41e45aaac91da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875262"
---
# <a name="type-collection-editor-dialog-box"></a>Typauflistungs-Editor (Dialogfeld)

Das Dialogfeld typauflistungs- **Editor** wird verwendet, um den **Sende** -und **Empfangs** Aktivitäten bekannte Typen hinzuzufügen. Dieses Dialogfeld wird auch verwendet, um der **InvokeMethod** -Aktivität generische Typargumente hinzuzufügen. Wenn für die **Sende** -und **Empfangs** Aktivitäten verwendet wird, um bekannte Typen hinzuzufügen, muss im Dialogfeld typauflistungs- **Editor** die typergänzungen eindeutig sein. Wenn ein doppelter Typ hinzugefügt und für die Änderung ein Commit ausgeführt wird, indem Sie auf **OK** klicken, wird eine Fehlermeldung zurückgegeben. Bei Verwendung für die **InvokeMethod** -Aktivität zum Hinzufügen von generischen Typargumenten ermöglicht das Dialogfeld typauflistungs- **Editor** das Hinzufügen doppelter Typen.

Weitere Informationen finden Sie unter [Data Contract Known Types](/dotnet/framework/wcf/feature-details/data-contract-known-types).

In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Typsammlung** beschrieben.

|Benutzeroberflächenelement|BESCHREIBUNG|
|-|-----------------|
|**Type List**|Eine Liste der Typen, die hinzugefügt oder entfernt wurden.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>So öffnen Sie den Typauflistungs-Editor für die Send- und die Receive-Aktivität

1. Wählen Sie die **Sende** -oder **Empfangs** Aktivität in der Entwurfs Ansicht aus.

2. Drücken Sie **F4** , um das **Eigenschaften** Fenster zu aktivieren.

3. Klicken Sie im **Eigenschaften** Fenster neben der **KnownTypes** -Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>So öffnen Sie den Typauflistungs-Editor für die InvokeMethod-Aktivität

1. Wählen Sie die **InvokeMethod** -Aktivität in der Entwurfs Ansicht aus.

2. Drücken Sie **F4** , um das **Eigenschaften** Fenster zu aktivieren.

3. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche mit den Auslassungs Punkten neben der Eigenschaft **genericTypeArguments** .
