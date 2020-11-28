---
title: 'Gewusst wie: Darstellen einer Auflistungszuordnung (Klassen-Designer)'
description: Lernen Sie, eine Auflistungszuordnung im Klassen-Designer darzustellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b1e5be53f829949cfffbdc7db727b1117aa9de8
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901075"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Vorgehensweise: Darstellen einer Auflistungszuordnung im Klassen-Designer

Eigenschaften und Felder, die Auflistungen eines anderen Typs darstellen, können als Auflistungszuordnung im Klassendiagramm angezeigt werden. Anders als bei einer regulären Zuordnung, bei der ein Feld oder eine Eigenschaft als eine Zeile dargestellt wird, welche die Eigentümerklasse mit dem Feldtyp verknüpft, wird eine Auflistungszuordnung als eine Zeile dargestellt, welche die Eigentümerklasse mit dem gesammelten Typ verknüpft.

## <a name="to-create-a-collection-association"></a>So erstellen Sie eine Auflistungszuordnung

1. Erstellen Sie verschlüsselt eine Eigenschaft oder ein Feld, deren bzw. dessen Typ selbst eine stark typisierte Auflistung ist.

2. Erweitern Sie im Klassendiagramm die Klasse so, dass Felder und Eigenschaften angezeigt werden.

3. Klicken Sie in der Klasse mit der rechten Maustaste auf das Feld oder die Eigenschaft, und wählen Sie **Als Auflistungszuordnung anzeigen** aus.

Die Eigenschaft oder das Feld wird als Zuordnungslinie dargestellt, die mit dem gesammelten Typ verknüpft ist.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Erstellen von Zuordnungen zwischen Typen](how-to-create-associations-between-types.md)
- [Entwerfen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
