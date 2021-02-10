---
title: '&apos;Neuerungen im Visual Studio 2017 SDK | Microsoft-Dokumentation'
description: Das Visual Studio SDK verfügt über neue und aktualisierte Features für Visual Studio 2017, einschließlich des aktualisierten VSIX Version 3-Formats.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ab9183eacfc82aa70c22dec551883561b021b58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931247"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Neuerungen in Visual Studio 2017 SDK&#39;s

Das Visual Studio SDK verfügt über die folgenden neuen und aktualisierten Features für Visual Studio 2017.

## <a name="vsix-v3-format"></a>VSIX v3-Format

Zur Unterstützung der neuen einfachen Installation von Visual Studio 2017 wurde das VSIX-Erweiterungs Manifest-Format auf Version 3 (VSIX v3) aktualisiert.

Das neue Format unterstützt Folgendes:

* Explizites Deklarieren der erforderlichen Komponenten, die vom vsixinstaller erkannt und installiert werden.
* Ngen-Assemblys bei der Erweiterungs Installation.
* Installieren von Assets außerhalb des üblichen Erweiterungs Stamms.

Weitere Informationen zu diesen Änderungen finden Sie in den folgenden Themen:

* [Änderungen an der Erweiterbarkeit für Visual Studio 2017](breaking-changes-2017.md)
* [NGen-Unterstützung in VSIX v3](ngen-support.md)
* [Installieren außerhalb des Ordners für Erweiterungen](set-install-root.md)
* [Häufig gestellte Fragen zu Visual Studio 2017-Erweiterbarkeit](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrieren des Erweiterbarkeits Projekts zu Visual Studio 2017

Informationen zum Aktualisieren der Erweiterbarkeits Projekte und ihrer VSIX-Manifeste auf Visual Studio 2017 finden Sie unter Gewusst [wie: Migrieren von Erweiterungs Projekten zu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Benutzerdefinierte Projekt-und Element Vorlagen

Ab Visual Studio 2017 werden keine Scans nach benutzerdefinierten Projekt- und Elementvorlagen mehr durchgeführt. Die Erweiterung muss nun Vorlagenmanifestdateien mit dem Installationspfad dieser Vorlagen enthalten. Sie können Ihre VSIX-Erweiterungen mithilfe von Visual Studio 2017 aktualisieren. Wenn Sie eine Erweiterung über eine MSI-Datei bereitstellen, müssen Sie die Vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt-und Element Vorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das Vorlagenmanifestschema ist in der [Referenz zum Visual Studio-Vorlagenmanifestschema](../extensibility/visual-studio-template-manifest-schema-reference.md) dokumentiert.

## <a name="updated-extension-performance-guidelines"></a>Aktualisierte Empfehlungen zur Erweiterungs Leistung

Im Artikel [Verwalten von VSPackages](managing-vspackages.md) finden Sie eine neue Vorgehens [Weise: Diagnose der Erweiterungs Leistung](how-to-diagnose-extension-performance.md) , um zu veranschaulichen, wie Erweiterungs Auswirkungen auf Start-und Ladezeiten von Visual Studio erkannt und analysiert werden.
