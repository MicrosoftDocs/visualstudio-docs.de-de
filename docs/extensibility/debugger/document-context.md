---
title: Dokument Kontext | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Dokument Kontext beim Debuggen in Visual Studio, das eine Position in einer Quelldatei oder eine Position in einem Quelldokument für einen Code Kontext darstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d19830346ea09731dde608e019109f61011cd60
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915530"
---
# <a name="document-context"></a>Dokument Kontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein *Dokument Kontext*:

- Stellt eine Position in einer Quelldatei dar. Für Sprachen, in denen die Quelldatei möglicherweise nicht vorhanden ist, identifiziert ein Dokument Kontext eine Position in einem Dokument, das in der Regel von der Laufzeitumgebung generiert wird. Beispielsweise kann eine Skript-Engine ein Dokument aus einem Skript generieren. Weitere Informationen finden Sie unter [Document Position](../../extensibility/debugger/document-position.md).

- Beschreibt eine Position in einem Quelldokument, die einem Code Kontext entspricht. Der Symbol Handler ordnet dem Dokumentations Kontext einen Code Kontext zu, wobei die von einem Compiler oder einem Interpreter generierten Informationen verwendet werden.

- Wird von einer [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Schnittstelle implementiert.

## <a name="see-also"></a>Weitere Informationen
- [Code Kontext](../../extensibility/debugger/code-context.md)
- [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md)
- [Symbol Anbieter Schnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)
