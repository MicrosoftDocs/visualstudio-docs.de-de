---
title: Aktivieren von Tests der programmierten UI Ihrer Steuerelemente | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7190a7f698868642c58d1de2ff801e328859b9db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851805"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Aktivieren von Tests der programmierten UI Ihrer Steuerelemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Steuerelemente können einfacher getestet werden, wenn Sie Unterstützung für das Framework für den Test der programmierten UI implementieren. Der Umfang der Unterstützung kann schrittweise erweitert werden. Sie können zunächst mit der Unterstützung von Aufzeichnung und Wiedergabe sowie Eigenschaftenvalidierung beginnen. Darauf aufbauend können Sie dem Test-Generator für codierte UI ermöglichen, die benutzerdefinierten Eigenschaften des Steuerelements zu erkennen, und benutzerdefinierte Klassen bereitstellen, um mit generiertem Code auf diese Eigenschaften zuzugreifen. Außerdem können Sie dazu beitragen, dass Aktionen vom Test-Generator der programmierten UI auf eine Art aufgezeichnet werden, die den Zweck der jeweiligen Aktion genauer widerspiegelt.

 **In diesem Thema:**

1. [Datensatz-, Wiedergabe -und Eigenschaftvalidierung durch Implementierung der Barrierefreiheit unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [Benutzerdefinierte Eigenschaftenvalidierung durch Implementierung eines Eigenschaftenanbieters unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [Codegenerierung durch Implementierung einer Klasse zum Zugriff auf benutzerdefinierte Eigenschaften unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [Unterstützen Intent-fähiger Aktionen durch Implementieren eines Aktions Filters](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![Cuit-&#95;voll](../test/media/cuit-full.png "CUIT_Full")

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a><a name="recordandplayback"></a> Unterstützung von Aufzeichnung und Wiedergabe und Eigenschafts Validierung durch Implementieren von Barrierefreiheit
 Der Test-Generator der programmierten UI erfasst Informationen zu den Steuerelementen, die während einer Aufzeichnung gefunden werden, und generiert dann Code zur Wiedergabe dieser Sitzung. Wenn Barrierefreiheit vom Steuerelement nicht unterstützt wird, erfasst der Test-Generator für codierte UI Aktionen wie Mausklicks anhand der Bildschirmkoordinaten. Bei der Wiedergabe des Tests werden diese Mausklicks vom generierten Code an den gleichen Bildschirmkoordinaten ausgeführt. Wenn sich das Steuerelement beim Wiedergeben des Tests an einer anderen Stelle auf dem Bildschirm befindet, kann der generierte Code die entsprechende Aktion für das Steuerelement nicht ausführen. Dies kann zu Fehlern führen, wenn die Testwiedergabe auf unterschiedlichen Bildschirmkonfigurationen oder in anderen Umgebungen erfolgt oder Änderungen am Benutzeroberflächenlayout vorgenommen wurden.

 ![Cuit-&#95;recordnosupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 Wenn Sie jedoch Barrierefreiheit implementieren, wird diese vom Test-Generator der programmierten UI im Rahmen der Testaufzeichnung und Codegenerierung für das Erfassen der Informationen zum Steuerelement verwendet. Bei der anschließenden Ausführung des Tests erfolgt die Wiedergabe der entsprechenden Ereignisse durch den generierten Code auf dem Steuerelement, auch wenn sich dieses an einer anderen Stelle der Benutzeroberfläche befindet. Testautors können mithilfe der grundlegenden Eigenschaften des Steuerelements auch Asserts erstellen.

 ![Cuit-&#95;Datensatz](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>So unterstützen Sie Aufzeichnung und Wiedergabe, Eigenschaftvalidierung und Navigation für ein Windows Forms-Steuerelement
 Barrierefreiheit kann wie in der folgenden Prozedur dargestellt implementieren werden. Ein ausführliche Anleitung finden Sie unter <xref:System.Windows.Forms.AccessibleObject>.

 ![Cuit-&#95;verfügbar](../test/media/cuit-accessible.png "CUIT_Accessible")

1. Implementieren Sie eine von <xref:System.Windows.Forms.Control.ControlAccessibleObject> abgeleitete Klasse, und überschreiben Sie die <xref:System.Windows.Forms.Control.AccessibilityObject%2A>-Eigenschaft, um ein Objekt der Klasse zurückzugeben.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Überschreiben Sie die Eigenschaften und Methoden <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> sowie <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> des Barrierefreiheitsobjekts.

3. Implementieren Sie ein anderes Barrierefreiheitsobjekt für das untergeordnete Steuerelement, und überschreiben Sie die <xref:System.Windows.Forms.Control.AccessibilityObject%2A>-Eigenschaft dieses Steuerelements, um das Barrierefreiheitsobjekt zurückzugeben.

4. Überschreiben Sie die Eigenschaften und Methoden <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> sowie <xref:System.Windows.Forms.AccessibleObject.Select%2A> für das Barrierefreiheitsobjekt des untergeordneten Steuerelements.

> [!NOTE]
> Dieses Thema beginnt mit dem Barrierefreiheitsbeispiel für das <xref:System.Windows.Forms.AccessibleObject> in dieser Prozedur. Darauf aufbauend werden anschließend die restlichen Prozeduren erläutert. Zum Erstellen einer funktionierenden Version des Barrierefreiheitsbeispiels entwickeln Sie eine Konsolenanwendung und ersetzen dann den Code in "Program.cs" durch den Beispielcode. Sie müssen Verweise auf Barrierefreiheit, System.Drawing und System.Windows.Forms hinzufügen. Sie sollten für die Barrierefreiheit **Interoptypen einbetten** zu **FALSE** ändern, um eine Buildwarnungen zu vermeiden. Sie können den Ausgabetyp des Projekts von **Konsolenanwendung** in **Windows-Anwendung** ändern, damit beim Ausführen der Anwendung kein Konsolenfenster angezeigt wird.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a><a name="customproprties"></a> Unterstützen der Überprüfung benutzerdefinierter Eigenschaften durch Implementieren eines Eigenschaften Anbieters
 Sobald Sie grundlegende Unterstützung für Aufzeichnung und Wiedergabe sowie Eigenschaftenvalidierung implementiert haben, können Sie die benutzerdefinierten Eigenschaften des Steuerelements für Tests der codierten UI verfügbar machen, indem Sie ein <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> Plug-In implementieren. Beispielsweise wird von der folgenden Prozedur ein Eigenschaftenanbieter erstellt, mit dem Tests der programmierten UI auf die Zustandseigenschaft der untergeordneten CurveLegend-Steuerelemente des Diagrammsteuerelements zugreifen können.

 ![Cuit-&#95;Custom-Eigenschaften](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>So unterstützen Sie die Validierung benutzerdefinierter Eigenschaften
 ![Cuit-&#95;Eigenschaften](../test/media/cuit-props.png "CUIT_Props")

1. Überschreiben Sie die zugreifbare <xref:System.Windows.Forms.AccessibleObject.Description%2A>-Eigenschaft des Kurvenlegendenobjekts, um Werte von Rich-Eigenschaften aus der Beschreibungszeichenfolge zu übergeben (durch Semikolons (;) von der Hauptbeschreibung und voneinander getrennt, wenn mehrere Eigenschaften implementiert werden).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. Erstellen Sie ein UI-Test-Erweiterungspaket für das Steuerelement, indem Sie ein Klassenbibliotheksprojekt erstellen und Verweise auf Barrierefreiheit, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common sowie Microsoft.VisualStudio.TestTools.Extension hinzufügen. Ändern Sie für die Barrierefreiheit **Interoptypen einbetten** zu **FALSE**.

3. Fügen Sie eine von <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> abgeleitete Eigenschaftenanbieterklasse hinzu.

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

4. Implementieren Sie den Eigenschaftenanbieter, indem Sie Eigenschaftennamen und Eigenschaftendeskriptoren in <xref:System.Collections.Generic.Dictionary%602> einfügen.

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. Überschreiben Sie <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>, um anzugeben, dass die Assembly steuerelementspezifische Unterstützung für das Steuerelement und dessen untergeordneten Elemente bietet.

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. Überschreiben Sie die verbleibenden abstrakten Methoden von <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. Fügen Sie ein von <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> abgeleitete Erweiterungspaketklasse hinzu.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. Definieren Sie das `UITestExtensionPackage`-Attribut für die Assembly.

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. Überschreiben Sie in der Erweiterungspaketklasse <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>, um bei Anforderung eines Eigenschaftenanbieters die entsprechende Klasse zurückzugeben.

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. Überschreiben Sie die verbleibenden abstrakten Methoden und Eigenschaften von <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. Erstellen Sie die Binärdateien, und kopieren Sie sie nach **%ProgramFiles%\Gemeinsame Dateien\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Dieses Erweiterungspaket wird auf jedes Steuerelement vom Typ "Text" angewendet. Mehrere Steuerelemente des gleichen Typs müssen separat getestet werden, und Sie müssen die beim Aufzeichnen der Tests bereitzustellenden Erweiterungspakete verwalten.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a><a name="codegeneration"></a> Unterstützen der Code Generierung durch Implementierung einer Klasse für den Zugriff auf benutzerdefinierte Eigenschaften
 Wenn der Test-Generator für codierte UI aus einer Sitzungsaufzeichnung Code generiert, wird für den Zugriff auf die Steuerelemente die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>-Klasse verwendet.

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 Wenn ein Eigenschaftenanbieter für den Zugriff auf die benutzerdefinierten Eigenschaften des Steuerelements implementiert wurde, können Sie hierfür eine spezialisierte Klasse hinzufügen, um den generierten Code zu vereinfachen.

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>So fügen Sie eine spezialisierte Klasse zum Zugriff auf das Steuerelement hinzu
 ![Cuit-&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. Implementieren Sie eine von <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> abgeleitete Klasse, und fügen in der Sucheigenschaftenauflistung des Konstruktors den Typ des Steuerelements hinzu.

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. Implementieren Sie die benutzerdefinierten Eigenschaften des Steuerelements als Eigenschaften der Klasse.

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. Überschreiben Sie die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName>-Methode des Eigenschaftenanbieters, um den Typ der neuen Klasse für die untergeordneten Kurvenlegendensteuerelemente zurückzugeben.

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. Überschreiben Sie die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A>-Methode des Eigenschaftenanbieters, um den Typ der PropertyNames-Methode der neuen Klasse zurückzugeben.

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a><a name="intentawareactions"></a> Absichtsbewusste Aktionen durch Implementierung eines Aktionsfilters unterstützen
 Beim Aufzeichnen eines Tests in Visual Studio werden alle Maus- und Tastaturereignisse erfasst. In einigen Fällen kann jedoch der Zweck der durch die Reihe von Maus- und Tastaturereignissen bewirkten Aktion verloren gehen. Wenn das Steuerelement beispielsweise AutoVervollständigen unterstützt, kann bei der Wiedergabe des Tests in einer anderen Umgebung der gleiche Satz von Maus- und Tastaturereignissen einen abweichenden Wert ergeben. Sie können ein Aktionsfilter-Plug-In hinzufügen, von dem die Reihe der Tastatur- und Mausereignisse durch eine einzelne Aktion ersetzt wird. Dadurch können Sie die zur Auswahl eines Werts führende Reihe von Tastatur- und Mausereignissen durch eine einzelne Aktion zum Festlegen des Wert ersetzen. Auf diese Weise können die aufgrund von AutoVervollständigen in verschiedenen Umgebungen auftretenden Unterschiede bei Tests der codierten UI vermieden werden.

### <a name="to-support-intent-aware-actions"></a>So unterstützen Sie absichtbewusste Aktionen
 ![Cuit-&#95;Aktionen](../test/media/cuit-actions.png "CUIT_Actions")

1. Implementieren Sie eine Aktionsfilter Klasse, die von [UITestAction Filter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))abgeleitet wird und die Eigenschaften [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [aktiviert](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) und [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110))außer Kraft setzt.

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. Überschreiben Sie `UITestActionFilter.ProcessRule`. In diesem Beispiel wird eine Doppelklickaktion durch eine Einzelklickaktion ersetzt.

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. Fügen Sie den Aktionsfilter der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A>-Methode des Erweiterungspakets hinzu.

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. Erstellen Sie die Binärdateien, und kopieren Sie sie nach „%ProgramFiles%\Gemeinsame Dateien\Microsoft Shared\VSTT\10.0\UITestExtensionPackages“.

> [!NOTE]
> Der Aktionsfilter ist nicht von der Implementierung der Barrierefreiheit oder vom Eigenschaftenanbieter abhängig.

## <a name="debug-your-property-provider-or-action-filter"></a>Den Eigenschaftenanbieter oder Aktionsfilter debuggen
 Der Eigenschaftenanbieter und Aktionsfilter werden in einem Erweiterungspaket implementiert, das vom Test-Generator für codierte UI in einem von der Anwendung getrennten Prozess geladen und ausgeführt wird.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>So debuggen Sie den Eigenschaftenanbieter oder Aktionsfilter

1. Erstellen Sie die Debugversion des Erweiterungspakets, und kopieren Sie die DLL- und PDB-Dateien nach „%ProgramFiles%\Gemeinsame Dateien\Microsoft Shared\VSTT\10.0\UITestExtensionPackages“.

2. Führen Sie die Anwendung aus (nicht im Debugger.)

3. Führen Sie den Test-Generator für codierte UI aus

     `codedUITestBuilder.exe  /standalone`

4. Fügen Sie den Debugger an den codedUITestBuilder-Prozess an.

5. Legen Sie im Code Haltepunkte fest.

6. Erstellen Sie im Test-Generator für codierte UI Asserts zum Testen des Eigenschaftenanbieters und Aufzeichnungsaktionen zum Testen der Aktionsfilter.

## <a name="external-resources"></a>Externe Ressourcen

### <a name="guidance"></a>Anleitungen
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Windows.Forms.AccessibleObject>
- [Verwenden der Benutzeroberflächen Automatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
