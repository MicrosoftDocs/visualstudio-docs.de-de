---
title: API-Referenz für das Modellierungs-SDK
description: Erfahren Sie, wie das Visual Studio-SDK für Visualisierung und Modellierung die Plattform bereitstellt, auf der Ihre DSLs-Tools (Domain-Specific Languages) erstellt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 721527b71e12b2c6143fa952d663cccc2786b34f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361078"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>API-Referenz für Modellierungs-SDK für Visual Studio

Das Visual Studio-SDK für Visualisierung und Modellierung bietet die Plattform, auf der die Tools für domänenspezifische Sprachen (DSL) erstellt werden.

Dieser Abschnitt enthält Referenzmaterial für Namespaces, deren Namen mit "Microsoft. VisualStudio. Modeling" beginnen.

|Namespace|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klassen wie ModelElement, das die Basisklasse aller Domänen Klassen ist, die Sie in einer DSL definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klassen, die einen Teil einer DSL-Definition bilden.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Die Tools für den Modell Speicher-Viewer und die Leistungsmessung.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klassen wie shapeelement, die die Basisklasse aller Formen sind, die Sie in einer DSL definieren.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gesten-und Auswahlmethoden.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Die API des DSL-Definitions-Designers.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interne Klassen des DSL-Definitions-Designers.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Attribute, die es Ihnen ermöglichen, den DSL-Designer mit Befehlen, Gesten und Validierung zu erweitern.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Erweiterungs Methoden für ModelElement, die DSL-Erweiterbarkeit implementieren.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Erweiterbarkeits Attribute|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Ermöglicht es Ihnen, Teile eines Modells als schreibgeschützt zu gestalten.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Die ModelBus-API, mit der Sie unterschiedliche Modelle integrieren können.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|Das Dialogfeld, in dem Benutzer zu Modellen und Elementen navigieren können, um ModelBus-Verweise zu erstellen.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Der Auswahl Dienst.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|ModelBus-Adapter Framework für Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|Das Auswahl Dialogfeld, in dem Benutzer zu Modellen und Elementen navigieren können, um ModelBus-Verweise zu erstellen.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Die Schnittstelle zwischen DSLs und Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Ermöglicht das Definieren von Kontextmenü Befehlen (Kontextmenü).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Ermöglicht das Definieren von Validierungs Einschränkungen.|

## <a name="see-also"></a>Siehe auch

- [Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)
