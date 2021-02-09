---
title: Visual Studio-Tools für Installationsszenarien für Office-Runtime
description: Erfahren Sie, wie Sie die Visual Studio 2010-Tools für Office-Laufzeit installieren können. In diesem Artikel werden drei Installationsszenarien beschrieben.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 10b747602a1c5af9f63c567103a80405341019af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921796"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio-Tools für Installationsszenarien für Office-Runtime
  Sie können die Visual Studio 2010-Tools für Office-Laufzeit auf drei Arten installieren:

- Wenn Sie Visual Studio installieren.

- Wenn Sie Microsoft Office installieren.

- Wenn Sie die weitervertreibbare Visual Studio 2010-Tools für Office-Laufzeit installieren.

  Die installierten Laufzeitkomponenten hängen von der Konfiguration des Computers und dem Installationsszenario ab.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Laufzeitkomponenten, die in jedem Installationsszenario installiert werden
 Die Visual Studio 2010-Tools für Office-Laufzeit enthält drei Komponenten: das Office-projektmappenlade Tool, die Office-Erweiterungen für das .NET Framework 3,5 und die Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher. Wenn Sie die Laufzeit installieren, wird das Ladeprogramm für Office-Projektmappen immer installiert. Die Installation der Office-Erweiterungen für .NET Framework hängt von der Konfiguration des Computers und dem Installationsszenario ab. Wenn eine der Office-Erweiterungen bei der erstmaligen Installation der Laufzeit nicht installiert werden kann, installiert die Laufzeit die fehlenden Office-Erweiterungen später automatisch, sobald bestimmte Anforderungen erfüllt sind. Diese Funktion der Laufzeit heißt *install on Demand*.

 In der folgenden Tabelle ist dargestellt, welche Laufzeitkomponenten bei den einzelnen Laufzeitinstallationsszenarios standardmäßig installiert werden. Weitere Informationen zu den einzelnen Szenarien finden Sie weiter unten.

|Laufzeitinstallationsszenario|Ladeprogramm für Office-Projektmappen|Office-Erweiterungen für .NET Framework 3.5|Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Office-Erweiterungen für [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] und höher|Ja|Ja, wenn .NET Framework 3.5 bereits installiert ist.|Ja|Ja|
|Mit [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Ja|Ja, wenn .NET Framework 3.5 bereits installiert ist.|Nein|Nein|
|Mit Office 2010 Service Pack 1 (SP1) oder höher|Ja|Ja, wenn .NET Framework 3.5 bereits installiert ist.|Ja, wenn [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] bereits installiert ist.|Nein|
|Mit dem verteilbaren Laufzeitpaket|Ja|Ja, wenn .NET Framework 3.5 bereits installiert ist.|Ja, wenn [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] bereits installiert ist.|Ja, wenn [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] bereits installiert ist.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Installieren der Laufzeit mit Visual Studio oder dem Microsoft Office Developer Tools für Visual Studio
 Wenn Sie die Office Developer Tools in Visual Studio installieren, werden die Office-Erweiterungen für [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] und [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] immer auf dem Entwicklungscomputer installiert. Die Office-Erweiterungen für .NET Framework 3.5 werden nur installiert, wenn .NET Framework 3.5 bereits auf dem Entwicklungscomputer vorhanden ist. Falls Sie .NET Framework 3.5 nach der Installation von [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] installieren, installiert die Laufzeit automatisch die Office-Erweiterungen für .NET Framework 3.5, wenn Sie zum ersten Mal ein Office-Projekt mit der Zielversion .NET Framework 3.5 erstellen.

> [!WARNING]
> Sie können kein Office-Projekt mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] oder höher erstellen, das .NET Framework 3.5 als Ziel verwendet.

 Weitere Informationen zum Installieren der Office Developer Tools finden Sie unter Gewusst [wie: Konfigurieren eines Computers zum Entwickeln von Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)-Projektmappen.

### <a name="install-the-runtime-with-office"></a>Installieren der Laufzeit mit Office
 Wenn Sie Office installieren, werden die Office-Erweiterungen für .NET Framework 3.5 installiert, sofern .NET Framework 3.5 bereits auf dem Computer vorhanden ist. Falls Sie .NET Framework 3.5 nach der Installation von Office installieren, installiert die Laufzeit automatisch die Office-Erweiterungen für .NET Framework 3.5, wenn zum ersten Mal von einer Office-Anwendung versucht wird, eine Projektmappe mit der Zielversion .NET Framework 3.5 zu laden.

 Die Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher werden nicht zusammen mit Office installiert. Dies gilt auch, wenn [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher beim Installieren von Office bereits vorhanden ist.

 Die Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] werden zusammen mit Office installiert. Endbenutzer erhalten die Office-Erweiterungen für [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] durch Installieren eines Windows-Updates.

 Um sicherzustellen, dass die Benutzer über die erforderlichen Erweiterungen für die Verwendung Ihrer Anwendung verfügen, müssen Sie die neueste Version der verteilbaren Visual Studio 2010-Tools für Office-Laufzeit als erforderliche Komponente für Ihre Lösung einschließen. Weitere Informationen zu Voraussetzungen finden Sie unter [Voraussetzungen für Office-Lösungen für die Bereitstellung](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Installieren der Laufzeit mithilfe der weitervertreibbaren Runtime
 Sie können die Laufzeit installieren, indem Sie die weitervertreibbare Visual Studio 2010-Tools für Office-Laufzeit manuell ausführen oder das verteilbare Element als erforderliche Komponente einschließen, wenn Sie eine Office-Projekt Mappe bereitstellen.

 Wenn Sie die Laufzeit mithilfe der verteilbaren Visual Studio 2010-Tools für Office-Laufzeit installieren, werden die Office-Erweiterungen für die .NET Framework 3,5 und die Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher installiert, wenn die entsprechenden Versionen der .NET Framework bereits auf dem Computer vorhanden sind. Ist eine dieser .NET Framework-Versionen beim Installieren der Laufzeit nicht auf dem Computer vorhanden, werden die Office-Erweiterungen für die fehlende .NET Framework-Version zu diesem Zeitpunkt nicht installiert. Falls Sie die fehlende .NET Framework-Version zu einem späteren Zeitpunkt installieren, installiert die Laufzeit die entsprechenden Office-Erweiterungen automatisch, wenn das nächste Mal eine Projektmappe, die die Erweiterungen erfordert, installiert (wenn die Laufzeit mit einer mit ClickOnce bereitgestellten Projektmappe installiert wurde) oder geladen wird (wenn die Laufzeit mit einer mit Windows Installer bereitgestellten Projektmappe installiert wurde).

 Weitere Informationen zum Einschließen von Voraussetzungen in eine ClickOnce-Lösung finden Sie unter Gewusst [wie: Installieren von erforderlichen Komponenten auf Endbenutzer Computern zum Ausführen von Office](/previous-versions/bb608608(v=vs.110))-Projektmappen. Weitere Informationen zum manuellen Installieren der Laufzeit aus dem verteilbaren Paket finden Sie unter Gewusst [wie: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Visual Studio-Tools für Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Assemblys in der Visual Studio-Tools für Office-Laufzeit](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)