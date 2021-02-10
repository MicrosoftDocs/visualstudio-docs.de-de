---
title: 'Warnung: Skriptdebuggen deaktiviert | Microsoft-Dokumentation'
description: In diesem Artikel wird die Warnung „Skriptdebuggen deaktiviert“ erläutert, die auftritt, wenn Sie versuchen, ein Skript zu debuggen, ohne das Debuggen von Skripts im Internet Explorer zuzulassen. Außerdem werden die Schritte zum Aktivieren dieser Funktion erläutert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 052445b1dbb69c433220caf5764413e04f0909fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883999"
---
# <a name="warning-script-debugging-disabled"></a>Warnung: Skriptdebuggen deaktiviert
Skriptdebuggen ist in Internet Explorer derzeit deaktiviert

 Diese Warnung wird ausgegeben, wenn Sie versuchen, Skripts zu debuggen, ohne dass Skriptdebuggen in Internet Explorer aktiviert ist. Das Skriptdebuggen ist in Internet Explorer aus Sicherheitsgründen standardmäßig deaktiviert.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>So aktivieren Sie das Skriptdebuggen in Internet Explorer

1. Wählen Sie in Internet Explorer im Menü **Extras** die Option **Internetoptionen** aus.

2. Klicken Sie im Dialogfeld **Internetoptionen** auf die Registerkarte **Erweitert**.

3. Zeigen Sie auf der Registerkarte **Erweitert** unter der Kategorie **Browsen** das Feld **Einstellungen** an.

4. Deaktivieren Sie **Skriptdebugging deaktivieren (Internet Explorer)** .

5. Klicken Sie auf **OK**.

6. Beenden Sie Internet Explorer, und starten Sie die Anwendung neu.

     Die neuen Einstellungen sind jetzt wirksam.

## <a name="see-also"></a>Siehe auch
- [How to: Anfügen an ein Skript](attach-to-running-processes-with-the-visual-studio-debugger.md)