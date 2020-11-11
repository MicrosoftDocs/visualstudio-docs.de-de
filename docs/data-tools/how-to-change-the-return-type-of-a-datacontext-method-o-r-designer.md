---
title: Rückgabetyp der DataContext-Methode ändern
description: Erfahren Sie, wie Sie den Rückgabetyp einer DataContext-Methode ändern, wenn Sie eine gespeicherte Prozedur oder Funktion im objektrelationaler Designer (O/R-Designer) ablegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 20ff0e4764acf4f2f0f8dea77ed815a9aa430abe
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435051"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Vorgehensweise: Ändern des Rückgabetyps für eine DataContext-Methode (O/R-Designer)
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext> Methode (basierend auf einer gespeicherten Prozedur oder Funktion erstellt) unterscheidet sich abhängig davon, wo Sie die gespeicherte Prozedur oder Funktion im **O/R-Designer** ablegen. Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt (wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt). Wenn Sie ein Element in einem leeren Bereich des **O/R-Designers** ablegen, <xref:System.Data.Linq.DataContext> wird eine Methode erstellt, die einen automatisch generierten Typ zurückgibt. Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie und klicken im Fenster **Eigenschaften** auf die Eigenschaft **Rückgabetyp**.

> [!NOTE]
> <xref:System.Data.Linq.DataContext>-Methoden können nicht wiederhergestellt werden, wenn ein Rückgabetyp auf eine Entitätsklasse festgelegt ist, um so den automatisch generierten Typ mithilfe des Fensters **Eigenschaften** zurückzugeben. Zum Zurücksetzen einer <xref:System.Data.Linq.DataContext> Methode, die einen automatisch generierten Typ zurückgibt, müssen Sie das ursprüngliche Datenbankobjekt erneut auf den **O/R-Designer** ziehen.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode vom automatisch generierten Typ in eine Entitätsklasse

1. Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>-Methode aus.

2. Wählen Sie im Fenster **Eigenschaften** die Option **Rückgabetyp** und anschließend in der Liste **Rückgabetyp** eine verfügbare Entitätsklasse aus. Wenn die gewünschte Entitäts Klasse nicht in der Liste enthalten ist, fügen Sie Sie hinzu, oder erstellen Sie Sie im **O/R-Designer** , um Sie der Liste hinzuzufügen.

3. Speichern Sie die *DBML* -Datei.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>So ändern Sie den Rückgabetyp einer DataContext-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ

1. Wählen Sie im Bereich **Methoden** die <xref:System.Data.Linq.DataContext>-Methode aus, und löschen Sie sie.

2. Ziehen Sie das Datenbankobjekt aus **Server-Explorer** oder **Datenbank-Explorer** auf einen leeren Bereich des **O/R-Designers**.

3. Speichern Sie die *DBML* -Datei.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
