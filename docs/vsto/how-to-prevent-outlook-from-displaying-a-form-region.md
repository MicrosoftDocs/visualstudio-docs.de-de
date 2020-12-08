---
title: 'Gewusst wie: verhindern der Anzeige eines Formular Bereichs in Outlook'
description: Erfahren Sie, wie Sie verhindern können, dass Microsoft Office Outlook einen Formular Bereich für ein bestimmtes Element anzeigt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f247bf82d51fda6d321b45c16f91b857300cc1e4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847675"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Gewusst wie: verhindern der Anzeige eines Formular Bereichs in Outlook
  Es kann Situationen geben, in denen Sie nicht möchten, dass Microsoft Office Outlook einen Formular Bereich für ein bestimmtes Element anzeigt. Wenn ein Kontakt Element z. b. keine Geschäftsadresse enthält, können Sie verhindern, dass ein Formular Bereich angezeigt wird, in dem der Speicherort des Unternehmens in einer Karte angezeigt wird.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>So verhindern Sie, dass Outlook einen Formular Bereich anzeigt

1. Öffnen Sie die Codedatei für den Formular Bereich, den Sie ändern möchten.

2. Erweitern Sie den Code Bereich der **Formular Bereich-Factory** .

3. Fügen Sie dem- `FormRegionInitializing` Ereignishandler Code hinzu, mit dem die- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Eigenschaft der- <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> Klasse auf **true** festgelegt wird.

   Wenn das Kontakt Element in diesem Beispiel keine Adresse enthält, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> wird die-Eigenschaft auf **true** festgelegt, und der Formular Bereich wird nicht angezeigt.

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Siehe auch
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Gewusst wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
