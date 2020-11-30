---
title: Integrieren von Geschäftsdaten in SharePoint | Microsoft-Dokumentation
description: Hier erhalten Sie eine allgemeine Übersicht über das Integrieren von Geschäftsdaten in SharePoint durch Erstellen eines Modells für den BDC-Dienst (Business Data Connectivity).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3156adc286222282ae63f70f70838bc6b7155a8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304350"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrieren von Geschäftsdaten in SharePoint
  Sie können Geschäftsdaten in SharePoint integrieren. Geschäftsdaten stammen aus Back-End-Serveranwendungen wie [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel und SAP oder von einem Webdienst. Benutzer können Geschäftsdaten mithilfe externer Listen oder mit Webparts für Geschäftsdaten anzeigen, hinzufügen, ändern oder löschen.  Benutzer können auch offline mit einer Microsoft Office-Anwendung wie Microsoft Outlook auf diese Daten zugreifen. Weitere Informationen finden Sie unter [Wo können externe Daten angezeigt werden?](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Erstellen Sie ein Modell für den BDC-Dienst (Business Data Connectivity), um Daten mit SharePoint zu integrieren. Bei dem BDC-Dienst handelt es sich um eine Anwendung in SharePoint, die Informationen über Daten in Geschäftsanwendungen speichert. Weitere Informationen finden Sie im Artikel zum [BDC-Dienst (Business Data Connectivity)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modelle in Visual Studio
 In Visual Studio können Sie mit Modellen benutzerdefinierten Code zum Abrufen und Ändern von Daten schreiben, die aus Back-End-Datenquellen stammen. Sie können auch Daten aus mehreren Datenquellen aggregieren. Beispielsweise können Sie eine Liste von Kunden anzeigen, die Daten aus einer [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]-Datenbank und einem Webdienst enthält.

 Außerdem können Sie Modelle importieren, die bereits in SharePoint bereitgestellt wurden. Nachdem Sie ein Modell importiert haben, können Sie benutzerdefinierten Code hinzufügen oder einfach Visual Studio verwenden, um das Modell zu packen und für mehrere SharePoint-Serverfarmen bereitzustellen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Entwerfen eines Modells in Visual Studio
 Sie können ein Modell mithilfe eines Designers und mehrerer Toolfenster entwerfen. Während Sie das Modell entwerfen, generiert Visual Studio den XML-Code für das Modell. Weitere Informationen finden Sie unter [Übersicht über die Tools zum Entwerfen von BDC-Modellen](../sharepoint/bdc-model-design-tools-overview.md).

 Modelle enthalten Entitäten und Methoden.

### <a name="entities"></a>Entitäten
 Eine Entität beschreibt eine Sammlung von Feldern. Beispielsweise kann eine Entität eine Tabelle in einer Datenbank darstellen. Eine Identität wird in SharePoint als externer Inhaltstyp angezeigt. Weitere Informationen über externe Inhaltstypen finden Sie unter [Was sind externe Inhaltstypen?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14)).

### <a name="methods"></a>Methoden
 Mithilfe von Methoden können Benutzer eines externen Inhaltstyps Aktionen für die Felder einer Entität durchführen. Beispielsweise könnte eine Updater-Methode Benutzern das Ändern der Adresse und des Geburtsdatums eines Kunden ermöglichen, wenn die Entität `Customer` die Felder `Address` und `BirthDate` aufweist.

 Visual Studio generiert eine Dienstcodedatei für jede Entität in Ihrem Modell. Wenn Sie eine Methode zu Ihrem Modell hinzufügen, generiert Visual Studio eine entsprechende Methode in der Dienstcodedatei. Fügen Sie Code zu jeder Methode hinzu, um die entsprechenden Aufgaben durchzuführen. Wenn Sie beispielsweise die Creator-Methode zum Modell hinzufügen, generiert Visual Studio eine Creator-Methode in Ihrer Dienstcodedatei. Diese Methode wird vom BDC-Dienst aufgerufen, wenn ein Benutzer in einer auf dem Modell basierenden Liste auf **Neues Element** klickt. Fügen Sie daher Code zur Creator-Methode hinzu, der neue Daten zu einer Datenquelle hinzufügt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)|In diesem Artikel erfahren Sie, wie Sie ein neues Modell erstellen oder ein Modell importieren, das Sie aus SharePoint exportiert haben.|
|[Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)|In diesem Artikel wird erläutert, wie Sie die Elemente eines Modells mithilfe der Entwurfstools von Visual Studio entwerfen.|
|[Verwenden von SharePoint Designer verglichen mit Visual Studio beim Erstellen von Lösungen mithilfe von BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Dieser Artikel unterstützt Sie beim Treffen der Entscheidung, ob Sie Visual Studio oder SharePoint Designer zum Erstellen eines Modells für den BDC-Dienst verwenden sollten.|
