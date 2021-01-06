---
title: Verwandte Dienste und Schnittstellen (Quellcodeverwaltungs-VSPackage)
titleSuffix: ''
description: Erfahren Sie mehr über die Schnittstellen für die Quell Code Verwaltung VSPackage im Visual Studio SDK. Das Paket implementiert einige Schnittstellen und verwendet andere für die Quell Code Verwaltung.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af5c971b804e1c288bf710f6627c0e769e790ee1
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876342"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Verwandte Dienste und Schnittstellen (Quellcodeverwaltungs-VSPackage)

In diesem Abschnitt werden alle in der Quell Code Verwaltung enthaltenen VSPackage-Schnittstellen im aufgeführt [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Das VSPackage der Quell Code Verwaltung implementiert einige dieser Schnittstellen und verwendet andere zum Ausführen von Quell Code Verwaltungs Tasks.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Von und implementierte Schnittstellen für Quellcodeverwaltungs-VSPackages

 Die folgenden Schnittstellen werden in beschrieben [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , und das Quellcodeverwaltungs-VSPackage implementiert abhängig von der gewünschten featuremenge eine Teilmenge davon. Einige Schnittstellen werden als erforderlich gekennzeichnet und müssen von jedem Quell Code Verwaltungs-VSPackage implementiert werden.

 Für die Schnittstellen, die ein Paket nicht implementiert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt eine Standard Implementierung bereit. Beachten Sie, dass die Standard Implementierung für den Fall konzipiert ist, dass kein VSPackage registriert und kein Projekt gesteuert wird. Ein ordnungsgemäß geschriebenes VSPackage für die Quell Code Verwaltung implementiert alle notwendigen Schnittstellen, anstatt Sie der Standard Implementierung dieser Schnittstellen zu überschreiten.

 Ein Quellcodeverwaltungs-VSPackage muss einen privaten Dienst implementieren, der einige oder alle der folgenden Schnittstellen kapselt.

 Schnittstellen:

- Erforderlich: die entsprechende Entität (Quellcodeverwaltungs-VSPackage, Quellcodeverwaltungs-Stub, Projekt) muss die-Schnittstelle implementieren.

- Empfohlen: die Entität muss diese Schnittstelle implementieren. Andernfalls ist die Funktionalität der Quell Code Verwaltung möglicherweise eingeschränkt.

- Optional: die Entität kann diese Schnittstelle implementieren, um eine umfangreichere Funktionsgruppe bereitzustellen.

| Schnittstelle | Zweck | Implementiert von | Umsetzt? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Editoren bezeichnen diese Schnittstelle vor dem ändern oder Speichern einer Datei. Das VSPackage der Quell Code Verwaltung kann die Datei Auschecken oder den Vorgang ablehnen, wenn das Auschecken fehlschlägt. | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Diese Schnittstelle stellt grundlegende Funktionen der Quell Code Verwaltung für Projekte bereit, z. b. das registrieren und Aufheben der Registrierung von Projekten mit der Quell Code Verwaltung und das Bereitstellen von Unterstützung für | Quellcodeverwaltungs-VSPackage | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Diese Schnittstelle wird von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mithilfe der- <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> Funktion abgerufen, oder durch Umwandeln des Objekts, das in implementiert wird `IVsHierarchy` `IVsSccProject2` . Sie wird verwendet, um die Dateien in einem Projekt unter Quell Code Verwaltung zu übermitteln oder um das Projekt über den aktuellen Status oder Speicherort der Quell Code Verwaltung zu informieren. | Project | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Das Integrationsmodul verwendet diese Schnittstelle zum Festlegen des aktuellen aktiven VSPackages. | Quellcodeverwaltungs-VSPackage | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Diese Schnittstelle basiert auf einem Abonnement Modell. Jedes VSPackage kann signalisieren, dass es Dokument Ereignisse empfangen und von der Shell auf Ereignisse hingewiesen werden soll, die in der Regel auftreten. Es wird von implementiert und behandelt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , das wiederum Ereignisse übergibt, die den in `IVsTrackProjectDocumentsEvents2` das VSPackage implementieren. | Quellcodeverwaltungs-Stub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Diese Schnittstelle bietet Batch Verarbeitung, synchronisierte Lese-/Schreibvorgänge und eine erweiterte `OnQueryAddFiles` Methode. | Quellcodeverwaltungs-Stub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Projektmappen-Explorer** -und-Projekte wird diese Schnittstelle aufgerufen, wenn den Projekten neue Dateien hinzugefügt werden oder wenn Dateien und Ordner aus Projekten umbenannt oder gelöscht werden. Das VSPackage der Quell Code Verwaltung kann die Projektdatei Auschecken oder den Vorgang abbrechen. | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Projektmappen-Explorer** -und-Projekte rufen diese Schnittstelle als Reaktion auf Aufrufe der-Methoden der IVstrackProjectDocuments3-Schnittstelle auf. Mit dem Quellcodeverwaltungs-VSPackage können Batch Vorgänge nachverfolgt, synchronisierte Lese-/Schreibvorgänge ausgeführt und eine erweiterte Methode verwendet werden `OnQueryAddFiles` . | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Diese Schnittstelle bietet die Unterstützung der Registrierungs Verwaltung für Webprojekte. | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Diese Schnittstelle wird verwendet, um Quick Infos für die Dateien der Quell Code Verwaltung in den Projekten abzurufen. | Quellcodeverwaltungs-VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Diese Schnittstelle bietet Unterstützung für Namespace Erweiterungen. | Quellcodeverwaltungs-VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Das VSPackage verwendet diese Schnittstelle, um eine Namespace Erweiterung in die Dialogfelder " **neu**", " **Öffnen**" oder " **Speichern** " zu integrieren. Folglich können Projekte bei der Erstellung automatisch zur Quell Code Verwaltung hinzugefügt oder der Quell Code Verwaltung hinzugefügt werden, wenn ein Speichervorgang wirksam ist. | Quellcodeverwaltungs-VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Das VSPackage verwendet diese Schnittstelle, um zusätzliche Glyphen als Symbole der Quell Code Verwaltung für Knoten in **Projektmappen-Explorer** zu definieren. | Quellcodeverwaltungs-VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Im Dialogfeld **Hinzufügen** für Webprojekte wird diese Schnittstelle verwendet. Es bietet Methoden zum Durchsuchen eines Quell Code Verwaltungs Speicher Orts und zum Öffnen eines Webprojekts, das zuvor im Quellcodeverwaltungs-Repository an diesem Speicherort hinzugefügt wurde. | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Diese Schnittstelle bietet Unterstützung für das asynchrone Laden von Projekten aus der Quell Code Verwaltung. | Quellcodeverwaltungs-VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Diese Schnittstelle ermöglicht es Projekten, den Fortschritt des asynchronen Ladens zu beobachten, das von initiiert wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Diese Schnittstelle ermöglicht der IDE das Abfragen des VSPackage für die aktive Quell Code Verwaltung. Die IDE fragt den Wert der Quell Code Verwaltungs Einstellungen ab, die Bedeutung haben, auch wenn kein aktives VSPackage für die Quell Code Verwaltung registriert ist. Diese Schnittstelle wird von implementiert und behandelt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Quellcodeverwaltungs-Stub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Diese Schnittstelle wird verwendet, um das VSPackage der Quell Code Verwaltung zu registrieren. | Quellcodeverwaltungs-Stub | Erforderlich |
| <xref:EnvDTE.SourceControl> | Diese Schnittstelle wird bei der Automatisierung verwendet. Daher werden nur Funktionen verfügbar gemacht, die ohne Anzeige einer Benutzeroberfläche ausgeführt werden können. | Quellcodeverwaltungs-VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Diese Schnittstelle wird verwendet, um die Quell Code Verwaltungs Einstellungen in der Projektmappendatei (. sln) zu speichern. Die Einstellungen umfassen den Speicherort der Quell Code Verwaltung und Quellcodeverwaltungs-Statusflags. | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Diese Schnittstelle wird verwendet, um die Quell Code Verwaltungs Einstellungen in der Projektmappenoptionen (. suo) zu speichern. Dies kann benutzerspezifische Einstellungen der Quell Code Verwaltung umfassen, z. b. den Anmelde Speicherort des aktuellen Benutzers. | Quellcodeverwaltungs-VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Diese Schnittstelle wird verwendet, um Ereignisse zu überwachen, um Vorgänge wie das Einchecken von Projektdateien vor dem Schließen von Projektmappen oder das erhalten von neuen Dateien aus der Quell Code Verwaltung beim Öffnen eines Projekts auszuführen. | Quellcodeverwaltungs-VSPackage | Empfohlen |

## <a name="see-also"></a>Weitere Informationen
- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
