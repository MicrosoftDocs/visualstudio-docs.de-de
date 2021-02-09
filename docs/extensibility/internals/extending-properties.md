---
title: Erweitern von Eigenschaften | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Schnittstellen, die Sie implementieren müssen, und um aufzurufen, um die Liste der Eigenschaften in Visual Studio Eigenschaftenfenster zu erweitern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a777bf11f388873978f450184f1455236e9ff9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887080"
---
# <a name="extend-properties"></a>Erweitern von Eigenschaften
Das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster ist ein universeller Eigenschaften Browser für com-und COM+-Komponenten und unterstützt alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Produkte. Das **Eigenschaften** Fenster funktioniert mit `ITypeInfo` Typinformationen und com+-Metadaten, um die Entwurfszeit Eigenschaften für das aktuell ausgewählte Objekt in einem beliebigen anderen Fenster in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) aufzulisten.

 Das **Eigenschaften** Fenster, das durch Drücken von **F4** auf der Tastatur oder durch Auswahl von **Eigenschaften Fenster** im Menü **Ansicht** geöffnet werden kann, wird zum Anzeigen und Bearbeiten von Konfigurations unabhängigen Entwurfszeit Eigenschaften und-Ereignissen ausgewählter Objekte verwendet. Konfigurations abhängige Eigenschaften, die Projektmappen und Projekten zugeordnet sind, werden auf den Eigenschaften [Seiten](../../extensibility/internals/property-pages.md)angezeigt. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

 ![Übersicht über Eigenschaftenfenster](../../extensibility/internals/media/vspropertieswindow.png "vspropertieswindow") Eigenschaftenfenster

 Dieser Abschnitt enthält ausführliche Informationen zu den einzelnen Bereichen des Fensters **Eigenschaften** und zu den Schnittstellen, die Sie implementieren müssen, und zum Auffüllen des Fensters aufzurufen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Übersicht über Eigenschaftenfenster](../../extensibility/internals/properties-window-overview.md)

 Erläutert den Zweck des **Eigenschaften** Fensters in Relation zum Tool Fenster und Dokument Fenster.

- [Vorlagen Richtlinie und die Eigenschaftenfenster](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Erläutert, wie ein Projekt in einem Enterprise-Vorlagen Projekt enthalten ist und wie dieses Enterprise-Vorlagen Projekt Richtlinien erzwingen kann.

- [Eigenschaftenfenster Felder und Schnittstellen](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Erläutert die Grundlage für die Auswahl, die bestimmt, welche Informationen im **Eigenschaften** Fenster angezeigt werden.

- [Eigenschaftenfenster Objektliste](../../extensibility/internals/properties-window-object-list.md)

 Beschreibt den Zweck der Objektliste **Eigenschaften** Fenster, in dem beschrieben wird, dass die Umgebung, wenn ein anderes Objekt aus dieser Liste einen-Befehl auslöst, informiert wird, dass ein neues-Objekt ausgewählt wurde.

- [Eigenschaftenfenster Schaltflächen](../../extensibility/internals/properties-window-buttons.md)

 Erläutert den Zweck der vier Standard Schaltflächen, die auf der Symbolleiste des **Eigenschaften** Fensters angezeigt werden.

- [Eigenschaften Anzeige Raster](../../extensibility/internals/properties-display-grid.md)

 Erläutert, wo sich die Felder Eigenschaften Namen und Eigenschaftswerte im Raster befinden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Erläutert Projekte als Bausteine der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)

 Beschreibt, wie Sie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Plattform zum fortlaufenden testen und Debuggen von Anwendungen verwenden können, während Sie Sie erstellen.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Beschreibt die- `IDispatch` Schnittstelle, die zuerst zur Unterstützung von Automation entwickelt wurde und einen spät gebundenen Mechanismus zum Zugreifen auf und Abrufen von Informationen über die Methoden und Eigenschaften eines Objekts bereitstellt.

- [Verwalten von Anwendungseinstellungen (.NET)](../../ide/managing-application-settings-dotnet.md)

 Bietet einen Überblick über die Anwendungseinstellungen, mit denen Sie Ihre Anwendung so konfigurieren können, dass Eigenschaftswerte in einer externen Konfigurationsdatei gespeichert werden, anstatt im kompilierten Code der Anwendung.

- [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)

 Erläutert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die effiziente Verwaltung der Elemente, wie z. b. Verweise, Datenverbindungen, Ordner und Dateien, die für den Entwicklungsaufwand durch Projektmappen und Projekte erforderlich sind.

- [Erweitern anderer Teile von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Komponenten passen.
