---
title: 'Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um einen Ordner nach Namen Programm gesteuert abzurufen und dann den Inhalt des Ordners anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c05f8bc0174807a5336a9d9f79ac3dc81e87476e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953876"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Gewusst wie: Programm gesteuertes Abrufen eines Ordners anhand des Namens
  In diesem Beispiel wird ein Verweis auf einen benannten benutzerdefinierten Ordner abgerufen und dann der Inhalt des Ordners angezeigt.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Einen Ordner mit dem Namen "TestFolder".

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Ordnern](../vsto/working-with-folders.md)
- [Gewusst wie: Programm gesteuertes suchen innerhalb eines bestimmten Ordners](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Gewusst wie: Programm gesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Gewusst wie: Programm gesteuertes Erstellen von benutzerdefinierten Ordner Elementen](../vsto/how-to-programmatically-create-custom-folder-items.md)
