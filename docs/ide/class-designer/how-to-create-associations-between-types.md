---
title: Erstellen von Zuordnungen zwischen Typen
description: Lernen Sie, Zuordnungen zwischen verschiedenen Typen im Klassen-Designer zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 713b7349a6ccd008174b0f6c13c1df768cca65b5
ms.sourcegitcommit: 60e5a8a7ee91854356797d05f3b502572c4a4884
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933556"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Vorgehensweise: Erstellen von Zuordnungen zwischen Typen im Klassen-Designer

Anhand von Assoziationslinien im **Klassen-Designer** ist zu erkennen, in welcher Beziehung Klassen in einem Diagramm stehen. Eine Assoziationslinie stellt eine Klasse dar, die der Typ einer Eigenschaft oder eines Felds einer anderen Klasse im Projekt ist. In der Regel dienen Assoziationslinien zur Darstellung der wichtigsten Beziehungen zwischen Klassen im Projekt.

Sie können alle Felder und Eigenschaften als Assoziationen anzuzeigen. Je nachdem, welche Elemente im Diagramm hervorgehoben werden sollen, ist jedoch sinnvoller, nur wichtige Member als Assoziationen anzeigen. (Sie können weniger wichtige Member als reguläre Member anzeigen oder alle ausblenden.)

> [!NOTE]
> Der **Klassen-Designer** unterstützt nur Assoziationen in eine Richtung.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>So definieren Sie im Klassendiagramm eine Assoziationslinie

1. Wählen Sie in der Toolbox unter **Klassen-Designer** die Option **Zuordnung** aus.

2. Zeichnen Sie eine Linie zwischen den beiden Formen, die Sie mithilfe einer Assoziation miteinander verbinden möchten.

     In der ersten Klasse wird eine neue Eigenschaft erstellt. Diese Eigenschaft wird als Assoziationslinie (nicht als Eigenschaft in einem Depot in der Form) mit einem Standardnamen angezeigt. Der zugehörige Typ ist die Form, auf die die Assoziationslinie weist.

## <a name="to-change-the-name-of-an-association"></a>So ändern Sie den Namen einer Assoziation

Klicken Sie auf der Diagrammoberfläche auf die Bezeichnung der Assoziationslinie, und geben Sie eine neue Bezeichnung ein.

Führen Sie alternativ die folgenden Schritte aus:

1. Wählen Sie die Form aus, in der die als Assoziation angezeigte Eigenschaft enthalten ist.

   Die Form erhält den Fokus, und die zugehörigen Member werden in den Fenstern **Klassendetails** und **Eigenschaften** angezeigt.

2. Bearbeiten Sie nun entweder im Fenster **Klassendetails** oder **Eigenschaften** das Namensfeld der Eigenschaft, und drücken Sie die **EINGABETASTE**.

   Der Name wird im Fenster **Klassendetails**, auf der Assoziationslinie, im **Eigenschaftenfenster** und im Code aktualisiert.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Wechseln zwischen Member- und Zuordnungsnotation](how-to-change-between-member-notation-and-association-notation.md)
