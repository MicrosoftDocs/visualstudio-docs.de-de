---
title: 'Gewusst wie: Programm gesteuertes zugreifen auf Outlook-Kontakte'
description: Erfahren Sie, wie Sie Programm gesteuert auf Outlook-Kontakte zugreifen können. In diesem Beispiel werden alle Kontakte gesucht, deren Nachnamen eine angegebene Such Zeichenfolge enthalten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b82595aa3a09076b91211ba4ab45145b02ebcd9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903733"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Gewusst wie: Programm gesteuertes zugreifen auf Outlook-Kontakte
  In diesem Beispiel werden alle Kontakte gesucht, deren Nachnamen eine angegebene Such Zeichenfolge enthalten.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Kontakte, deren Nachname die Zeichenfolge "**na"** (z. b. "Tzipi Butnaru") im Ordner " **Contacts** " enthalten.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)
- [Gewusst wie: Programm gesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Gewusst wie: Programm gesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Gewusst wie: Programm gesteuertes suchen nach einer e-Mail-Adresse in Kontakten](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Outlook-Kontakten](../vsto/how-to-programmatically-delete-outlook-contacts.md)
