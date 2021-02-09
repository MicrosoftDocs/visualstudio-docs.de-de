---
title: Projektmappenkonfiguration | Microsoft-Dokumentation
description: Erfahren Sie, wie die vom Projekttyp unterstützten Projektmappenkonfigurationen implementiert werden, die das Verhalten des Starts (F5) und der Buildbefehle direkt steuern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99a0de44d5e7ac240187c929a8134ab47c7de55c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910982"
---
# <a name="solution-configuration"></a>Projektmappenkonfiguration
Projektmappenkonfigurationen speichern Eigenschaften auf Projektmappenebene. Sie leiten das Verhalten des **Starts** (F5 **) und der** Buildbefehle weiter. Standardmäßig wird mit diesen Befehlen die Debugkonfiguration erstellt und gestartet. Beide Befehle werden im Kontext einer Projektmappenkonfiguration ausgeführt. Dies bedeutet, dass der Benutzer mit dem Start und der Erstellung der aktiven Projekt Mappe mit den Einstellungen beginnen kann. Die Umgebung ist so konzipiert, dass Sie bei der Erstellung und Ausführung von Lösungen optimiert wird.

 Die standardmäßige Visual Studio-Symbolleiste enthält die Start Schaltfläche und eine Projektmappenkonfiguration auf der rechten Seite der Schaltfläche Start. Diese Liste ermöglicht es Benutzern, die Konfiguration auszuwählen, die beim Drücken von F5 gestartet werden soll, eigene Projektmappenkonfigurationen zu erstellen oder eine vorhandene Konfiguration zu bearbeiten.

> [!NOTE]
> Es sind keine Erweiterbarkeits Schnittstellen zum Erstellen oder Bearbeiten der Projektmappenkonfigurationen vorhanden. Hierzu muss `DTE.SolutionBuild` verwendet werden. Es gibt jedoch Erweiterbarkeits-APIs für die Verwaltung des Projektmappenbuilds. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Im folgenden wird erläutert, wie Sie die vom Projekttyp unterstützten Projektmappenkonfigurationen implementieren können:

- Project

   Zeigt die Namen der in der aktuellen Projekt Mappe gefundenen Projekte an.

- Konfiguration

   Um die Liste der Konfigurationen bereitzustellen, die vom Projekttyp unterstützt werden und auf den Eigenschaften Seiten angezeigt werden, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .

   In der Spalte Konfiguration wird der Name der Projekt Konfiguration angezeigt, die in dieser Projektmappenkonfiguration erstellt werden soll, und es werden alle Projekt Konfigurationen aufgelistet, wenn Sie auf die Pfeil Schaltfläche klicken. Die Umgebung Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> Methode auf, um diese Liste auszufüllen. Wenn die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Methode angibt, dass das Projekt die Konfigurations Bearbeitung unterstützt, werden auch neue oder Bearbeitungs Optionen unter der Überschrift "Konfiguration" angezeigt. Jede dieser Optionen startet Dialogfelder, in denen Methoden der `IVsCfgProvider2` -Schnittstelle zum Bearbeiten der Projekt Konfigurationen aufgerufen werden.

   Wenn ein Projekt keine Konfigurationen unterstützt, wird in der Spalte Konfiguration der Wert keine angezeigt, und ist deaktiviert.

- Plattform

   Zeigt die Plattform an, für die die ausgewählte Projekt Konfiguration erstellt wird, und listet alle verfügbaren Plattformen für das Projekt auf, wenn Sie auf die Pfeil Schaltfläche klicken. Die Umgebung Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> Methode auf, um diese Liste auszufüllen. Wenn die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Methode angibt, dass das Projekt Platt Form Bearbeitung unterstützt, werden unter der Platt Form Überschrift auch neue oder Bearbeitungs Optionen angezeigt. Jede dieser Auswahl Optionen startet Dialogfelder, die `IVsCfgProvider2` Methoden aufrufen, um die verfügbaren Plattformen des Projekts zu bearbeiten.

   Wenn ein Projekt Plattformen nicht unterstützt, wird in der Spalte Plattform für dieses Projekt der Wert keine angezeigt, und ist deaktiviert.

- Erstellen

   Gibt an, ob das Projekt von der aktuellen Projektmappenkonfiguration erstellt wird. Nicht ausgewählte Projekte werden nicht erstellt, wenn die Buildbefehle auf Projektmappenebene trotz der Projekt Abhängigkeiten aufgerufen werden, die Sie enthalten. Projekte, die nicht für die Erstellung ausgewählt wurden, sind weiterhin in Debuggen, ausführen, packen und Bereitstellen der Lösung enthalten.

- Bereitstellen

   Gibt an, ob das Projekt bereitgestellt wird, wenn die Befehle zum Starten oder Bereitstellen mit der ausgewählten projektmappenbuildkonfiguration verwendet werden. Das Kontrollkästchen für dieses Feld ist verfügbar, wenn das Projekt die Bereitstellung unterstützt, indem die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle für sein Objekt implementiert wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> .

  Nach dem Hinzufügen einer neuen Projektmappenkonfiguration kann der Benutzer diese im Dropdown-Listenfeld Projektmappenkonfiguration auf der Standard Symbolleiste auswählen, um diese Konfiguration zu erstellen und/oder zu starten.

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
