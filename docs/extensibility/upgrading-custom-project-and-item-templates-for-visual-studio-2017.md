---
title: Aktualisieren von benutzerdefinierten Projekt-und Element Vorlagen für Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Projekt und eine Element Vorlage aus früheren Versionen des Visual Studio SDK für die Verwendung mit Visual Studio 2017 und höheren Versionen aktualisieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 089baadcb60afcc8b32e287095b10ab30196ce17
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715976"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Aktualisieren des benutzerdefinierten Projekt-und Elementvorlagen für Visual Studio 2017

Ab Visual Studio 2017 werden von Visual Studioprojekt-und Element Vorlagen erkannt, die von einer VSIX-oder MSI-Datei auf andere Weise als frühere Versionen von Visual Studio installiert wurden. Wenn Sie über Erweiterungen verfügen, die benutzerdefinierte Projekt-oder Element Vorlagen verwenden, müssen Sie die Erweiterungen aktualisieren. In diesem Artikel wird erläutert, was Sie tun müssen.

Diese Änderung wirkt sich nur auf Visual Studio 2017 aus. Frühere Versionen von Visual Studio sind nicht betroffen.

Wenn Sie ein Projekt oder eine Element Vorlage als Teil einer VSIX-Erweiterung erstellen möchten, finden Sie weitere Informationen unter [Erstellen von benutzerdefinierten Projekt-und Element Vorlagen](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Vorlagen Scan

In früheren Versionen von Visual Studio hat **Devenv/Setup** oder **devenv/installvstemplates** den lokalen Datenträger durchsucht, um Projekt-und Element Vorlagen zu finden. Ab Visual Studio 2017 wird die Überprüfung nur für den Speicherort auf Benutzerebene durchgeführt. Der Standard Speicherort auf Benutzerebene ist **%UserProfile%\Documents \\<Visual Studio-Version \> \Vorlagen \\**. Dieser Speicherort wird für Vorlagen verwendet, die vom Befehl **Project**  >  **Export Templates...** generiert werden, wenn die Option **Vorlage automatisch in Visual Studio importieren** im Assistenten ausgewählt ist.

Für andere (Nichtbenutzer-) Speicherorte müssen Sie eine Manifest-Datei (. vstman) einschließen, die den Speicherort und andere Eigenschaften der Vorlage angibt. Die vstman-Datei wird zusammen mit der VSTEMPLATE-Datei generiert, die für Vorlagen verwendet wird. Wenn Sie die Erweiterung mit einer vsix-Datei installieren, können Sie dies erreichen, indem Sie die Erweiterung in Visual Studio 2017 neu kompilieren. Wenn Sie jedoch eine MSI-Anwendung verwenden, müssen Sie die Änderungen manuell vornehmen. Eine Liste der Aktionen, die Sie ausführen müssen, um diese Änderungen vorzunehmen, finden Sie unter  **Upgrades für Erweiterungen, die mit installiert wurden. MSI** weiter unten auf dieser Seite.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Aktualisieren einer VSIX-Erweiterung mit Projekt-oder Element Vorlagen

1. Öffnen Sie die Projekt Mappe in Visual Studio 2017. Sie werden aufgefordert, den Code zu aktualisieren. Klicken Sie auf **OK**.

2. Nachdem das Upgrade abgeschlossen ist, müssen Sie möglicherweise die Version des Installations Ziels ändern. Öffnen Sie im VSIX-Projekt die Datei "Source. Extension. vsixmanifest", und wählen Sie die Registerkarte **Ziele installieren** aus. Wenn das Feld **Versions Bereich** den Wert **[14,0]** hat, klicken Sie auf **Bearbeiten** , und ändern Sie es in Visual Studio 2017. Beispielsweise können Sie die Erweiterung auf **[14,0, 15,0]** festlegen, um die Erweiterung entweder in Visual Studio 2015 oder Visual Studio 2017 zu installieren, oder auf **[15,0]** , um Sie in Visual Studio 2017 zu installieren.

3. Kompilieren Sie den Code neu.

4. Schließen Sie Visual Studio.

5. Installieren Sie die VSIX.

6. Sie können das Update testen, indem Sie die folgenden Schritte ausführen:

    1. Die Datei Scan Änderung wird durch den folgenden Registrierungsschlüssel aktiviert:

         **reg Add hklm\software\microsoft\visualstudio\15.0\vstemplate/v disabletemplatescanning/t REG_DWORD/d 1/reg: 32**

    2. Nachdem Sie den Schlüssel hinzugefügt haben, führen Sie " **tovenv/installvstemplates**" aus.

    3. Öffnen Sie Visual Studio erneut. Sie sollten Ihre Vorlage am erwarteten Speicherort finden.

    > [!NOTE]
    > Die Projektvorlagen für Visual Studio-Erweiterbarkeit sind nicht verfügbar, wenn der Registrierungsschlüssel vorhanden ist. Sie müssen den Registrierungsschlüssel löschen (und " **tovenv/installvstemplates**" erneut ausführen), um Sie zu verwenden.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Weitere Empfehlungen zum Bereitstellen von Projekt-und Element Vorlagen

- Vermeiden Sie die Verwendung von ZIP-Vorlagen Dateien. ZIP-Vorlagen Dateien müssen dekomprimiert werden, um Ressourcen und Inhalte abzurufen, sodass Sie von Ihnen verwendet werden können. Stattdessen sollten Sie Projekt-und Element Vorlagen als einzelne Dateien in Ihrem eigenen Verzeichnis bereitstellen, um die Vorlagen Initialisierung zu beschleunigen. Bei VSIX-Erweiterungen werden bei der Erstellung der VSIX-Datei beim Erstellen der VSIX-Datei automatisch alle zip-Vorlagen entzippt.

- Vermeiden Sie die Verwendung von Paketen/Ressourcen-ID-Einträgen für den Vorlagen Namen, die Beschreibung, das Symbol oder die Vorschau, um unnötige Ressourcenassembly-Ladevorgänge bei der Vorlagen Ermittlung zu vermeiden Stattdessen können Sie lokalisierte Manifeste verwenden, um einen Vorlagen Eintrag für jedes Gebiets Schema zu erstellen, in dem lokalisierte Namen oder Eigenschaften verwendet werden.

- Wenn Sie Vorlagen als Dateielemente einschließen, liefert die Generierung von Manifesten möglicherweise nicht die erwarteten Ergebnisse. In diesem Fall müssen Sie dem VSIX-Projekt ein manuell generiertes Manifest hinzufügen.

## <a name="file-changes-in-project-and-item-templates"></a>Dateiänderungen in Projekt-und Element Vorlagen
Wir zeigen die Differenz Punkte zwischen der Visual Studio 2015-Version und der Visual Studio 2017-Version der Vorlagen Dateien, sodass Sie die neuen Dateien ordnungsgemäß erstellen können.

 Hier ist die standardmäßige Project. VSTEMPLATE-Datei, die von Visual Studio 2015 erstellt wurde:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Hier sehen Sie die vstman-Datei (Sie finden Sie im Manifest-Verzeichnis des VSIX-Projekts), die aus der Neuerstellung des VSIX-Projekts resultiert:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Die vom [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) -Element bereitgestellten Informationen bleiben unverändert. Das- **\<VSTemplateContainer>** Element verweist auf die VSTEMPLATE-Datei für die zugeordnete Vorlage.

 Hier ist die Standarddatei "Item. vstemplate", die von Visual Studio 2015 erstellt wurde:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Hier sehen Sie die vstman-Datei (Sie finden Sie im Manifest-Verzeichnis des VSIX-Projekts), die aus der Neuerstellung des VSIX-Projekts resultiert:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 Die vom-Element bereitgestellten Informationen **\<TemplateData>** bleiben unverändert. Das- **\<VSTemplateContainer>** Element verweist auf die VSTEMPLATE-Datei für die zugehörige Vorlage.

 Weitere Informationen zu den verschiedenen Elementen der vstman-Datei finden Sie unter [Schema Referenz für das Visual Studio-Vorlagen Manifest](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrades für Erweiterungen, die mit installiert werden. MSI

Einige MSI-basierte Erweiterungen stellen Vorlagen für gängige Vorlagen Speicherorte wie die folgenden Verzeichnisse bereit:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\ide\Extensions \\<ExtensionName \> \\<Project/ItemTemplates\>**

Wenn Ihre Erweiterung eine MSI-basierte Bereitstellung ausführt, müssen Sie das Vorlagen Manifest manuell generieren und sicherstellen, dass es in der Erweiterungs Einrichtung enthalten ist. Vergleichen Sie die oben aufgeführten vstman-Beispiele und die [Schema Referenz für das Visual Studio-Vorlagen Manifest](../extensibility/visual-studio-template-manifest-schema-reference.md).

Erstellen Sie separate Manifeste für Projekt-und Element Vorlagen, und Sie sollten wie oben beschrieben auf das Stamm Vorlagen Verzeichnis verweisen. Erstellen Sie ein Manifest pro Erweiterung und Gebiets Schema.

## <a name="see-also"></a>Weitere Informationen

- [Problembehandlung bei Vorlagen Ermittlung](troubleshooting-template-discovery.md)
- [Erstellen von benutzerdefinierten Projekt-und Element Vorlagen](creating-custom-project-and-item-templates.md)
