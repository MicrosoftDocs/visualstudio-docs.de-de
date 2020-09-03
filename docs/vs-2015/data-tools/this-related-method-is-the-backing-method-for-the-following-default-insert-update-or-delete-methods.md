---
title: Diese verwandte Methode ist die Unterstützungs Methode für die folgenden standardmäßigen Insert-, Update-oder Delete-Methoden. Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667181"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese verknüpfte Methode ist die dahinter liegende Methode für die folgenden standardmäßigen Insert-, Update- und Delete-Methoden. Wenn sie gelöscht wird, werden die entsprechenden Methoden ebenfalls gelöscht. Möchten Sie den Vorgang fortsetzen?

 Die ausgewählte `DataContext`-Methode wird derzeit als eine der Insert-, Update- oder Delete-Methoden für eine der Entitätsklassen im O/R-Designer verwendet. Durch das Löschen der ausgewählten Methode greift die Entitätsklasse, die diese Methode verwendete, auf das Standardlaufzeitverhalten zurück, um die Aktionen Einfügen, Aktualisieren oder Löschen bei einem Update auszuführen.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>So löschen Sie die ausgewählte Methode und bewirken, dass die Entitätsklasse Laufzeitupdates verwendet

- Klicken Sie auf **Ja**.

     Die ausgewählte Methode wird gelöscht und alle Klassen, die diese Methode zum Überschreiben des Updateverhaltens verwendet hatten, greifen wieder auf das standardmäßige LINQ to SQL-Laufzeitverhalten zurück.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>So schließen Sie das Meldungsfeld, ohne die ausgewählte Methode zu ändern

- Klicken Sie auf **Nein**.

     Das Meldungsfeld wird geschlossen, und es werden keine Änderungen vorgenommen.

## <a name="see-also"></a>Weitere Informationen
 [DataContext-Methoden (o/r-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Aktualisierungen, Einfügungen und Löschungen (o/r-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
