---
title: Interaktionsmuster für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Bibliothek mit allgemeinen Interaktionsmustern, die Sie beim Entwickeln neuer Features für Visual Studio verwenden können.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cd618b66eed900c2436704d40de5325c1205e85
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863488"
---
# <a name="interaction-patterns-for-visual-studio"></a>Interaktionsmuster für Visual Studio
## <a name="overview"></a>Übersicht
 Ein Entwurfsmuster ist im Allgemeinen der Kern eines Entwurfs, der in bestimmten Situationen angewendet werden kann, um Probleme mit ähnlichen Sätzen von Einschränkungen zu lösen. Funktions-und System-Designer verwenden diese Entwurfsmuster als Ausgangspunkte, die dann an ihre jeweilige Situation angepasst werden können.

 Visual Studio verfügt über eine Bibliothek mit allgemeinen Interaktionsmustern, die beim Aufbau neuer Features berücksichtigt werden sollten. Es gibt zwei Kern Kontexte für unsere Entwurfsmuster: Visual Studio-Client (devenv) und GitHub-codespaces (früher Visual Studio Online). Für einige Entwurfs Probleme gibt es ein allgegenwärtiges Muster, das in allen Situationen gut funktioniert. In vielen Fällen kann die Lösung jedoch für die Benutzeroberfläche, die in einem Browser angezeigt wird und die in einer Client Anwendung gehostet wird, unterschiedlich sein.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio-Client Mustertypen

|Mustertyp|BESCHREIBUNG|Beispiele|
|------------------|-----------------|--------------|
|**Muster auf Anwendungsebene**|Allgemeine Muster für die Anwendung, bestimmen oder Anzeigen des Anwendungs Kontexts sowie zusammengesetzte und Steuerelement Muster darin|-Tool Fenster<br />-Dokument Fenster|
|**Zusammengesetzte Muster**|Allgemeine Muster, die sich über Anwendungs Muster erstrecken können, oder ein bekanntes Muster, das aus mehreren Steuerelementen in einer unterschiedlichen Konfiguration besteht|-Ansicht wechseln<br />-List Builder<br />-Anzeigen von Daten<br />-Benachrichtigungen<br />-Validierung<br />-Auswahl Modelle|
|**Steuerelement Muster**|Besonderheiten bei der Erwartungs gemäße Verhalten von Steuerelementen auf niedriger Ebene|-Struktur Ansichten<br />-Bearbeiten in einem Raster Steuerelement|

## <a name="application-patterns"></a>Anwendungsmuster
 Auf hoher Ebene besteht die Visual Studio-Schnittstelle aus mehreren Fenstern, Dialogfeldern, Befehlen und Symbolleisten innerhalb einer einzelnen IDE. Die Visual Studio-Hierarchie legt Kontext-und Laufwerks Menüs fest. Die wichtigsten Integrationspunkte in der Benutzeroberfläche der IDE sind Dokument Fenster, Tool Fenster, Projekte, Befehlsstruktur, Text-Editor, Toolbox, Eigenschaftenfenster und Tools > Optionen.

 Es gibt grundlegende Verwendungs Muster für jeden der wichtigsten Integrationspunkte in der Benutzeroberfläche der IDE:

- [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Anwendungsmuster für Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Fenster Interaktionen](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Tool Fenster](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konventionen für Dokument-Editor](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekte](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Allgemeine Steuerelement Muster
 Steuerelement Muster sind hauptsächlich die Art und Weise, wie sich die einzelnen Steuerelemente Verhalten. Dies ist ein Bereich, in dem die Konsistenz am kritischsten ist.

 Die meisten allgemeinen Steuerelemente in Visual Studio sollten den Windows-Richtlinien für den Desktop entsprechen. Unsere Richtlinien umfassen nur Bereiche, in denen wir allgemeine Konventionen mit Visual Studio-spezifischen Interaktionen erweitern müssen, oder stellen, an denen wir die Richtlinien vollständig ersetzen, um Visual Studio so anzupassen, dass die Anforderungen unserer ausgereiften Benutzer erfüllt werden.

- [Allgemeine Steuerelementmuster für Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Allgemeine Steuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Textsteuerelemente](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Schaltflächen und Hyperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Zusammengesetzte Muster
 Es gibt eine Reihe von Methoden, die Benutzer für die Ausführung von Aufgaben erwarten. Wenn möglich, sollten Features so entworfen werden, dass diese Muster sowohl für die Interaktion als auch für den visuellen Entwurf verwendet werden.

 Obwohl in Visual Studio viele zusammengesetzte Muster vorhanden sind, sind einige der wichtigsten in Bezug auf die Konsistenz:

- [Zusammengesetzte Muster für Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [On-Object-Benutzeroberfläche und Peer](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Auswahl Modelle](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistenz und Speichern von Einstellungen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Fingereingabe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
