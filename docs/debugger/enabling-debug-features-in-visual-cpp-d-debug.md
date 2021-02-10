---
title: Aktivieren von Debugfunktionen in C++-Projekten (-D_DEBUG) | Microsoft-Dokumentation
description: In Visual C++ aktivieren Sie Debugfeatures, indem Sie _DEBUG definieren. In diesem Artikel werden die hierfür erforderlichen Schritte erklärt sowie wie Sie ein MFC-Programm verknüpfen, um es zu debuggen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: c0a8941fbda263ce3a2345a135594d2f9eec87e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871896"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Aktivieren von Debugfunktionen in C++-Projekten (/D_DEBUG)
Wenn Sie das Programm mit definiertem **_DEBUG**-Symbol kompilieren, aktivieren Sie damit die Debugfunktion in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], (z.B. Assertionen). Sie können **_DEBUG** auf zwei Arten definieren:

- Geben Sie im Quellcode **#define _DEBUG** an, oder

- Geben Sie die **/D_DEBUG**-Compileroption an. (Wenn Sie das Projekt in Visual Studio mit Assistenten erstellen, wird **/D_DEBUG** automatisch in der Debugkonfiguration definiert.)

  Wenn **_DEBUG** definiert wird, kompiliert der Compiler Codeabschnitte, die in **#ifdef _DEBUG** und `#endif` eingeschlossen sind.

  Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die korrekte MFC-Bibliotheksversion, mit der verknüpft werden soll, wird auf der Grundlage der definierten Symbole, z.B. **_DEBUG** und **_UNICODE**, von den MFC-Headerdateien bestimmt. Einzelheiten dazu finden Sie unter [Versionen der MFC-Bibliothek](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Siehe auch
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)