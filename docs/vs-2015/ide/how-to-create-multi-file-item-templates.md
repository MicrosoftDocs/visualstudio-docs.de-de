---
title: 'Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e70039f361ac3410a8ddcccb0f139d8bdcb32ed9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668089"
---
# <a name="how-to-create-multi-file-item-templates"></a>Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Elementvorlagen können nur ein Element angeben, manchmal besteht ein Element jedoch aus mehreren Dateien. Eine Windows Forms-Elementvorlage für Visual Basic erfordert beispielsweise folgende drei Dateien:

- Eine VB-Datei, die den Code für das Formular enthält.

- Eine DESIGNER.VB-Datei, die die Designer-Informationen für das Formular enthält.

- Eine RESX-Datei, die die eingebetteten Ressourcen für das Formular enthält.

  Elementvorlagen mit mehreren Dateien erfordern Parameter, um sicherzustellen, dass die richtigen Erweiterungen verwendet werden, wenn das Element in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt wird. Wenn Sie eine Elementvorlage mithilfe des **Assistenten zum Exportieren von Vorlagen** erstellen, werden diese Parameter automatisch generiert, und keine weitere Bearbeitung ist erforderlich. In den folgenden Schritten wird erläutert, wie diese Parameter dafür verwendet werden, das Erstellen der richtigen Erweiterung sicherzustellen.

### <a name="to-manually-create-a-multi-file-item-template"></a>Manuelles Erstellen einer Elementvorlage mit mehreren Dateien

1. Erstellen Sie die Elementvorlage wie eine Elementvorlage mit einer einzelnen Datei. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).

2. Fügen Sie jedem `ProjectItem`-Element das `TargetFileName`-Attribut hinzu. Legen Sie die Werte des `TargetFileName`-Attributs auf „$fileinputname$.*Dateierweiterung*“ fest, wobei *Dateierweiterung* der Erweiterung der Datei entspricht, die in die Vorlage eingefügt wird. Beispiel:

    ```
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     Wenn ein Element, das von dieser Vorlage abgeleitet wurde, zu einem Projekt hinzugefügt wird, basieren die Dateinamen auf dem Namen, den der Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben hat.

3. Wählen Sie die Dateien aus, die in die Vorlage eingefügt werden sollen, und klicken Sie mit der rechten Maustaste auf die Auswahl. Klicken Sie dann auf **Senden an** und auf **ZIP-komprimierter Ordner**. Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.

4. Fügen Sie die ZIP-Datei am Speicherort der Benutzerelementvorlage ein. Standardmäßig ist dies das Verzeichnis \Eigene Dateien\Visual Studio *Version*\Templates\ItemTemplates\\. Weitere Informationen finden Sie unter Gewusst [wie: Suchen und organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows Forms-Vorlage. Wenn ein Element basierend auf dieser Vorlage erstellt wird, stimmen die Namen der drei erstellten Dateien mit dem Namen überein, der im Dialogfeld **Neues Element hinzufügen** eingegeben wurde.

```
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md) Gewusst [wie: Erstellen von Element Vorlagen](../ide/how-to-create-item-templates.md) Vorlagen [Parametern](../ide/template-parameters.md) Gewusst [wie: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md)
