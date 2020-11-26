---
title: CATIDs für Objekte, die normalerweise zum Erweitern von Projekten verwendet werden
description: Erlernen Sie die CATIDs für Objekte, die zum Erweitern von Project-und ProjectItem-Automatisierungs Objekten für Visual Basic-, Visual c#-und Visual C++-Projekte verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b0b20425cd1508db29932e9687d00055e4db58c
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190017"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden
In der folgenden Tabelle sind CATIDs aufgelistet, die zum `Project` Erweitern `ProjectItem` von und Automatisierungs Objekten für- [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] -und- [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte verwendet werden. Diese CATIDs werden in *VSLangProj. olb* definiert.

## <a name="listing-of-catids"></a>Auflistung von CATIDs

|name|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610d4614-d0d5-11d2-8599-006097c68e81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610d4615-d0d5-11d2-8599-006097c68e81}|

## <a name="visual-basic-catids"></a>CATIDs Visual Basic
 In der folgenden Tabelle sind CATIDs aufgelistet, die zum Erweitern von Browse-Objekten verwendet werden [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . Sie sind alle in *VSLangProj. olb* definiert.

|name|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0b3824bd575f}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67o8dd11-14eb-489b-87f 0-|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932dc619-2eaa-4192-B7E6-3d15ad31df49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289b812-8191-4e81-b7b3-174045ab0cb5}|

## <a name="visual-c-catids"></a>Visual c#-CATIDs
 Die folgenden CATIDs können zum Erweitern von Browse-Objekten verwendet werden [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Sie sind alle in *VSLangProj. olb* definiert.

|name|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4ef9f 003-95-4d60-96b0-212979f 2 A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227f-4963-ADB6-3a43388513ca}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8d58e6af-ed4e-48b0-8c7b-c74ef0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914fe278-054a-45dB-bfi9e-5F 22484cc84c}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F 0fa3b8-C855-4a4e-95a5-cb45c67d6c27}|

## <a name="c-catids"></a>C++-CATIDs
 Die folgenden [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekt System-CATIDs werden in Typbibliotheken in .NET 2003 nicht verfügbar gemacht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und müssen in den Code eingefügt werden, wenn Sie diese Projekt Objekte erweitern möchten. Diese CATIDs werden in den Typbibliotheken in späteren Versionen von enthalten sein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|name|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 Im folgenden Codebeispiel wird veranschaulicht, wie diese CATIDs in Ihrem Code programmiert werden.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Die folgenden [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekt System-CATIDs werden in den Typbibliotheken in .NET 2003 ebenfalls nicht verfügbar gemacht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und müssen in den Code eingefügt werden, wenn Sie diese Projekt Objekte erweitern möchten. Diese CATIDs sind nur in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 verfügbar und nicht in den späteren Versionen von verfügbar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|name|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593dcfce-20a7-48e4-aca1-49ade9049887}|
|`CVCActiveXReferenceNode`|{9e8182d3-c60a-44f 4-a74b-14c90ef9cace}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 Im folgenden Codebeispiel wird veranschaulicht, wie diese CATIDs in Ihrem Code programmiert werden:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Die GUIDs für die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] -und- [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen sind in der folgenden Tabelle aufgeführt.

| Projekttyp | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Weitere Informationen
- [Projekt-und Projekt Element Vorlagen hinzufügen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
