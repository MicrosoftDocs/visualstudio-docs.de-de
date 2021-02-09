---
title: Beitrag zum Automatisierungs Modell | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie zum Visual Studio-Automatisierungs Modell beitragen, indem Sie eine Reihe von Richtlinien befolgen, wenn Sie ein VSPackage entwerfen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ea8d477b377f78f5c836ec4661989cdbf8999c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884610"
---
# <a name="contribute-to-the-automation-model"></a>Zum Automatisierungs Modell beitragen
Visual Studio bietet eine Reihe von Automatisierungs Schnittstellen für die Anpassung der Umgebung. Das Automatisierungs Modell ist das Objektmodell, mit dem Endbenutzer Visual Studio-Add-Ins und-Erweiterungen erstellen können.

 Außerdem ist es für Sie als VSPackage-Entwickler geeignet, zum Automatisierungs Modell beizutragen. auf diese Weise ermöglichen Sie Endbenutzern des VSPackages das Erstellen von Add-Ins und bieten im Allgemeinen ein konsistentes Benutzer Modell, wenn Sie Ihr VSPackage in verwenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Um die Endbenutzer Leistung konsistent zu gestalten, können Sie beim Entwerfen des VSPackages eine Reihe von Richtlinien befolgen, damit das Automatisierungs Modell für Ihr VSPackage den Ideen in folgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>In diesem Abschnitt
- [Übersicht über das Automatisierungs Modell](../../extensibility/internals/automation-model-overview.md)

 Definiert das Automatisierungs Modell als Verwandte Gruppen von Objekten, die die wichtigsten Facetten der allgemeinen Umgebung steuern. Diese Gruppe von Objekten wird in einem Diagramm des Automatisierungs Modells dargestellt.

- [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Erläutert die zwei Hauptmethoden zum Bereitstellen von Automatisierung für Ihr VSPackage.

- [Verfügbar machen von Projekt Objekten](../../extensibility/internals/exposing-project-objects.md)

 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen von VSPackage-spezifischen Objekten.

- [Projekt Modellierung](../../extensibility/internals/project-modeling.md)

 Erläutert die Standard Projekt Objekte, die zum Erstellen der Automatisierung für den neuen Projekttyp erforderlich sind, und veranschaulicht den Pfad, dem die Projektautomatisierung folgt. Dieses Thema enthält auch Auflistungen von Deklarationen und Implementierungen für-Klassen.

- [Ereignisse verfügbar machen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen von Ereignissen für das Automatisierungs Modell.

- [Automatisierungsunterstützung für options Seiten](../../extensibility/internals/automation-support-for-options-pages.md)

 Beschreibt, wie ein Automatisierungs Objekt zurückgegeben wird, um Eigenschaften des Dialog Felds benutzerdefinierte **Optionen** für das VSPackage im **Tool** Menü durch Erweiterung des-Objekts zu unterstützen `DTE.Properties` .

- [Automatisierung für Code bereitstellen](../../extensibility/internals/providing-automation-for-code.md)

 Erläutert, dass das Erstellen eines Automatisierungs Modells für Ihren Code nicht erforderlich ist. In diesem Thema wird jedoch ein Link bereitgestellt, der aufschlussreiche Informationen zu Code Modellen bereitstellt.

- [Vorgehensweise: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Erläutert, dass das Bereitstellen von Automatisierung eine gute Idee ist, wenn Sie Automation-Objekte in einem Fenster verfügbar machen möchten und die Umgebung nicht bereits ein vorgefertigte Automatisierungs Objekt bereitstellt. Erläutert die Automatisierung für Tool Fenster und Dokument Fenster.

- [Verwenden des Automatisierungs Modells](../../extensibility/internals/using-the-automation-model.md)

 Bietet zwei Codebeispiele, die zeigen, wie ein automatisierungsconsumer die anfänglichen Project Automation-Objekte abruft.

- [Automatisierung für Konfigurations-und SelectedItem-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Enthält Informationen zur Automatisierung für Konfigurations-und SelectedItems-Objekte.

## <a name="reference"></a>Verweis
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Enthält ein Codebeispiel, das zeigt, wie ein VSPackage an dem DTE-Automatisierungs Objektmodell teilnimmt. Listet Parameter, Rückgabewerte und ausgewählte Hinweise auf.
