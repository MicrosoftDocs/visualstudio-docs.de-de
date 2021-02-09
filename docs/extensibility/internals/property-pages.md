---
title: Eigenschaften Seiten | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Arbeiten mit Eigenschaften Seiten für den neuen Projekttyp im Visual Studio SDK, mit dem Benutzer Projekteigenschaften anzeigen und ändern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd7d1ce463377daa2800d5c3e635adc71935d9d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883167"
---
# <a name="property-pages"></a>Eigenschaftenseiten
Mithilfe von Eigenschaften Seiten können Benutzer von der Projekt Konfiguration abhängige und unabhängige Eigenschaften anzeigen und ändern. Eine Schaltfläche für Eigenschaften **Seiten** ist im **Eigenschaften** Fenster oder auf Projektmappen-Explorer Symbolleiste für Objekte aktiviert, die eine Eigenschaften Seitenansicht des ausgewählten Objekts bereitstellen. Eigenschaften Seiten werden von der Umgebung erstellt und stehen für Projektmappen und Projekte zur Verfügung. Sie können jedoch auch für Projekt Elemente verfügbar gemacht werden, die Konfigurations abhängige Eigenschaften verwenden. Diese Funktion kann verwendet werden, wenn Dateien in einem Projekt unterschiedliche compilerswitcheinstellungen zum ordnungsgemäßen erstellen benötigen.

