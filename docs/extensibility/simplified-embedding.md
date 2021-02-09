---
title: Vereinfachte Einbettung | Microsoft-Dokumentation
description: Erfahren Sie mehr über das vereinfachte einbetten, das in einem Editor aktiviert werden kann, wenn sein Dokument Ansichts Objekt ein untergeordnetes Element von Visual Studio ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f62e3a4f33193f36e76b1286ae3d35d26706b3ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928093"
---
# <a name="simplified-embedding"></a>Vereinfachtes Einbetten
Vereinfachte Einbettungen werden in einem Editor aktiviert, wenn das Dokument Ansichts Objekt (d. h. ein untergeordnetes Element von) übergeordnet ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle wird implementiert, um Ihre Fenster Befehle zu verarbeiten. Vereinfachte Einbettungs Editoren können keine aktiven Steuerelemente hosten Die Objekte, die zum Erstellen eines Editors mit vereinfachter Einbettung verwendet werden, sind in der folgenden Abbildung dargestellt.

 ![Vereinfachte Einbettungs-Editor-Grafik](../extensibility/media/vssimplifiedembeddingeditor.gif "vssimplifiedembeddingeditor") Editor mit vereinfachter Einbettung

> [!NOTE]
> Von den Objekten in dieser Abbildung ist nur das- `CYourEditorFactory` Objekt zum Erstellen eines standardmäßigen dateibasierten Editors erforderlich. Wenn Sie einen benutzerdefinierten Editor erstellen, müssen Sie nicht implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , da Ihr Editor wahrscheinlich über einen eigenen Mechanismus für die private Persistenz verfügt. Für Nichtbenutzer definierte Editoren müssen Sie dies jedoch tun.

 Alle Schnittstellen, die zum Erstellen eines Editors mit vereinfachter Einbettung implementiert werden, sind im- `CYourEditorDocument` Objekt enthalten. Wenn Sie jedoch mehrere Sichten von Dokument Daten unterstützen möchten, teilen Sie die Schnittstellen auf separate Daten und Objekte anzeigen, wie in der folgenden Tabelle aufgeführt.

|Schnittstelle|Speicherort der Schnittstelle|Zweck|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Sicht|Stellt eine Verbindung mit dem übergeordneten Fenster bereit.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sicht|Behandelt Befehle.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Sicht|Ermöglicht Aktualisierungen der Statusleiste.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Sicht|Aktiviert **Toolbox** Elemente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Daten|Sendet Benachrichtigungen, wenn die Datei geändert wird.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Daten|Aktiviert das Feature "Speichern unter" für einen Dateityp.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Daten|Aktiviert die Persistenz für das Dokument.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Daten|Ermöglicht die Unterdrückung von Datei Änderungs Ereignissen, z. b. das Auslösen von Neuladen.|
