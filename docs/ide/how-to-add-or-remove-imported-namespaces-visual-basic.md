---
title: Hinzufügen und Entfernen von importierten Namespaces (Visual Basic)
description: Erfahren Sie, wie Sie importierte Namespaces hinzufügen oder entfernen und Benutzerimporte hinzufügen oder entfernen.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: how-to
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18e3010e9798f3c056afd5ffc7964ace3f734f53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970841"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Vorgehensweise: Hinzufügen oder Entfernen von importierten Namespaces (Visual Basic)

Das Importieren eines Namespace ermöglicht Ihnen die Verwendung von Elementen aus diesem Namespace in Ihrem Code. Es ist nicht notwendig, das Element vollzuqualifizieren. Wenn Sie beispielsweise in der Klasse `System.Messaging.MessageQueue` auf die Methode `Create` zugreifen möchten, können Sie den `System.Messaging`-Namespace importieren und auf das benötigte Element im Code als `MessageQueue.Create` verweisen.

Importierte Namespaces werden auf der Seite **Verweise** des **Projekt-Designers** verwaltet. Die Importe, die Sie in diesem Dialogfeld angeben, werden direkt an den Compiler (*/imports*) weitergegeben und gelten für alle Dateien in Ihrem Projekt. Verwenden Sie die `Imports`-Anweisung, um einen Namespace in einer einzelnen Quellcodedatei zu verwenden.

### <a name="to-add-an-imported-namespace"></a>So fügen Sie einen importierten Namespace hinzu

1. Doppelklicken Sie im **Projektmappen-Explorer** auf den Knoten **Mein Projekt** für das Projekt.

2. Klicken Sie im **Projekt-Designer** auf die Registerkarte **Verweise**.

3. Aktivieren Sie in der Liste **Importierte Namespaces** das Kontrollkästchen für den Namespace, den Sie hinzufügen möchten.

    > [!NOTE]
    > Der Namespace muss sich in einer Komponente befinden, auf die verwiesen wird, damit er importiert werden kann. Wenn der Namespace nicht in der Liste angezeigt wird, müssen Sie einen Verweis auf die Komponente hinzufügen, in der er enthalten ist. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>So entfernen Sie einen importierten Namespace

1. Doppelklicken Sie im **Projektmappen-Explorer** auf den Knoten **Mein Projekt** für das Projekt.

2. Klicken Sie im **Projekt-Designer** auf die Registerkarte **Verweise**.

3. Deaktivieren Sie in der Liste **Importierte Namespaces** das Kontrollkästchen für den Namespace, den Sie entfernen möchten.

## <a name="user-imports"></a>Benutzerimporte
Mithilfe von Benutzerimporten können Sie anstatt des gesamten Namespace eine bestimmte Klasse innerhalb eines Namespace importieren. Beispiel: Ihre Anwendung verfügt über einen Import für den <xref:System.Diagnostics>-Namespace, Sie sind aber nur interessiert an der `Debug`-Klasse innerhalb dieses Namespace. Sie können <xref:System.Diagnostics.Debug> als Benutzerimport definieren und anschließend den Import für <xref:System.Diagnostics> löschen.

Wenn Sie Ihre Meinung später ändern und feststellen, dass Sie doch die Klasse `EventLog` benötigt hätten, können Sie <xref:System.Diagnostics.EventLog> als Benutzerimport eingeben und <xref:System.Diagnostics.Debug> mithilfe der Updatefunktionalität überschreiben.

### <a name="to-add-a-user-import"></a>So fügen Sie einen Benutzerimport hinzu

1. Doppelklicken Sie im **Projektmappen-Explorer** auf den Knoten **Mein Projekt** für das Projekt.

2. Klicken Sie im **Projekt-Designer** auf die Registerkarte **Verweise**.

3. Geben Sie im Textfeld unter der Liste **Importierte Namespaces** den vollständigen Namen des Namespace inklusive Stammnamespace ein, den Sie importieren möchten.

4. Klicken Sie auf die Schaltfläche **Benutzerimport hinzufügen**, um den Namespace der Liste **Importierte Namespaces** hinzuzufügen.

    > [!NOTE]
    > Die Schaltfläche **Benutzerimport hinzufügen** wird deaktiviert, wenn der Namespace mit einem Namespace übereinstimmt, der sich bereits auf der Liste befindet, da Sie einen Import nicht zweimal hinzufügen können.

### <a name="to-update-a-user-import"></a>So aktualisieren Sie einen Benutzerimport

1. Doppelklicken Sie im **Projektmappen-Explorer** auf den Knoten **Mein Projekt** für das Projekt.

2. Klicken Sie im **Projekt-Designer** auf die Registerkarte **Verweise**.

3. Wählen Sie in der Liste **Importierte Namespaces** den Namespace aus, den Sie ändern möchten.

4. Geben Sie im Textfeld unter der Liste **Importierte Namespaces** den Namen für den neuen Namespace ein.

5. Klicken Sie auf die Schaltfläche **Benutzerimport aktualisieren**, um den Namespace in der Liste **Importierte Namespaces** zu aktualisieren.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)
