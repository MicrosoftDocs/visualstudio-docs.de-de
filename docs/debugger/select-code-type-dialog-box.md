---
title: Dialogfeld „Codetyp auswählen“ | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über das Dialogfeld „Codetyp auswählen“ in Visual Studio. Zum Öffnen dieses Dialogfelds öffnen Sie das Dialogfeld An den Prozess anhängen und klicken auf die Schaltfläche Auswählen.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f73f2f56a4e60d0030d897d64662ad438027d41
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205514"
---
# <a name="select-code-type-dialog-box"></a>Dialogfeld "Codetyp auswählen"

Zum Öffnen dieses Dialogfelds öffnen Sie das Dialogfeld **An den Prozess anhängen** und klicken auf die Schaltfläche **Auswählen**.

**Zu debuggenden Codetyp automatisch bestimmen**: Der entsprechende Debugger wird auf Grundlage des ausgeführten Codetyps ausgewählt.

**Diese Codetypen debuggen:** Wählen Sie in der bereitgestellten Liste die zu debuggenden Codetypen aus. Dies kann hilfreich sein, wenn [ein Fehler beim Anfügen behandelt wird](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Diese Option schränkt die Erkennung auf die Typen von Code ein, die Sie debuggen möchten.

::: moniker range=">=vs-2019"
- Blazor WebAssembly – clientseitige Blazor WebAssembly-Instanz
- GPU – Softwareemulator – In einem GPU-Softwareemulator ausgeführter C++-Code
- JavaScript (Chrome) – In Chrome ausgeführtes JavaScript
- JavaScript (Microsoft Edge – Chromium) – In auf Chromium basierendem Microsoft Edge für Windows 10 ausgeführtes JavaScript
- JavaScript CDP (V3)-Debugger – Für das Debuggen in einem CDP-Client verwendetes Chrome DevTools Protocol, Version 3
- Verwaltet (CoreCLR) – .NET Core
- Verwaltet (Native Kompilierung) – C++-/CLR-Code
- Verwaltet (v3.5, v3.0, v2.0) – .NET Framework-Code für .NET Framework 2.0 und höher (bis 3.5)
- Verwaltet (v. 4.6, v 4.5, v 4.0) – .NET Framework-Code für .NET Framework 4.0 und höher
- Nativ – C/C++
- Debuggen von Node.js – Von Node.js-Runtime gehosteter Code
- Python – Python 
- Skript – Gibt den allgemeinen Skriptdebugger für JavaScript an. Wählen Sie restriktivere Optionen, wenn sie für Ihr Szenario zutreffen, wie z. B. JavaScript (Chrome).
- T-SQL – Transact-SQL
- Unity – Unity
- Verwalteter Kompatibilitätsmodus – Gibt den Legacydebugger für verwalteten Code an, der typischerweise beim Debuggen im gemischten Modus mit C++-/CLR-Code verwendet wird (aktiviert „Bearbeiten und fortfahren“ für den gemischten Modus) oder um Erweiterungen für den Legacydebugger zu unterstützen. In den meisten Szenarien für das Debuggen im gemischtem Modus wählen Sie **Nativ** und die entsprechenden **verwalteten** Codetypen anstelle des verwalteten Kompatibilitätsmodus aus.
::: moniker-end

In den meisten Szenarien wird das Anfügen mehrerer Debugger in derselben Debugsitzung nicht unterstützt. Möglicherweise können Sie dazu eine zweite Instanz von Visual Studio verwenden.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
