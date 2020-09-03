---
title: 'Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6675a136b2bbdc1ef19d90ee19ecf7497053bfe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282046"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)
Wenn Sie Datenbankobjekte mit Namen, die in s oder IES enden, von **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)ziehen, werden die Namen der generierten Entitäts Klassen standardmäßig von Plural in Singular geändert. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Das Hinzufügen einer `Customers` Tabelle zum **O/R-Designer** führt beispielsweise dazu, dass eine Entitäts Klasse mit dem Namen erstellt `Customer` wird, da die Klasse nur Daten für einen einzelnen Kunden enthält.

> [!NOTE]
> Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie im Dialogfeld **Optionen** den Knoten **Datenbanktools**.

    > [!NOTE]
    > Wählen Sie **Alle Einstellungen anzeigen** aus, wenn der Knoten **Datenbanktools** nicht angezeigt wird.

3. Klicken Sie auf **O/R-Designer**.

4. Legen Sie die **Pluralisierung von Namen** **auf "**  =  **false** " fest, um den **O/R-Designer** so festzulegen, dass er die Klassennamen nicht ändert.

5. Legen Sie die **Pluralisierung von Namen** auf **aktiviert**  =  **true** fest, um pluralisierungs Regeln auf die Klassennamen von Objekten anzuwenden, die dem **O/R-Designer**hinzugefügt wurden.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
