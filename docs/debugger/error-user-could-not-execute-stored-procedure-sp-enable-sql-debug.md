---
title: Der Benutzer konnte die gespeicherte Prozedur „sp_enable_sql_debug“ nicht ausführen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41576d83ecff9f501b56ecc3fef3878f7c8a00b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870908"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Fehler: Der Benutzer konnte die gespeicherte Prozedur „sp_enable_sql_debug“ nicht ausführen

Die gespeicherte Prozedur "sp_enable_sql_debug" konnte auf dem Server nicht ausgeführt werden. Mögliche Ursachen:

- Ein Verbindungsproblem. Es muss eine stabile Verbindung mit dem Server bestehen.

- Fehlende erforderliche Berechtigungen für den Server. Zum Debuggen auf SQL Server 2005 müssen sowohl das Konto, unter dem Visual Studio ausgeführt wird, als auch das Konto, unter dem die Verbindung mit SQL Server hergestellt wird, Mitglieder der Systemadministratoren-Rolle sein. Das Konto, mit dem die Verbindung mit SQL Server hergestellt wird, ist entweder das Windows-Benutzerkonto (bei Windows-Authentifizierung) oder ein Konto mit Benutzer-ID und Kennwort (bei SQL-Authentifizierung).

Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen der Berechtigungen für das Debuggen von SQL Server](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Siehe auch

- [How to: Festlegen der Berechtigungen für das Debuggen von SQL Server](/previous-versions/w1bhybwz(v=vs.100))
- [Einrichten des Transact-SQL-Debuggings](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))