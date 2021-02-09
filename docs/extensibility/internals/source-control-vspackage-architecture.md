---
title: Architektur der Quellcodeverwaltungs-VSPackage | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Architektur eines Quell Code Verwaltungs Pakets, bei dem es sich um ein VSPackage handelt, das Visual Studio Funktionen als Quell Code Verwaltungsdienst bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e4de5f46746f79e1c7598e1c2a2a6af6ae1d92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912690"
---
# <a name="source-control-vspackage-architecture"></a>Architektur von Quellcodeverwaltungs-VSPackages
Ein Quell Code Verwaltungspaket ist ein VSPackage, das Dienste verwendet, die die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bereitstellt. In der Rückgabe stellt ein Quell Code Verwaltungspaket seine Funktionalität als Quell Code Verwaltungsdienst bereit. Außerdem ist ein Quell Code Verwaltungspaket eine vielseitiger Alternative als ein Quellcodeverwaltungs-Plug-in für die Integration der Quell Code Verwaltung in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Ein Quellcodeverwaltungs-Plug-in, das die Quellcodeverwaltungs-Plug-in-API implementiert, hält einen strengen Vertrag an. Beispielsweise kann ein Plug-in die Standard [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche (UI) nicht ersetzen. Außerdem ermöglicht die Plug-in-API für die Quell Code Verwaltung kein Plug-in, um ein eigenes Quell Code Verwaltungsmodell zu implementieren. Ein Quell Code Verwaltungspaket überschreitet jedoch beide Einschränkungen. Ein Quell Code Verwaltungspaket verfügt über die komplette Kontrolle über die Benutzeroberflächen Funktion eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzers. Außerdem kann ein Quell Code Verwaltungspaket ein eigenes Quell Code Verwaltungsmodell und eine eigene Logik verwenden und alle auf die Quell Code Verwaltung bezogenen Benutzeroberflächen definieren.

## <a name="source-control-package-components"></a>Paket Komponenten Source-Control
 Wie im Architektur Diagramm gezeigt, ist eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente mit dem Namen "Quellcodeverwaltungs-Stub" ein VSPackage, mit dem ein Quell Code Verwaltungspaket in integriert wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Der Quellcodeverwaltungs-Stub verarbeitet die folgenden Aufgaben.

- Stellt die allgemeine Benutzeroberfläche bereit, die für die Registrierung des Quell Code Verwaltungs Pakets erforderlich ist.

- Lädt ein Quell Code Verwaltungspaket.

- Legt ein Quell Code Verwaltungspaket als aktiv/inaktiv fest.

  Der Quellcodeverwaltungs-Stub sucht nach dem aktiven Dienst für das Quell Code Verwaltungspaket und leitet alle eingehenden Dienst Aufrufe aus der IDE an dieses Paket weiter.

  Das Quell Code Verwaltungs Adapter-Paket ist ein spezielles Quell Code Verwaltungspaket, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereitstellt. Dieses Paket ist die zentrale Komponente zum unterstützen von Quellcodeverwaltungs-Plug-ins basierend auf der Quellcodeverwaltungs-Plug-in-API. Wenn ein Quellcodeverwaltungs-Plug-in das aktive Plug-in ist, sendet der Quellcodeverwaltungs-Stub seine Ereignisse an das Quellcodeverwaltungs-Adapter Paket. Das Quellcodeverwaltungs-Adapter Paket kommuniziert wiederum mit dem Quellcodeverwaltungs-Plug-in mithilfe der Quellcodeverwaltungs-Plug-in-API und stellt außerdem eine Standardbenutzer Oberfläche bereit, die für alle Quellcodeverwaltungs-Plug-ins üblich ist.

  Wenn ein Quell Code Verwaltungspaket das aktive Paket ist, kommuniziert der Quellcodeverwaltungs-Stub auf der anderen Seite über die Source-Control Paket Schnittstellen direkt mit dem Paket [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Das Quell Code Verwaltungspaket ist für das Hosting der eigenen Quell Code Verwaltungs Benutzeroberfläche verantwortlich.

  ![Grafik zur Quellverwaltungsarchitektur](../../extensibility/internals/media/vsipsccarch.gif "Vsipsccarch")

  Für ein Quell Code Verwaltungspaket [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt keinen Quell Code Verwaltungs Code oder eine API für die Integration bereit. Vergleichen Sie dies mit dem unter [Erstellen eines Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/creating-a-source-control-plug-in.md) beschriebenen Verfahren, bei dem das Quellcodeverwaltungs-Plug-in eine starre Reihe von Funktionen und Rückrufen implementieren muss.

  Wie jedes VSPackage ist ein Quell Code Verwaltungspaket ein COM-Objekt, das mithilfe von erstellt werden kann `CoCreateInstance` . Das VSPackage ist für die IDE verfügbar, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] indem implementiert wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Wenn eine Instanz erstellt wurde, empfängt ein VSPackage einen Website Zeiger und eine <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle, die dem VSPackage Zugriff auf die verfügbaren Dienste und Schnittstellen in der IDE bereitstellt.

  Das Schreiben eines VSPackage-basierten Quell Code Verwaltungs Pakets erfordert erweiterte Programmierkenntnisse als das Schreiben eines API-basierten Plug-in für die Quellcodeverwaltungs-Plug-ins.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
