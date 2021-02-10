---
title: Die Transact-SQL-Ausführung wurde ohne Debuggen beendet | Microsoft-Dokumentation
ms.date: 11/08/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
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
ms.openlocfilehash: 660b6c8b1f8d09baf35d3d019fe80d428e9d7525
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871129"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Fehler: Das Ausführen von Transact-SQL wurde ohne Debuggen beendet

Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact-SQL- oder SQLCLR-Prozedur zu debuggen und der Debugger keine Debugmeldungen von der SQL Server-Instanz empfängt.

Dies kann durch Netzwerkprobleme oder Probleme auf der SQL Server-Instanz verursacht worden sein, die wahrscheinlichste Ursache ist jedoch ein Berechtigungsproblem.

Zwei Konten sind beteiligt:

- Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.

- Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird. Dieses Konto muss nicht unbedingt mit der Identität übereinstimmen, unter der Visual Studio ausgeführt wird, wenn die Verbindung die SQL-Authentifizierung verwendet.

  SQL-Debuggen erfordert, dass das Anwendungskonto mit dem Verbindungskonto übereinstimmen muss oder über Systemadministratorrechte verfügt.

  Wenn Sie einen SQL-Kontonamen wie „sa“ verwenden, muss das Anwendungskonto auf der SQL Server-Instanz als Systemadministrator eingerichtet sein. Standardmäßig sind Administratoren auf dem Computer, auf dem SQL Server ausgeführt wird, SQL Server-Systemadministratoren.

  So können Sie diesen Fehler korrigieren:

  - Überprüfen Sie die Berechtigungseinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen der Berechtigungen für das Debuggen von SQL Server](/previous-versions/w1bhybwz(v=vs.100))

  - Stellen Sie sicher, dass SQL-Debuggen ordnungsgemäß eingerichtet ist.

  - Weitere Informationen erhalten Sie vom Netzwerk- oder Datenbankadministrator.

## <a name="see-also"></a>Siehe auch

- [Einrichten des Transact-SQL-Debuggings](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [How to: Festlegen der Berechtigungen für das Debuggen von SQL Server](/previous-versions/w1bhybwz(v=vs.100))
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)