---
title: Übersicht über Konfigurationsoptionen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Optionen für Projekt Konfigurationen in Visual Studio. Eine Konfiguration ist ein Buildtyp, der mit einem benannten Satz von Eigenschaften und Dateispeicher Orten beschrieben wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa018d340e016ba5c9f424f705599a150ecdc818
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884688"
---
# <a name="configuration-options-overview"></a>Übersicht über Konfigurationsoptionen
Projekte in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können mehrere Konfigurationen unterstützen, die erstellt, gedebuggten, ausgeführt und/oder bereitgestellt werden können. Eine Konfiguration ist ein Buildtyp, der mit einem benannten Satz von Eigenschaften beschrieben wird, in der Regel compilerswitches und Dateispeicher Orte. Standardmäßig enthalten neue Lösungen zwei Konfigurationen: *Debug* und *Release*. Diese Konfigurationen können mithilfe ihrer Standardeinstellungen angewendet oder geändert werden, um Ihre spezifischen Anforderungen an Projektmappen und/oder Projektanforderungen zu erfüllen. Einige Pakete können auf zwei Arten erstellt werden: als ActiveX-Editor oder als direkte Komponente. Projekte müssen jedoch nicht mehrere Konfigurationen unterstützen. Wenn nur eine Konfiguration verfügbar ist, wird diese Konfiguration allen Lösungs Konfigurationen zugeordnet.

 Konfigurationen bestehen in der Regel aus zwei Teilen: dem Konfigurations Namen (z. b. *Debug* oder *Release*) und den Platt Form Einstellungen. Der Platt Form Name einer Konfiguration identifiziert die Umgebung, auf die die Konfiguration ausgerichtet ist, z. b. einen API-Satz oder eine Betriebssystem Plattform. Benutzer von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können keine Plattform erstellen. Sie müssen aus der Auswahl wählen, die ein VSPackage für das Projekt zulässt. Wenn ein Benutzer ein VSPackage installiert, kann die Übermittlungs Plattform, die während der Entwicklung des Pakets erstellt wurde, basierend auf den Kriterien, die vom Paket Ersteller festgelegt wurden, einen beliebigen Platt Form Namen sehen. Der Benutzer kann dann aus der Liste der Plattformen auswählen, die über das VSPackage verfügbar gemacht werden, wenn die Eigenschaften Seiten instanziiert werden.

 Platt Form Namen sind optional, da nicht alle Projekte das Konzept von Plattformen unterstützen. Wenn in einer Konfiguration ein Platt FormName fehlt, wird die Zeichenfolge **N/v** in der Benutzeroberfläche angezeigt.

 Jede Lösung verfügt über einen eigenen Satz von Konfigurationen, von denen jeweils nur eine aktiv sein kann. Eine Projektmappenkonfiguration ist ein Satz von nur einer Konfiguration aus jedem Projekt. Die "nicht mehr als"-Bedingung ist darauf zurückzuführen, dass ein Projekt aus einer Projektmappenkonfiguration ausgeschlossen wird. Benutzer können eigene benutzerdefinierte Projektmappenkonfigurationen erstellen.

 In der folgenden Tabelle sind die typischen Konfigurationseinstellungen für ein-Projekt veranschaulicht. Die Zeilen werden mit Konfigurations Namen und den Spalten mit Platt Form Namen gekennzeichnet.

|Konfigurationsname|Plattform: Win32|Plattform: Win64|
|------------------------|----------------------|----------------------|
|*Debuggen*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Release*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|–|\<MyConfig Win64 settings>|

