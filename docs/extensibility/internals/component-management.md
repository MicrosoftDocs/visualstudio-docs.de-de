---
title: Komponenten Verwaltung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Windows Installer Komponenten verwalten, wenn Sie ein VSPackage-Installationsprogramm in Visual Studio erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 648a1c90b143a0f38f8911fcaed3ee1ed16908b6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304918"
---
# <a name="component-management"></a>Komponenten Verwaltung
Aufgaben Einheiten in der Windows Installer werden als Windows Installer Komponenten (manchmal als "wics" oder "nur Komponenten" bezeichnet) bezeichnet. Eine GUID identifiziert jedes WIC, bei dem es sich um die grundlegende Einheit für die Installation und die Verweis Zählung für Setups handelt, die Windows Installer verwenden.

 Obwohl Sie zum Erstellen des VSPackage-Installers mehrere Produkte verwenden können, wird in dieser Erläuterung die Verwendung von Windows Installer-Dateien (*MSI*-Dateien) vorausgesetzt. Wenn Sie das Installationsprogramm erstellen, müssen Sie die Datei Bereitstellung ordnungsgemäß verwalten, damit die richtige Verweis Zählung immer erfolgt. Folglich stören verschiedene Versionen Ihres Produkts in einer Mischung aus Installations-und Deinstallations Szenarios nicht gegenseitig.

 In Windows Installer erfolgt die Verweis Zählung auf Komponentenebene. Sie müssen ihre Ressourcen sorgfältig organisieren – Dateien, Registrierungseinträge usw. – in Komponenten. Es gibt andere Ebenen der Organisation – z. b. Module, Features und Produkte –, die in verschiedenen Szenarien hilfreich sein können. Weitere Informationen finden Sie unter [Windows Installer Grundlagen](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Richtlinien zum Erstellen von Setup für die parallele Installation

- Verfassen von Dateien und Registrierungs Schlüsseln, die von Versionen gemeinsam genutzt werden, in Ihre eigenen Komponenten.

     Auf diese Weise können Sie Sie problemlos in der nächsten Version verwenden. Beispielsweise können Sie Bibliotheken, die Global registriert sind, Dateierweiterungen, andere in **HKEY_CLASSES_ROOT** registrierte Elemente usw. eingeben.

- Gruppieren Sie freigegebene Komponenten in separaten Mergemodulen.

     Diese Strategie hilft Ihnen beim Erstellen einer ordnungsgemäßen Installation für eine parallele Installation.

- Installieren Sie freigegebene Dateien und Registrierungsschlüssel, indem Sie die gleichen Windows Installer Komponenten in verschiedenen Versionen verwenden.

     Wenn Sie eine andere Komponente verwenden, werden Dateien und Registrierungseinträge deinstalliert, wenn ein VSPackage mit Versions Angabe deinstalliert wird, aber noch ein anderes VSPackage installiert ist.

- Mischen Sie versionierte und freigegebene Elemente in derselben Komponente nicht.

     Dadurch ist es nicht mehr möglich, freigegebene Elemente an einem globalen Speicherort zu installieren und Elemente mit Versions Angabe für isolierte Standorte zu installieren.

- Verwenden Sie keine freigegebenen Registrierungsschlüssel, die auf Dateien mit Versions Angabe verweisen.

     Wenn Sie dies tun, werden die freigegebenen Schlüssel überschrieben, wenn ein anderes VSPackage mit Versions Angabe installiert wird. Nachdem Sie die zweite Version entfernt haben, ist die Datei, auf die der Schlüssel verweist, nicht mehr vorhanden.

## <a name="see-also"></a>Siehe auch
- [Auswählen zwischen freigegebenen und versionierten VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage-Setup Szenarien](../../extensibility/internals/vspackage-setup-scenarios.md)
