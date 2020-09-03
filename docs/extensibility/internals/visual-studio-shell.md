---
title: Visual Studio Shell | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704001"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ist der primäre Agent der Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die Shell stellt die erforderliche Funktionalität bereit, damit VSPackages gemeinsame Dienste gemeinsam verwenden können. Da das architektonische Ziel von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] darin besteht, die primäre Funktionalität in den VSPackages zu schützen, ist die Shell ein Framework, um grundlegende Funktionen bereitzustellen und die Kommunikation zwischen den Komponenten-VSPackages zu unterstützen.

## <a name="shell-responsibilities"></a>Shellzuständigkeiten
 Die Shell besteht aus den folgenden Hauptaufgaben:

- Unterstützende (über COM-Schnittstellen) grundlegende Elemente der Benutzeroberfläche (UI). Hierzu gehören Standardmenüs und Symbolleisten, Dokument Fensterrahmen oder untergeordnete MDI-Fenster (multidocument Interface) sowie Tool Fensterrahmen und Andock Unterstützung.

- Verwalten einer Liste aller gegenwärtig geöffneten Dokumente in einer laufenden dokumententabelle (RDT), um die Persistenz von Dokumenten zu koordinieren und sicherzustellen, dass ein Dokument nicht auf mehr als eine Weise geöffnet werden kann, oder auf nicht kompatible Weise.

- Unterstützung der Befehls-und Befehls Bearbeitungs Schnittstelle, `IOleCommandTarget` .

- VSPackages werden zu den richtigen Zeitpunkten geladen. Das verzögerte Laden eines VSPackages ist erforderlich, um die Leistung der Shell zu verbessern.

- Verwaltung bestimmter gemeinsamer Dienste wie z. b. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , das grundlegende Shellfunktionen bereitstellt, und <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , das grundlegende Fenster Funktionen bereitstellt.

- Verwalten der Projektmappendateien (. sln). Lösungen enthalten Gruppen verwandter Projekte, ähnlich wie Arbeitsbereichs Dateien (. DSW) in Visual C++ 6,0.

- Nachverfolgen der shellweiten Auswahl, des Kontexts und der Währung. Die Shell verfolgt die folgenden Elementtypen:

  - Das aktuelle Projekt

  - Das aktuelle Projekt Element oder die aktuelle Element-Itemid. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Die aktuelle Auswahl für das **Eigenschaften** Fenster oder `SelectionContainer`

  - Die UI-Kontext-IDs oder cmduiguids, die die Sichtbarkeit von Befehlen, Menüs und Symbolleisten steuern

  - Die derzeit aktiven Elemente, z. b. aktives Fenster, Dokument und rückgängig-Manager

  - Die Benutzer Kontext Attribute, die dynamische Hilfe Steuern

  Die Shell vermittelt auch die Kommunikation zwischen installierten VSPackages und aktuellen Diensten. Es unterstützt die Kernfunktionen der Shell und macht Sie für alle in integrierten VSPackages verfügbar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Zu diesen Kern Features zählen die folgenden Elemente:

- Info **-Dialogfeld** und Begrüßungsbildschirm

- **Neue Dialogfelder hinzufügen und vorhandenes Element hinzufügen**

- **Klassenansicht** Fenster und **Objektkatalog**

- **Verweise** (Dialogfeld)

- **Dokument** Gliederungs Fenster

- Fenster " **Dynamische Hilfe** "

- **Suchen** und **ersetzen**

- Dialogfelder " **Projekt öffnen** " und " **Datei öffnen** " im Menü " **neu** "

- Dialogfeld " **Optionen** " **im Menü "** Extras"

- **Eigenschaften** Fenster

- **Projektmappen-Explorer**

- **Aufgabenliste** Fenster

- **Werkzeugkasten**

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
