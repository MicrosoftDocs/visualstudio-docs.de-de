---
title: SQL kann SSDEBUGPS nicht finden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67d7602357a39cbdce0c96b494f4c02758533e73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871389"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL kann SSDEBUGPS nicht finden

SSDEBUGPS.dll ist die Hostkomponente von SQL Server-Debuggen.

Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer ist. Mögliche Ursachen sind: Entweder wurde Remotedebuggen-Setup nie ausgeführt, oder diese Datei wurde gelöscht.

Es gibt zwei Möglichkeiten, diesen Fehler zu beheben: Entweder führen Sie Remotedebuggen-Setup erneut aus, oder Sie kopieren die Datei auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer.

Wenn Sie Remotedebuggen-Setup erneut ausführen möchten, folgen Sie den Anweisungen unter [Remotedebuggen](../debugger/remote-debugging.md).

Wenn Sie eine Kopie von „ssdebugps.dll“ finden, können Sie sie auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer kopieren. Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \Programme\Gemeinsame Dateien\Microsoft Shared\SQL-Debuggen. Sie finden sie möglicherweise auf einem anderen [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer oder auf einem Computer, auf dem Visual Studio 2005 installiert ist.

So kopieren Sie „SSDEBUGPS.dll“ auf den SQL Server 2005-Computer:

1. Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer.

2. Registrieren Sie sie, indem Sie eine **Eingabeaufforderung** öffnen und den folgenden Befehl ausführen:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
