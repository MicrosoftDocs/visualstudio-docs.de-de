---
title: 'Gewusst wie: Programm gesteuertes bestimmen des aktuellen Outlook-Elements'
description: Erfahren Sie, wie Sie das aktuelle Microsoft Outlook-Element Programm gesteuert ermitteln können. In diesem Beispiel wird das Explorer. SelectionChange-Ereignis verwendet.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 720028528c036bf4485ca529f735fd26b1ff6e9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963834"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Gewusst wie: Programm gesteuertes bestimmen des aktuellen Outlook-Elements
  Dieses Beispiel verwendet das `Explorer.SelectionChange` -Ereignis, um den Namen des aktuellen Ordners und einige Informationen über das ausgewählte Element anzuzeigen. Der Code zeigt dann das ausgewählte Element an.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Termin-, Kontakt-und e-Mail-Elemente in Microsoft Office Outlook.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Gewusst wie: Programm gesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
