---
title: Attribute für die Website Unterstützung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Website-Support Attribute, die für die Erweiterung der Funktionalität von Visual Studio mithilfe von Website Projekten erforderlich sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9beee39ca6968b0922bc134fa21e0cde3d6dd3b6
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487867"
---
# <a name="web-site-support-attributes"></a>Attribute der Websiteunterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Das Website Projekt kann erweitert werden, um Unterstützung für webprogrammier Sprachen bereitzustellen. Die Sprache muss sich bei registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit Projektvorlagen im Dialogfeld **neue Website** angezeigt werden können, wenn die Sprache ausgewählt ist.

Das IronPython Studio-Beispiel enthält Website Unterstützung. Das Beispiel enthält die folgenden Attribut Klassen, um IronPython als Code Behind-Sprache für neue Webprojekte zu registrieren.

## <a name="websiteprojectattribute"></a>Websiteprojectattribute
 Dieses Attribut wird in das Sprachprojekt eingefügt. Die Sprache wird der Liste der webprogrammier Sprachen in der Liste **Sprache** im Dialogfeld **neue Website** hinzugefügt. Mit dem folgenden Code wird beispielsweise IronPython zur Liste hinzugefügt:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Dieses Attribut legt auch den Vorlagen Pfad so fest, dass er auf den Vorlagen Ordner verweist. Weitere Informationen zum Speicherort des Ordners "Vorlagen" finden Sie [unter Vorlagen für Website Unterstützung](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>Websiteprojectrelatedfilesattribute
 Dieses Attribut wird in das Sprachprojekt eingefügt. Dadurch kann das Website Projekt einen Dateityp (Related) unter einem anderen Dateityp (primär) im **Projektmappen-Explorer** Schachteln.

 Der folgende Code gibt z. b. an, dass eine IronPython-Code Behind-Datei mit einer ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer IronPython-Website Lösung erstellt wird, wird eine neue py-Quelldatei generiert und als untergeordneter Knoten der ASPX-Seite angezeigt.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>Provideintellisentsproviderattribute
 Dieses Attribut wird im Sprachprojekt Paket abgelegt. Er wählt den IntelliSense-Anbieter für die Sprache aus.

 Der folgende Code gibt z. b. an, dass eine Instanz von pythonintellisenseprovider, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , bei Bedarf erstellt werden soll, um Sprachdienste bereitzustellen.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Die ivsintellisenseproject-Implementierung behandelt Verweise und ruft den sprach Compiler auf, wenn eine Webseite mit Code angefordert, jedoch nicht zwischengespeichert wird.

## <a name="see-also"></a>Weitere Informationen
- [Websiteunterstützung](../../extensibility/internals/web-site-support.md)
