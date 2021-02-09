---
title: DataContext-Methoden (O/R-Designer)
description: Verstehen Sie die DataContext-Methoden im Kontext der LINQ to SQL Tools für Visual Studio. Diese Methoden führen gespeicherte Prozeduren und Funktionen in einer Datenbank aus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 64b5643704024ee689a011f5285b41be818dc5cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858968"
---
# <a name="datacontext-methods-or-designer"></a>DataContext-Methoden (O/R-Designer)

<xref:System.Data.Linq.DataContext> Methoden (im Kontext der [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sind Methoden der <xref:System.Data.Linq.DataContext> -Klasse, die gespeicherte Prozeduren und Funktionen in einer Datenbank ausführen.

Die <xref:System.Data.Linq.DataContext>-Klasse ist eine [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klasse, die als Verbindung zwischen einer SQL Server-Datenbank und den [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Entitätsklassen dient, die dieser Datenbank zugeordnet sind. Die <xref:System.Data.Linq.DataContext>-Klasse enthält die Verbindungszeichenfolgeninformationen und die Methoden zum Herstellen einer Verbindung mit einer Datenbank und zum Ändern der Daten in der Datenbank. Standardmäßig enthält die <xref:System.Data.Linq.DataContext>-Klasse mehrere Methoden, die Sie aufrufen können, z. B. die <xref:System.Data.Linq.DataContext.SubmitChanges%2A>-Methode, die aktualisierte Daten aus [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klassen an die Datenbank sendet. Sie können auch zusätzliche <xref:System.Data.Linq.DataContext>-Methoden erstellen, die gespeicherten Prozeduren und Funktionen zugeordnet werden. Das heißt, wenn Sie diese benutzerdefinierten Methoden aufrufen, wird die gespeicherte Prozedur oder Funktion in der Datenbank ausgeführt, der die <xref:System.Data.Linq.DataContext> Methode zugeordnet ist. Sie können der <xref:System.Data.Linq.DataContext>-Klasse neue Methoden hinzufügen, wie Sie auch anderen Klassen Methoden hinzufügen würden, um diese zu erweitern. In Diskussionen über <xref:System.Data.Linq.DataContext> Methoden im Kontext des **O/R-Designers** sind es jedoch die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet werden, die besprochen werden.

## <a name="methods-pane"></a>Methodenbereich

<xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind, werden im **Methoden** Bereich des **O/R-Designers** angezeigt. Der Bereich **Methoden** befindet sich neben dem Bereich **Entitäten** (der Hauptentwurfsoberfläche). Im Bereich **Methoden** werden alle <xref:System.Data.Linq.DataContext> Methoden aufgelistet, die Sie mit dem **O/R-Designer** erstellt haben. Standardmäßig ist der **Methoden** Bereich leer. Ziehen Sie gespeicherte Prozeduren oder Funktionen aus **Server-Explorer** oder **Datenbank-Explorer** auf den **O/R-Designer** , um Methoden zu erstellen <xref:System.Data.Linq.DataContext> und den **Methoden** Bereich aufzufüllen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Öffnen und schließen Sie den Methoden Bereich, indem Sie mit der rechten Maustaste auf den **O/R-Designer** klicken und dann auf **Methoden Bereich ausblenden** oder **Methoden Bereich anzeigen** klicken oder die Tastenkombination **STRG** + **1** verwenden.

## <a name="two-types-of-datacontext-methods"></a>Zwei Typen von DataContext-Methoden

DataContext-Methoden sind Methoden, die gespeicherten Prozeduren und Funktionen in der Datenbank zugeordnet werden. Sie können DataContext-Methoden für den **Methoden** Bereich des **O/R-Designers** erstellen und hinzufügen. Es gibt zwei verschiedene Typen von <xref:System.Data.Linq.DataContext>-Methoden, die sich dadurch unterscheiden, dass von dem einen mindestens ein Resultset zurückgegeben wird und von dem anderen nicht:

- <xref:System.Data.Linq.DataContext>-Methoden, die ein oder mehrere Resultsets zurückgeben:

   Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>-Methode, wenn eine Anwendung nur gespeicherte Prozeduren und Funktionen in der Datenbank ausführen und die Ergebnisse zurückgeben muss. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. Linq. ISingleResult \<T> und <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext>-Methoden, die keine Resultsets zurückgeben, wie Einfüge-, Update- und Löschvorgänge für eine bestimmte Entitätsklasse.

   Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>-Methode, wenn eine Anwendung gespeicherte Prozeduren ausführen muss, statt das [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Standardverhalten zum Speichern geänderter Daten zwischen einer Entitätsklasse und der Datenbank zu verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Rückgabetypen von DataContext-Methoden

Wenn Sie gespeicherte Prozeduren und Funktionen aus dem **Server-Explorer** oder **Datenbank-Explorer** in den **O/R-Designer** ziehen, unterscheidet sich der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext>-Methode je nach dem Ablageort des Elements. Wenn Sie die Elemente direkt auf einer vorhandenen Entitäts Klasse ablegen, wird eine <xref:System.Data.Linq.DataContext> Methode mit dem Rückgabetyp der Entitäts Klasse erstellt. Wenn Sie Elemente in einem leeren Bereich des **O/R-Designers** (in beiden Bereichen) ablegen, wird eine <xref:System.Data.Linq.DataContext> Methode erstellt, die einen automatisch generierten Typ zurückgibt. Der automatisch generierte Typ weist den Namen auf, der mit dem Namen und den Eigenschaften der gespeicherten Prozedur oder der Funktion übereinstimmt, die den von der gespeicherten Prozedur oder Funktion zurückgegebenen Feldern zugeordnet werden.

> [!NOTE]
> Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben. Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>-Methode zu überprüfen oder zu ändern, markieren Sie sie, und überprüfen Sie die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**. Weitere Informationen finden Sie unter Gewusst [wie: Ändern des Rückgabe Typs einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Objekte, die Sie aus der Datenbank auf die O/R-Designer-Oberfläche ziehen, werden automatisch basierend auf dem Namen der Objekte in der Datenbank benannt. Wenn Sie das gleiche Objekt mehrmals ziehen, wird am Ende des neuen Namens eine Zahl hinzugefügt, die die Namen unterscheidet. Wenn Namen von Datenbankobjekten Leerzeichen oder in Visual Basic oder C# nicht unterstützte Zeichen enthalten, wird das entsprechende Zeichen durch einen Unterstrich ersetzt.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Gespeicherten Prozeduren](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer) (Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O/R-Designer))](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
