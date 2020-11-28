---
title: Erstellen von Elementvorlagen
description: Erfahren Sie, wie Sie mit dem Assistenten zum Exportieren von Vorlagen eine Elementvorlage in Visual Studio erstellen.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: abf058526a6ff48a37d4c7585e7deabe1decb14a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597274"
---
# <a name="how-to-create-item-templates"></a>Vorgehensweise: Erstellen von Elementvorlagen

In diesem Artikel wird erläutert, wie Sie eine Elementvorlage mithilfe des **Assistenten zum Exportieren von Vorlagen** erstellen können. Wenn Ihre Vorlage mehrere Dateien enthalten soll, finden Sie im Artikel [Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md) entsprechende Informationen dazu.

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Hinzufügen einer Elementvorlage zum Dialogfeld „Neues Element hinzufügen“

1. Erstellen oder Öffnen Sie ein Projekt in Visual Studio.

1. Fügen Sie dem Projekt ein Element hinzu, und ändern Sie dieses nach Bedarf.

1. Ändern Sie die Codedatei, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen. Weitere Informationen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).

1. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.

1. Wählen Sie auf der Seite **Vorlagentyp auswählen** **Elementvorlage** aus, wählen Sie das Projekt mit dem Element aus, und klicken Sie anschließend auf **Weiter**.

1. Wählen Sie auf der Seite **Zu exportierendes Element auswählen** das Element aus, für das Sie eine Vorlage erstellen wollen, und klicken Sie anschließend auf **Weiter**.

1. Wählen Sie auf der Seite **Elementverweise auswählen** die Assemblyverweise aus, die zur Vorlage hinzugefügt werden sollen, und klicken Sie anschließend auf **Weiter**.

1. Geben Sie auf der Seite **Vorlagenoptionen auswählen** einen Namen, ggf. eine Beschreibung sowie ein Symbol für Ihre Vorlage ein, fügen Sie ein Vorschaubild hinzu, und klicken Sie anschließend auf **Fertig stellen**.

    Die Dateien für die Vorlage werden einer *ZIP*-Datei hinzugefügt und in das von Ihnen im Assistenten angegebene Verzeichnis kopiert. Der Standardspeicherort ist der Ordner *%USERPROFILE%\Documents\Visual Studio \<version\>\My Exported Templates*.

1. Suchen Sie die exportierte Vorlage, wenn Sie im **Assistenten zum Exportieren von Vorlagen** nicht die Option **Vorlage automatisch in Visual Studio importieren** ausgewählt haben. Kopieren Sie die Vorlage dann in das Verzeichnis der Benutzerelementvorlage. Der Standardspeicherort ist der Ordner *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ItemTemplates*.

1. Schließen Sie Visual Studio, und öffnen Sie es anschließend erneut.

1. Erstellen Sie ein neues Projekt, oder öffnen Sie ein vorhandenes Projekt, und klicken Sie anschließend auf **Projekt** > **Neues Element hinzufügen**, oder drücken Sie **STRG**+**UMSCHALT**+**A**.

   Die Elementvorlage wird im Dialogfeld **Neues Element hinzufügen** angezeigt. Wenn Sie dem **Assistenten zum Exportieren von Vorlagen** eine Beschreibung hinzugefügt haben, wird diese rechts neben dem Dialogfeld angezeigt.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Aktivieren der Elementvorlage für die Verwendung in einem Universellen Windows-App-Projekt

Der Assistent nimmt Ihnen einen Großteil der Arbeit beim Erstellen der Standardvorlage ab. In vielen Fällen müssen Sie die *VSTEMPLATE*-Datei jedoch manuell bearbeiten, nachdem Sie die Vorlage exportiert haben. Wenn z.B. das Element im Dialogfeld **Neues Element hinzufügen** für ein Universelles Windows-App-Projekt angezeigt werden soll, müssen Sie einige zusätzliche Schritte ausführen.

