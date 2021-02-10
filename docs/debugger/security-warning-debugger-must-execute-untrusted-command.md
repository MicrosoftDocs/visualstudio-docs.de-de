---
title: 'Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d845719b758d3d64280337a1ab4138f2948ee97b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838989"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen
Diese Warnmeldung wird bei Verwendung des Quellservers angezeigt. Diese Meldung besagt, dass der Befehl, den der Debugger zum Abrufen von Quellcode ausführen muss, nicht in der Liste der vertrauenswürdigen Befehle für Quellserver in der Datei "srcsvr.ini" aufgeführt ist. Wenn dies ein gültiger Befehl ist, können Sie ihn der Datei "srcsvr.ini" hinzufügen. Andernfalls sollten Sie ihn nicht ausführen. Weitere Informationen finden Sie unter [Angeben von Symbol (.pdb)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Meldungstext
 **Der Debugger muss den folgenden nicht vertrauenswürdigen Befehl ausführen, um Quellcode vom Quellserver abzurufen.**

 **Wenn die Debugsymboldatei (\*.pdb) nicht aus einer bekannten und vertrauenswürdigen Quelle stammt, ist dieser Befehl möglicherweise ungültig oder kann nicht sicher ausgeführt werden.**

 **Möchten Sie diesen Befehl ausführen?**

## <a name="uielement-list"></a>UIElement-Liste
 Textfeld: Auszuführender Befehl aus der PDB-Datei.

 Ausführen: Lässt die Ausführung des Befehls zu.

 Nicht ausführen: Beendet die Ausführung des Befehls und das Herunterladen der Datei vom Quellserver.

## <a name="see-also"></a>Siehe auch
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Quellserver](/windows/desktop/Debug/source-server-and-source-indexing)