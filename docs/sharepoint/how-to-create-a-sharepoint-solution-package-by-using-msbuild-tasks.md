---
title: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Aufgaben
description: Erfahren Sie, wie Sie ein SharePoint-Lösungspaket (. wsp) mithilfe von MSBuild-Befehlszeilen auf einem Entwicklungs Computer erstellen, bereinigen und validieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f4c1d2e986b6a810cc568efd9577be87a38fdefb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873540"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Vorgehensweise: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Aufgaben
  Sie können ein SharePoint-Paket (*. wsp*) mithilfe von MSBuild-Befehlszeilen auf einem Entwicklungs Computer erstellen, bereinigen und validieren. Sie können diese Befehle auch zum Automatisieren des Buildprozesses verwenden, indem Sie Team Foundation Server auf einem Buildcomputer verwenden.

## <a name="build-a-sharepoint-package"></a>Erstellen eines SharePoint-Pakets

#### <a name="to-build-a-sharepoint-package"></a>So erstellen Sie ein SharePoint-Paket

1. Klicken Sie im Windows- **Startmenü** auf **Alle Programme**  >  **Zubehör**  >  **Eingabeaufforderung**.

2. Wechseln Sie in das Verzeichnis, in dem sich Ihr SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl ein, um ein Paket für das Projekt zu erstellen. Ersetzen Sie *ProjectFileName* durch den Namen des Projekts.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Beispielsweise können Sie einen der folgenden Befehle ausführen, um ein SharePoint-Projekt mit dem Namen ListDefinition1 zu verpacken.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Bereinigen eines SharePoint-Pakets

#### <a name="to-clean-a-sharepoint-package"></a>So bereinigen Sie ein SharePoint-Paket

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Wechseln Sie in das Verzeichnis, in dem sich Ihr SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl ein, um ein Paket für das Projekt zu bereinigen. Ersetzen Sie *ProjectFileName* durch den Namen des Projekts.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Beispielsweise können Sie einen der folgenden Befehle ausführen, um ein SharePoint-Projekt mit dem Namen ListDefinition1 zu bereinigen.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Überprüfen eines SharePoint-Pakets

#### <a name="to-validate-a-sharepoint-package"></a>So überprüfen Sie ein SharePoint-Paket

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Wechseln Sie in das Verzeichnis, in dem sich Ihr SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl ein, um ein Paket für das Projekt zu validieren. Ersetzen Sie *ProjectFileName* durch den Namen des Projekts.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Beispielsweise können Sie einen der folgenden Befehle ausführen, um ein SharePoint-Projekt mit dem Namen ListDefinition1 zu validieren.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Festlegen von Eigenschaften in einem SharePoint-Paket

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>So legen Sie eine Eigenschaft in einem SharePoint-Paket fest

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Wechseln Sie in das Verzeichnis, in dem sich Ihr SharePoint-Projekt befindet.

3. Geben Sie den folgenden Befehl ein, um eine Eigenschaft in einem Paket für das Projekt festzulegen. Ersetzen Sie *propertyName* durch die Eigenschaft, die Sie festlegen möchten.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Beispielsweise können Sie den folgenden Befehl ausführen, um die Warnstufe festzulegen.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Weitere Informationen
- [SharePoint-Features erstellen](../sharepoint/creating-sharepoint-features.md)
- [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Gewusst wie: Hinzufügen und Entfernen von Elementen zu SharePoint-Features](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
