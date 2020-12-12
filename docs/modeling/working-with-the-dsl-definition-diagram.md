---
title: Arbeiten mit dem DSL-Definitionsdiagramm
description: Erfahren Sie, dass das Diagramm einer DSL-Tool Definition ein wichtiges Tool zum Definieren einer domänenspezifischen Sprache ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d489bfde8b095e35bc652f1cdb7588b07458e48e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362833"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Arbeiten mit dem DSL-Definitionsdiagramm
Das Diagramm einer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Definition ist ein wichtiges Tool zum Definieren der domänenspezifischen Sprache. Sie können Ihrem Domänenmodell Elemente hinzufügen und Beziehungen im Diagramm festlegen. Darüber hinaus können Sie das Layout des Diagramms ändern, um dieses besser lesbar zu machen.

## <a name="the-layout-of-the-diagram"></a>Das Layout des Diagramms
 Das [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Definitions Diagramm verfügt über zwei Partitionen: die Partition **Klassen und Beziehungen** und die Partition **Diagramm Elemente** . Die Partition **Klassen und Beziehungen** zeigt Domänen Klassen, Domänen Beziehungen und Vererbung an. Die Partition **Diagramm Elemente** zeigt Form Klassen, Connector-Klassen, Swimlane-Klassen und das generierte Designer Diagramm an.

 Domänen Klassen können an mehreren Speicherorten in den **Klassen-und Beziehungs** Partitionen angezeigt werden. Eine Domänenklassendefinition zeigt eine Vererbungsstruktur an, wenn es sich um die Basisklasse für andere Domänenklassen handelt. Eine Beziehungsstruktur wird angezeigt, wenn es sich um die Quelle von einbettenden Beziehungen oder Verweisbeziehungen handelt. Domänenklassenplatzhalter werden als die Ziele der einbettenden Beziehung oder der Verweisbeziehung angezeigt. Standardmäßig werden Platzhalter Elemente angezeigt, wenn das Depot mit den **Domänen Eigenschaften** reduziert ist. Die Vererbung sowie einbettende Beziehungen oder Verweisbeziehungen werden nicht angezeigt.

 Wenn Sie eine Domänen Klasse hinzufügen, wird Sie im unteren Teil der Partition **Klassen und Beziehungen** angezeigt. Wenn Sie eine einbettende Beziehung oder eine Verweisbeziehung hinzufügen, wird diese unterhalb und rechts neben der Quelldomänenklasse gezeichnet.

 Wenn Sie Domänenklassen und Beziehungen hinzufügen, kann das Suchen nach einer bestimmten Domänenklasse unter Umständen schwierig werden. Sie können eine Domänen Klasse suchen, indem Sie im DSL- **Explorer** mit der rechten Maustaste darauf klicken und dann **in Diagramm suchen** klicken.

 In den folgenden Abschnitten wird beschrieben, wie Sie die Darstellung des Diagramms ändern können, sodass dieses besser lesbar ist.

## <a name="copying-elements"></a>Kopieren von Elementen
 Sie können die Elemente im DSL-Definitionsdiagramm kopieren, ausschneiden und einfügen.

## <a name="zooming-in-or-out-on-the-diagram"></a>Verkleinern oder Vergrößern im Diagramm
 Sie können das Diagramm vergrößern oder verkleinern, indem Sie die Symbolleiste des **DSL-Designers** verwenden, um die Zoomstufe festzulegen.

## <a name="hiding-map-lines"></a>Ausblenden von Zuordnungslinien
 Bei Zuordnungslinien handelt es sich um Linien, die zwischen einer Domänenklasse oder Domänenbeziehung und der entsprechend zugeordneten Form oder dem zugeordneten Konnektor gezeichnet werden. Sie können Karten Linien ausblenden, indem Sie auf der Symbolleiste des **DSL-Designers** auf die Schaltfläche **map Lines anzeigen** klicken. Klicken Sie erneut auf die Schaltfläche, um die Linien anzuzeigen.

## <a name="changing-the-diagram-layout"></a>Ändern des Diagrammlayouts
 Sie können das Layout der **Klassen-und Beziehungs** Partition wie folgt ändern.

### <a name="expandcollapse"></a>Erweitern/Reduzieren
 Sie können die Größe eines Depot-Shape-Elements, das eine Domänen Klasse oder eine Form darstellt, verringern, indem Sie mit der rechten Maustaste **darauf klicken und** dann auf reduzieren klicken. Dadurch wird das **Domänen Eigenschaften** Depot der Form ausgeblendet. Klicken Sie mit **der rechten** Maustaste auf die Form, und klicken Sie dann auf **erweitern**.

### <a name="move-updown"></a>Nach oben/unten verschieben
 Sie können eine Domänen Klasse oder ein Diagramm Element in der Partition nach oben oder unten verschieben, indem Sie mit der rechten Maustaste auf das Element und dann **auf nach oben** oder **nach unten** klicken. Wenn Sie ein Platzhalterelement verschieben, das als das Ziel einer einbettenden Beziehung oder einer Verweisbeziehung angezeigt wird, wird die Beziehung ebenfalls verschoben.

### <a name="expandcollapse-relationships-tree"></a>Beziehungsstruktur erweitern/reduzieren
 Wenn eine Domänen Klasse die Quell Rolle in Einbettungs-oder Verweis Beziehungen mit anderen Domänen Klassen wieder gibt, können Sie die Beziehungen ausblenden, indem Sie mit der rechten Maustaste auf die Domänen Klassendefinition und dann auf **Beziehungs** Struktur reduzieren klicken. Um die Beziehungen anzuzeigen, klicken Sie mit der rechten Maustaste auf das Definitions Element, und klicken Sie dann auf **Beziehungsstruktur erweitern**.

### <a name="expandcollapse-inheritance-tree"></a>Vererbungsstruktur erweitern/reduzieren
 Wenn eine Domänen Klasse die Basisklasse anderer Domänen Klassen ist, können Sie die Vererbungs Struktur ausblenden, indem Sie mit der rechten Maustaste auf die Domänen Klassendefinition und dann auf **Vererbungs** Struktur zuklappen klicken. Klicken Sie zum Anzeigen der Vererbungs Struktur mit der rechten Maustaste auf das Definitions Element, und klicken Sie dann auf **Vererbungs Struktur erweitern**.

### <a name="bring-tree-here"></a>Struktur verschieben
 Um das Diagramm zu konsolidieren, klicken Sie mit der rechten Maustaste auf eine Platzhalter-Domänen Klasse und klicken dann **hier** auf Struktur einfügen. Die Platzhalter-Domänenklasse wird zu einem Definitionselement und zeigt die Vererbungs- und Beziehungsstrukturen an. Das frühere Definitionselement wird zu einem Platzhalterelement, wenn es sich dabei um das Ziel einer Beziehung oder um das untergeordnete Element einer Vererbungsbeziehung handelt. Ansonsten wird es nicht länger angezeigt.

### <a name="split-tree"></a>Struktur teilen
 Sie können Vererbungs-oder Beziehungsstrukturen aufteilen, indem Sie mit der rechten Maustaste auf die Domänen Klassendefinition klicken, die Sie anzeigt, und dann auf Struktur **Teilen** klicken Das Definitionselement wird zu einem Platzhalterelement, und die Definitionsdomänenklasse wird nun zusammen mit den entsprechenden Vererbungs- und Beziehungsstrukturen unten in der Partition angezeigt.

### <a name="show-as-class"></a>Als Klasse anzeigen
 Wenn eine Domänen Beziehung abgeleitete Beziehungen aufweist oder wenn Sie Einbettungs-oder Verweis Beziehungen zu anderen Domänen Beziehungen aufweist, können Sie die Beziehung als Klasse anzeigen, indem Sie mit der rechten Maustaste auf die Beziehung klicken und dann auf **als Klasse anzeigen** klicken. Die Beziehung wird mit einem **Domänen Eigenschaften** Depot angezeigt und zeigt die Vererbungs-und Beziehungsstrukturen an.

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))