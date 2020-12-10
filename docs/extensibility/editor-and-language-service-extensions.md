---
title: Editor-und Sprachdienst Erweiterungen | Microsoft-Dokumentation
description: Sie können die meisten Funktionen des Visual Studio Code-Editors erweitern, der mit Windows Presentation Foundation implementiert wird und in verwaltetem Code geschrieben ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b15d5f970bfc6a32489991b578a54f2eadc96ea
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995823"
---
# <a name="editor-and-language-service-extensions"></a>Editor-und Sprachdienst Erweiterungen
Die meisten Features von Visual Studio Code-Editor können erweitert werden. Der Editor basiert auf dem Windows Presentation Foundation (WPF) und wird in verwaltetem Code geschrieben. Obwohl dieser Entwurf sich von den Entwürfen in früheren Versionen von Visual Studio unterscheidet, bietet er die meisten der gleichen Funktionen. Um den Editor zu erweitern, verwenden Sie den Managed Extensibility Framework (MEF).

 Das Visual Studio SDK bietet Adapter, die als *Shims* bezeichnet werden, um VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie jedoch über ein vorhandenes VSPackage verfügen, empfiehlt es sich, es auf die neue Technologie zu aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erzielen.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Einführung in die Verwendung der Editor-Element Vorlagen.|
|[Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)|Links zu Dokumenten, die den Entwurf und die Features des Kern Editors einführen und zeigen, wie Sie erweitert werden.|
|[Legacy Schnittstellen im Editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|Links zu Dokumenten, in denen erläutert wird, wie Sie aus vorhandenem Code auf den Core-Editor zugreifen.|
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Links zu Dokumenten, die erläutern, wie benutzerdefinierte Editoren erstellt werden.|
|[Erweiterbarkeit von Legacy Sprachdiensten](../extensibility/internals/legacy-language-service-extensibility.md)|Links zu Dokumenten, in denen beschrieben wird, wie Programmiersprachen in Visual Studio integriert werden.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Führt die Managed Extensibility Framework (MEF) ein.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Führt die Windows Presentation Foundation (WPF) ein.|
