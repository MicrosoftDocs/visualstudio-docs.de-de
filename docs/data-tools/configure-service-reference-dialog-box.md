---
title: Dienstverweis konfigurieren (Dialogfeld)
description: Verwenden Sie das Dialogfeld Dienst Verweis konfigurieren in Visual Studio, um das Verhalten der Windows Communication Foundation (WCF)-Dienste zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1dc1d82b0267e5e0655f3ebef8eb08806ad319a8
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518725"
---
# <a name="configure-service-reference-dialog-box"></a>Dienstverweis konfigurieren (Dialogfeld)

Im Dialogfeld **Dienst Verweis konfigurieren** können Sie das Verhalten der Windows Communication Foundation (WCF)-Dienste konfigurieren.

Klicken Sie mit der rechten Maustaste auf einen Dienstverweis im **Projektmappen-Explorer** , und wählen Sie **Dienstverweis konfigurieren** aus, um auf das Dialogfeld **Dienstverweis konfigurieren** zuzugreifen. Sie können auch auf das Dialogfeld zugreifen, indem Sie im Dialogfeld **Dienstverweis hinzufügen** auf die Schaltfläche **Erweitert** klicken.

## <a name="task-list"></a>Aufgabenliste

- Geben Sie zum Ändern der Adresse, unter der ein WCF-Dienst gehostet wird, die neue Adresse in das Feld **Adresse** ein.

- Wählen Sie zum Ändern der Zugriffsebene für Klassen in einem WCF-Client ein Zugriffsebenenschlüsselwort in der Liste **Zugriffsebene für generierte Klassen** aus.

- Aktivieren Sie zum asynchronen Aufrufen der Methoden eines WCF-Diensts das Kontrollkästchen **Asynchrone Vorgänge generieren**.

- Aktivieren Sie zum Generieren von Nachrichtenvertragstypen in einem WCF-Client das Kontrollkästchen **Meldungsverträge immer generieren**.

- Wählen Sie die Typen aus den Listen **Sammlungstyp** und **Wörterbuchsammlungstyp** aus, um Listen- oder Wörterbuchsammlungstypen für einen WCF-Client anzugeben.

- Deaktivieren Sie das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden** , um die Typfreigabe zu deaktivieren. Aktivieren Sie zum Aktivieren der Typfreigabe für eine Teilmenge an referenzierten Assemblys das Kontrollkästchen **Typen in Assemblys, auf die verwiesen wird, wiederverwenden** , klicken Sie auf **Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden** , und wählen Sie die gewünschten Verweise in der Liste **Assemblys, auf die verwiesen wird** aus.

## <a name="uielement-list"></a>UIElement-Liste

**Adresse**

Aktualisiert die Webadresse, in der ein Dienst Verweis nach einem Dienst sucht. Während der Entwicklung kann der Dienst z. b. auf einem Entwicklungs Server gehostet und später auf einen Produktionsserver verschoben werden. Dies erfordert eine Adressänderung.

> [!NOTE]
> Das Adressenelement ist nicht verfügbar, wenn das Dialogfeld **Dienstverweis konfigurieren** aus dem Dialogfeld **Dienstverweis hinzufügen** angezeigt wird.

**Zugriffsebene für generierte Klassen**

Bestimmt die Codezugriffsebene für WCF-Clientklassen.

> [!NOTE]
> Bei Websiteprojekten ist diese Option immer auf `Public` festgelegt und kann nicht geändert werden. Weitere Informationen finden Sie unter [Troubleshooting service references (Problembehandlung bei Dienstverweisen)](../data-tools/troubleshooting-service-references.md).

**Asynchrone Vorgänge generieren**

Bestimmt, ob WCF-Dienst Methoden synchron (Standard) oder asynchron aufgerufen werden.

**Aufgabenbasierte Vorgänge generieren**

Wenn Sie asynchronen Code schreiben, können Sie mit dieser Option die Task Parallel Library (TPL) nutzen, die mit .NET 4 eingeführt wurde. Weitere Informationen finden Sie unter [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Meldungsverträge immer generieren**

Bestimmt, ob Nachrichten Vertragstypen für einen WCF-Client generiert werden. Weitere Informationen zu Nachrichtenverträgen finden Sie unter[Using message contracts (Verwendung von Nachrichtenverträgen)](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Sammlungstyp**

Gibt den Listenauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Array>.

**Wörterbuchsammlungstyp**

Gibt den Wörterbuchauflistungstyp für einen WCF-Client an. Der Standardtyp ist <xref:System.Collections.Generic.Dictionary%602>.

**Typen in Assemblys, auf die verwiesen wird, wiederverwenden**

Bestimmt, ob ein WCF-Client versucht, zu verwenden, was in referenzierten Assemblys bereits vorhanden ist, anstatt neue Typen zu erstellen, wenn ein Dienst hinzugefügt oder aktualisiert Diese Option ist standardmäßig aktiviert.

**Typen in allen Assemblys, auf die verwiesen wird, wiederverwenden**

Wenn diese Option ausgewählt ist, werden alle Typen in der Liste der Assemblys, auf die **verwiesen** wird, Diese Option ist standardmäßig ausgewählt.

**Typen in folgenden Assemblys, auf die verwiesen wird, wiederverwenden**

Wenn diese Option ausgewählt ist, werden nur die ausgewählten Typen in der Liste Assemblys, auf die **verwiesen** wird

**Liste „Assemblys, auf die verwiesen wird“**

Enthält eine Liste der referenzierten Assemblys für das Projekt oder die Website. Wenn Sie in angegebenen Assemblys, auf die verwiesen wird, **Wiederverwendungs Typen** auswählen, können Sie einzelne Assemblys auswählen

**Webverweis hinzufügen**

Zeigt das Dialogfeld **Webverweis hinzufügen** an.

> [!NOTE]
> Diese Option sollte nur für Projekte verwendet werden, die auf die Version 2,0 der .NET Framework abzielen.
>
> [!NOTE]
> Die Schaltfläche **Webverweis hinzufügen** ist nur verfügbar, wenn das Dialogfeld **Dienst Verweis konfigurieren** im Dialog **Feld Dienstverweis hinzufügen** angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [How to: Add a reference to a web service (Vorgehensweise: Hinzufügen eines Verweises auf einen Webdienst)](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation-Dienste und WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
