---
title: Code Kontext | Microsoft-Dokumentation
description: Erfahren Sie mehr über Code Kontexte beim Debuggen in Visual Studio, die eine Position im Code beschreiben, die vorhanden ist, wenn ein Programm an einem Haltepunkt angehalten wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60eabaca8d39d40649e20e022b25ce1b02bd8faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914308"
---
# <a name="code-context"></a>Code Kontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein **Code Kontext**:

- Stellt eine Abstraktion einer Position im Code bereit, wie Sie der Debug-Engine (de) bekannt ist. Für die meisten Lauf Zeit Architekturen kann ein Code Kontext als Adresse im Anweisungs Datenstrom eines Programms betrachtet werden. Bei nicht herkömmlichen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, kann ein Code Kontext auf andere Weise dargestellt werden.

- Beschreibt die aktuelle Position im Ausführungsdaten Strom des Programms, das Sie Debuggen.

- Ist nur vorhanden, wenn ein Programm an einem Haltepunkt angehalten wurde.

- Verfügt über einen zugeordneten Dokument Kontext.

- Wird von einer [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) -Schnittstelle implementiert.

## <a name="see-also"></a>Weitere Informationen
- [Dokument Kontext](../../extensibility/debugger/document-context.md)
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)
