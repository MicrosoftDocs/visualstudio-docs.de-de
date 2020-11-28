---
title: Erstellen von Elementvorlagen mit mehreren Dateien
description: Erfahren Sie, wie Sie eine Elementvorlage in Visual Studio erstellen, die aus mehreren Dateien besteht.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a947d23bd7094e003bae3cfe880299bb3698d92e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597261"
---
# <a name="how-to-create-multi-file-item-templates"></a>Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien

Elementvorlagen können nur ein Element angeben, manchmal besteht ein Element jedoch aus mehreren Dateien. Eine Windows Forms-Elementvorlage erfordert beispielsweise folgende drei Dateien:

- Eine Datei, die den Code für das Formular enthält

- Eine Datei, die Designer-Informationen für das Formular enthält

- Eine Datei, die die eingebetteten Ressourcen für das Formular enthält

Elementvorlagen mit mehreren Dateien erfordern Parameter, um sicherzustellen, dass die richtigen Erweiterungen verwendet werden, wenn das Element erstellt wird. Wenn Sie eine Elementvorlage mit mehreren Dateien mithilfe des **Assistenten zum Exportieren von Vorlagen** erstellen, werden diese Parameter automatisch generiert, und keine weitere Bearbeitung ist erforderlich.

## <a name="use-the-export-template-wizard"></a>Verwenden des Assistenten zum Exportieren von Vorlagen

Eine Elementvorlage mit mehreren Dateien wird auf dieselbe Weise erstellt, wie eine Elementvorlage mit nur einer Datei. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md). Wählen Sie auf der Seite **Zu exportierendes Element auswählen** die Datei aus, von denen anderen Dateien abhängig sind (z.B. eine Windows Forms-Formulardatei). Der Assistent fügt der Vorlage automatische sämtliche abhängigen Dateien hinzu, z.B. Designer- und Ressourcendateien.

## <a name="manually-create-a-multi-file-item-template"></a>Manuelles Erstellen einer Elementvorlage mit mehreren Dateien

1. Erstellen Sie die Elementvorlage auf dieselbe Weise, wie Sie manuell eine Elementvorlage erstellen würden, die nur aus einer Datei besteht. Fügen Sie dabei allerdings jede Datei hinzu, die Bestandteil des Elements mit mehreren Dateien ist.

1. Fügen Sie der *VSTEMPLATE*-XML-Datei für jede einzelne Datei ein `ProjectItem`-Element hinzu. Fügen Sie anschließend diesem Element ein `TargetFileName`-Attribut hinzu. Legen Sie den Wert des `TargetFileName`-Attributs auf *$fileinputname$.FileExtension* fest, wobei *FileExtension* der Erweiterung der Datei entspricht, die in der Vorlage enthalten ist. Zum Beispiel:

    ```xml
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

     > [!NOTE]
     > Wenn ein Element, das von dieser Vorlage abgeleitet wurde, einem Projekt hinzugefügt wird, werden die Dateinamen von dem Namen abgeleitet, den der Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben hat.

1. Wählen Sie die Dateien aus, die in die Vorlage eingefügt werden sollen, und klicken Sie mit der rechten Maustaste auf die Auswahl. Klicken Sie dann auf **Senden an** > **ZIP-komprimierter Ordner**.

   Die ausgewählten Dateien werden in eine *ZIP*-Datei komprimiert.

1. Kopieren Sie die *ZIP*-Datei an den Speicherort der Benutzerelementvorlage. Standardmäßig ist dies das Verzeichnis *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates*. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Schließen Sie Visual Studio, und öffnen Sie es anschließend erneut.

1. Erstellen Sie ein neues Projekt, oder öffnen Sie ein vorhandenes Projekt, und klicken Sie anschließend auf **Projekt** > **Neues Element hinzufügen**, oder drücken Sie **STRG**+**UMSCHALT**+**A**.

   Die Elementvorlagen mit mehreren Dateien werden im Dialogfeld **Neues Element hinzufügen** angezeigt.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Windows Forms-Vorlage. Wenn ein Element basierend auf dieser Vorlage erstellt wird, stimmen die Namen der drei erstellten Dateien mit dem Namen überein, der im Dialogfeld **Neues Element hinzufügen** eingegeben wurde.

```xml
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

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [How to: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [How to: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md)
