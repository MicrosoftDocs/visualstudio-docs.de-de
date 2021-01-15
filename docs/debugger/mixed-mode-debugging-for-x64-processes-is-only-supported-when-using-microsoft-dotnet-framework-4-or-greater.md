---
title: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
description: .NET Framework-Versionen vor Version 4 bieten keine Unterstützung für das Debuggen im gemischten Modus von x64-Prozessen. In diesem Artikel finden Sie Problemumgehungen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039f97fc102e98ba0b6809c4aae402c0f26c5cc1
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975224"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
.NET Framework-Versionen vor Version 4 bieten keine Unterstützung für das Debuggen im gemischten Modus von x64-Prozessen. Das bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu nativem Code oder von nativem Code zu verwaltetem Code wechseln können.

### <a name="workarounds"></a>Problemumgehung

- Aktualisieren Sie das Projekt, um Microsoft .NET Framework 4 oder höher zu verwenden.

     - oder -

     Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.

     - oder -

     Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>So ändern Sie die Plattform in 32-Bit (Visual Basic oder C#)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.

3. Klicken Sie auf **Plattform**, und wählen Sie x86 aus der Liste der Plattformen aus.

     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32-Bit-Prozess wünschen.

### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie Win32 aus der Liste der Plattformen aus.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Siehe [Einrichten von SQL-Debuggen](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Siehe auch
- [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)