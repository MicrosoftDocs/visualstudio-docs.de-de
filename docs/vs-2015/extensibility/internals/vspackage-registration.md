---
title: VSPackage-Registrierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a11f05edb4e7d476fdbcab82d365f9327dd4869a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685288"
---
# <a name="vspackage-registration"></a>VSPackage-Registrierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackages müssen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] darauf hinweisen, dass Sie installiert sind und geladen werden sollten. Dieser Vorgang wird durch Schreiben von Informationen in die Registrierung durchgeführt. Dies ist ein typischer Auftrag eines Installationsprogramms.  
  
> [!NOTE]
> Bei der VSPackage-Entwicklung ist es ein akzeptiertes Verfahren, die Selbstregistrierung zu verwenden. [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)]Partner können Ihre Produkte jedoch nicht mithilfe der Selbstregistrierung im Rahmen des Setups versenden.  
  
 Registrierungseinträge in einem Windows Installer Paket werden im Allgemeinen in der Registrierungs Tabelle vorgenommen. Sie können auch Dateierweiterungen in der Registrierungs Tabelle registrieren. Windows Installer bietet jedoch integrierte Unterstützung durch die Tabellen für programmatische Bezeichner (ProgID), Klasse, Erweiterung und Verb. Weitere Informationen finden Sie unter [Datenbanktabellen](https://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Stellen Sie sicher, dass Ihre Registrierungseinträge der Komponente zugeordnet sind, die für die ausgewählte parallele Strategie geeignet ist. Registrierungseinträge für eine freigegebene Datei sollten z. b. der Windows Installer Komponente der Datei zugeordnet werden. Ebenso müssen Registrierungseinträge für eine versionsspezifische Datei der Komponente dieser Datei zugeordnet werden. Andernfalls [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] könnte das VSPackage in anderen Versionen durch das Installieren oder Deinstallieren des VSPackage für eine Version von unterbrechen. Weitere Informationen finden Sie [unter unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md) .  
  
> [!NOTE]
> Die einfachste Möglichkeit zum Verwalten der Registrierung besteht darin, dieselben Daten in denselben Dateien sowohl für die Registrierung bei der Registrierung als auch für die Installation der Registrierung zu verwenden. Einige Installer-Entwicklungs Tools können z. b. die Datei im. reg-Format zur Buildzeit nutzen. Wenn Entwickler. reg-Dateien für Ihre eigenen täglichen Entwicklungs-und Debuggingdateien verwalten, können dieselben Dateien automatisch in das Installationsprogramm eingeschlossen werden. Wenn Sie Registrierungsdaten nicht automatisch freigeben können, müssen Sie sicherstellen, dass die Kopie der Registrierungsdaten des Installers aktuell ist.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrieren von nicht verwalteten VSPackages  
 Nicht verwaltete VSPackages (einschließlich derjenigen, die von der Visual Studio-Paket Vorlage generiert werden) verwenden zum Speichern von Registrierungsinformationen ATL-Style. RGS-Dateien. Das RGS-Dateiformat ist für ATL spezifisch und kann im Allgemeinen nicht unverändert von einem Installations Authoring Tool verwendet werden. Registrierungsinformationen für das VSPackage-Installationsprogramm müssen separat verwaltet werden. Beispielsweise können Entwickler Dateien im reg-Format synchron mit RGS-Dateiänderungen aufbewahren. Die reg-Dateien können mit regedit für Entwicklungsarbeiten zusammengeführt oder von einem Installer genutzt werden.  
  
## <a name="registering-managed-vspackages"></a>Verwaltete VSPackages werden registriert  
 Das regpkg-Tool liest die Registrierungs Attribute aus einem verwalteten VSPackage und kann die Informationen entweder direkt in die Registrierung schreiben oder. reg-Format Dateien schreiben, die von einem Installer genutzt werden können.  
  
> [!NOTE]
> Das regpkg-Tool ist nicht Verteil Bar und kann nicht verwendet werden, um ein VSPackage auf dem System eines Benutzers zu registrieren.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Gründe für die Selbstregistrierung von VSPackages beim Installations Zeitpunkt  
 Ihre VSPackage-Installationsprogramme sollten sich nicht auf die Selbstregistrierung verlassen. Auf den ersten Blick scheint das Beibehalten der Registrierungs Werte eines VSPackages nur im VSPackage selbst eine gute Idee zu sein. Da Entwickler die für Ihre Routinearbeit und Tests verfügbaren Registrierungs Werte benötigen, ist es sinnvoll, die Beibehaltung einer separaten Kopie der Registrierungsdaten im Installationsprogramm zu vermeiden. Das Installationsprogramm kann sich auf das VSPackage selbst verlassen, um Registrierungs Werte zu schreiben.  
  
 Obwohl die Selbstregistrierung in der Theorie eine Reihe von Fehlern aufweist, die Sie für die VSPackage-Installation ungeeignet machen:  
  
- Für die ordnungsgemäße Unterstützung der Installation, der Installation, des Rollbacks der Installation und der Deinstallation müssen Sie vier benutzerdefinierte Aktionen für jedes verwaltete VSPackage erstellen, das sich selbst registriert, indem regpkg aufgerufen wird.  
  
- Der Ansatz für die parallele Unterstützung erfordert möglicherweise, dass Sie vier benutzerdefinierte Aktionen erstellen, die regsvr32 oder regpkg für jede unterstützte Version von Aufrufen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Für eine Installation mit selbst registrierten Modulen kann kein sicheres Rollback ausgeführt werden, da es nicht möglich ist, zu sagen, ob die selbst registrierten Schlüssel von einem anderen Feature oder einer anderen Anwendung verwendet werden.  
  
- Selbst registrierte DLLs sind manchmal mit zusätzlichen DLLs verknüpft, die nicht vorhanden sind oder die falsche Version sind. Im Gegensatz dazu können Windows Installer DLLs unter Verwendung der Registrierungs Tabellen registrieren, ohne dass vom aktuellen Status des Systems abhängig ist.  
  
- Dem selbst Registrierungscode kann der Zugriff auf Netzwerkressourcen, z. b. Typbibliotheken, verweigert werden, wenn eine Komponente sowohl als "aus der Quelle ausführen" angegeben als auch in der Tabelle "selfreg" aufgeführt ist. Dies kann dazu führen, dass die Installation der Komponente während einer administrativen Installation fehlschlägt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Verwaltete Paket Registrierung](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
