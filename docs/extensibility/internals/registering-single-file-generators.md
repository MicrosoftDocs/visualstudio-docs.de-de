---
title: Registrieren von einzelnen Datei Generatoren | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Tool in Visual Studio registrieren, um es zu instanziieren und einem bestimmten Projekttyp zuzuordnen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a0ce4afeddebdec8519467e1f4249095ce98f6b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875257"
---
# <a name="registering-single-file-generators"></a>Registrieren von Generatoren einzelner Dateien
Um ein benutzerdefiniertes Tool in verfügbar zu machen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , müssen Sie es registrieren, damit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es instanziieren und einem bestimmten Projekttyp zuordnen kann.

### <a name="to-register-a-custom-tool"></a>So registrieren Sie ein benutzerdefiniertes Tool

1. Registrieren Sie die benutzerdefinierte Tool-DLL entweder in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokalen Registrierung oder in der Systemregistrierung unter HKEY_CLASSES_ROOT.

    Hier sind z. b. die Registrierungsinformationen für das verwaltete MSDataSetGenerator-Tool, das Folgendes enthält [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Erstellen Sie einen Registrierungsschlüssel im gewünschten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hive unter der Generatoren \\ -*GUID* , wobei *GUID* die GUID ist, die durch das Projekt System oder den Dienst der jeweiligen Sprache definiert ist. Der Name des Schlüssels wird zum programmgesteuerten Namen Ihres benutzerdefinierten Tools. Der benutzerdefinierte Tool Schlüssel weist die folgenden Werte auf:

   - (Standardwert)

        Optional. Stellt eine benutzerfreundliche Beschreibung des benutzerdefinierten Tools bereit. Dieser Parameter ist optional, wird jedoch empfohlen.

   - CLSID

        Erforderlich. Gibt den Bezeichner der Klassenbibliothek der COM-Komponente an, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - Generatesdesigntimesource

        Erforderlich. Gibt an, ob Typen aus Dateien, die von diesem benutzerdefinierten Tool erstellt werden, visuellen Designern zur Verfügung gestellt werden. Der Wert dieses Parameters muss (0) 0 (null) für Typen sein, die für visuelle Designer nicht verfügbar sind, oder (1) 1 für Typen, die visuellen Designern zur Verfügung stehen.

   > [!NOTE]
   > Sie müssen das benutzerdefinierte Tool separat für jede Sprache registrieren, für die das benutzerdefinierte Tool verfügbar sein soll.

    Der MSDataSetGenerator registriert sich z. b. einmal für jede Sprache:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementieren von Generatoren einzelner Dateien](../../extensibility/internals/implementing-single-file-generators.md)
- [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Einführung in das BuildManager-Objekt](/previous-versions/8f9kffa8(v=vs.140))