---
title: Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d2f066bb7501085b66ba724f94840314063cd2ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281889"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.

Mindestens eines der aus **Server-Explorer** oder **Datenbank-Explorer** auf den **o/r-Designer** gezogenen Elemente enthält einen Datentyp, der vom **o/r-Designer**nicht unterstützt wird, z. b. [CLR-benutzerdefinierte Typen](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Erstellen Sie eine auf der gewünschten Tabelle basierende Ansicht, in der der nicht unterstützte Datentyp nicht enthalten ist.

2. Ziehen Sie die Ansicht von **Server-Explorer** oder **Datenbank-Explorer** auf den Designer.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
