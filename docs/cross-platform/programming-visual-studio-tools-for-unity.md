---
title: Programmieren mit Visual Studio-Tools für Unity | Microsoft-Dokumentation
description: Hier finden Sie Beispiele für die Programmierung mithilfe der VSTU-API (Visual Studio-Tools für Unity). Sie erhalten Informationen dazu, wie Sie von VSTU erstellte Projektdateien anpassen. Sie erfahren, wie Sie den Unity-Protokollrückruf mit VSTU freigeben.
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0372cfd110df77867a683b27b17f92cd70ba75aa
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039884"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programmieren von Visual Studio-Tools für Unity
In diesem Abschnitt finden Sie Beispiele für die Verwendung der Visual Studio-Tools für Unity-API.

## <a name="examples"></a>Beispiele
 Hier sind einige Beispiele, die zeigen, wie Sie Visual Studio-Tools für Unity-APIs verwenden können.

### <a name="customize-project-files-created-by-vstu"></a>Anpassen von mit VSTU erstellten Projektdateien
 Visual Studio-Tools für Unity bieten während der Generierung der Projektdatei einen Rückruf im Unity-Stil. Informationen dazu, wie Sie die Projektdatei ändern können, wenn diese erneut generiert wird, finden Sie unter [Anpassen von mit VSTU erstellten Projektdateien](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Freigeben des Unity-Protokollrückrufs für VSTU
 Visual Studio-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann. Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU-Rückruf Ihren Rückruf stören. Informationen dazu, wie Sie den Unity-Protokollrückruf mit VSTU freigeben können, finden Sie unter [Freigeben des Unity-Protokollrückrufs für VSTU](../cross-platform/share-the-unity-log-callback-with-vstu.md).
