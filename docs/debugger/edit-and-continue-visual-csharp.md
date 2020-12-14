---
title: Bearbeiten und Fortfahren (Visual C#) | Microsoft-Dokumentation
description: „Bearbeiten und fortfahren“ ist für Visual C#-Projekte verfügbar. Hier erfahren Sie, welche Änderungen unterstützt werden und wie Sie steuern können, ob und wann Ihre Änderungen angewendet werden.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 55406001e4017c853895002445d9bd5d614b4b20
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862880"
---
# <a name="edit-and-continue-visual-c"></a>Bearbeiten und Fortfahren (Visual C#)
 Mit Bearbeiten und Fortfahren für C# können Sie beim Debuggen Codeänderungen im Unterbrechungsmodus vornehmen. Die Änderungen können übernommen werden, ohne die Debugsitzung anhalten und neu starten zu müssen. Im Ausführmodus ist der Quellcode-Editor schreibgeschützt.

 Die Funktion "Bearbeiten und Fortfahren" unterstützt bis auf einige Ausnahmen die meisten Änderungen, die Sie möglicherweise während einer Debugsitzung vornehmen möchten. Weitere Informationen finden Sie unter [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

 „Bearbeiten und Fortfahren“ wird in UWP in Windows 10 sowie für x86- und x64-Apps unterstützt, die für .NET Framework 4.6 oder höhere Versionen vorgesehen sind (.NET Framework ist nur als Desktopversion verfügbar).

 > [!NOTE]
 > Nicht unterstützte Apps und Plattformen sind u. a. Silverlight 5 und Windows 8.1.

 Wenn „Bearbeiten und Fortfahren“ aktiviert ist, werden unterstützte Änderungen automatisch übernommen, wenn Sie einen Ausführungsbefehl des Debuggers verwenden (z.B. **Weiter**, **Schritt**, **Nächste Anweisung festlegen**) oder eine Funktionsauswertung im Debuggerfenster durchführen.

 Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von „Bearbeiten und Fortfahren“ (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Siehe auch
- [How to: Verwenden von „Bearbeiten und fortfahren“ (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Schreiben und Debuggen von ausgeführtem XAML-Code mit XAML Hot Reload in Visual Studio](../xaml-tools/xaml-hot-reload.md)
