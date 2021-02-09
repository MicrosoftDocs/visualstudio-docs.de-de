---
title: 'Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio'
description: Erfahren Sie, wie Sie ein XML-Schema einem Microsoft Office Word-Dokument zuordnen können, während das Dokument in Visual Studio geöffnet ist.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900933"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio
  **Wichtig** Die Informationen, die in diesem Thema in Bezug auf Microsoft Word beschrieben werden, werden exklusiv für den Vorteil und die Verwendung von Einzelpersonen und Organisationen präsentiert, die sich außerhalb der USA und ihrer Gebiete befinden oder Programme verwenden, die unter, Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden Diese Informationen zu Microsoft Word werden möglicherweise nicht von Einzelpersonen oder Organisationen in den USA oder deren Territorien gelesen oder verwendet, die von Microsoft Word-Produkten verwendet werden, die nach dem 10. Januar 2010 von Microsoft lizenziert wurden. Diese Produkte Verhalten sich nicht identisch mit Produkten, die vor diesem Datum lizenziert sind, oder für die Verwendung außerhalb der USA lizenziert und lizenziert wurden.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Sie können ein XML-Schema einem Dokument zuordnen, während das Dokument in Visual Studio geöffnet ist. Sie verwenden dieselben Microsoft Office Word-Tools, die Sie verwenden, wenn das Dokument außerhalb von Visual Studio geöffnet ist. Das Office-Projekt erstellt dieselben Objekte, unabhängig davon, ob Sie das Schema vor oder nach dem Erstellen der Word-Projekt Mappe dem Dokument zuordnen.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>So ordnen Sie ein XML-Schema einem Word-Dokument in Visual Studio zu

1. Öffnen Sie in Visual Studio das Word-Dokument oder das Vorlagen Projekt.

2. Klicken Sie in das Dokument, um den Fokus auf den Designer zu verschieben.

3. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Klicken Sie in der Gruppe **XML** auf **Schema**.

     Das Dialogfeld **Vorlagen und Add-ins** wird geöffnet.

5. Klicken Sie auf die Registerkarte **XML-Schema** .

6. Klicken Sie auf **Schema hinzufügen**.

     Das Dialogfeld **Schema hinzufügen** wird geöffnet.

7. Navigieren Sie zu ihrer Schema Datei, wählen Sie Sie aus, und klicken Sie dann auf **Öffnen**.

     Das Dialogfeld **Schema Einstellungen** wird geöffnet.

8. Weisen Sie einen Alias zu, oder klicken Sie auf **OK** , um das Schema ohne Alias hinzuzufügen.

9. Klicken Sie auf **OK**.

     Das Fenster **XML-Struktur** wird geöffnet.

10. Ziehen Sie Elemente aus dem Fenster **XML-Struktur** an die Orte in Ihrem Dokument, an denen die entsprechenden Steuerelemente erstellt werden sollen.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [XML-Schemas und-Daten in Anpassungen auf Dokument Ebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
