---
title: Debuggen von Windows-API-Funktionen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Windows-API-Funktion debuggen, in der NT-Symbole geladen sind. Sie verwenden im 32-Bit-Code die ergänzte Form des Funktionsnamens, um den Breakpoint festzulegen.
ms.custom: SEO-VS-2020, seodec18
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d84bdc20ab4601798e1f967c1352468e750fa9bd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155212"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Wie können Funktionen der Windows-API gedebuggt werden?
Wenn Sie eine Windows API-Funktion debuggen möchten, in der NT-Symbole geladen sind, müssen Sie wie im Folgenden beschrieben vorgehen.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>So legen Sie einen Haltepunkt für eine Windows API-Funktion mit NT-Symbolen fest

- Geben Sie in den [Haltepunkt der Funktion](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file) die Namen der Funktion und der DLL ein, in der sich die Funktion befindet (siehe den [Kontextoperator](../debugger/context-operator-cpp.md)). Verwenden Sie im 32-Bit-Code die ergänzte Form des Funktionsnamens. Zum Festlegen eines Breakpoints für **MessageBeep** müssen Sie z. B. Folgendes eingeben:

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Informationen zum Abrufen des ergänzten Namens finden Sie unter [Anzeigen von ergänzten Namen](/previous-versions/5x49w699(v=vs.140)).

     Sie können den ergänzten Namen testen und ihn im Disassemblycode anzeigen. Während die Funktion im Visual Studio-Debugger angehalten ist, klicken Sie im Code-Editor oder im Aufruflistenfenster mit der rechten Maustaste auf die Funktion, und wählen Sie **Gehe zu Disassembly**.

- In 64-Bit-Code können Sie den nicht ergänzten Namen verwenden.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
