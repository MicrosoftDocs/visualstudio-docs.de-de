---
title: Anweisungs Vervollständigung in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie, wie die Anweisungs Vervollständigung funktioniert und wie Sie in einem VSPackage in Ihrem Legacy Sprachdienst implementiert wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 815b47a700e87852596d7a65e341953f65b66cf9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894828"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Anweisungsvervollständigung in einem Legacysprachdienst
Die Anweisungs Vervollständigung ist der Prozess, mit dem der Sprachdienst Benutzern hilft, ein sprach Schlüsselwort oder Element zu beenden, das Sie im Kern-Editor eingegeben haben. In diesem Thema wird erläutert, wie die Anweisungs Vervollständigung funktioniert und wie Sie in Ihrem Sprachdienst implementiert wird.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren der Anweisungs Vervollständigung finden Sie unter Exemplarische Vorgehensweise [: Anzeigen der Anweisungs Vervollständigung](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="implementing-statement-completion"></a>Implementieren von Anweisungs Abschluss
 Im Kern-Editor wird mit der Anweisungs Vervollständigung eine spezielle Benutzeroberfläche aktiviert, die Ihnen interaktiv hilft, Code einfacher und schneller zu schreiben. Mithilfe der Anweisungs Vervollständigung können relevante Objekte oder Klassen bei Bedarf angezeigt werden. Dies vermeidet, dass Sie bestimmte Elemente merken müssen, oder dass Sie Sie in einem Hilfe Referenz Thema nachschlagen müssen.

 Zum Implementieren der Anweisungs Vervollständigung muss die Sprache einen Anweisungs Vervollständigungs-, der analysiert werden kann. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]Verwendet z. b. einen Punkt Operator (.), während [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] einen Pfeil (->)-Operator verwendet. Ein Sprachdienst kann mehr als einen-auslösen verwenden, um die Anweisungs Vervollständigung zu initiieren. Diese Trigger werden im Befehls Filter programmiert.

## <a name="command-filters-and-triggers"></a>Befehls Filter und-Trigger
 Befehls Filter fangen Vorkommen des Triggers oder der Trigger ab. Um der Ansicht den Befehls Filter hinzuzufügen, implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Sie die-Schnittstelle, und fügen Sie Sie an die Ansicht an, indem Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode aufrufen. Sie können denselben Befehls Filter ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) für alle Aspekte Ihres sprach Dienstanbieter verwenden, z. b. Anweisungs Vervollständigung, Fehlermarkierungen und Methoden Tipps. Weitere Informationen finden Sie unter [intercepting Legacy Language Service Commands](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Wenn der-Editor im Editor – insbesondere im Text Puffer – eingegeben wird, ruft der Sprachdienst die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode auf. Dies bewirkt, dass der Editor die Benutzeroberfläche aufführt, sodass der Benutzer aus den Kandidaten der Anweisungs Vervollständigung wählen kann. Diese Methode erfordert, dass Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> und die <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> Flags als Parameter implementieren. Die Liste der Vervollständigungs Elemente wird in einem scrolllistenfeld angezeigt. Wenn der Benutzer die Eingabe fortsetzt, wird die Auswahl im Listenfeld aktualisiert, um die nächstgelegene Entsprechung zu den zuletzt eingegebenen Zeichen widerzuspiegeln. Der Kern-Editor implementiert die Benutzeroberfläche für die Anweisungs Vervollständigung, aber der Sprachdienst muss die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle implementieren, um einen Satz von Kandidaten Vervollständigungs Elementen für die Anweisung zu definieren.

## <a name="see-also"></a>Weitere Informationen
- [Abfangen von Befehlen von Legacysprachdiensten](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