> [!NOTE]
> Sie können keine *myconfig* -Projektmappenkonfiguration erstellen, die eine Win32-Plattform ausschließt, es sei denn, das Projekt, auf das Sie abzielen, unterstützt

 Wenn Sie die aktive Konfiguration für eine Lösung ändern, wird der Satz von Projekt Konfigurationen ausgewählt, die in dieser Lösung erstellt, ausgeführt, debuggten oder bereitgestellt werden. Wenn Sie z. b. die aktive Projektmappenkonfiguration von *Release* in *Debug* ändern, werden alle Projekte in dieser Projekt Mappe automatisch mit der Konfiguration des Projekts erstellt, die in der Debugkonfiguration der Projekt Mappe angegeben ist. Die Konfigurationen der Projekte werden auch als *Debug* bezeichnet, es sei denn, der Benutzer hat manuell Änderungen am Configuration Manager der Umgebung vorgenommen.

 Die für jedes Projekt gespeicherten projektmappenkonfigurationseigenschaften enthalten den Projektnamen, den Namen der Projekt Konfiguration, Flags, die angeben, ob erstellt oder bereitgestellt werden soll, und den Namen der Plattform. Weitere Informationen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).

 Der Benutzer kann projektmappenkonfigurations-Parameter anzeigen und festlegen, indem er die Projekt Mappe in der Hierarchie (Projektmappen-Explorer) auswählt und die Eigenschaften Seiten öffnet. Auf ähnliche Weise können Sie Projekt Konfigurationsparameter anzeigen und festlegen, indem Sie in Projektmappen-Explorer ein Projekt auswählen und die Eigenschaften Seiten für das Projekt öffnen.

 Der Benutzer kann mit den Einstellungen für die Releasekonfiguration und allen anderen ggf. mit Debugkonfigurationseinstellungen auch ein Projekt erstellen. Weitere Informationen finden Sie unter [Project Configuration for Building](../../extensibility/internals/project-configuration-for-building.md).

 Das folgende Diagramm zeigt, wie die Schnittstellen implementiert werden, die Projektmappen-und Projekt Konfigurationen unterstützen:

 ![Grafik zu Konfigurations Schnittstellen](../../extensibility/internals/media/vsconfiginterfaces.gif "vsconfiginterfaces") Konfigurations Schnittstellen

 Einige Anmerkungen im Zusammenhang mit dem vorherigen Diagramm:

- `IDispatch` wird im Konfigurationsobjekt als optional gekennzeichnet. Insbesondere ist es optional, dass die Konfigurations Schnittstellen für das Browse-Objekt vorhanden sind.

- `IVsDebuggableProjectCfg` ist im Konfigurationsobjekt als optional gekennzeichnet, ist aber für die Debugunterstützung erforderlich.

- `IVsProjectCfg2` ist im Konfigurationsobjekt als optional gekennzeichnet, wird jedoch für die Unterstützung der Ausgabe Gruppierung benötigt.

- Das Konfigurations Anbieter Objekt ist als optionales Objekt gekennzeichnet, aber die Option ist der Ort, an dem es implementiert wird. Sie können das-Objekt für das Project-Objekt oder ein separates-Objekt implementieren.

- `IVsCfgProvider2` wird für Platt Form Unterstützung und Konfigurations Bearbeitung benötigt. `IVsCfgProvider` ist ausreichend, wenn Sie diese Funktion nicht implementieren.

- Einige dieser Objekte, die im Diagramm als separate Objekte dargestellt werden, können in der gleichen Klasse kombiniert werden, die auf Grundlage ihrer spezifischen Entwurfs Anforderungen praktisch ist. In anderen Themen dieses Abschnitts werden jedoch die Objekte und Schnittstellen, die diesen Objekten zugeordnet sind, gemäß dem im Diagramm dargestellten Szenario erläutert.

- Bestimmte Objekte werden separat implementiert. Das Erstellen von Projekten und Projektmappen erfolgt beispielsweise in separaten Threads, und das Objekt zum Verwalten des Builds wird getrennt von dem Objekt, das die Konfiguration für den Build beschreibt.

  Weitere Informationen zu den Schnittstellen von Konfigurationsobjekten und Konfigurations Anbieter Objekten im vorherigen Diagramm finden Sie unter [Project Configuration Object](../../extensibility/internals/project-configuration-object.md). Außerdem bietet die [Projekt Konfiguration für die Erstellung](../../extensibility/internals/project-configuration-for-building.md) Weitere Informationen zum Konfigurations-Generator und zum Erstellen von Abhängigkeits Objekt-Schnittstellen, und die [Projekt Konfiguration zum Verwalten der Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md) beschreibt die Schnittstellen, die an den Konfigurations Bereitsteller und die Bereitstellungs Abhängigkeits Objekte angehängt sind Zum Schluss beschreibt die [Projekt Konfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md) die Schnittstellen der Ausgabe Gruppe und der Ausgabe Objekte sowie die Verwendung von Eigenschaften Seiten, um Konfigurations abhängige Eigenschaften anzuzeigen und festzulegen.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Projekt Konfiguration zum aufbauen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
