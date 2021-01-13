---
title: Untersuchen von Systemcode nach einer Ausnahme | Microsoft-Dokumentation
description: Es wird beschrieben, wie Sie Code in einem Systemaufruf untersuchen, um die Ursache einer Ausnahme zu ermitteln. Das Verfahren kann auch angewendet werden, wenn die Symbole für den Systemcode noch nicht geladen wurden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eceb9f898b4329940408e4063dc73d81e2a604a4
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903454"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Vorgehensweise: Untersuchen von Systemcode nach einer Ausnahme
Wenn eine Ausnahme auftritt, müssen Sie unter Umständen Code in einem Systemaufruf prüfen, um die Ursache für die Ausnahme zu ermitteln. Im folgenden Verfahren wird die entsprechende Vorgehensweise erläutert, wenn Sie keine Symbole für den Systemcode geladen haben oder wenn Nur mein Code aktiviert ist.

### <a name="to-examine-system-code-following-an-exception"></a>So prüfen Sie Systemcode nach einer Ausnahme

1. Klicken Sie mit der rechten Maustaste in das Fenster **Aufrufliste**, und klicken Sie dann auf **Externen Code anzeigen**.

     Wenn Nur mein Code nicht aktiviert ist, ist diese Option nicht im Kontextmenü verfügbar, und Systemcode wird standardmäßig angezeigt.

2. Klicken Sie mit der rechten Maustaste auf die externen Codeframes, die jetzt im Fenster **Aufrufliste** angezeigt werden.

3. Zeigen Sie auf **Symbole laden aus**, und klicken Sie dann auf **Microsoft-Symbolserver**.

    1. Wenn Nur mein Code aktiviert wurde, wird ein Dialogfeld angezeigt. Es gibt an, dass Nur mein Code jetzt deaktiviert wurde. Dies ist für die schrittweise Ausführung von Systemaufrufen erforderlich.

    2. Das Dialogfeld **Öffentliche Symbole werden heruntergeladen** wird angezeigt. Nach Abschluss des Downloadvorgangs wird das Dialogfeld geschlossen.

4. Sie können jetzt den Systemcode im Fenster **Aufrufliste** und anderen Fenstern prüfen. Sie können beispielsweise auf einen Aufruflistenrahmen doppelklicken, um den Code in einer Quelle oder im Fenster **Disassembly** anzuzeigen.

## <a name="see-also"></a>Siehe auch
- [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)