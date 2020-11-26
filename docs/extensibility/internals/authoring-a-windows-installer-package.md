---
title: Erstellen eines Windows Installer Pakets | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Windows Installer Paket für Visual Studio erstellen, das aus Datenbanktabellen besteht, die Datei-und Registrierungsdaten enthalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82c96bdf8e73f7d40b41220524edef022c216f1b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190121"
---
# <a name="author-a-windows-installer-package"></a>Erstellen eines Windows Installer Pakets
Daten steuern das Windows Installer Modell. Anstatt ein prozedurales Skript zum Kopieren von Dateien und zum Schreiben von Registrierungs Einträgen zu schreiben, schreiben Sie z. b. Zeilen und Spalten in Datenbanktabellen, die Datei-und Registrierungsdaten enthalten.

## <a name="database-entries"></a>Datenbankeinträge
Um ein VSPackage zu installieren, muss ein Windows Installer Paketdaten Bank Einträge enthalten, um die folgenden Aufgaben auszuführen:

- Durchsuchen Sie das System, um zu ermitteln, welche Versionen des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage unterstützt (mit Windows Installer Tabellen, die AppSearch, complocator, reglocator, drlocator und Signature enthalten).

- Brechen Sie die Installation ab, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installiert ist oder eine andere System Anforderung des VSPackage nicht erfüllt wird (mithilfe der LaunchCondition-Tabelle).

- Installieren Sie das VSPackage und abhängige Dateien (mithilfe der Verzeichnis-, Komponenten-und Datei Tabellen).

- Fügen Sie die entsprechenden Informationen für das VSPackage zur Registrierung hinzu (mithilfe der Registrierungs Tabelle).

- Integrieren Sie das VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von **devenv.exe/Setup** (mithilfe der CustomAction-Tabelle).

Weitere Informationen finden Sie unter [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Setup Tools
Eine Reihe von Setup Tools von Drittanbietern bieten eine Entwicklungsumgebung für Windows Installer Pakete. Die folgenden kostenlosen Tools sind verfügbar:

- InstallShield Limited Edition

   Sie können eine begrenzte Version von InstallShield über das Visual Studio-Dialogfeld " **Neues Projekt** " erhalten. Erweitern Sie **andere Projekttypen** , und wählen Sie dann **Setup und Bereitstellung** aus. Wählen Sie die Vorlage InstallShield aus.

- Windows Installer XML-Toolset

   Das WiX-Toolset (Windows Installer XML) erstellt Windows Installer Pakete aus XML-Quelldateien. Das WiX-Toolset ist ein Microsoft-Open-Source-Projekt. Sie können den Quellcode und ausführbare Dateien aus dem [WiX-Toolset](https://sourceforge.net/projects/wix/)herunterladen.

   Informationen zu kommerziellen Produkten, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe von in integriert [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] werden, finden Sie unter [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
