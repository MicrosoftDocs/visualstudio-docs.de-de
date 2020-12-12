---
title: Überwachungs Eigenschaft zur DSL-Definition hinzufügen
description: Erfahren Sie mehr über die Eigenschaft nach Verfolgungs Domäne und darüber, wie Sie einem Domänen Modell eine nach Verfolgungs Eigenschaft hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6709ede3de16a78e0042d035a87a715b9ce4c80c
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361208"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Hinzufügen einer Nachverfolgungseigenschaft zu einer domänenspezifischen Sprachdefinition

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Domänen Modell eine nach Verfolgungs Eigenschaft hinzugefügt wird.

Eine nach *Verfolgungs Domänen* Eigenschaft ist eine Eigenschaft, die vom Benutzer aktualisiert werden kann, jedoch über einen Standardwert verfügt, der mithilfe der Werte anderer Domänen Eigenschaften oder-Elemente berechnet wird.

Beispielsweise verfügt die Anzeige Name-Eigenschaft einer Domänen Klasse in den Domain-Specific Sprach Tools (DSL-Tools) über einen Standardwert, der mit dem Namen der Domänen Klasse berechnet wird. ein Benutzer kann den Wert zur Entwurfszeit jedoch ändern oder auf den berechneten Wert zurücksetzen.

In dieser exemplarischen Vorgehensweise erstellen Sie eine domänenspezifische Sprache (DSL) mit einer Namespace-nach Verfolgungs Eigenschaft, die über einen Standardwert verfügt, der auf der Standard Namespace-Eigenschaft des Modells basiert. Weitere Informationen zu Überwachungs Eigenschaften finden Sie unter [Definieren von Überwachungs Eigenschaften](/previous-versions/cc825929(v=vs.100)).

- Die DSL-Tools unterstützen die Nachverfolgung von Eigenschaften Deskriptoren. Der DSL-Designer kann jedoch nicht zum Hinzufügen einer nach Verfolgungs Eigenschaft zu einer Sprache verwendet werden. Daher müssen Sie benutzerdefinierten Code hinzufügen, um die nach Verfolgungs Eigenschaft zu definieren und zu implementieren.

  Eine nach Verfolgungs Eigenschaft hat zwei Zustände: Nachverfolgung und Aktualisierung durch den Benutzer. Überwachungs Eigenschaften haben die folgenden Funktionen:

- Im nach Verfolgungs Zustand wird der Wert der nach Verfolgungs Eigenschaft berechnet, und der Wert wird aktualisiert, wenn andere Eigenschaften im Modell geändert werden.

- Wenn der Wert der Eigenschaft nach der Aktualisierung durch den Benutzer Zustand lautet, behält der Wert der Eigenschaft Nachverfolgung den Wert bei, den der Benutzer zuletzt festgelegt hat.

- Im Fenster **Eigenschaften** ist der **Reset** -Befehl für die nach Verfolgungs Eigenschaft nur aktiviert, wenn die-Eigenschaft im aktualisierten Benutzer Zustand ist. Der **Reset** -Befehl legt den Status der Überwachungs Eigenschaft auf "Tracking" fest.

- Im Fenster **Eigenschaften** wird der Wert in einer regulären Schriftart angezeigt, wenn sich die Überwachungs Eigenschaft im Überwachungszustand befindet.

- Wenn sich im **Eigenschaften** Fenster die nach Verfolgungs Eigenschaft im aktualisierten Benutzer Zustand befindet, wird der Wert in einer fett formatierten Schriftart angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie diese exemplarische Vorgehensweise starten können, müssen Sie zunächst die folgenden Komponenten installieren:

| Komponente | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Erstellen des Projekts

1. Erstellen Sie ein Domain-Specific-sprach-Designer-Projekt. Vergeben Sie den Namen `TrackingPropertyDSL`.

