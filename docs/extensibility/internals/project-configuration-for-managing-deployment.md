---
title: Projekt Konfiguration zum Verwalten der Bereitstellung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Bereitstellung für den erwarteten Speicherort für Debugging und Installation und die zwei Möglichkeiten, wie Visual Studio Projekte unterstützt, die die Bereitstellung
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ebdc1dc529e73e17ba55a0b4766f11dced4addcb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893645"
---
# <a name="project-configuration-for-managing-deployment"></a>Projektkonfiguration für die Verwaltung der Bereitstellung
Die Bereitstellung ist das physische Verschieben der Ausgabe Elemente aus einem Buildprozess an den erwarteten Speicherort zum Debuggen und installieren. Beispielsweise könnte eine Webanwendung auf einem lokalen Computer erstellt und dann auf dem Server platziert werden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Möglichkeiten, wie Projekte an der Bereitstellung beteiligt sein können:

- Als Gegenstand des Bereitstellungs Prozesses.

- Als Manager des Bereitstellungs Prozesses.

  Bevor Lösungen bereitgestellt werden können, müssen Sie zunächst ein Bereitstellungs Projekt hinzufügen, um die Bereitstellungs Optionen zu konfigurieren. Wenn das Bereitstellungs Projekt nicht bereits vorhanden ist, werden Sie gefragt, ob Sie ein Projekt erstellen möchten, **Wenn Sie im** Menü **Erstellen** die Option Projekt Mappe bereitstellen auswählen oder mit der rechten Maustaste auf die Lösung klicken. Wenn Sie auf **Ja** klicken, wird das Dialogfeld **Neues Projekt hinzufügen** mit ausgewähltem Remote Bereitstellungs- **Assistenten** geöffnet

  Der Assistent für die Remote Bereitstellung fragt Sie nach dem Anwendungstyp (Windows oder Web), den einzuschließenden Projekt Ausgabegruppen, zusätzlichen Dateien, die Sie einschließen möchten, und dem Remote Computer, auf dem Sie die Bereitstellung durchzuführen. Auf der letzten Seite des Assistenten wird eine Zusammenfassung der ausgewählten Optionen angezeigt.

  Bei Projekten, bei denen es sich um einen Bereitstellungs Prozess handelt, werden Ausgabe Elemente erzeugt, die in eine Alternative Umgebung verschoben werden müssen. Diese Ausgabe Elemente werden als Parameter für die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Schnittstelle beschrieben, deren Hauptzweck darin besteht, dass Projekte Ausgaben gruppieren können. Weitere Informationen zur Implementierung von finden Sie unter `IVsProjectCfg2` [Projekt Konfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

  Bereitstellungs Projekte, die den Bereitstellungs Prozess verwalten, aktivieren den Befehl bereitstellen und reagieren, wenn dieser Befehl ausgewählt ist. Bei Bereitstellungs Projekten wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> -Schnittstelle implementiert, um die Bereitstellung auszuführen und Aufrufe an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> Schnittstelle zu senden, um Statusereignisse

  Konfigurationen können Abhängigkeiten angeben, die sich auf Ihre Build-oder Bereitstellungs Vorgänge auswirken. Abhängigkeiten erstellen oder bereitstellen sind Projekte, die entweder erstellt oder bereitgestellt werden müssen, bevor oder nachdem die Konfigurationen selbst erstellt oder bereitgestellt wurden. Buildabhängigkeiten zwischen Projekten werden mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> -Schnittstelle beschrieben und stellen Abhängigkeiten mit der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Schnittstelle bereit Weitere Informationen finden Sie unter [Project Configuration for Building](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
