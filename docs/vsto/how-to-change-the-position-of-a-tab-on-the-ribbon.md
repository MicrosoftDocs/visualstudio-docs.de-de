---
title: 'Vorgehensweise: Ändern der Position einer Registerkarte im Menüband'
description: Mithilfe des Registerkarten Auflistungs-Editors können Sie die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern und benutzerdefinierte Registerkarten vor oder nach einer integrierten Registerkarte im Menüband positionieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dc0b4548ffa4e5efa75734b5528a7021cf122bfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921919"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Vorgehensweise: Ändern der Position einer Registerkarte im Menüband
  Mithilfe des Registerkarten Auflistungs- **Editors** können Sie die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern. Sie können benutzerdefinierte Registerkarten vor oder nach einer integrierten Registerkarte im Menüband positionieren. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Beispielsweise ist die Registerkarte " **Daten** " eine integrierte Registerkarte in Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>So ändern Sie die Reihenfolge der Registerkarten auf dem Menüband

1. Wählen Sie in **Projektmappen-Explorer** die Menüband-Codedatei (*VB* -oder *CS* -Datei) aus.

2. Klicken Sie im Menü **Ansicht** auf **Designer**.

3. Klicken Sie mit der rechten Maustaste auf den Menüband-Designer und dann auf **Eigenschaften**.

4. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft **Tabs** aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")).

     Der **Editor für Register** Karten Auflistung wird angezeigt.

5. Wählen Sie im Registerkarten Auflistungs- **Editor** in der Liste **Mitglieder** die Registerkarte aus, die Sie verschieben möchten, und klicken Sie auf die nach-oben-oder nach-unten-Pfeile, um

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>So positionieren Sie eine Registerkarte vor oder nach einer integrierten Registerkarte auf dem Menüband

1. Wählen Sie im Menüband-Designer eine benutzerdefinierte Registerkarte aus.

2. Erweitern Sie im Fenster **Eigenschaften** die **ControlID** -Eigenschaft, und stellen Sie dann sicher, dass der Wert der **ControlIdType** -Eigenschaft auf **Custom** festgelegt ist.

3. Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **Position** .

4. Legen Sie die **PositionType** -Eigenschaft auf den entsprechenden Wert fest:

    - **BeforeOfficeId** positioniert die Gruppe vor einer angegebenen integrierten Registerkarte.

    - **AfterOfficeId** positioniert die Gruppe nach einer angegebenen integrierten Registerkarte.

5. Legen Sie die **OfficeId-** Eigenschaft auf die Steuerelement-ID einer integrierten Registerkarte fest.

     Eine Liste der Steuerelement-IDs finden Sie in den [Hilfedateien von Office 2010: überflüssige Office-Steuer](https://www.microsoft.com/download/details.aspx?id=6627)Element Bezeichner.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
