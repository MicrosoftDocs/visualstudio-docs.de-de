---
title: 'Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen'
description: Weitere Informationen finden Sie unter Hinzufügen von Validierung zu Entitäts Klassen. Hinzufügen einer Validierung für Änderungen an einem Wert in einer bestimmten Spalte. Fügen Sie eine Validierung für Updates einer Entitäts Klasse hinzu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 08d60b254867c02c7cc406709a95117a11d669c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858812"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen
Durch den Vorgang der *Validierung* von Entitätsklassen wird bestätigt, dass die in Datenobjekte eingegebenen Werte den Einschränkungen eines Objektschemas oder den bestehenden Regeln für die Anwendung entsprechen. Es dient der Fehlervermeidung, Daten vor dem Senden von Aktualisierungen an zugrunde liegende Datenbanken auf Gültigkeit zu überprüfen. Dadurch wird auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank verringert.

Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellen partielle Methoden bereit, die es Benutzern ermöglichen, den von einem Designer generierten Code zu erweitern, der bei Einfügungen, Aktualisierungen und Löschungen von vollständigen Entitäten und auch während und nach einzelnen Spalten Änderungen ausgeführt wird.

> [!NOTE]
> Dieses Thema enthält die grundlegenden Schritte zum Hinzufügen von Validierungen zu Entitäts Klassen mithilfe des **O/R-Designers**. Da es möglicherweise schwierig ist, diese generischen Schritte ohne Verweis auf eine bestimmte Entitäts Klasse auszuführen, wird eine exemplarische Vorgehensweise bereitgestellt, in der tatsächliche Daten verwendet werden.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Validierung für Änderungen am Wert in einer bestimmten Spalte hinzufügen
Dieses Verfahren veranschaulicht, wie Daten auf Gültigkeit geprüft werden, wenn sich der Wert in einer Spalte ändert. Da die Validierung innerhalb der Klassendefinition (nicht der Benutzeroberfläche) ausgeführt wird, wird eine Ausnahme ausgelöst, wenn die Validierung aufgrund des Werts nicht durchgeführt werden kann. Implementieren Sie eine Fehlerbehandlung für den Code in der Anwendung, der die Änderung von Spaltenwerten durchführt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>So validieren Sie Daten während einer Änderung eines Spaltenwerts

1. Öffnen oder erstellen Sie eine neue LINQ to SQL Klassen-Datei (**. dbml** -Datei) im **O/R-Designer**. (Doppelklicken Sie im **Projektmappen-Explorer** auf die **DBML**-Datei.)

2. Klicken Sie im **O/R-Designer** mit der rechten Maustaste auf die Klasse, der Sie Validierungen hinzufügen möchten, und klicken Sie dann auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.

3. Platzieren Sie den Cursor in der partiellen Klasse.

4. Für Visual Basic-Projekte:

    1. Erweitern Sie die Liste **Methodenname**.

    2. Suchen Sie die **OnSPALTENNNAMEChanging**-Methode für die Spalte, der Sie eine Validierung hinzufügen möchten.

    3. Der partiellen Klasse wird eine `OnCOLUMNNAMEChanging`-Methode hinzugefügt.

    4. Fügen Sie den folgenden Code hinzu, um zunächst zu überprüfen, ob ein Wert eingegeben wurde, und dann sicherzustellen, dass der für die Spalte eingegebene Wert für die Anwendung gültig ist. Das `value`-Argument enthält den vorgeschlagenen Wert, fügen Sie daher Logik hinzu, um sicherzustellen, das es sich um einen gültigen Wert handelt:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Für C#-Projekte:

    Da c#-Projekte Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die Spalten veränderlichen partiellen Methoden zu erstellen. Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen. Klicken Sie auf die Methode zur Spaltenänderung für die Spalte, der Sie Validierung hinzufügen möchten. Der folgende Code ähnelt dem Code, der generiert wird, wenn Sie eine partielle Spalten veränderliche Methode auswählen:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Hinzufügen von Validierungen für Updates zu einer Entitäts Klasse
Neben der Überprüfung von Werten während Änderungen können Sie auch Daten auf Gültigkeit prüfen, wenn versucht wird, eine vollständige Entitätsklasse zu aktualisieren. Validierung während eines versuchten Updates ermöglicht Ihnen, Werte in mehreren Spalten zu vergleichen, wenn die Geschäftsregeln dies erfordern. Das folgende Verfahren veranschaulicht die Validierung beim Versuch, eine vollständige Entitätsklasse zu aktualisieren.

> [!NOTE]
> Der Validierungscode für Updates vollständiger Entitätsklassen wird in der partiellen <xref:System.Data.Linq.DataContext>-Klasse ausgeführt (statt in der partiellen Klasse einer bestimmten Entitätsklasse).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>So validieren Sie Daten während eines Updates einer Entitätsklasse

1. Öffnen oder erstellen Sie eine neue LINQ to SQL Klassen-Datei (**. dbml** -Datei) im **O/R-Designer**. (Doppelklicken Sie im **Projektmappen-Explorer** auf die **DBML**-Datei.)

2. Klicken Sie im **O/R-Designer** mit der rechten Maustaste in einen leeren Bereich, und klicken Sie auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für den `DataContext` geöffnet.

3. Platzieren Sie den Cursor in die partielle Klasse für den `DataContext`.

4. Für Visual Basic-Projekte:

    1. Erweitern Sie die Liste **Methodenname**.

    2. Klicken Sie auf **UpdateENTITYCLASSNAME**.

    3. Der partiellen Klasse wird eine `UpdateENTITYCLASSNAME`-Methode hinzugefügt.

    4. Greifen Sie auf die Werte einzelner Spalten mithilfe des `instance`-Arguments zu, wie im folgenden Code dargestellt:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Für C#-Projekte:

    Da c#-Projekte Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partielle-Methode zu erstellen `UpdateCLASSNAME` . Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen. Klicken Sie auf die Update-Methode für die Klasse, der Sie die Validierung hinzufügen möchten. Der folgende Code ähnelt dem Code, der generiert wird, wenn Sie eine `UpdateCLASSNAME` partielle Methode auswählen:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Validieren von Daten](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
