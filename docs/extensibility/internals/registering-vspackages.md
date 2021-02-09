---
title: Registrieren von VSPackages | Microsoft-Dokumentation
description: Eine pkgdef-Datei enthält Informationen, die andernfalls der Systemregistrierung hinzugefügt werden. Erfahren Sie, wie Visual Studio pkgdef-Dateien verwendet, um ein VSPackage zu beschreiben/zu suchen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 111debccd1623901790c83e743469327ffdd667e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905839"
---
# <a name="registering-vspackages"></a>Registrieren von VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stützt sich auf pkgdef-Dateien, um ein VSPackage zu beschreiben und zu suchen. Eine pkgdef-Datei enthält alle Registrierungsinformationen, die andernfalls der Systemregistrierung hinzugefügt würden. Verwaltete VSPackages werden durch Hinzufügen von Attributen zum Quellcode und anschließendem Ausführen des [Dienstprogramms "| atepkgdef](../../extensibility/internals/createpkgdef-utility.md) " für die resultierende Assembly registriert, um eine pkgdef-Datei zu generieren.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Beschreibt den Lade Pfad für VSPackages.

- [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Erläutert, wie ein VSPackage registriert wird.
