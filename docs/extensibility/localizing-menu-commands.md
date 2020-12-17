---
title: Lokalisieren von Menübefehlen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie lokalisierten Text für Menü-und Symbolleisten Befehle bereitstellen, indem Sie lokalisierte vsct-Dateien und lokalisierte RESX-Dateien für Ihr VSPackage erstellen.
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51f3692a4539eddbf35e24de8024eadd39031080
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97615602"
---
# <a name="localize-menu-commands"></a>Lokalisieren von Menübefehlen

Sie können lokalisierten Text für Menü-und Symbolleisten Befehle angeben, indem Sie lokalisierte *vsct* -Dateien und lokalisierte *RESX* -Dateien für das VSPackage erstellen und dann die Projektdateien aktualisieren, um die Änderungen einzubeziehen.

Informationen dazu, wie Sie die Installation lokalisieren, finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalisieren von Befehlsnamen

In VSPackages werden Menübefehle und Symbolleisten Schaltflächen in der *vsct* -Datei definiert.

1. Ändern Sie in **Projektmappen-Explorer** den Namen der *vsct* -Datei von *Dateiname. vsct* in *filename. en-US. vsct*.

2. Erstellen Sie für jede lokalisierte Sprache eine Kopie von *Dateiname. en-US. vsct* .

    Benennen Sie die einzelnen Kopier *Dateinamen. { Locale}. vsct*, wobei " *{locale}* " ein bestimmter Kultur Name ist. Eine Liste der Kultur Namen Werte finden Sie unter [von Microsoft zugewiesene](/windows/uwp/publish/supported-languages)Gebiets Schema-IDs.

    Diese *Dateinamen. Locale. vsct* -Dateien enthalten den lokalisierten Menütext für das Paket.

3. Öffnen Sie jeden *Dateinamen. Locale. vsct* -Datei, um den Text zu lokalisieren.

   1. Ändern Sie die Werte für das [ButtonText](../extensibility/buttontext-element.md) -Element entsprechend der jeweiligen Sprache.

   2. Wenn Sie lokalisierte Symbole bereitstellen, ändern Sie die [Bitmap](../extensibility/bitmap-element.md) -Werte so, dass Sie auf die Zieldateien zeigen.

      Das folgende Beispiel zeigt den Text der Schaltfläche Englisch und Spanisch für einen Befehl zum Öffnen eines Fensters des Fensters "Familienstruktur-Explorer".

      [*FamilyTree. en-US. vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-es. vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Lokalisieren anderer Textressourcen

Andere Text Ressourcen als Befehlsnamen werden in Ressourcen Dateien (*RESX*-Dateien) definiert.

1. Benennen Sie *VSPackage. resx* in *VSPackage. en-US. resx* um.

2. Erstellen Sie für jede lokalisierte Sprache eine Kopie der Datei " *VSPackage. en-US. resx* ".

     Benennen Sie jedes Kopie- *VSPackage. { Locale}. resx*, wobei *{locale}* ein bestimmter Kultur Name ist.

3. Benennen Sie *Resources. resx* in *Resources. en-US. resx* um.

4. Erstellen Sie für jede lokalisierte Sprache eine Kopie der Datei " *Resources. en-US. resx* ".

     Benennen Sie die einzelnen Kopier *Ressourcen. { Locale}. resx*, wobei *{locale}* ein bestimmter Kultur Name ist.

5. Öffnen Sie jede *RESX* -Datei, um die Zeichen folgen Werte entsprechend der jeweiligen Sprache und Kultur zu ändern. Das folgende Beispiel zeigt die lokalisierte Ressourcendefinition für die Titelleiste eines Tool Fensters.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-es. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Einbinden lokalisierter Ressourcen in das Projekt

Sie müssen die Datei *AssemblyInfo.cs* und die Projektdatei ändern, um die lokalisierten Ressourcen zu integrieren.

1. Öffnen Sie im-Editor aus dem Knoten **Eigenschaften** in **Projektmappen-Explorer** *AssemblyInfo.cs* oder *AssemblyInfo. vb* .

2. Fügen Sie den folgenden Eintrag hinzu.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Dadurch wird US-Englisch als Standardsprache festgelegt.

3. Entladen Sie das Projekt.

4. Öffnen Sie die Projektdatei im Editor.

5. Fügen Sie im root- `Project` Element ein- `PropertyGroup` Element mit einem- `UICulture` Element hinzu, das Ihrer Standardsprache entspricht.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Dadurch wird US-Englisch als standardmäßige Benutzeroberflächen Kultur für Windows Presentation Foundation (WPF)-Steuerelemente festgelegt.

6. Suchen Sie das- `ItemGroup` Element, das- `EmbeddedResource` Elemente enthält.

7. `EmbeddedResource`Ersetzen Sie im-Element, das *VSPackage. en-US. resx* aufruft, das `ManifestResourceName` -Element durch ein `LogicalName` -Element, das auf festgelegt ist `VSPackage.en-US.Resources` , wie folgt:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Kopieren Sie für jede lokalisierte Sprache das-  `EmbeddedResource` Element für `VsPackage.en-US` , und legen Sie das **include** -Attribut und das **LogicalName** -Element der Kopie auf das Ziel Gebiets Schema fest.

9. Fügen Sie für jedes lokalisierte `VSCTCompile` Element ein-Element hinzu, `ResourceName` das auf verweist `Menus.ctmenu` , wie im folgenden Beispiel gezeigt:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Speichern Sie die Projektdatei, und laden Sie das Projekt erneut.

11. Erstellen Sie das Projekt.

     Dadurch werden eine Hauptassembly und Ressourcenassemblys für jede Sprache erstellt. Informationen zum Lokalisieren des Bereitstellungs Prozesses finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md) .

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
