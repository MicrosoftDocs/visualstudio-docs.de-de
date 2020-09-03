---
title: Exportieren von UML-Diagrammen in Bilddateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: b29ce2a5-0ee3-4ab7-9aa3-13ca9c6b37a2
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c095291cd02d591d9e493601b598a63c1ccb6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669652"
---
# <a name="export-uml-diagrams-to-image-files"></a>Exportieren von UML-Diagrammen in Bilddateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein UML-Dokument aus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in ein Bild exportieren, das sich unter der Programmsteuerung befindet. Dies könnte beispielsweise bei der automatischen Erstellung von Dokumenten von Interesse sein.

 Wenn Sie ein Dokument manuell als Bild exportieren möchten, können Sie die Formen eines Diagramms in andere Programme wie Word einfügen. Dokumente können auch im XPS-Format gedruckt werden. Weitere Informationen finden Sie unter [Exportieren von Diagrammen als Bilder](../modeling/export-diagrams-as-images.md).

## <a name="saving-an-image"></a>Speichern eines Bilds
 Im folgenden Code wird ein Kontextmenübefehl definiert, der ein Bild in einer Datei speichert.

> [!NOTE]
> Damit dieser Code als Menübefehl funktioniert, muss er in einer MEF-Komponente integriert werden. Weitere Informationen finden Sie unter [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

 Der Code First verwendet [IShape. GetObject](/previous-versions/ee789371(v=vs.140)) , um die <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> der zugrunde liegenden Implementierung zu erhalten. Dieser Typ verfügt über die <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.CreateBitmap%2A>-Methode.

```
namespace SaveToImage
{
  using System.ComponentModel.Composition; // for [Import], [Export]
  using System.Drawing; // for Bitmap
  using System.Drawing.Imaging; // for ImageFormat
  using System.Linq; // for collection extensions
  using System.Windows.Forms; // for SaveFileDialog
  using Microsoft.VisualStudio.Modeling.Diagrams;
    // for Diagram
  using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    // for IGestureExtension, ICommandExtension, ILinkedUndoContext
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    // for IDiagramContext
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    // for designer extension attributes

  /// <summary>
  /// Called when the user clicks the menu item.
  /// </summary>
  // Context menu command applicable to any UML diagram
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  [UseCaseDesignerExtension]
  [SequenceDesignerExtension]
  [ComponentDesignerExtension]
  [ActivityDesignerExtension]
  class CommandExtension : ICommandExtension
  {
    [Import]
    IDiagramContext Context { get; set; }

    public void Execute(IMenuCommand command)
    {
      // Get the diagram of the underlying implementation.
      Diagram dslDiagram = Context.CurrentDiagram.GetObject<Diagram>();
      if (dslDiagram != null)
      {
        string imageFileName = FileNameFromUser();
        if (!string.IsNullOrEmpty(imageFileName))
        {
          Bitmap bitmap = dslDiagram.CreateBitmap(
           dslDiagram.NestedChildShapes,
           Diagram.CreateBitmapPreference.FavorClarityOverSmallSize);
          bitmap.Save(imageFileName, GetImageType(imageFileName));
        }
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Set Enabled and Visible to specify the menu item status.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = Context.CurrentDiagram != null
        && Context.CurrentDiagram.ChildShapes.Count() > 0;
    }

    /// <summary>
    /// Menu text.
    /// </summary>
    public string Text
    {
      get { return "Save To Image..."; }
    }

    /// <summary>
    /// Ask the user for the path of an image file.
    /// </summary>
    /// <returns>image file path, or null</returns>
    private string FileNameFromUser()
    {
      SaveFileDialog dialog = new SaveFileDialog();
      dialog.AddExtension = true;
      dialog.DefaultExt = "image.bmp";
      dialog.Filter = "Bitmap ( *.bmp )|*.bmp|JPEG File ( *.jpg )|*.jpg|Enhanced Metafile (*.emf )|*.emf|Portable Network Graphic ( *.png )|*.png";
      dialog.FilterIndex = 1;
      dialog.Title = "Save Diagram to Image";
      return dialog.ShowDialog() == DialogResult.OK ? dialog.FileName : null;
    }

    /// <summary>
    /// Return the appropriate image type for a file extension.
    /// </summary>
    /// <param name="fileName"></param>
    /// <returns></returns>
    private ImageFormat GetImageType(string fileName)
    {
      string extension = System.IO.Path.GetExtension(fileName).ToLowerInvariant();
      ImageFormat result = ImageFormat.Bmp;
      switch (extension)
      {
        case ".jpg":
          result = ImageFormat.Jpeg;
          break;
        case ".emf":
          result = ImageFormat.Emf;
          break;
        case ".png":
          result = ImageFormat.Png;
          break;
      }
      return result;
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen
 [Exportieren von Diagrammen als Bilder](../modeling/export-diagrams-as-images.md) [Definieren eines Menübefehls in einem Modellierungs Diagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
