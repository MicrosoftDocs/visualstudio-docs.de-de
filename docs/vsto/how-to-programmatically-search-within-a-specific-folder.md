---
title: 'Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Programm gesteuert innerhalb eines bestimmten Microsoft Outlook-Ordners zu suchen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa569a2c301cb495f109a612d817937159c257c6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524537"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners
  In diesem Codebeispiel `Find` werden die `FindNext` -Methode und die-Methode verwendet, um Text im Feld Betreff von e-Mail-Nachrichten im **Posteingang** zu suchen. Diese Methode verwendet einen Zeichen folgen Filter, um den Buchstaben T als Anfangsbuchstaben des Texts zu überprüfen `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