2. Legen Sie im **Assistenten für domänenspezifische sprach-Designer** die folgenden Optionen fest:

    1. Wählen Sie die Vorlage " **minimallanguage** " aus.

    2. Verwenden Sie den Standardnamen für die domänenspezifische Sprache `TrackingPropertyDSL` .

    3. Legen Sie die Erweiterung für Modelldateien auf fest `trackingPropertyDsl` .

    4. Verwenden Sie das Standardvorlagen Symbol für die Modelldateien.

    5. Legen Sie den Namen des Produkts auf fest `Product Name` .

    6. Legen Sie den Namen des Unternehmens auf fest `Company Name` .

    7. Verwenden Sie den Standardwert für den Stamm Namespace für Projekte in der Projekt Mappe `CompanyName.ProductName.TrackingPropertyDSL` .

    8. Hiermit wird der Assistent ermöglicht, eine Schlüsseldatei mit starkem Namen für die Assemblys zu erstellen.

    9. Überprüfen Sie die Details der Lösung, und klicken Sie dann auf **Fertig** stellen, um das DSL-Definitions Projekt zu erstellen.

## <a name="customize-the-default-dsl-definition"></a>Anpassen der standardmäßigen DSL-Definition
 In diesem Abschnitt passen Sie die DSL-Definition so an, dass Sie die folgenden Elemente enthält:

- Eine Namespace-nach Verfolgungs Eigenschaft für jedes Element des Modells.

- Eine boolesche isnamespacetracking-Eigenschaft für jedes Element des Modells. Diese Eigenschaft gibt an, ob sich die nach Verfolgungs Eigenschaft im Überwachungs Status oder im aktualisierten nach Benutzer Zustand befindet.

- Eine Standard Namespace-Eigenschaft für das Modell. Diese Eigenschaft wird verwendet, um den Standardwert der Eigenschaft Namespace Verfolgung zu berechnen.

- Eine berechnete customelements-Eigenschaft für das Modell. Diese Eigenschaft gibt den Anteil von Elementen an, die über einen benutzerdefinierten Namespace verfügen.

### <a name="to-add-the-domain-properties"></a>So fügen Sie die Domänen Eigenschaften hinzu

1. Klicken Sie im DSL-Designer mit der rechten Maustaste auf die Domänen Klasse **examplemodel** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **DomainProperty**.

    1. Benennen Sie die neue Eigenschaft `DefaultNamespace` .

    2. Legen Sie im **Eigenschaften** Fenster für die neue Eigenschaft den **Standardwert** auf fest `DefaultNamespace` , und legen Sie **Typ** auf **Zeichenfolge** fest.

2. Fügen Sie der Domänen Klasse **examplemodel** eine Domänen Eigenschaft mit dem Namen hinzu `CustomElements` .

     Legen Sie im **Eigenschaften** Fenster für die neue Eigenschaft **Art** auf **berechnet** fest.

3. Fügen Sie der " **ExampleElement** "-Domänen Klasse eine Domänen Eigenschaft mit dem Namen hinzu `Namespace` .

     Legen Sie im Fenster **Eigenschaften** für die neue Eigenschaft den Wert durchsuchbar auf **false** fest, und **legen Sie** **Art** auf **CustomStorage** fest.

4. Fügen Sie der " **ExampleElement** "-Domänen Klasse eine Domänen Eigenschaft mit dem Namen hinzu `IsNamespaceTracking` .

     Legen Sie im Fenster **Eigenschaften** für die neue Eigenschaft die Einstellung **ist browsefähig** auf **false** fest, legen Sie den **Standardwert** auf fest `true` , und legen Sie **Typ** auf **Boolean** fest.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>So aktualisieren Sie die Diagramm Elemente und DSL-Details

1. Klicken Sie im DSL-Designer mit der rechten Maustaste auf die Form " **exampleshape** Geometry", zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Text Decorator**.

    1. Benennen Sie den neuen Text Decorator `NamespaceDecorator` .

    2. Legen Sie im **Eigenschaften** Fenster für den Text-Decorator die **Position** auf **InnerBottomLeft** fest.

