---
title: Die Eigenschaft ist Teil der Zuordnung.
description: Die Eigenschaft kann nicht gelöscht werden, da sie Teil der Zuordnung ist
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d473c3aa83bc5ac4ca802067b9b9eb32073d32f1
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036209"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Die Eigenschaft &lt;Eigenschaftenname&gt; kann nicht gelöscht werden, da sie Teil der Zuordnung &lt;Zuordnungsname&gt; ist

Die ausgewählte Eigenschaft wurde als **Zuordnungseigenschaft** für die Zuordnung zwischen den in der Fehlermeldung angegebenen Klassen festgelegt. Eigenschaften können nicht gelöscht werden, wenn sie an einer Zuordnung zwischen Datenklassen beteiligt sind.

Legen Sie die **Zuordnungseigenschaft** auf eine andere Eigenschaft der Datenklasse fest, damit die gewünschte Eigenschaft gelöscht werden kann.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wählen Sie im **O/R-Designer** die Zuordnungslinie aus, die die in der Fehlermeldung angegebenen Datenklassen verbindet.

2. Doppelklicken Sie auf die Linie, um das Dialogfeld **Zuordnungs-Editor** zu öffnen.

3. Entfernen Sie die Eigenschaft aus den **Zuordnungseigenschaften**.

4. Versuchen Sie erneut, die Eigenschaft zu löschen.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)