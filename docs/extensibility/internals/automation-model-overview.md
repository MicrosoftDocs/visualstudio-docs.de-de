---
title: Übersicht über das Automatisierungs Modell | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Visual Studio-Automatisierungs Modell, das aus einem Satz von Objekten besteht, für die Sie ein Visual Studio-Add-in oder eine Erweiterung schreiben können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26184263d5f269ebf6922c5dd85a37e93356e935
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906017"
---
# <a name="automation-model-overview"></a>Übersicht über das Automatisierungs Modell
Das Automatisierungs Modell besteht aus einem Satz von Objekten, für die Sie ein Visual Studio-Add-in oder eine Erweiterung schreiben können. Ein Add-in ist eine Anwendung, die die Visual Studio-Umgebung bearbeiten und häufige Aufgaben automatisieren kann. Mit einer Visual Studio-Erweiterung können benutzerdefinierte Visual Studio-Komponenten erstellt oder der Funktionalität von Standardkomponenten wie dem Text-Editor hinzugefügt werden.

## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungs Modell
 Das Automatisierungs Modell besteht aus verwandten Gruppen von Objekten, die die wichtigsten Facetten der allgemeinen Umgebung steuern. Das folgende Diagramm zeigt den umfangreichen Satz von Visual Studio-Objekten, die das Automatisierungs Modell bilden.

 ![Visual Studio-Automatisierungs Objekt Diagramm](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsvisualstudioautomationobjectchart")

 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](/previous-versions/esk3eey8(v=vs.140)).

 Die Umgebung stellt ein Modell für unterschiedliche Funktionsbereiche bereit. Beispielsweise gibt es ein Code Modell für verschiedene Elemente, die möglicherweise im Code gefunden werden. Es ist ein Dokument Modell für verschiedene Dokument Elemente vorhanden. Ein Bereich, der Projektbereich, ist von besonderem Interesse für VSPackage-Anbieter. Wahrscheinlich möchten Sie, dass Ihre neuen Projekttypen auf die gleiche Weise zum Automatisierungs Modell beitragen [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zum Automatisierungs Modell beitragen. Dieser Vorgang ist unter [Bereitstellen der Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)beschrieben.

 Orte, an denen Sie in Erwägung gezogen werden, das Automatisierungs Modell der Umgebung zu erweitern:

- Project

- Dokument

- Code

- Erstellen

Weitere Informationen zur Automatisierung finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015). Dieses Dokument und die Dokumente, zu denen es Links enthält, helfen Ihnen, Entscheidungen darüber zu treffen, wie Sie Automation für Ihr VSPackage bereitstellen sollten.

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen eines Add-ins](/previous-versions/80493a3w(v=vs.140))