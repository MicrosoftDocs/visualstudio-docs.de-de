---
title: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises
description: Weitere Informationen finden Sie unter Hinzufügen, aktualisieren oder Entfernen eines Windows Communication Foundation (WCF)-Datendienst Verweises.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6e6c289038c3f8cb9d1586ae4a1f7a84b563239f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436432"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Vorgehensweise: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises

::: moniker range="vs-2017"
Ein *Dienst Verweis* ermöglicht einem Projekt den Zugriff auf eine oder mehrere [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Verwenden Sie das Dialogfeld **Dienstverweis hinzufügen** , um [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in der aktuellen Projekt Mappe lokal, in einem lokalen Netzwerk oder im Internet zu suchen.
::: moniker-end
::: moniker range=">=vs-2019"
Mit dem Knoten **verbundene Dienste** in **Projektmappen-Explorer** können Sie auf den **Microsoft WCF Web Service Reference Provider** zugreifen, mit dem Sie Windows Communication Foundation (WCF)-Datendienst Verweise verwalten können.
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Hinzufügen eines WCF-Dienst Verweises

### <a name="to-add-a-reference-to-an-external-service"></a>So fügen Sie einen Verweis auf einen externen Dienst hinzu

::: moniker range="vs-2017"

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Namen des Projekts, dem Sie den Dienst hinzufügen möchten, und klicken Sie dann auf **Dienstverweis hinzufügen**.

   Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.

1. Geben Sie im Feld **Adresse** die URL für den Dienst ein, und klicken Sie dann auf **suchen, um** nach dem Dienst zu suchen. Wenn der Dienst Benutzernamen-und Kenn Wort Sicherheit implementiert, werden Sie möglicherweise aufgefordert, einen Benutzernamen und ein Kennwort einzugeben.

    > [!NOTE]
    > Sie sollten nur auf Dienste aus einer vertrauenswürdigen Quelle verweisen. Wenn Sie Verweise aus nicht vertrauenswürdigen Quellen hinzufügen, hat das möglicherweise Auswirkungen auf die Sicherheit.

     Sie können auch die URL aus der **Adress** Liste auswählen, in der die vorherigen 15 URLs gespeichert sind, bei denen gültige Dienst Metadaten gefunden wurden.

     Eine Statusanzeige wird angezeigt, wenn die Suche ausgeführt wird. Sie können die Suche jederzeit abbrechen, indem Sie auf " **Abbrechen** " klicken.

1. Erweitern Sie in der Liste **Dienste** den Knoten für den Dienst, den Sie verwenden möchten, und wählen Sie eine Entitätenmenge aus.

1. Geben Sie im Feld **Namespace** den Namespace ein, der für den Verweis verwendet werden soll.

1. Klicken Sie auf **OK** , um dem Projekt den Verweis hinzuzufügen.

     Es wird ein Dienst Client (Proxy) generiert, und Metadaten, die den Dienst beschreiben, werden der *app.config* Datei hinzugefügt.
::: moniker-end
::: moniker range=">=vs-2019"
1. Doppelklicken oder tippen Sie in **Projektmappen-Explorer** auf den Knoten **verbundene Dienste** .

   Die Registerkarte **Dienste konfigurieren** wird geöffnet.

1. Wählen Sie **Microsoft WCF Web Service Reference Provider** aus.

   Das Dialogfeld **WCF-Webdienst Verweis konfigurieren** wird angezeigt.

   ![Screenshot des Dialog Felds "WCF-Webdienst Anbieter"](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. Geben Sie im Feld **URI** die URL für den Dienst ein, **und klicken Sie dann auf Suchen** , um nach dem Dienst zu suchen. Wenn der Dienst Benutzernamen-und Kenn Wort Sicherheit implementiert, werden Sie möglicherweise aufgefordert, einen Benutzernamen und ein Kennwort einzugeben.

    > [!NOTE]
    > Sie sollten nur auf Dienste aus einer vertrauenswürdigen Quelle verweisen. Wenn Sie Verweise aus nicht vertrauenswürdigen Quellen hinzufügen, hat das möglicherweise Auswirkungen auf die Sicherheit.

     Sie können auch die URL aus der **URI** -Liste auswählen, in der die vorherigen 15 URLs gespeichert sind, bei denen gültige Dienst Metadaten gefunden wurden.

     Eine Statusanzeige wird angezeigt, wenn die Suche ausgeführt wird. Sie können die Suche jederzeit abbrechen, indem Sie auf " **Abbrechen** " klicken.

1. Erweitern Sie in der Liste **Dienste** den Knoten für den Dienst, den Sie verwenden möchten, und wählen Sie eine Entitätenmenge aus.

1. Geben Sie im Feld **Namespace** den Namespace ein, der für den Verweis verwendet werden soll.

1. Klicken Sie auf **Fertig** stellen, um den Verweis auf das Projekt hinzuzufügen.

     Es wird ein Dienst Client (Proxy) generiert, und Metadaten, die den Dienst beschreiben, werden der *app.config* Datei hinzugefügt.

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>So fügen Sie einen Verweis auf einen Dienst in der aktuellen Projekt Mappe hinzu

::: moniker range="vs-2017"

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Namen des Projekts, dem Sie den Dienst hinzufügen möchten, und klicken Sie dann auf **Dienstverweis hinzufügen**.

    Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.

1. Klicken Sie auf **ermitteln**.

    Alle Dienste (sowohl [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] als auch WCF-Dienste) in der aktuellen Projekt Mappe werden der Liste der **Dienste** hinzugefügt.

1. Erweitern Sie in der Liste **Dienste** den Knoten für den Dienst, den Sie verwenden möchten, und wählen Sie eine Entitätenmenge aus.

1. Geben Sie im Feld **Namespace** den Namespace ein, der für den Verweis verwendet werden soll.

1. Klicken Sie auf **OK** , um dem Projekt den Verweis hinzuzufügen.

    Ein Dienst Client (Proxy) generiert, und Metadaten, die den Dienst beschreiben, werden der *app.config* Datei hinzugefügt.
::: moniker-end
::: moniker range=">=vs-2019"
1. Doppelklicken oder tippen Sie in **Projektmappen-Explorer** auf den Knoten **verbundene Dienste** . 

   Die Registerkarte **Dienste konfigurieren** wird geöffnet.

1. Wählen Sie **Microsoft WCF Web Service Reference Provider** aus.

   Das Dialogfeld **WCF-Webdienst Verweis konfigurieren** wird angezeigt.

1. Klicken Sie auf **ermitteln**.

    Alle Dienste (sowohl [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] als auch WCF-Dienste) in der aktuellen Projekt Mappe werden der Liste der **Dienste** hinzugefügt.

1. Erweitern Sie in der Liste **Dienste** den Knoten für den Dienst, den Sie verwenden möchten, und wählen Sie eine Entitätenmenge aus.

1. Geben Sie im Feld **Namespace** den Namespace ein, der für den Verweis verwendet werden soll.

1. Klicken Sie auf **Fertig** stellen, um den Verweis auf das Projekt hinzuzufügen.

    Ein Dienst Client (Proxy) generiert, und Metadaten, die den Dienst beschreiben, werden der *app.config* Datei hinzugefügt.

::: moniker-end

## <a name="update-a-service-reference"></a>Aktualisieren eines Dienst Verweises

Der Entity Data Model für eine [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ändert sich manchmal. Wenn dies der Fall ist, müssen Sie den Dienst Verweis aktualisieren.

### <a name="to-update-a-service-reference"></a>So aktualisieren Sie einen Dienst Verweis

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Dienst Verweis, und klicken Sie dann auf **Dienst Verweis aktualisieren**.

     Ein Status Dialogfeld wird angezeigt, während der Verweis vom ursprünglichen Speicherort aus aktualisiert wird, und der Dienst Client wird erneut generiert, um Änderungen an den Metadaten widerzuspiegeln.

## <a name="remove-a-service-reference"></a>Entfernen eines Dienst Verweises

Wenn ein Dienst Verweis nicht mehr verwendet wird, können Sie ihn aus der Projekt Mappe entfernen.

### <a name="to-remove-a-service-reference"></a>So entfernen Sie einen Dienst Verweis

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Dienst Verweis, und klicken Sie dann auf **Löschen**.

     Der Dienst Client wird aus der Projekt Mappe entfernt, und die Metadaten, die den Dienst beschreiben, werden aus der *app.config* Datei entfernt.

    > [!NOTE]
    > Jeglicher Code, der auf den Dienst Verweis verweist, muss manuell entfernt werden.

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
