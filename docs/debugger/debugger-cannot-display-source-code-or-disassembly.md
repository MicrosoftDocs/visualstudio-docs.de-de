---
title: Debugger kann keinen Quellcode oder Disassembly anzeigen
description: In diesem Artikel werden die Gründe für die Meldung „Debugger cannot display source code or disassembly for the current location where execution has stopped.“ (Der Debugger kann für die aktuelle Position, an der die Ausführung abgebrochen wurde, keinen Quellcode anzeigen oder keine Disassemblierung vornehmen.) erläutert.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2966405378d2a6144c921c442e7412a41c454c52
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873066"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debugger kann keinen Quellcode oder Disassembly anzeigen
Inhalt dieses Fehlers:

 Der Debugger kann keinen Quellcode oder Disassembly für die aktuelle Position anzeigen.

 Diese Fehlermeldung kann mehrere Ursachen haben:

- Während des Debuggens einer Sprache, die die Disassembly nicht unterstützt, wurde ein Haltepunkt an einer Position erreicht, für die kein Quellcode vorhanden ist. Öffnen Sie das Fenster **Haltepunkte**, suchen Sie den Haltepunkt, und löschen Sie ihn.

- Beim Debuggen von Skripts wurde ein Haltepunkt erreicht, während das Programm keine Threads enthielt. Wählen Sie im Menü **Debuggen** die Option **Schritt** oder **Weiter** aus, um das Debuggen fortzusetzen.

- Der Debugger konnte aus Sicherheitsgründen keine Stapel-, Register- und andere Kontextinformationen aus dem zu debuggenden Programm lesen. Dies passiert meistens, wenn Sie eine Webanwendung debuggen und nicht die erforderlichen Berechtigungen für den Zugriff auf das virtuelle Verzeichnis haben. Setzen Sie die Berechtigung für das virtuelle Verzeichnis auf Anonym, und führen Sie den Vorgang erneut aus.

## <a name="see-also"></a>Siehe auch
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)