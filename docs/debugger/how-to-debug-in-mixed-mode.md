---
title: Debuggen im gemischten Modus | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie das Debuggen im gemischten Modus (verwalteter und nativer Code) auf den Eigenschaftenseiten des Projekts der aufrufenden App aktivieren.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1144fa2f775427a3a46feda46d8bba015e960f2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913250"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Vorgehensweise: Debuggen im gemischten Modus (C#, C++, Visual Basic)

In den folgenden Verfahren wird beschrieben, wie Sie das Debuggen für verwalteten und nativen Code aktivieren. Dies wird auch als Debuggen im gemischten Modus bezeichnet. Es gibt zwei Szenarien für das Debuggen im gemischten Modus:

- Die App, die eine DLL aufruft, ist in nativem Code geschrieben, und die DLL wird verwaltet.

- Die App, die eine DLL aufruft, ist in verwaltetem Code geschrieben und die DLL in nativem Code. Ein Tutorial, in dem Sie ausführlich durch dieses Szenario geführt werden, finden Sie unter [Debuggen von verwaltetem und nativem Code](../debugger/how-to-debug-managed-and-native-code.md).

Sie können sowohl verwaltete als auch native Debuggger auf den Seiten **Eigenschaften** des Projekts der aufrufenden App aktivieren. Die Einstellungen unterscheiden sich zwischen nativen und verwalteten Apps.

Wenn Sie keinen Zugriff auf das Projekt einer aufrufenden App haben, können Sie die DLL aus dem DLL-Projekt debuggen. Der gemischte Modus ist nicht erforderlich, wenn Sie nur das DLL-Projekt debuggen. Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Abhängig von Ihren Visual Studio-Einstellungen oder Ihrer Visual Studio-Edition können sich die Dialogfelder und Befehle von den in diesem Artikel beschriebenen Dialogfeldern und Menübefehlen unterscheiden. Wenn Sie Ihre Einstellungen ändern möchten, wählen Sie **Extras** > **Einstellungen importieren und exportieren** aus. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Aktivieren des Debuggens im gemischten Modus für eine native aufrufende App

1. Wählen Sie in **Projektmappen-Explorer** das C++-Projekt aus, klicken Sie auf das Symbol **Eigenschaften**, und drücken Sie **ALT**+**EINGABETASTE**, oder klicken Sie mit der rechten Maustaste, und wählen Sie **Eigenschaften** aus.

1. Erweitern Sie im Dialogfeld **\<Project>-Eigenschaftenseiten** den Knoten **Konfigurationseigenschaften**, und wählen Sie dann **Debugging** aus.

1. Legen Sie **Debuggertyp** auf **Gemischt** oder **Automatisch** fest.

1. Klicken Sie auf **OK**.

   ![Debuggen im gemischten Modus aktivieren](../debugger/media/dbg-mixed-mode-from-native.png "Debuggen im gemischten Modus aktivieren")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Aktivieren des Debuggens im gemischten Modus für eine verwaltete aufrufende App

1. Wählen Sie in **Projektmappen-Explorer** das C#- oder Visual Basic-Projekt aus, wählen Sie das Symbol **Eigenschaften** aus, und drücken Sie **ALT**+**EINGABETASTE**, oder klicken Sie mit der rechten Maustaste, und wählen Sie **Eigenschaften** aus.

1. Wählen Sie die Registerkarte **Debuggen** aus, und wählen Sie dann **Debuggen von nativem Code aktivieren** aus.

1. Schließen Sie die Eigenschaftenseite, um die Änderungen zu speichern.

   ![Debuggen von nativem Code aktivieren](../debugger/media/dbg-mixed-mode-from-csharp.png "Debuggen von nativem Code aktivieren")

> [!NOTE]
> In den meisten Visual Studio Versionen ab Visual Studio 2017 müssen Sie die Datei *launchSettings.json* statt der Projekteigenschaften verwenden, um das Debuggen im gemischten Modus für nativen Code in einer .NET Core-App zu aktivieren. Ausführlichere Informationen finden Sie unter [Debuggen von verwaltetem und nativem Code](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Siehe auch

- [How to: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md)