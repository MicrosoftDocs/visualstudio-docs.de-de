---
title: 'Gewusst wie: Programm gesteuertes Suchen eines bestimmten Kontakts'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Programm gesteuert nach einem bestimmten Kontakt in Microsoft Outlook zu suchen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6813a137558a245c66d4b24deac07b1a6a77796a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524606"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Gewusst wie: Programm gesteuertes Suchen eines bestimmten Kontakts
  Dieses Beispiel durchsucht einen Outlook-Kontaktordner über den Vor- und Nachnamen nach einem bestimmten Kontakt. Im Beispiel wird vorausgesetzt, dass ein Kontakt namens **John Evans** im Kontaktordner vorhanden ist.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