1. Führen Sie die im obenstehenden Abschnitt beschriebenen Schritte aus, um eine Elementvorlage zu exportieren.

1. Extrahieren Sie die zuvor erstellte *ZIP*-Datei, und öffnen Sie die *VSTEMPLATE*-Datei in Visual Studio.

1. Fügen Sie für ein Universelles Windows-Projekt in C# das folgende XML innerhalb des `<TemplateData>`-Elements hinzu:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Speichern Sie in Visual Studio die *VSTEMPLATE*-Datei, und schließen Sie sie.

1. Kopieren Sie die *VSTEMPLATE*-Datei, und fügen Sie sie wieder in die *ZIP*-Datei ein.

     Wenn das Dialogfeld **Datei kopieren** angezeigt wird, wählen Sie die Option **Kopieren und ersetzen** aus.

Sie können nun ein Element auf der Grundlage dieser Vorlage einem Universellen Windows-Projekt hinzufügen, indem Sie das Dialogfeld **Neues Element hinzufügen** verwenden.

## <a name="enable-templates-for-specific-project-subtypes"></a>Aktivieren von Vorlagen für bestimmte Projektuntertypen

Sie können angeben, dass die Vorlage nur für bestimmte Projektuntertypen wie Windows, Office, Datenbank oder Web angezeigt wird.

1. Suchen Sie nach dem `ProjectType`-Element in der *VSTEMPLATE*-Datei für die Elementvorlage.

1. Fügen Sie ein [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)-Element unmittelbar nach dem `ProjectType`-Element hinzu.

1. Legen Sie den Textwert des Elements auf einen der folgenden Werte fest:

    - Windows
    - Office
    - Datenbank
    - Web

Beispiel: `<ProjectSubType>Database</ProjectSubType>`.

Im folgenden Beispiel wird eine Elementvorlage für **Office**-Projekte dargestellt.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="manually-create-an-item-template"></a>Manuelles Erstellen einer Elementvorlage

In einigen Fällen sollten Sie eine Elementvorlage manuell von Grund auf neu erstellen.

1. Erstellen Sie ein Projekt und ein Projektelement.

2. Bearbeiten Sie das Projektelement solange, bis es als Vorlage gespeichert werden kann.

3. Ändern Sie nach Bedarf die Codedatei, um anzugeben, an welcher Stelle Parameter ersetzt werden sollen. Weitere Informationen zu Parameterersetzungen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).

4. Erstellen Sie eine XML-Datei, und speichern Sie sie mit der Erweiterung *VSTEMPLATE* in demselben Verzeichnis wie die Projektelementdatei.

5. Erstellen Sie die *VSTEMPLATE*-XML-Datei, um Metadaten für Elementvorlagen bereitzustellen. Weitere Informationen finden Sie unter [Template schema reference (extensibility) (Schemareferenz zu Vorlagen (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md) und im Beispiel im vorherigen Abschnitt.

6. Speichern Sie die *VSTEMPLATE*-Datei, und schließen Sie sie.

7. Wählen Sie im **Windows-Explorer** die Dateien aus, die in Ihrer Vorlage enthalten sein sollen. Klicken Sie mit der rechten Maustaste auf Auswahl, und klicken Sie anschließend auf **Senden an** > **ZIP-komprimierter Ordner**. Die ausgewählten Dateien werden in eine *ZIP*-Datei komprimiert.

::: moniker range="vs-2017"

8. Kopieren Sie die *ZIP*-Datei, und fügen Sie sie an dem Speicherort für die Benutzerelementvorlage ein. Das Standardverzeichnis ist *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Kopieren Sie die *ZIP*-Datei, und fügen Sie sie an dem Speicherort für die Benutzerelementvorlage ein. Das Standardverzeichnis ist *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [How to: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio Template Schema Reference (Extensibility) (Schemareferenz zu Vorlagen für Visual Studio (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md)
