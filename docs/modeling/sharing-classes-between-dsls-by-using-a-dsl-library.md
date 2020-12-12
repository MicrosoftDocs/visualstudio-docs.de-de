---
title: Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
description: Erfahren Sie, wie Sie im Visual Studio-SDK für Visualisierung und Modellierung eine unvollständige DSL-Definition erstellen können, die Sie in eine andere DSL importieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1685fe4fc7db6728ebc1ca6a12e27bb6f42589b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363756"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
Im Visual Studio-Visualisierungs-und Modellierungs-SDK können Sie eine unvollständige DSL-Definition erstellen, die Sie in eine andere DSL importieren können. Auf diese Weise können Sie allgemeine Teile von ähnlichen Modellen berücksichtigen.

## <a name="creating-and-using-dsl-libraries"></a>Erstellen und Verwenden von DSL-Bibliotheken

#### <a name="to-create-a-dsl-library"></a>So erstellen Sie eine DSL-Bibliothek

1. Erstellen Sie ein neues DSL-Projekt, und wählen Sie die Vorlage DSL Library Solution aus.

     Ein einzelnes DSL-Projekt wird mit einem leeren Modell erstellt.

2. Sie können Domänen Klassen, Beziehungen, Formen usw. hinzufügen.

     Die Elemente in der Bibliothek müssen keinen einzelnen Einbettungs Baum bilden.

     Um eine Beziehung zu definieren, die Importierer verwenden kann, erstellen Sie zwei Domänen Klassen, und erstellen Sie die Beziehung zwischen Ihnen.

     Legen Sie den **Vererbungsmodifizierer** der Domänen Klassen auf fest `Abstract` .

3. Sie können Elemente hinzufügen, die Sie im DSL-Explorer definieren, z. b. Verbindungs-Generatoren.

4. Sie können Anpassungen hinzufügen, die zusätzlichen Code erfordern, z. b. Validierungs Einschränkungen.

5. Klicken Sie auf **alle Vorlagen transformieren**.

6. Erstellen Sie das Projekt.

7. Wenn Sie die DSL für andere zu verwendende Personen verteilen, müssen Sie sowohl die kompilierte Assembly (dll) als auch die Datei bereitstellen `DslDefinition.dsl` . Sie finden die kompilierte Assembly in einem Ordner unter `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>So importieren Sie eine DSL-Bibliothek

1. Klicken Sie in einer anderen DSL-Definition im **DSL-Explorer** mit der rechten Maustaste auf die Stamm Klasse der DSL, und klicken Sie dann auf **neuen dsllibrary-Import hinzufügen**.

2. Legen Sie in der Eigenschaftenfenster den **Dateipfad** der Bibliothek fest. Sie können entweder einen relativen oder einen absoluten Pfad verwenden.

    Die importierte Bibliothek wird im DSL-Explorer im schreibgeschützten Modus angezeigt.

3. Sie können die importierten Klassen als Basisklassen verwenden. Erstellen Sie eine Domänen Klasse in der importierten DSL, und legen Sie in der Eigenschaftenfenster **Basisklasse** auf eine importierte Klasse fest.

4. Klicken Sie auf Alle Vorlagen transformieren.

5. Fügen Sie dem DSL-Projekt einen Verweis auf die Assembly (dll) hinzu, die vom DSL-Bibliotheksprojekt erstellt wurde.

6. Erstellen Sie die Projektmappe.

   In einer DSL-Bibliothek können andere Bibliotheken importiert werden. Wenn Sie eine Bibliothek importieren, werden die zugehörigen Importe auch automatisch im DSL-Explorer angezeigt.

## <a name="see-also"></a>Siehe auch

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
