---
title: Nicht unterstützte Datentypen
description: Mindestens ein ausgewähltes Element enthält einen Datentyp, der vom Designer nicht unterstützt wird. Informationen zu dieser Visual Studio O/R-Designer-Meldung anzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c50d47363217a87147275a406d5370cc8736c10b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866644"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.

Mindestens eines der aus **Server-Explorer** oder **Datenbank-Explorer** auf den **o/r-Designer** gezogenen Elemente enthält einen Datentyp, der vom **o/r-Designer** nicht unterstützt wird, z. b. [CLR-benutzerdefinierte Typen](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Erstellen Sie eine auf der gewünschten Tabelle basierende Ansicht, in der der nicht unterstützte Datentyp nicht enthalten ist.

2. Ziehen Sie die Ansicht von **Server-Explorer** oder **Datenbank-Explorer** auf den Designer.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
