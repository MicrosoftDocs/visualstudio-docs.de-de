---
title: Bindung an Daten im XAML-Designer
description: Erfahren Sie, wie Sie Daten an ein Steuerelement im XAML-Designer binden, indem Sie Daten Bindungseigenschaften mithilfe der Zeichenfläche und der Eigenschaftenfenster festlegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6bf3bd24b4a232899c64f6c0ecd819b0fe0f83a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961312"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>Exemplarische Vorgehensweise: Bindung an Daten im XAML-Designer

Im XAML-Designer können Sie Datenbindungseigenschaften einstellen, indem sie die Zeichenfläche und das Eigenschaftenfenster benutzen. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Daten an ein Steuerelement gebunden werden. Die exemplarische Vorgehensweise zeigt insbesondere, wie eine einfache Einkaufswagenklasse erstellt wird, die über eine [DependencyProperty](xref:Windows.UI.Xaml.DependencyProperty) mit der Bezeichnung `ItemCount` verfügt, und wie die Eigenschaft `ItemCount` an die Eigenschaft **Text** eines [TextBlock](xref:Windows.UI.Xaml.Controls.TextBlock)-Steuerelements gebunden wird.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>So erstellen Sie eine Klasse zur Verwendung als Datenquelle

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C#** oder **Visual Basic** aus, erweitern Sie den Knoten **Windows Desktop**, und wählen Sie dann die Vorlage **WPF-Anwendung** aus.

1. Geben Sie dem Projekt den Namen **BindingTest**, und wählen Sie anschließend die Schaltfläche **OK**.

1. Öffnen Sie die Datei **MainWindow.xaml.cs** (oder **MainWindow.xaml.vb**), und fügen Sie den folgenden Code hinzu. In C# fügen Sie den Code im Namespace `BindingTest` hinzu (vor der letzten schließenden Klammer in der Datei). Fügen Sie in Visual Basic einfach die neue Klasse hinzu.

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   Durch diesen Code wird der Wert „0“ (null) als Standardelementanzahl mithilfe des [PropertyMetadata](xref:Windows.UI.Xaml.PropertyMetadata)-Objekts festgelegt.

1. Klicken Sie im Menü **Datei** auf die Option **Erstellen** > **Projektmappe erstellen**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>So binden Sie die ItemCount-Eigenschaft an ein TextBlock-Steuerelement

1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für **MainWindow.xaml**, und wählen Sie **Ansicht-Designer** aus.

1. Klicken Sie in der Toolbox auf ein [Raster](xref:Windows.UI.Xaml.Controls.Grid)-Steuerelement, um es dem Formular hinzuzufügen.

1. Wenn Sie `Grid` ausgewählt haben, klicken Sie im Eigenschaftenfenster auf **Neu** neben der **DataContext**-Eigenschaft.

1. Vergewissern Sie sich, dass im Dialogfeld **Objekt auswählen** das Kontrollkästchen **Alle Assemblys anzeigen** deaktiviert ist, wählen Sie dann **ShoppingCart** unter dem **BindingTest**-Namespace aus, und klicken Sie anschließend auf die Schaltfläche **OK**.

     Die folgende Abbildung zeigt das Dialogfeld **Objekt auswählen** mit der ausgewählten Option **ShoppingCart**.

     ![Dialogfeld „Objekt auswählen“](../designers/media/blendselectobject.png)

1. Wählen Sie in der **Toolbox** ein `TextBlock`-Steuerelement aus, um es dem Formular hinzuzufügen.

1. Wenn Sie das `TextBlock`-Steuerelement ausgewählt haben, wählen Sie im Eigenschaftenfenster den Eigenschaftenmarker rechts neben der **Text**-Eigenschaft aus, und klicken anschließend auf **Datenbindung erstellen**. (Der Eigenschaftenmarker sieht wie ein kleines Feld aus.)

1. Wählen Sie im Dialogfeld „Datenbindung erstellen“ im Feld **Pfad** die **ItemCount: (int32)**-Eigenschaft aus, und klicken Sie dann auf **OK**.

     Die folgende Abbildung zeigt das Dialogfeld **Datenbindung erstellen**, wobei die Eigenschaft **ItemCount** ausgewählt ist.

     ![Dialogfeld „Datenbindung erstellen“](../designers/media/xaml_create_data_binding.png)

1. Drücken Sie **F5** , um die APP auszuführen.

     Die Steuerung `TextBlock` sollte den Standardwert von 0 als Text anzeigen.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Dialogfeld „Wertkonverter hinzufügen“](/previous-versions/hh965588(v=vs.140))