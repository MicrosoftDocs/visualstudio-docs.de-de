---
title: Unterstützungs Methode kann nicht gelöscht werden.
description: Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 94e9f1f91aa5c879e0e3ed0034e0d1f554901513
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866371"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.

Diese verwandte Methode ist die Unterstützungs Methode für die folgenden Standard- `Insert` ,- `Update` oder- `Delete` Methoden. Wenn sie gelöscht wird, werden die entsprechenden Methoden ebenfalls gelöscht. Möchten Sie den Vorgang fortsetzen?

Die ausgewählte `DataContext` Methode wird derzeit als eine der `Insert` `Update` Methoden, oder `Delete` für eine der Entitäts Klassen im **O/R-Designer** verwendet. Das Löschen der ausgewählten Methode bewirkt, dass die Entitäts Klasse, die diese Methode verwendet hat, zum standardmäßigen Laufzeitverhalten für das Einfügen, aktualisieren oder löschen während eines Updates zurückkehrt.

## <a name="selected-method-options"></a>Optionen für ausgewählte Methoden

- Um die ausgewählte Methode zu löschen, sodass die Entitäts Klasse Lauf Zeit Updates verwendet, klicken Sie auf **Ja**.

   Die ausgewählte Methode wird gelöscht, und alle Klassen, die diese Methode zum Überschreiben des Aktualisierungs Verhaltens verwendet haben, werden auf die standardmäßige LINQ to SQL Laufzeitverhalten zurückgesetzt.

- Um das Meldungs Feld zu schließen und die ausgewählte Methode unverändert zu lassen, klicken Sie auf **Nein**.

   Das Meldungsfeld wird geschlossen, und es werden keine Änderungen vorgenommen.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)