2. Wählen Sie im DSL-Designer die Linie aus, die die Klasse **ExampleElement** mit der Form **exampleshape** verbindet.

    1. Wählen Sie im Fenster **DSL-Details** die Registerkarte **Decorator** -Zuordnungen aus.

    2. Wählen Sie in der Liste **Decorators** den **Namen namespacedecorator** aus, aktivieren Sie das entsprechende Kontrollkästchen, und wählen Sie dann in der Liste **Anzeige Eigenschaft** die Option **Namespace** aus.

3. Erweitern Sie im **DSL-Explorer** den Ordner **Domänen Klassen** , klicken Sie mit der rechten Maustaste auf den Knoten **ExampleElement** , und klicken Sie dann auf **neuen Domänentyp Deskriptor hinzufügen**.

    1. Erweitern Sie den Knoten **ExampleElement** , und wählen Sie den Knoten **benutzerdefinierter Typdeskriptor (Domänentyp Deskriptor)** aus.

    2. Legen Sie im Fenster **Eigenschaften** für den Domänentyp Deskriptor den Wert **Benutzer** definiert auf **true** fest.

4. Wählen Sie im **DSL-Explorer** den Knoten **XML-Serialisierungsverhalten** aus.

    1. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **benutzerdefinierter Post-Lade** Vorgang auf **true** fest.

## <a name="transform-templates"></a>Transformations Vorlagen

Nachdem Sie die Domänen Klassen und-Eigenschaften für die DSL definiert haben, können Sie überprüfen, ob die DSL-Definition ordnungsgemäß transformiert werden kann, um den Code für das Projekt neu zu generieren.

1. Klicken Sie auf der Symbolleiste **Projektmappen-Explorer** auf **alle Vorlagen transformieren**.

