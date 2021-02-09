---
title: Managed Extensibility Framework im Editor | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Managed Extensibility Framework, mit der Sie eigene Komponenten erstellen können, um den Editor im Visual Studio SDK zu erweitern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5965ca211710b0710626118f016b2cb3fec116b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915147"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Im Editor Managed Extensibility Framework
Der Editor wird mithilfe von Managed Extensibility Framework-Komponenten (MEF) erstellt. Sie können Ihre eigenen MEF-Komponenten erstellen, um den Editor zu erweitern, und der Code kann auch Editor-Komponenten nutzen.

## <a name="overview-of-the-managed-extensibility-framework"></a>Übersicht über den Managed Extensibility Framework
 Die MEF ist eine .NET-Bibliothek, mit der Sie Features einer Anwendung oder Komponente hinzufügen und ändern können, die dem MEF-Programmiermodell folgt. Der Visual Studio-Editor kann MEF-Komponenten Teile bereitstellen und nutzen.

 Die MEF ist in der .NET Framework Version 4 *System.ComponentModel.Composition.dll* Assembly enthalten.

 Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Komponenten Teile und Kompositions Container
 Ein Komponenten Teil ist eine Klasse oder ein Member einer Klasse, die eine (oder beide) der folgenden Aktionen ausführen kann:

- Verwenden einer anderen Komponente

- Von einer anderen Komponente genutzt werden

  Stellen Sie sich z. b. eine Einkaufs Anwendung vor, die über eine Bestell Eingabe Komponente verfügt, die von Produkt Verfügbarkeitsdaten abhängt, die von einer Warehouse-Bestands Komponente In MEF-Begriffen kann der Inventur Teil Produkt Verfügbarkeitsdaten *exportieren* , und der Bestell Eintrags Teil kann die Daten *importieren* . Der Bestell Eintrags Teil und der Inventur Teil müssen sich nicht gegenseitig informieren. der *Kompositions Container* (der von der Host Anwendung bereitgestellt wird) ist dafür verantwortlich, den Export Satz zu verwalten und die Exporte und Importe zu beheben.

  Der Kompositions Container, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> , befindet sich in der Regel im Besitz des Hosts. Der Kompositions Container verwaltet einen *Katalog* exportierter Komponenten Teile.

### <a name="export-and-import-component-parts"></a>Exportieren und Importieren von Komponenten teilen
 Sie können jede beliebige Funktionalität exportieren, sofern Sie als öffentliche Klasse oder als öffentliches Member einer Klasse (Eigenschaft oder Methode) implementiert ist. Sie müssen den Komponenten Teil nicht von ableiten <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Stattdessen müssen Sie <xref:System.ComponentModel.Composition.ExportAttribute> der Klasse oder dem Klassenmember, die Sie exportieren möchten, ein-Attribut hinzufügen. Dieses Attribut gibt den *Vertrag* an, mit dem ein anderer Komponenten Teil ihre Funktionalität importieren kann.

### <a name="the-export-contract"></a>Der Exportvertrag
 <xref:System.ComponentModel.Composition.ExportAttribute>Definiert die Entität (Klasse, Schnittstelle oder Struktur), die exportiert wird. In der Regel nimmt das Export-Attribut einen Parameter an, der den Typ des Exports angibt.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Standardmäßig definiert das- <xref:System.ComponentModel.Composition.ExportAttribute> Attribut einen Vertrag, bei dem es sich um den Typ der exportierenden Klasse handelt.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Im Beispiel entspricht das Default- `[Export]` Attribut `[Export(typeof(TestAdornmentLayerDefinition))]` .

 Sie können auch eine Eigenschaft oder Methode exportieren, wie im folgenden Beispiel gezeigt.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importieren eines MEF-Exports
 Wenn Sie einen MEF-Export nutzen möchten, müssen Sie den-Vertrag (in der Regel den-Typ) kennen, mit dem er exportiert wurde, und ein- <xref:System.ComponentModel.Composition.ImportAttribute> Attribut mit diesem Wert hinzufügen. Standardmäßig nimmt das Import-Attribut einen Parameter an, der der Typ der Klasse ist, den er ändert. In den folgenden Codezeilen wird der- <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> Typ importiert.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Editor-Funktionalität von einem MEF-Komponenten Teil erhalten
 Wenn Ihr vorhandener Code ein MEF-Komponenten Teil ist, können Sie die MEF-Metadaten verwenden, um editorkomponententeile zu verwenden.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>So nutzen Sie die Editor-Funktionalität von einem MEF-Komponenten Teil

1. Fügen Sie Verweise auf *System.Composition.ComponentModel.dll* im globalen Assemblycache (Global Assembly Cache, GAC) und auf die editorassemblys hinzu.

2. Fügen Sie die relevanten using-Direktiven hinzu.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Fügen Sie das- `[Import]` Attribut wie folgt zu ihrer Dienst Schnittstelle hinzu.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Wenn Sie den Dienst erhalten haben, können Sie eine beliebige Komponente nutzen.

5. Wenn Sie die Assembly kompiliert haben, platzieren Sie Sie im *. Ordner \common7\ide\components \* Ihrer Visual Studio-Installation.

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