## <a name="using-property-pages"></a>Verwenden von Eigenschaften Seiten
 Wenn eine Eigenschaften Seite bereits angezeigt wird und sich die Auswahl ändert (z. b. von einer Projekt Mappe zu einem Projekt), werden die in den Seiten angezeigten Informationen geändert, um die Eigenschaften für die neue Auswahl anzuzeigen. Wenn keine Eigenschaften für das Objekt vorhanden sind, die Eigenschaften Seiten unterstützen, ist die Eigenschaften Seite leer.

 Wenn mehrere Objekte ausgewählt sind, wird auf der Eigenschaften Seite die Schnittmenge der Eigenschaften für alle ausgewählten Elemente angezeigt. Wenn das ausgewählte Element keine Konfigurations abhängigen Eigenschaften enthält und auf die Schaltfläche **Eigenschaften Seiten** auf der Projektmappen-Explorer Symbolleiste geklickt wird, konzentrieren Sie sich auf die Änderungen auf die Eigenschaftenfenster. Weitere Informationen zum Eigenschaftenfenster und zur Auswahl finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).

 Wenn Eigenschaften für mehrere Objekte angezeigt werden und Sie einen Wert auf einer Eigenschaften Seite ändern, werden alle Werte für die Objekte auf den neuen Wert festgelegt, auch wenn Sie anfänglich anders waren und die Seite leer war, als die Eigenschaften eines einzelnen Objekts angezeigt wurden.

 Es gibt zwei allgemeine Typen von Dialogfeldern für **ProjectProperty-Seiten** , die in verfügbar sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Im ersten werden z. b. für Visual Basic Projekte die Eigenschaften Seiten in einem Feld Format angezeigt, wie im folgenden Screenshot gezeigt. In der zweiten, weiter unten in diesem Abschnitt gezeigten, hostet die Eigenschaften Seite ein Eigenschaften Raster ähnlich dem, das im Eigenschaften Fenster von gefunden wurde.

 ![Eigenschaften Seiten Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsvbproppages") Projekteigenschaften Seiten (Dialogfeld) mit Feld Format und Baumstruktur

 Die Struktur im Dialogfeld Eigenschaften Seiten wird nicht mithilfe von erstellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Die Umgebung wird auf der Grundlage des von der <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> -Schnittstelle und der-Schnittstelle an Sie weiter gegebenen levelnamens <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> erstellt.

 Auf den Eigenschaften Seiten sind nur zwei Kategorien der obersten Ebene verfügbar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

- Allgemeine Eigenschaften, in denen Konfigurations unabhängige Informationen für die ausgewählten Objekte angezeigt werden. Wenn eine der allgemeinen Eigenschaften Unterkategorien ausgewählt ist, sind die Optionen Konfiguration, Plattform und Configuration Manager am oberen Rand des Dialog Felds nicht verfügbar.

- Konfigurations Eigenschaften, die Konfigurations abhängige Informationen im Zusammenhang mit Debuggen, Optimierung und buildparametern für die Projekt Mappe oder das Projekt enthalten.

  Sie können keine zusätzlichen Kategorien der obersten Ebene erstellen, aber Sie können wählen, ob Sie in ihrer Implementierung von eine oder die andere anzeigen möchten `IVsPropertyPage` . Wenn Sie z. b. keine Konfigurations unabhängigen Eigenschaften haben, die für ein Objekt angezeigt werden sollen, können Sie auswählen, dass die Kategorie Allgemeine Eigenschaften nicht angezeigt werden soll. Wenn `ISpecifyPropertyPages` Sie `ISpecifyPropertyPages` im Konfigurationsobjekt implementieren (das Objekt `IVsCfg` , das, und verknüpfte Schnittstellen implementiert), werden allgemeine Eigenschaften angezeigt, wenn aus dem Browse-Objekt und den Konfigurations Eigenschaften des Elements implementiert wird `IVsProjectCfg` .

  Jede Kategorie, die unter einer Kategorie der obersten Ebene angezeigt wird, stellt eine separate Eigenschaften Seite dar. Kategorie-und unterkategorieeinträge, die im Dialogfeld verfügbar sind, werden durch ihre Implementierung von `ISpecifyPropertyPages` und bestimmt `IVsPropertyPage` .

  `IDispatch` Objekte für Elemente im Auswahl Container, die auf Eigenschaften Seiten anzuzeigende Eigenschaften aufweisen, `ISpecifyPropertyPages` um eine Liste der Klassen-IDs aufzuzählen. Die Klassen-IDs werden als Variablen an `ISpecifyPropertyPages` und verwendet, um die Eigenschaften Seiten zu instanziieren. Die Liste der Klassen-IDs wird auch an weitergegeben `IVsPropertyPage` , um die Struktur auf der linken Seite des Dialog Felds zu erstellen. Die Eigenschaften Seiten übergeben dann Informationen an das `IDispatch` Objekt, das implementiert, `ISpecifyPropertyPages` und füllen die Informationen für jede Seite aus.

  Die Eigenschaften des Browse-Objekts werden mithilfe von `IDispatch` für jedes Objekt im Auswahl Container abgerufen.

  Die Implementierung `Help::DisplayTopicFromF1Keyword` von in Ihrem VSPackage stellt die Funktionalität für die Schaltfläche Hilfe bereit.

  Weitere Informationen finden Sie unter `IDispatch` und `ISpecifyPropertyPages` in der MSDN Library.

  Der zweite Typ von Eigenschaften Seiten, die in den Beispielen angezeigt werden, hostet ein Formular des Eigenschaften Rasters, wie im folgenden Screenshot gezeigt.

  ![VC-Eigenschaften Seiten](../../extensibility/internals/media/vsvcproppages.gif "vsvcproppages") Eigenschaften Seiten (Dialogfeld) mit Eigenschaften Raster

  Die-Schnittstellen `IVSMDPropertyBrowser` und `IVSMDPropertyGrid` (deklariert in vsmanaged. h) werden verwendet, um das Eigenschaften Raster in einem Dialogfeld oder Fenster zu erstellen und aufzufüllen.

  Die Architektur der Projekte hat sich stark von früheren Versionen von geändert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Insbesondere hat sich das Konzept geändert, in dem sich das Projekt befindet. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibt es kein Konzept für ein aktives Projekt. In früheren Entwicklungsumgebungen war das aktive Projekt das Projekt, für das Build-und Bereitstellungs Befehle unabhängig vom Kontext standardmäßig auf festgestellt wurden. Nun steuert und bestimmt die Lösung, welche Build-und Bereitstellungs Befehle auf welche Projekte angewendet werden.

  Was zuvor ein aktives Projekt war, wird nun auf eine von drei unterschiedlichen Arten aufgezeichnet:

- Das Startprojekt

   Sie können ein Projekt oder Projekte auf der Eigenschaften Seite der Projekt Mappe angeben, die gestartet wird, wenn der Benutzer F5 drückt oder im Menü Build die Option Ausführen auswählt. Dies funktioniert ähnlich wie das alte aktive Projekt in dem Sinne, dass sein Name in Projektmappen-Explorer mit fett formatierter Schriftart angezeigt wird.

   Sie können das Startprojekt als Eigenschaft im Automatisierungs Modell abrufen, indem Sie aufrufen `DTE.Solution.SolutionBuild.StartupProjects` . In einem VSPackage werden die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> Methode oder die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> Methode aufgerufen. `IVsSolutionBuildManager` ist auf SID_SVsSolutionBuildManager als Dienst verfügbar `QueryService` . Weitere Informationen finden Sie unter [Projekt Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md) und Projektmappenkonfiguration. [](../../extensibility/internals/solution-configuration.md)

- Konfiguration des aktiven Projektmappenbuilds

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügt über eine aktive Projektmappenkonfiguration, die im Automatisierungs Modell durch Implementieren von verfügbar ist `DTE.Solution.SolutionBuild.ActiveConfiguration` . Eine Projektmappenkonfiguration ist eine Sammlung, die eine Projekt Konfiguration für jedes Projekt in der Projekt Mappe enthält (jedes Projekt kann über mehrere Konfigurationen auf mehreren Plattformen mit unterschiedlichen Namen verfügen). Weitere Informationen zu den Eigenschaften Seiten der Projekt Mappe finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).

- Aktuell ausgewähltes Projekt

   Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> Sie die-Methode, um die Projekt Hierarchie und das ausgewählte Projekt Element abzurufen. Aus DTE verwenden Sie die `SelectedItems.SelectedItem.Project` -Methode und die- `SelectedItems.SelectedItem.ProjectItem` Methode. Es gibt Beispielcode unter diesen Überschriften in den Kern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dokumenten.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
