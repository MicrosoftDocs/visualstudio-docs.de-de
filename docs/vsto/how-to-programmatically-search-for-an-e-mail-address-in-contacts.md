---
title: Programm gesteuertes Suchen einer e-Mail-Adresse in Kontakten
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um eine e-Mail-Adresse in Ihren Microsoft Outlook-Kontakten Programm gesteuert zu finden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7fa6578612fb81d9d025e613697c4342bac11bee
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528228"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Gewusst wie: Programm gesteuertes suchen nach einer e-Mail-Adresse in Kontakten
  In diesem Beispiel wird ein Kontaktordner nach Kontakten durchsucht, die den Domänennamen **example.com** in ihren E-Mail-Adressen aufweisen.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel benötigen Sie Folgendes:

- Kontakte mit dem Domänennamen **example.com** in ihren E-Mail-Adressen (z. B. `somebody@example.com`), die einen Vor- und Nachnamen aufweisen.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)
- [Gewusst wie: Programm gesteuertes Senden von e-Mails](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Gewusst wie: Programm gesteuertes zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Gewusst wie: Programm gesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
