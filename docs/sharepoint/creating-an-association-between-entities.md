---
title: Erstellen einer Zuordnung zwischen Entitäten | Microsoft-Dokumentation
description: Erstellen Sie eine Zuordnung zwischen Entitäten in Ihrem Business Data Connectivity (BDC)-Modell. Erfahren Sie mehr über Zuordnungs Methoden und Zuordnungs Typen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7efd3d622e40c21574c0aa9e39263d53979706ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949193"
---
# <a name="create-an-association-between-entities"></a>Erstellen einer Zuordnung zwischen Entitäten
  Sie können Beziehungen zwischen Entitäten in Ihrem Business Data Connectivity (BDC)-Modell definieren, indem Sie Zuordnungen erstellen. Visual Studio generiert Methoden, die Consumer des Modells mit Informationen zu den einzelnen Zuordnungen bereitstellen. Diese Methoden können von SharePoint-Webparts, Listen oder benutzerdefinierten Anwendungen genutzt werden, um Daten Beziehungen in einer Benutzeroberfläche (UI) anzuzeigen.

## <a name="create-an-association"></a>Erstellen einer Zuordnung
 Erstellen Sie eine Zuordnung, indem Sie das Zuordnungs Steuerelement in der Visual Studio- **Toolbox** auswählen. Wählen Sie **dabei die erste** Entität (Quell Entität) aus, und wählen Sie dann die zweite Entität (als Ziel Entität bezeichnet) Sie können die Details der Zuordnung im **Association-Editor** definieren. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Zuordnungs Methoden
 Anwendungen wie SharePoint Business Data-Webparts nutzen Zuordnungen, indem Sie Methoden in der Dienstklasse einer Entität aufrufen. Sie können der Dienstklasse einer Entität Methoden hinzufügen, indem Sie Sie im **Association-Editor** auswählen.

 Standardmäßig fügt der **Association Editor** der Quell-und Ziel Entität eine Association-Navigations Methode hinzu. Eine Association-Navigations Methode in der Quell Entität ermöglicht es Consumern, eine Liste von Ziel Entitäten abzurufen. Eine Association-Navigations Methode in der Ziel Entität ermöglicht es Consumern, die Quell Entität abzurufen, die sich auf eine Ziel Entität bezieht.

 Sie müssen den Code den einzelnen Methoden hinzufügen, um die entsprechenden Informationen zurückzugeben. Sie können auch andere Arten von Methoden hinzufügen, um erweiterte Szenarios zu unterstützen. Weitere Informationen zu den einzelnen Methoden finden Sie [unter Unterstützte Vorgänge](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Typen von Zuordnungen
 Sie können zwei Typen von Zuordnungen im BDC-Designer erstellen: Fremdschlüssel basierte Zuordnungen und Fremdschlüssel lose Zuordnungen.

### <a name="foreign-key-based-association"></a>Fremdschlüssel basierte Zuordnung
 Sie können eine Fremdschlüssel basierte Zuordnung erstellen, indem Sie einen Bezeichner in der Quell Entität mit Typdeskriptoren verknüpfen, die in der Ziel Entität definiert sind. Diese Beziehung ermöglicht Consumer des Modells, eine erweiterte Benutzeroberfläche für Ihre Benutzer bereitzustellen. Beispielsweise ein Formular in Outlook, das es einem Benutzer ermöglicht, einen Verkaufsauftrag zu erstellen, der Kunden in einer Dropdown Liste anzeigen kann. oder eine Liste mit Verkaufsaufträgen in SharePoint, mit der Benutzer eine Profilseite für einen Kunden öffnen können.

 Um eine Fremdschlüssel basierte Zuordnung zu erstellen, verknüpfen Sie Bezeichner und Typdeskriptoren mit dem gleichen Namen und Typ. Beispielsweise können Sie eine Fremdschlüssel basierte Zuordnung zwischen einer `Contact` -Entität und einer- `SalesOrder` Entität erstellen. Die- `SalesOrder` Entität gibt einen `ContactID` Typdeskriptor als Teil des Rückgabe Parameters von Finder oder bestimmten Finder-Methoden zurück. Beide Typdeskriptoren werden im **Association-Editor** angezeigt. Um eine Fremdschlüssel basierte Beziehung zwischen der `Contact` Entität und der `SalesOrder` Entität zu erstellen, wählen Sie den `ContactID` Bezeichner neben jedem dieser Felder aus.

 Fügen Sie der Association Navigator-Methode der Quell Entität, die eine Auflistung von Ziel Entitäten zurückgibt, Code hinzu. Im folgenden Beispiel werden die Verkaufsaufträge für einen Kontakt zurückgegeben.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 Fügen Sie der Association Navigator-Methode der Ziel Entität, die eine Quell Entität zurückgibt, Code hinzu. Im folgenden Beispiel wird der Kontakt zurückgegeben, der mit dem Verkaufsauftrag verknüpft ist.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>Fremdschlüssel Zuordnung
 Sie können eine Zuordnung erstellen, ohne den Feldtyp Deskriptoren Bezeichner zuordnen zu müssen. Erstellen Sie diese Art von Zuordnung, wenn die Quell Entität über keine direkte Beziehung mit der Ziel Entität verfügt. Beispielsweise verfügt eine `SalesOrderDetail` Tabelle nicht über einen Fremdschlüssel, der einem Primärschlüssel in einer Tabelle zugeordnet ist `Contact` .

 Wenn Sie Informationen in der Tabelle anzeigen möchten, die `SalesOrderDetail` sich auf eine bezieht `Contact` , können Sie eine Fremdschlüssel Zuordnung zwischen der `Contact` Entität und der `SalesOrderDetail` Entität erstellen.

 Geben Sie in der Association-Navigations Methode der- `Contact` Entität die `SalesOrderDetail` Entitäten zurück, indem Sie Tabellen miteinander verbinden oder eine gespeicherte Prozedur aufrufen.

 Im folgenden Beispiel werden die Details aller Verkaufsaufträge durch das Verbinden von Tabellen zurückgegeben.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 Geben Sie in der Association-Navigations Methode der- `SalesOrderDetail` Entität den entsprechenden zurück `Contact` . Dies wird im folgenden Beispiel veranschaulicht:

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)
