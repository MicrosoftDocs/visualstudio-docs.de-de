---
title: „Bearbeiten und fortfahren“ wird für F# nicht unterstützt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4fef61335679e3f82d5916726981e003bf9c332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428456"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Bearbeiten und Fortfahren wird für F# nicht unterstützt #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Debuggen von F#-Code wird Bearbeiten und Fortfahren nicht unterstützt. Das Bearbeiten von F#-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden. Codeänderungen werden während der Debugsitzung nicht übernommen. Daher führen alle während des Debuggens an F#-Code vorgenommenen Bearbeitungen dazu, dass der Quellcode nicht mit dem gerade gedebuggten Code übereinstimmt.
