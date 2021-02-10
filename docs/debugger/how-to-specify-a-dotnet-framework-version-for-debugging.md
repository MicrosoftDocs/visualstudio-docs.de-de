---
title: Angeben einer .NET Framework-Version für das Debuggen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine ältere Version von .NET Framework für das Debuggen festlegen. Der Visual Studio-Debugger unterstützt das Debuggen sowohl älterer .NET Framework-Versionen als auch der aktuellen Version.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 197cd51d31729119d48e255d038ad2e53f17a891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908365"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Hier erfahren Sie mehr über das Angeben einer älteren .NET Framework-Version für das Debuggen (C#, Visual Basic, F#).

Der Visual Studio-Debugger unterstützt das Debuggen sowohl älterer Versionen des Microsoft .NET Framework als auch der aktuellen Version. Wenn Sie eine Anwendung von Visual Studio aus starten, erkennt der Debugger stets die richtige Version des .NET Framework für die Anwendung, die Sie debuggen. Wenn die Anwendung jedoch bereits ausgeführt wird und Sie beginnen, mithilfe von **Anfügen an** zu debuggen, kann der Debugger möglicherweise nicht immer eine frühere Version des .NET Framework erkennen. Dann erhalten Sie eine Fehlermeldung, die besagt,

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

Für den seltenen Fall, dass dieser Fehler auftritt, können Sie in einem Registrierungsschlüssel die Version festlegen, die vom Debugger verwendet werden soll.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>So geben Sie eine .NET Framework-Version für das Debuggen an

1. Durchsuchen Sie das Verzeichnis Windows\Microsoft.NET\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind. Die Versionsnummern haben folgendes Format:

    `V1.1.4322`

    Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.

2. Starten Sie den **Registrierungs-Editor** (regedit).

3. Öffnen Sie im **Registrierungs-Editor** den Ordner HKEY_LOCAL_MACHINE.

4. Navigieren Sie zu: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, und klicken Sie auf **Neuer Schlüssel**. Geben Sie dem neuen Schlüssel den Namen `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. Suchen Sie unter {449EC4CC-30D2-4032-9256-EE18EB41B62B} in der Spalte **Name** den Schlüssel CLRVersionForDebugging.

   1. Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf {449EC4CC-30D2-4032-9256-EE18EB41B62B}, und klicken Sie dann auf **Neuer Zeichenfolgenwert**. Klicken Sie dann mit der rechten Maustaste auf den neuen Zeichenfolgenwert, klicken Sie auf **Umbenennen**, und geben Sie `CLRVersionForDebugging` ein.

6. Doppelklicken Sie auf **CLRVersionForDebugging**.

7. Geben Sie im Feld **Zeichenfolge bearbeiten** die .NET Framework-Versionsnummer in das Feld **Wert** ein. Zum Beispiel: V1.1.4322

8. Klicken Sie auf **OK**.

9. Schließen Sie den **Registrierungs-Editor**.

     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben. Stellen Sie außerdem sicher, dass Sie eine Version des .NET Framework verwenden, die von Visual Studio unterstützt wird. Der Debugger ist mit der aktuellen .NET Framework-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.

## <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)