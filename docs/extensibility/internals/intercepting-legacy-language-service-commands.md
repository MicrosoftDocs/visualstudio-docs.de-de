---
title: Abfangen von Legacy-Sprachdienst Befehlen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Befehls Filter in Visual Studio verwenden, um Legacy-Sprachdienst Befehle abzufangen und sprachspezifisches Verhalten hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6a759f0cef7329d14d7d1472d38f662c0206448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839793"
---
# <a name="intercepting-legacy-language-service-commands"></a>Abfangen von Befehlen von Legacysprachdiensten
Mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Sie den Sprachdienst Befehle abfangen, die von der Textansicht andernfalls behandelt werden. Dies ist nützlich für sprachspezifisches Verhalten, das von der Textansicht nicht verwaltet wird. Sie können diese Befehle abfangen, indem Sie der Textansicht einen oder mehrere Befehls Filter aus dem Sprachdienst hinzufügen.

## <a name="getting-and-routing-the-command"></a>Erhalten und Weiterleiten des Befehls
 Ein Befehls Filter ist ein <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt, mit dem bestimmte Zeichensequenzen oder Schlüsselbefehle überwacht werden. Sie können einer einzelnen Textansicht mehrere Befehls Filter zuordnen. Jede Textansicht verwaltet eine Kette von Befehls Filtern. Nachdem Sie einen neuen Befehls Filter erstellt haben, fügen Sie der Kette den Filter für die entsprechende Textansicht hinzu.

 Wenden Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode für den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> an, um der Kette den Befehls Filter hinzuzufügen. Wenn Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Befehl ausführen, gibt einen weiteren Befehls Filter zurück, an den Sie die Befehle übergeben können, die der Befehls Filter nicht behandelt.

 Die folgenden Optionen stehen für die Befehls Behandlung zur Verfügung:

- Behandeln Sie den Befehl, und übergeben Sie dann den Befehl an den nächsten Befehls Filter in der Kette.

- Behandeln Sie den Befehl, und übergeben Sie den Befehl nicht an den nächsten Befehls Filter.

- Behandeln Sie den Befehl nicht, sondern übergeben Sie den Befehl an den nächsten Befehls Filter.

- Ignorieren Sie den Befehl. Behandeln Sie Sie nicht im aktuellen Filter, und übergeben Sie Sie nicht an den nächsten Filter.

  Informationen zu den Befehlen, die ihr Sprachdienst verarbeiten soll, finden Sie unter [wichtige Befehle für Sprachdienst Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).
