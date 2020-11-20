---
title: Nicht unterstützter Datenbankanbieter
description: Die ausgewählte Verbindung verwendet einen nicht unterstützten Datenbankanbieter. Anzeigen von Informationen zu dieser Visual Studio-objektrelationaler Designer Meldung (O/R-Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 06e08f9a9c28698ae2ee2fecfbcec64c39666c8a
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998346"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.

Diese Meldung wird angezeigt, wenn Sie Elemente ziehen, die nicht den .NET Framework Datenanbieter für SQL Server von **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)verwenden.

Der **O/R-Designer** unterstützt nur Datenverbindungen, bei denen der .NET Framework Anbieter für SQL Server verwendet wird. Nur Verbindungen zu Microsoft SQL Server oder zur Microsoft SQL Server-Datenbankdatei sind gültig.

Um diesen Fehler zu beheben, fügen Sie nur Elemente aus Datenverbindungen hinzu, die die .NET Framework Datenanbieter für die SQL Server zum **O/R-Designer** verwenden.

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Data.SqlClient>
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
