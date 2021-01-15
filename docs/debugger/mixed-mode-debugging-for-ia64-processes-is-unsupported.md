---
title: Debuggen im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt
description: Visual Studio unterstützt kein Debugging im gemischten Modus für verwalteten und nativen Code in IA64-Prozessen (Itanium). In diesem Artikel finden Sie Problemumgehungen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65969e354a5d1ed2dc1cf54ca31e6088cc19de7a
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975250"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt.
Visual Studio unterstützt kein Debugging im gemischten Modus für verwalteten und systemeigenen Code in IA64-Prozessen. Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu systemeigenem Code oder von systemeigenem Code zu verwaltetem Code wechseln können.

### <a name="workarounds"></a>Problemumgehung

- Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.

     - oder -

     Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>So ändern Sie die Plattform in 32-Bit (Visual Basic oder C#)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend im Kontextmenü auf **Eigenschaften**.

2. Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.

3. Klicken Sie auf **Plattform**, und wählen Sie x86 aus der Liste der Plattformen aus.

     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32-Bit-Prozess wünschen.

### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend im Kontextmenü auf **Eigenschaften**.

2. Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie Win32 aus der Liste der Plattformen aus.

## <a name="see-also"></a>Siehe auch
- [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)