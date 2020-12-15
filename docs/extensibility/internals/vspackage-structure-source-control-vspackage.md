---
title: VSPackage-Struktur (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das SDK für das Quell Code Verwaltungspaket, das Richtlinien für ein VSPackage mit einem Quellcodeverwaltungs-Implementierer für die Integration in Visual Studio enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5850dfb2448364124c8f1778eac48ac9c653269
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487958"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage-Struktur (Quellcodeverwaltungs-VSPackage)

Das Quell Code Verwaltungspaket-SDK enthält Richtlinien für das Erstellen eines VSPackages, das es einem Quellcodeverwaltungs-Implementierer ermöglicht, seine Funktionen der Quell Code Verwaltung in die Visual Studio-Umgebung zu integrieren. Ein VSPackage ist eine COM-Komponente, die in der Regel von der integrierten Entwicklungsumgebung (IDE) von Visual Studio nach Bedarf geladen wird, basierend auf den Diensten, die vom Paket in den zugehörigen Registrierungs Einträgen angekündigt werden. Jedes VSPackage muss implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Ein VSPackage nutzt normalerweise Dienste, die von der Visual Studio-IDE angeboten werden, und stellt einige Dienste bereit.

Ein VSPackage deklariert seine Menü Elemente und legt einen Standardelement Zustand über die vsct-Datei fest. Die Visual Studio-IDE zeigt die Menü Elemente in diesem Zustand an, bis das VSPackage geladen wurde. Anschließend wird die VSPackage-Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aufgerufen, um Menü Elemente zu aktivieren oder zu deaktivieren.

## <a name="source-control-package-characteristics"></a>Merkmale der Quell Code Verwaltungs Pakete

Ein VSPackage für die Quell Code Verwaltung ist tief in Visual Studio integriert. Die VSPackage-Semantik umfasst Folgendes:

- Schnittstelle, die durch das VSPackage implementiert werden soll (die- `IVsPackage` Schnittstelle)

- Implementierung von UI-Befehlen (vsct-Datei und Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle)

- Die Registrierung des VSPackage bei Visual Studio.

Das VSPackage der Quell Code Verwaltung muss mit diesen anderen Visual Studio-Entitäten kommunizieren:

- Projekte

- Editoren

- Lösungen

- Windows

- Die laufende Dokument Tabelle

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Möglicherweise genutzte Visual Studio-Umgebungs Dienste

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Svsregisterscciprovider-Dienst

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Implementierte und aufgerufene VSIP-Schnittstellen

Ein Quell Code Verwaltungspaket ist ein VSPackage und kann daher direkt mit anderen VSPackages interagieren, die in Visual Studio registriert sind. Um die vollständige Palette der Funktionen der Quell Code Verwaltung bereitzustellen, kann ein Quellcodeverwaltungs-VSPackage mit Schnittstellen arbeiten, die von Projekten oder der Shell bereitgestellt werden.

Jedes Projekt in Visual Studio muss implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> , um als Projekt in der Visual Studio-IDE erkannt zu werden. Diese Schnittstelle ist jedoch nicht für die Quell Code Verwaltung spezialisiert. Projekte, die unter Quell Code Verwaltung erwartet werden, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Diese Schnittstelle wird von der Quellcodeverwaltungs-VSPackage verwendet, um ein Projekt nach seinem Inhalt abzufragen und um ihm Symbole und Bindungs Informationen (die Informationen, die zum Herstellen einer Verbindung zwischen dem Serverstandort und dem Speicherort eines Projekts, das der Quell Code Verwaltung unterliegt) bereitzustellen.

Das VSPackage der Quell Code Verwaltung implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , das wiederum es Projekten ermöglicht, sich selbst für die Quell Code Verwaltung zu registrieren und deren Statussymbole abzurufen.

Eine vollständige Liste der Schnittstellen, die von einem Quellcodeverwaltungs-VSPackage berücksichtigt werden müssen, finden Sie unter [verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Weitere Informationen

- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
