---
title: Roadmap für die Erweiterung des Debuggers | Microsoft-Dokumentation
description: Die Visual Studio-debuggingdokumentation enthält Beispiele, eine Referenz und verschiedene Szenarien, die typische Möglichkeiten zum Anpassen des Debuggers veranschaulichen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be0f746a849a8370b145a46f9fbf6340a1dc98fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961091"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap für die Erweiterung des Debuggers
Diese Dokumentation enthält Anleitungen und Referenzinformationen zum Erweitern des [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] Debuggers mit dem [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die debuggingdokumentation enthält Beispiele, eine umfassende Referenz und einige repräsentative Szenarios, in denen typische Möglichkeiten zum Anpassen des Debuggers aufgezeigt werden.

 Der Compiler und seine Ausgabe bestimmen, was zum Einrichten des Debuggens in Ihrem Produkt erforderlich ist. Wenn der Compiler Folgendes:

- Gibt das systemeigene Windows-Betriebssystem an und schreibt *. PDB* -Datei: Sie können Programme mit dem systemeigenen Code Debug Engine (de) Debuggen, das in integriert ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Sie müssen keine de-oder-Ausdrucks Auswertung implementieren. Die Ausdrucks Auswertung wird für die Syntax der Programmiersprache C++ geschrieben.

- Erzeugt die MSIL-Ausgabe (Microsoft Intermediate Language). Sie können Programme mit dem verwalteten Code Debugmodul de Debuggen, das auch in integriert ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Daher muss nur eine Ausdrucks Auswertung implementiert werden. Eine Beispiel Ausdrucks Auswertung wird für Sie bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:

   [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)

   [Ausdrucks Auswertungs Kontext](../../extensibility/debugger/expression-evaluation-context.md)

   [Ausdrucks Auswertung im Break-Modus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Schreiben einer Common Language Runtime Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Als Ziel für ein proprietäres Betriebssystem oder eine andere Laufzeitumgebung müssen Sie Ihre eigene de schreiben. Ein Tutorial, das eine einfache de mithilfe von ATL-COM erstellt, wird bereitgestellt. Weitere Informationen finden Sie unter den folgenden Themen:

   [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: Erstellen einer Debug-Engine mithilfe von ATL-COM](/previous-versions/bb147024(v=vs.90))

   [Implementieren eines Port Anbieters](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)