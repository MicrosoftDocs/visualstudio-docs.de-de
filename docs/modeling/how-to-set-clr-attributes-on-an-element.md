---
title: 'Gewusst wie: Festlegen von CLR-Attributen für ein Element'
description: Erfahren Sie, wie Sie jedes Attribut hinzufügen können, das von der System. Attribute-Klasse erbt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9f8b16edcbe575ebac67f4acde9111a9511b85
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363847"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Gewusst wie: Festlegen von CLR-Attributen für ein Element
Benutzerdefinierte Attribute sind spezielle Attribute, die Domänen Elementen, Formen, Connectors und Diagrammen hinzugefügt werden können. Sie können beliebige Attribute hinzufügen, die von der- `System.Attribute` Klasse erben.

### <a name="to-add-a-custom-attribute"></a>Hinzufügen eines benutzerdefinierten Attributs

1. Wählen Sie im **DSL-Explorer** das Element aus, dem Sie ein benutzerdefiniertes Attribut hinzufügen möchten.

2. Klicken Sie im **Eigenschaften** Fenster neben der Eigenschaft **benutzerdefinierte Attribute** auf das Symbol zum Durchsuchen (**..**.).

     Das Dialogfeld **Attribute bearbeiten** wird geöffnet.

3. Klicken Sie in der Spalte **Name** auf, **\<add attribute>** und geben Sie den Namen des Attributs ein. Drücken Sie die EINGABETASTE.

4. Die Zeile unter dem Attributnamen zeigt Klammern an. Geben Sie in dieser Zeile einen Parametertyp für das Attribut ein (z. b. `string` ), und drücken Sie dann die EINGABETASTE.

5. Geben Sie in der Spalte **Name-Eigenschaft** einen geeigneten Namen ein, z `MyString` . b..

6. Klicken Sie auf **OK**.

     Die Eigenschaft **benutzerdefinierte Attribute** zeigt nun das Attribut im folgenden Format an:

     `[`*AttributeName* `(` *Parameter Name* `=` *Typ*`)]`

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))