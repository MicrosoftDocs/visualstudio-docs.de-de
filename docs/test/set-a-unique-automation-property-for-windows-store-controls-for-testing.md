---
title: Festlegen einer eindeutigen Automatisierungseigenschaft – Testen von UWP-Steuerelementen
description: Hier erfahren Sie, wie Sie eine eindeutige Automatisierungseigenschaft auf Grundlage des XAML-Steuerelements in Ihrer XAML-basierten UWP-Anwendung zuweisen, um einen Test der programmierten UI auszuführen.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 5af4f9c70696144e0efb420ab27860a1969bddc6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328328"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Festlegen einer eindeutigen Automatisierungseigenschaft für UWP-Steuerelemente für Tests

Wenn Sie Tests der programmierten UI für Ihre XAML-basierte UWP-App ausführen möchten, muss jedes Steuerelement durch eine eindeutige Automatisierungseigenschaft gekennzeichnet werden. Sie können eine eindeutige Automatisierungseigenschaft auf Grundlage des Typs des XAML-Steuerelements in der Anwendung zuweisen.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statische XAML-Definition

Zum Angeben einer eindeutigen Automatisierungseigenschaft für ein Steuerelement, das in der XAML-Datei definiert ist, können Sie **AutomationProperties.AutomationId** oder **AutomationProperties.Name** implizit oder explizit festlegen (siehe folgende Beispiele). Durch Festlegen eines dieser Werte erhält das Steuerelement eine eindeutige Automatisierungseigenschaft, mit der das Steuerelement identifiziert werden kann, wenn Sie einen Test der programmierten UI oder eine Aktionsaufzeichnung erstellen.

### <a name="set-the-property-implicitly"></a>Implizites Festlegen der Eigenschaft

Legen Sie **AutomationProperties.AutomationId** auf **ButtonX** fest. Verwenden Sie dazu die **Name**-Eigenschaft in der XAML für das Steuerelement.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Legen Sie **AutomationProperties.Name** auf **ButtonY** fest. Verwenden Sie dazu die **Content**-Eigenschaft in der XAML für das Steuerelement.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Explizites Festlegen der Eigenschaft

Legen Sie **AutomationProperties.AutomationId** explizit in der XAML für das Steuerelement auf **ButtonX** fest.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Legen Sie **AutomationProperties.Name** explizit in der XAML für das Steuerelement auf **ButtonY** fest.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Zuweisen eindeutiger Namen

In Blend für Visual Studio können Sie eine Option auswählen, um interaktiven Elementen wie Schaltflächen, Listenfeldern, Kombinationsfeldern und Textfeldern eindeutige Namen zuzuweisen. Dadurch erhalten die Steuerelemente eindeutige Werte für **AutomationProperties.Name**.

Klicken Sie auf **Extras** > **Interaktive Elemente benennen**, um vorhandenen Steuerelementen eindeutige Namen zuzuweisen.

![„Interaktive Elemente benennen“ in Blend für Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Um neu hinzugefügten Steuerelementen automatisch eindeutige Namen zuzuordnen, klicken Sie auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen. Klicken Sie auf **XAML-Designer**, und wählen Sie dann **Interaktive Elemente beim Erstellen automatisch benennen** aus. Wählen Sie **OK** aus, um das Dialogfeld zu schließen.

## <a name="use-a-data-template"></a>Verwenden einer Datenvorlage

Sie können eine einfache Vorlage mit **ItemTemplate** definieren, um die Werte in einem Listenfeld an Variablen zu binden:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

Sie können auch eine Vorlage mit **ItemContainerStyle** verwenden, um die Werte an Variablen zu binden:

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemContainerStyle>
      <Style TargetType="ListBoxItem">
         <Setter Property="Template">
            <Setter.Value>
               <ControlTemplate TargetType="ListBoxItem">
                  <Grid>
                     <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                  </Grid>
               </ControlTemplate>
            </Setter.Value>
         </Setter>
      </Style>
   </ListBox.ItemContainerStyle>
</ListBox>
```

In beiden Beispielen müssen Sie anschließend die **ToString()** -Methode von **ItemSource** entsprechend der Darstellung mit dem folgenden Codebeispiel überschreiben. Dieser Code gewährleistet, dass der **AutomationProperties.Name**-Wert festgelegt wird und eindeutig ist, da mit Bindungen nicht für jedes datengebundene Listenelement eine eindeutige Automatisierungseigenschaft festgelegt werden kann. Das Festlegen eines eindeutigen Werts für **AutomationProperties.Name** ist in diesem Fall ausreichend.

> [!NOTE]
> Damit können die inneren Inhalte des Listenelements auch auf eine Zeichenfolge in der Mitarbeiterklasse festgelegt werden. Wie im vorliegenden Beispiel gezeigt, wird dem Schaltflächen-Steuerelement innerhalb jedes Listenelements eine eindeutige Automatisierungs-ID zugewiesen, bei der es sich um die Mitarbeiter-ID handelt.

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

## <a name="use-a-control-template"></a>Verwenden einer Steuerelementvorlage

Sie können eine Steuerelementvorlage verwenden, damit jede Instanz eines bestimmten Typs eine eindeutige Automatisierungseigenschaft erhält, wenn sie im Code definiert ist. Erstellen Sie die Vorlage, damit **AutomationProperty** an eine eindeutige ID in der Steuerelementinstanz gebunden wird. Im folgenden XAML-Code wird eine Methode zur Erstellung der Bindung mit einer Steuerelementvorlage veranschaulicht:

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

Wenn Sie zwei Instanzen einer Schaltfläche mithilfe dieser Steuerelementvorlage definieren, wird die Automatisierungs-ID auf die eindeutige Inhaltszeichenfolge für die Steuerelemente in der Vorlage festgelegt. Dies sehen Sie im folgenden XAML-Code:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dynamische Steuerelemente

Wenn Sie über Steuerelemente verfügen, die dynamisch mit dem Code und nicht statisch oder mithilfe von Vorlagen in den XAML-Dateien erstellt wurden, müssen Sie die **Content**- oder die **Name**-Eigenschaft für das Steuerelement festlegen. Dadurch wird sichergestellt, dass jedes dynamische Steuerelement über eine eindeutige Automatisierungseigenschaft verfügt. Wenn beispielsweise ein Kontrollkästchen angezeigt werden muss, wenn ein Listenelement ausgewählt wird, können Sie diese Eigenschaften festlegen, wie im Folgenden dargestellt:

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
{
   CheckBox cb = new CheckBox();
   cb.Content = txt; // Sets the AutomationProperties.Name
   cb.Height = 50;
   cb.Width = 100;
   cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
   panel.Children.Add(cb);
}
```

## <a name="see-also"></a>Weitere Informationen

- [Testen von UWP-Apps mit Tests der programmierten UI](../test/test-uwp-app-with-coded-ui-test.md)
