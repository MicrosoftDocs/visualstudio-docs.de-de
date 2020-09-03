---
title: Festlegen eines Hintergrund Bilds in einem Diagramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b7d206852101a1d99a08eac710d88e93afe4a04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671209"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Festlegen eines Hintergrundbilds für ein Diagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Visualisierungs- und Modellierungs-SDK von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] können Sie das Hintergrundbild für einen generierten Designer mithilfe von benutzerdefiniertem Code festlegen.

## <a name="setting-the-background-image"></a>Hintergrundbild festlegen

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>So legen Sie ein Hintergrundbild für einen generierten Designer fest

1. Kopieren Sie die Bilddatei, die Sie als Diagrammhintergrund verwenden möchten, in das Verzeichnis "Dsl\Resources" des aktuellen Projekts.

2. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner dsl\resources, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Element**.

3. Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zum Ordner "dsl\resources".

4. Klicken Sie in der Liste **Dateityp** auf **Bilddateien**.

5. Klicken Sie auf die Bilddatei, die Sie in das Verzeichnis kopiert haben, und klicken Sie dann auf **Hinzufügen**.

6. Klicken Sie mit der rechten Maustaste auf DSL und dann auf **Eigenschaften** , um die Eigenschaften des DSL-Projekts zu öffnen.

7. Klicken Sie auf der Registerkarte **Ressourcen** auf **dieses Projekt enthält keine Standard Ressourcen Datei. Klicken Sie hier, um eine zu erstellen.**

8. Fügen Sie die Bilddatei der Ressourcen Datei hinzu, indem Sie das Bild von **Projektmappen-Explorer** in das Fenster "Ressourcen" ziehen.

9. Öffnen Sie das Menü "Datei", und klicken Sie auf die Option zum Speichern der Projekteigenschaften.

10. Prüfen Sie, ob die Datei "Dsl\Properties\Resources.resx" vorhanden ist und die Datei "Resources.Designer.cs" enthält.

11. Wenn Resources.Designer.cs nicht vorhanden ist, klicken Sie in **Projektmappen-Explorer**auf die Datei Resources. resx.

12. Legen Sie im Fenster **Eigenschaften** die Eigenschaft `Custom Tool` auf `ResXFileCodeGenerator`fest.

13. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das DSL-Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie auf **neuer Ordner**.

14. Benennen Sie den Ordner als **Benutzer**definiert.

15. Klicken Sie mit der rechten Maustaste auf den Ordner Custom, zeigen Sie auf **Hinzufügen**, und klicken Sie auf **Neues Element**

16. Klicken Sie im Dialogfeld **Neues Element hinzufügen** in der Liste **Vorlagen** auf **Codedatei**.

17. Geben Sie im Feld **Name den Namen** ein `BackgroundImage.cs` , und klicken Sie auf **Hinzufügen**.

18. Kopieren Sie den folgenden Code in die Datei "BackgroundImage.cs", und passen Sie den Namespace, den Diagrammklassennamen und den Bilddatei-Ressourcennamen an.

     Ersetzen Sie "MyDiagramClass" durch den Namen der partiellen Diagrammklasse, die in "Dsl\GeneratedCode\Diagrams.cs" definiert ist. Den richtigen Namespace können Sie auch aus der Datei "Dsl\GeneratedCode\Diagrams.cs" abrufen.

    ```
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [navigieren und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Weitere Informationen
 [Definieren von Formen und Connectors](../modeling/defining-shapes-and-connectors.md) [Anpassen von Text-und Bildfeldern](../modeling/customizing-text-and-image-fields.md) [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md) [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
