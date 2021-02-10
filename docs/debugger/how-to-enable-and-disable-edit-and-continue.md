---
title: Aktivieren und Deaktivieren von „Bearbeiten und Fortfahren“ | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie zur Entwurfszeit „Bearbeiten und Fortfahren“ in den Visual Studio-Optionen deaktivieren und aktivieren. Die Funktion "Bearbeiten und Fortfahren" funktioniert nur in Debugversionen.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 51ff58b02e4ea0a197b6a13f12487226269413ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884376"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Vorgehensweise: Aktivieren und Deaktivieren von „Bearbeiten und Fortfahren“ (C#, VB und C++)

Sie können im Visual Studio-Dialogfeld **Optionen** die Option **Bearbeiten und Fortfahren** zur Entwurfszeit aktivieren oder deaktivieren. Die Funktion **Bearbeiten und Fortfahren** funktioniert nur in Debugversionen. Weitere Informationen hierzu finden Sie unter [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

Bei nativem C++ erfordert **Bearbeiten und Fortfahren** die Verwendung der `/INCREMENTAL`-Option. Weitere Informationen zu den Featureanforderungen in C++ finden Sie in diesem [Blogbeitrag](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) und unter [Bearbeiten und Fortfahren (C++)](../debugger/edit-and-continue-visual-cpp.md).

**Aktivieren oder Deaktivieren von „Bearbeiten und Fortfahren“:**

1. Wenn Sie sich in einer Debugsitzung befinden, beenden Sie das Debuggen (**Debuggen** > **Debuggen beenden** oder **UMSCHALT**+**F5**).

1. Klicken Sie unter **Extras** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen** > **Allgemein** im rechten Bereich auf **Bearbeiten und Fortfahren**.

    > [!NOTE]
    > Wenn IntelliTrace aktiviert ist und Sie IntelliTrace-Ereignisse und Aufrufinformationen erfassen, wird "Bearbeiten und Fortfahren" deaktiviert. Weitere Informationen finden Sie unter [IntelliTrace für Visual Studio Enterprise (C#, Visual Basic, C++)](../debugger/intellitrace.md).

1. Stellen Sie bei C++-Code sicher, dass **Natives Bearbeiten und Fortfahren aktivieren** ausgewählt ist, und legen Sie die zusätzlichen Optionen fest:
    - **Änderungen beim Fortfahren anwenden (nur nativ)**

      Wenn diese Option ausgewählt ist, werden Codeänderungen von Visual Studio automatisch kompiliert und angewendet, wenn Sie das Debuggen fortsetzen. Andernfalls können Sie Änderungen mithilfe von **Debuggen** > **Codeänderungen übernehmen** anwenden.

    - **Warnung bei veraltetem Code (nur nativ)**

      Wenn diese Option ausgewählt ist, werden Warnungen zu veraltetem Code ausgegeben.

1. Klicken Sie auf **OK**.
