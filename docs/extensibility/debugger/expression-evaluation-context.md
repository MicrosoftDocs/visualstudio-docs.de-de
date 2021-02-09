---
title: Ausdrucks Auswertungs Kontext | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Kontext der Ausdrucks Auswertung, der einen Kontext für die Ausdrucks Auswertung darstellt und vorhanden ist, wenn ein Programm an einem Haltepunkt angehalten wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 127746b06ef09496ef8f50aa874ff32e2f983f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921543"
---
# <a name="expression-evaluation-context"></a>Ausdrucks Auswertungs Kontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein **Ausdrucks Auswertungs Kontext**:

- Stellt einen Kontext für die Ausdrucks Auswertung dar. Im Allgemeinen entspricht ein Evaluierungs Kontext dem lexikalischen Gültigkeitsbereich, in dem Variablen, Parameter, Funktionen und Methoden ausgewertet werden. Ein Ausdrucks Auswertungs Kontext, der einem Stapel Rahmen zugeordnet ist, stellt z. b. den Kontext zum Auswerten lokaler Variablen, Methoden Parameter und Klassenmember bereit (falls zutreffend).

- Ist vorhanden, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst ist eine Datenstruktur, die einen analysierten Ausdruck darstellt, der zum Binden und auswerten innerhalb des angegebenen Kontexts bereit ist.

     Im Detail werden Ausdrücke mithilfe der Methode " [Parser Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " erstellt. Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und Typ der Variablen oder des Arguments und seinen Werts enthält. Diese Zeichenfolge wird im Überwachungsfenster oder im Fenster Lokal der IDE angezeigt.

     Wenn eine `BSTR` und eine [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle angegeben sind, kann eine Debug-Engine (de) eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle erstellen, indem Sie einen Ausdruck initialisieren. Bei einer `IDebugExpression2` Schnittstelle kann der Wert durch synchrone oder asynchrone Ausdrucks Auswertung einen Wert erhalten. Dieser Wert wird zusammen mit dem Namen und dem Typ der Variablen oder des Arguments zur Anzeige an die IDE gesendet.

## <a name="see-also"></a>Weitere Informationen
- [Ausdrucks Bewertungs Schnittstellen](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)
