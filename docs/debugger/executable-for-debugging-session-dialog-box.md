---
title: Ausführbare Datei für die Debugsitzung (Dialogfeld) | Microsoft-Dokumentation
description: Sie müssen eine ausführbare Datei angeben, um die DLL aufzurufen und diese zu debuggen. Hier erfahren Sie mehr über das Dialogfeld, das angezeigt wird, wenn keine ausführbare Datei angegeben ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4f1f1a88ad30d5102043571473be0d72d71a054
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863048"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Ausführbare Datei für die Debugsitzung (Dialogfeld)

Dieses Dialogfeld wird angezeigt, wenn Sie eine DLL debuggen, für die keine ausführbare Datei festgelegt wurde. In Visual Studio können DLLs nicht direkt gestartet werden. Stattdessen wird die angegebene ausführbare Datei gestartet. Sie können die DLL debuggen, wenn diese durch die ausführbare Datei aufgerufen wird.

 **Name der ausführbaren Datei** Geben Sie den Pfad zu einer ausführbaren Datei ein, mit der die zu debuggende DLL aufgerufen wird.

 **URL, von der aus auf das Projekt zugegriffen werden kann (nur ATL-Server)** Wenn Sie eine ATL-Server-DLL debuggen, geben Sie die URL ein, unter der sich das Projekt befindet.

 Nach der Eingabe werden diese Einstellungen in den Eigenschaftenseiten des Projekts gespeichert, sodass Sie diese bei späteren Debugsitzungen nicht erneut eingeben müssen. Wenn Sie diese Einstellungen ändern möchten, können Sie die Eigenschaftenseiten öffnen und die Werte ändern. Weitere Informationen zum Angeben einer ausführbaren Datei für die Debugsitzung finden Sie unter [Debuggen von DLLs](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)