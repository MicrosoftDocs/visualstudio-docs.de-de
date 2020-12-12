---
title: Steuern der Sichtbarkeit eines Symbols oder Decorator-Elements
description: Erfahren Sie, wie Sie die Sichtbarkeit eines Symbols oder Decorator-Elements abhängig vom Zustand der Eigenschaften im Modell steuern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bdf97cc10543f066665506d3e238386dc39f0d4f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363496"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Steuern der Sichtbarkeit eines Symbols oder Decorator-Elements
Ein *Decorator* ist ein Symbol oder eine Textzeile, die auf einer Form in einer domänenspezifischen Sprache (DSL) angezeigt wird. Sie können festlegen, dass der Decorator abhängig vom Zustand der Eigenschaften im Modell angezeigt und ausgeblendet wird. Beispielsweise können in einer Form, die eine Person darstellt, verschiedene Symbole angezeigt werden, die abhängig vom Geschlecht der Person, der Anzahl der untergeordneten Elemente usw. angezeigt werden.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Steuern der Sichtbarkeit eines Symbols oder Decorators
 Bei der folgenden Prozedur wird davon ausgegangen, dass Sie bereits eine Form und deren Zuordnung zu einer Domänen Klasse definiert haben. Weitere Informationen finden Sie unter Vorgehens [Weise beim Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>So steuern Sie die Sichtbarkeit eines Symbols oder Text-Decorator-Elements

1. Fügen Sie im DSL-Definitions Diagramm der Form Klasse die Symbole oder Text-Decorator hinzu, die angezeigt werden sollen.

   1. Klicken Sie mit der rechten Maustaste auf die Form Klasse, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf den erforderlichen Typ von Decorator.

   2. Legen Sie die Eigenschaft **Position** des Decorator-Objekts fest. Mehr als ein Decorator kann dieselbe Position aufweisen. Beispielsweise könnten die Symbole für männlich und weiblich die gleiche Position aufweisen.

   3. Legen Sie die Eigenschaft **Standard Symbol** eines Symbols Decorator-Objekts fest.

2. Wählen Sie die Diagramm Element Zuordnung aus, bei der es sich um die graue Linie zwischen der Shape-Klasse und der Domänen Klasse im DSL-Definitions Diagramm handelt.

3. Wählen Sie im Fenster DSL-Details auf der Registerkarte **Decorator** -Zuordnungen einen Decorator aus. Beispielsweise "maldecorator".

4. Aktivieren Sie das Kontrollkästchen **Sichtbarkeits Filter** .

5. Wenn die Domänen Eigenschaft, die die Sichtbarkeit Steuern soll, in der unmittelbaren Domänen Klasse ist, lassen **Sie Pfad zur Filter Eigenschaft** leer.

    Klicken Sie andernfalls auf das Dropdown Menü, und navigieren Sie zu der Beziehung oder der Klasse, in der sich die Eigenschaft befindet.

   - Um einen Fehlerbericht zu vermeiden, sollten Sie nicht durch eine Beziehung navigieren, die im Navigations Tool mit "*" gekennzeichnet ist.

6. Legen Sie die **Filter-Eigenschaft** auf eine Domänen Eigenschaft fest. Beispielsweise Geschlecht.

7. Fügen Sie in der Liste **Sicht barkeits Einträge** Werte dieser Domänen Eigenschaft hinzu, für die der Decorator sichtbar sein soll. Beispiel: männlich.

8. Wiederholen Sie die Schritte für jedes Symbol.

9. **Transformieren Sie alle Vorlagen**, erstellen und ausführen, und öffnen Sie ein Testdiagramm.

10. Wenn Sie den steuernden Eigenschafts Wert ändern, sollten die Decorator angezeigt und ausgeblendet werden.

    Häufig möchten Sie, dass die Sichtbarkeit durch eine komplexere Formel gesteuert wird als eine einfache Gruppe von Werten. Wenn z. b. ein Symbol von der Anzahl der Links eines bestimmten Typs abhängt, oder wenn es von einem abhängt, ob eine Zahl in einem bestimmten Bereich liegt. Verwenden Sie in diesem Fall das folgende Verfahren.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>So steuern Sie die Sichtbarkeit eines Decorator-Elements auf der Grundlage einer Formel

1. Fügen Sie der Domänen Klasse eine berechnete Domänen Eigenschaft hinzu. Legen Sie im Fenster **Eigenschaften** die folgenden Werte fest:

     **IsBrowsable =** `False` **: Hiermit wird die-Eigenschaft für den Benutzer** ausgeblendet.    

     **Art =** `Calculated` **Dies bedeutet, dass Sie Code bereitstellen, der seinen Wert berechnet** .    

     **Name** für Beispiel **decoratorcontrol**

     **Sorte** = `Boolean`

     Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speicher Eigenschaften](../modeling/calculated-and-custom-storage-properties.md).

2. Legen Sie die neue Eigenschaft zum Steuern der Decorator-Sichtbarkeit.

    1. Wählen Sie die Diagramm Element Zuordnung aus, bei der es sich um die graue Linie von der Domänen Klasse bis zur Form handelt. Öffnen Sie im Fenster " **DSL-Details** " die Registerkarte " **decoratormap** ".

    2. Aktivieren Sie das Kontrollkästchen **Sichtbarkeits Filter** .

    3. Wählen Sie in der **Filter-Eigenschaft** die Steuerelement Eigenschaft **decoratorcontrol** aus.

    4. Geben Sie unter **Sichtbarkeits Einträge** ein `True` .

3. Klicken Sie in der Symbolleiste **Projektmappen-Explorer** auf **alle Vorlagen transformieren** .

4. Klicken Sie im Menü **Erstellen** auf Projekt Mappe **Erstellen** .

5. Doppelklicken Sie auf den angezeigten Fehlerbericht: "*YourClass* enthält keine Definition für getdecoratorcontrolvalue...".

     Der Text-Editor wird unter "dsl\generatedcode\domainclasses.cs" geöffnet. Oberhalb des markierten Fehlers ist ein Kommentar, der Sie anfordert, eine Methode hinzuzufügen.

6. Beachten Sie den Namespace, die Klasse und die Methode, die fehlen.  Beispiel: Company. FamilyTree. Person. getdecoratorcontrolvalue ().

7. Schreiben Sie in einer separaten Codedatei eine partielle Klassendefinition, die die fehlende Methode enthält. Zum Beispiel:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [navigieren und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Erstellen Sie die Projekt Mappe neu.

## <a name="see-also"></a>Siehe auch

- [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)
- [Festlegen eines Hintergrundbilds für ein Diagramm](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)