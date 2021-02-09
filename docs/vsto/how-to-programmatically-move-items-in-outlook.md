---
title: 'Gewusst wie: Programm gesteuertes Verschieben von Elementen in Outlook'
description: Erfahren Sie, wie Sie Elemente Programm gesteuert in Microsoft Outlook verschieben können. In diesem Beispiel werden ungelesene e-Mail-Nachrichten aus dem Posteingang in den Ordner Test verschoben
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 770f056dc681e1ee2cd6704f9bd1d42afae4957b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888861"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Gewusst wie: Programm gesteuertes Verschieben von Elementen in Outlook
  In diesem Beispiel werden ungelesene e-Mail-Nachrichten aus dem **Posteingang** in den Ordner **Test** verschoben Im Beispiel werden nur Nachrichten mit dem Wort **Test** im- `Subject` Feld verschoben.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Ein Outlook Mail-Ordner mit dem Namen " **Test**".

- Eine e-Mail-Nachricht, die mit dem Word- **Test** im `Subject` Feld eingeht.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Gewusst wie: Programm gesteuertes Ausführen von Aktionen beim Empfang einer e-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
