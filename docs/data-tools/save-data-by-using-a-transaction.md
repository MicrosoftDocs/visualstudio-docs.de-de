---
title: 'Vorgehensweise: Speichern von Daten mithilfe einer Transaktion'
description: Informieren Sie sich über das Speichern von Daten mithilfe einer Transaktion mit datasettools in Visual Studio. Sie speichern Daten in einer Transaktion, indem Sie den System. Transactions-Namespace verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c633ed01821f500e958d3c7549febc23cf33c09d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858487"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Vorgehensweise: Speichern von Daten mithilfe einer Transaktion

Sie speichern Daten in einer Transaktion, indem Sie den- <xref:System.Transactions> Namespace verwenden. Verwenden Sie das- <xref:System.Transactions.TransactionScope> Objekt, um an einer Transaktion teilzunehmen, die automatisch für Sie verwaltet wird.

Projekte werden nicht mit einem Verweis auf die *System. Transactions* -Assembly erstellt. Daher müssen Sie manuell einen Verweis auf Projekte hinzufügen, die Transaktionen verwenden.

Die einfachste Möglichkeit, eine Transaktion zu implementieren, besteht darin, ein- <xref:System.Transactions.TransactionScope> Objekt in einer-Anweisung zu instanziieren `using` . (Weitere Informationen finden Sie unter [using-Anweisung](/dotnet/visual-basic/language-reference/statements/using-statement)und [using-Anweisung](/dotnet/csharp/language-reference/keywords/using-statement).) Der Code, der in der-Anweisung ausgeführt wird, ist `using` an der Transaktion beteiligt.

Um einen Commit für die Transaktion durchzusetzen, wenden Sie die- <xref:System.Transactions.TransactionScope.Complete%2A> Methode als letzte Anweisung im Using-Block an.

Um ein Rollback für die Transaktion auszuführen, lösen Sie eine Ausnahme aus, bevor Sie die- <xref:System.Transactions.TransactionScope.Complete%2A> Methode aufrufen.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>So fügen Sie einen Verweis auf die System.Transactions.dll hinzu

1. Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus.

2. Wählen Sie auf der Registerkarte **.net** (Registerkarte **SQL Server** für SQL Server Projekte) die Option **System. Transactions** aus, und klicken Sie dann auf **OK**.

     Ein Verweis auf *System.Transactions.dll* wird dem Projekt hinzugefügt.

## <a name="to-save-data-in-a-transaction"></a>So speichern Sie Daten in einer Transaktion

- Fügen Sie Code hinzu, um Daten in der using-Anweisung zu speichern, die die Transaktion enthält. Der folgende Code zeigt, wie ein- <xref:System.Transactions.TransactionScope> Objekt in einer using-Anweisung erstellt und instanziiert wird:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Weitere Informationen

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
- [Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion](../data-tools/save-data-in-a-transaction.md)