2. Das System generiert den Code für die Lösung neu und speichert DslDefinition. DSL. Weitere Informationen zum XML-Format von Definitions Dateien finden Sie in [der Datei "DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md)".

## <a name="create-files-for-custom-code"></a>Erstellen von Dateien für benutzerdefinierten Code

Wenn Sie alle Vorlagen transformieren, generiert das System den Quellcode, der die domänenspezifische Sprache definiert, in den Projekten DSL und dslpackage. Um das stören des generierten Texts zu vermeiden, schreiben Sie den benutzerdefinierten Code in Dateien, die sich von den generierten Code Dateien unterscheiden.

Sie müssen Code bereitstellen, um den Wert und den Status der nach Verfolgungs Eigenschaft beizubehalten. Wenn Sie Ihren benutzerdefinierten Code aus dem generierten Code unterscheiden und Datei Benennungs Konflikte vermeiden möchten, platzieren Sie die benutzerdefinierten Code Dateien in einem separaten Unterordner.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das **DSL** -Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **neuer Ordner**. Benennen Sie den neuen Ordner `CustomCode` .

2. Klicken Sie mit der rechten Maustaste auf den neuen Ordner **customcode** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

3. Wählen Sie die Vorlage **Code Datei** aus, legen Sie den **Namen** auf fest `NamespaceTrackingProperty.cs` , und klicken Sie dann auf **OK**.

     Die Datei NamespaceTrackingProperty.cs wird erstellt und zur Bearbeitung geöffnet.

4. Erstellen Sie im Ordner die folgenden Code Dateien: `ExampleModel.cs,``HelperClasses.cs` , `Serialization.cs` und `TypeDescriptor.cs` .

5. Erstellen Sie im **dslpackage** -Projekt auch einen `CustomCode` Ordner, und fügen Sie ihm eine `Package.cs` Codedatei hinzu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Hinzufügen von Hilfsklassen zur Unterstützung von nach Verfolgungs Eigenschaften

Fügen Sie der Datei HelperClasses.cs die `TrackingHelper` Klassen und `CriticalException` wie folgt hinzu. Diese Klassen werden später in dieser exemplarischen Vorgehensweise referenziert.

1. Fügen Sie der Datei HelperClasses.cs den folgenden Code hinzu.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Hinzufügen von benutzerdefiniertem Code für den benutzerdefinierten Typdeskriptor

Implementieren Sie die- `GetCustomProperties` Methode für den Typdeskriptor für die `ExampleModel` Domänen Klasse.

> [!NOTE]
> Der Code, der von den DSL-Tools für den benutzerdefinierten Typdeskriptor für- `ExampleModel` Aufrufe generiert `GetCustomProperties` wird. die DSL-Tools generieren jedoch keinen Code, der die-Methode implementiert.

Wenn Sie diese Methode definieren, wird der nach Verfolgungs Eigenschaften Deskriptor für die Eigenschaft Namespace-Nachverfolgung erstellt. Außerdem ermöglicht das Bereitstellen von Attributen für die nach Verfolgungs Eigenschaft dem **Eigenschaften** Fenster das ordnungsgemäße Anzeigen der Eigenschaft.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>So ändern Sie den Typdeskriptor für die "examplemodel"-Domänen Klasse

1. Fügen Sie der Datei TypeDescriptor.cs den folgenden Code hinzu.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Hinzufügen von benutzerdefiniertem Code für das Paket

Der generierte Code definiert einen Typbeschreibungs Anbieter für die ExampleElement-Domänen Klasse. Sie müssen jedoch Code hinzufügen, um die DSL anzuweisen, diesen Typbeschreibungs Anbieter zu verwenden.

1. Fügen Sie der Datei Package.cs den folgenden Code hinzu.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>Hinzufügen von benutzerdefiniertem Code für das Modell

Implementieren Sie die- `GetCustomElementsValue` Methode für die- `ExampleModel` Domänen Klasse.

> [!NOTE]
> Der Code, der von den DSL-Tools für `ExampleModel` Aufrufe generiert `GetCustomElementsValue` wird. die DSL-Tools generieren jedoch keinen Code, der die-Methode implementiert.

Durch die Definition der- `GetCustomElementsValue` Methode wird die Logik für die berechnete Eigenschaft customelements von bereitstellt `ExampleModel` . Diese Methode zählt die Anzahl der `ExampleElement` Domänen Klassen, die über eine Namespace-nach Verfolgungs Eigenschaft verfügen, die über einen vom Benutzer aktualisierten Wert verfügt, und gibt eine Zeichenfolge zurück, die diese Anzahl als Anteil der Gesamt Elemente im Modell darstellt.

Fügen Sie außerdem eine `OnDefaultNamespaceChanged` -Methode zu hinzu `ExampleModel` , und überschreiben Sie die- `OnValueChanged` Methode der-Klasse, `DefaultNamespacePropertyHandler` `ExampleModel` um aufzurufen `OnDefaultNamespaceChanged` .

Da die Eigenschaft DefaultNamespace verwendet wird, um die Eigenschaft Namespace Verfolgung zu berechnen, `ExampleModel` muss alle `ExampleElement` Domänen Klassen Benachrichtigen, dass sich der Wert von DefaultNamespace geändert hat.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>So ändern Sie den Eigenschafts Handler für die nach verfolgte Eigenschaft

1. Fügen Sie der Datei ExampleModel.cs den folgenden Code hinzu.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>Hinzufügen von benutzerdefiniertem Code für die nach Verfolgungs Eigenschaft

Fügen Sie `CalculateNamespace` der `ExampleElement` Domänen Klasse eine Methode hinzu.

Wenn Sie diese Methode definieren, wird die Logik für die berechnete Eigenschaft customelements von bereitstellt `ExampleModel` . Diese Methode zählt die Anzahl der `ExampleElement` Domänen Klassen, die über eine Namespace-nach Verfolgungs Eigenschaft verfügen, die im aktualisierten Benutzer Zustand ist, und gibt eine Zeichenfolge zurück, die diese Anzahl als Anteil der Gesamt Elemente im Modell darstellt.

Fügen Sie außerdem Speicher für die-,-und-Methode hinzu, um die Eigenschaft Namespace Custom Storage der Domänen Klasse zu erhalten und festzulegen `ExampleElement` .

> [!NOTE]
> Der Code, den die DSL-Tools für generieren, `ExampleModel` Ruft die Get-und Set-Methode auf. die DSL-Tools generieren jedoch keinen Code, der die Methoden implementiert.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>So fügen Sie die Methode für den benutzerdefinierten Typdeskriptor hinzu

1. Fügen Sie der Datei NamespaceTrackingProperty.cs den folgenden Code hinzu.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>Benutzerdefinierten Code zur Unterstützung der Serialisierung hinzufügen

Fügen Sie Code hinzu, um das benutzerdefinierte nach Ladeverhalten für die XML-Serialisierung zu unterstützen.

> [!NOTE]
> Der Code, den die DSL-Tools generiert, ruft die `OnPostLoadModel` -Methode und die- `OnPostLoadModelAndDiagram` Methode auf. die DSL-Tools generieren jedoch keinen Code, der diese Methoden implementiert.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>So fügen Sie Code hinzu, um das benutzerdefinierte nach Ladeverhalten zu unterstützen

1. Fügen Sie der Datei Serialization.cs den folgenden Code hinzu.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>Testen der Sprache

Der nächste Schritt besteht darin, den DSL-Designer in einer neuen Instanz von zu erstellen und auszuführen, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] damit Sie überprüfen können, ob die nach Verfolgungs Eigenschaft ordnungsgemäß funktioniert.

1. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.

2. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

    Der experimentelle Build von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] öffnet die **debugprojektmappe** , die eine leere Testdatei enthält.

3. Doppelklicken Sie in **Projektmappen-Explorer** auf die Datei Test. trackingpropertydsl, um Sie im Designer zu öffnen, und klicken Sie dann auf die Entwurfs Oberfläche.

    Beachten Sie, dass im Fenster **Eigenschaften** für das Diagramm die Eigenschaft **Standard Namespace** den Wert **DefaultNamespace** und die Eigenschaft **benutzerdefinierte Elemente** **0/0** lautet.

4. Ziehen Sie ein **ExampleElement** -Element aus der **Toolbox** auf die Diagramm Oberfläche.

5. Wählen Sie im **Eigenschaften** Fenster für das-Element die Eigenschaft **Element Namespace** aus, und ändern Sie den Wert von **DefaultNamespace** in **otherNamespace**.

    Beachten Sie, dass der Wert des **Element Namespace** nun fett angezeigt wird.

6. Klicken Sie im **Eigenschaften** Fenster mit der rechten Maustaste auf **Element Namespace**, und klicken Sie dann auf **Zurücksetzen**.

    Der Wert der Eigenschaft wird in **DefaultNamespace** geändert, und der Wert wird in einer regulären Schriftart angezeigt.

    Klicken Sie mit der rechten Maustaste erneut auf **Element Namespace** . Der **Reset** -Befehl ist nun deaktiviert, da die-Eigenschaft zurzeit im Überwachungszustand ist.

7. Ziehen Sie ein weiteres **ExampleElement** aus der **Toolbox** auf die Diagramm Oberfläche, und ändern Sie dessen **Element-Namespace** in **otherNamespace**.

8. Klicken Sie auf die Entwurfs Oberfläche.

    Im **Eigenschaften** Fenster des Diagramms ist der Wert der **benutzerdefinierten Elemente** jetzt **1/2**.

9. Ändern Sie den **Standard Namespace** für das Diagramm von **DefaultNamespace** in **newNamespace**.

     Der **Namespace** des ersten Elements verfolgt die **standardmäßige Namespace** -Eigenschaft, während der **Namespace** des zweiten Elements seinen vom Benutzer aktualisierten Wert von **otherNamespace** beibehält.

10. Speichern Sie die Projekt Mappe, und schließen Sie dann den experimentellen Build.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie planen, mehr als eine nach Verfolgungs Eigenschaft zu verwenden oder nach Verfolgungs Eigenschaften in mehr als einer DSL zu implementieren, können Sie eine Textvorlage erstellen, um den allgemeinen Code für die Unterstützung der einzelnen Überwachungs Eigenschaften zu generieren. Weitere Informationen zu Textvorlagen finden Sie unter [Code Generierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md)