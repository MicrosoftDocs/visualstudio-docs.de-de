---
title: Nicht verwendete Werte und Parameter
description: Hier erfahren Sie mehr über nicht verwendete Wertzuweisungen, Variablen und Parameter und wie diese im Code-Editor in Visual Studio angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8768992ce3ef9f40ab0adba1724d43b32e5bde5c
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560706"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Nicht verwendete Wertzuweisungen, Variablen und Parameter

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Nicht verwendete Parameter werden ausgeblendet, und eine Warnung für nicht verwendete Ausdruckswerte generiert. Der Compiler führt außerdem eine Datenflussanalyse durch, um nicht verwendete Wertzuweisungen zu finden. Nicht verwendete Wertzuweisungen werden abgeblendet dargestellt, und eine Glühbirne mit einer [Schnellen Aktion](../quick-actions.md) wird angezeigt, um die redundante Zuweisung zu entfernen. Für nicht verwendete Variablen mit unbekannten Werten wird dagegen ein Vorschlag einer [Schnellen Aktion](../quick-actions.md) angezeigt, [Ausschussvariablen](/dotnet/csharp/discards) zu verwenden. (Ausschussvariablen sind temporäre Platzhaltervariablen, die im Anwendungscode bewusst nicht verwendet werden. Sie können die Speicherbelegung reduzieren und die Lesbarkeit Ihres Codes verbessern.)

**Hintergrund:** Sie haben Wertzuweisungen, Parameter oder Ausdruckswerte, die nicht verwendet werden.

**Vorteile**: Manchmal ist es gar nicht so einfach, zu bestimmen, ob eine Wertzuweisung, eine Variable oder ein Parameter noch verwendet wird. Indem diese Werte ausgeblendet werden oder ein Warnhinweis generiert wird, erhalten Sie einen sichtbaren Hinweis darauf, welchen Code Sie löschen können.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnose nicht verwendeter Ausdruckswerte und Parameter

1. Nehmen Sie eine beliebige Wertzuweisung, Variable oder Parameter, die bzw. der nicht verwendet wird.
2. Die nicht verwendete Zuweisung oder der Parameter wird abgeblendet dargestellt. Für den nicht verwendeten Ausdruckswert wird eine Warnung generiert.

  ![Nicht verwendeter Parameter](media/unused-parameter.png)
  ![Nicht verwendeter Wert](media/unused-value.png)
  ![Nicht verwendete Wertzuweisung](media/unused-value-assignment.png)
  ![Nicht verwendete Wertausschussvariable](media/unused-value-discard.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
