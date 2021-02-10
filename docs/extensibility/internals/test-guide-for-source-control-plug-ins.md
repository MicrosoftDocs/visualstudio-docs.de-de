---
title: Testleitfaden für Quellcodeverwaltungs-Plug-Ins | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ihr Quellcodeverwaltungs-Plug-In mit Visual Studio testen. Diese Übersicht bezieht allgemeine Testbereiche ein.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 951b83f425f1e7171c519fced3fa3a4644279621
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934141"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testleitfaden für Quellcodeverwaltungs-Plug-Ins
In diesem Artikel finden Sie einen Leitfaden für das Testen Ihrer Quellcodeverwaltungs-Plug-Ins mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Außerdem erhalten Sie einen umfassenden Überblick über die gängigsten Testbereiche sowie über einige andere komplexe Bereiche, die sich als problematisch erweisen könnten. Diese Übersicht soll jedoch nicht als umfassende Liste von Testfällen verstanden werden.

> [!NOTE]
> Manche Fehlerbehebungen und Verbesserungen an der aktuellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-IDE decken möglicherweise Probleme mit vorhandenen Quellcodeverwaltungs-Plug-Ins auf, die bisher bei Verwendung vorheriger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Versionen kein Thema waren. Sie sollten Ihre vorhandenen Quellcodeverwaltungs-Plug-Ins unbedingt in den in diesem Artikel aufgeführten Bereichen testen, selbst dann, wenn am Plug-In seit der vorherigen Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] keine Änderungen vorgenommen wurden.

## <a name="common-preparation"></a>Allgemeine Vorbereitung
 Ein Computer mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und eine Installation des Zielquellcodeverwaltungs-Plug-Ins sind erforderlich. Ein zweiter Computer mit ähnlicher Konfiguration kann für einige der „Aus Quellcodeverwaltung öffnen“-Tests verwendet werden.

## <a name="definition-of-terms"></a>Begriffsdefinition
 Verwenden Sie im Rahmen dieses Testleitfadens die folgenden Begriffsdefinitionen:

 Clientprojekt Jeder in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügbare Projekttyp, der die Quellcodeverwaltungsintegration unterstützt, z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

 Webprojekt Es gibt vier Arten von Webprojekten: Dateisystem, Lokale IIS, Remotestandorte und FTP.

- Dateisystemprojekte werden unter einem lokalen Pfad erstellt, sie benötigen jedoch keine Installation der Internetinformationsdienste (Internet Information Services, IIS), da der Zugriff intern über einen UNC-Pfad erfolgt. Außerdem können sie ähnlich wie Clientprojekte über die IDE einer Quellcodeverwaltung unterstellt werden.

- Lokale IIS-Projekte funktionieren mit einer IIS-Installation auf demselben Computer. Der Zugriff erfolgt über eine URL, die auf den lokalen Computer verweist.

- Remotestandortprojekte werden ebenfalls im Rahmen der IIS erstellt, sie unterliegen jedoch der Quellcodeverwaltung auf dem IIS-Servercomputer, nicht über die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-IDE.

- Der Zugriff auf FTP-Projekte erfolgt über einen FTP-Remoteserver. Diese Projekte können jedoch keiner Quellcodeverwaltung unterstellt werden.

  Eintragung Dies ist ein anderer Begriff für die Projektmappe oder das Projekt, das der Quellcodeverwaltung unterstellt ist.

  Versionsspeicher Hierbei handelt es sich um die Quellcodeverwaltungsdatenbank, auf die über die Plug-In-API der Quellcodeverwaltung zugegriffen wird.

## <a name="test-areas-covered-in-this-section"></a>In diesem Artikel behandelte Testbereiche

- [Testbereich 1: Hinzufügen/Öffnen über die Quellcodeverwaltung](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Fall 1a: Hinzufügen der Projektmappe zur Quellcodeverwaltung

  - Fall 1b: Öffnen der Projektmappe in der Quellcodeverwaltung

  - Fall 1c: Hinzufügen der Projektmappe aus der Quellcodeverwaltung

- [Testbereich 2: Abrufen aus der Quellcodeverwaltung](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Testbereich 3: Auschecken/Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Fall 3: Auschecken/Auschecken rückgängig machen

  - Fall 3a: Auschecken

  - Fall 3b: Nicht verbundenes Auschecken

  - Fall 3c: Bearbeiten/Speichern von Abfragen (Query Edit/Query Save, QEQS)

  - Fall 3d: Automatisches Auschecken

  - Fall 3e: Auschecken rückgängig machen

- [Testbereich 4: Einchecken](../../extensibility/internals/test-area-4-check-in.md)

  - Fall 4a: Bearbeitete Elemente

  - Fall 4b: Hinzufügen von Dateien

  - Fall 4c: Hinzufügen von Projekten

- [Testbereich 5: Ändern der Quellcodeverwaltung](../../extensibility/internals/test-area-5-change-source-control.md)

  - Fall 5a: Bind

  - Fall 5b: Aufheben der Bindung

  - Fall 5c: Neu binden

- [Testbereich 6: Löschen](../../extensibility/internals/test-area-6-delete.md)

- [Testbereich 7: Freigeben](../../extensibility/internals/test-area-7-share.md)

- [Testbereich 8: Plug-In-Wechsel](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Fall 8a: Automatische Änderung

  - Fall 8b: Projektmappenbasierte Änderung

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)
