---
title: Image Service-Tools | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Tools, die im Visual Studio SDK bereitgestellt werden und Ihnen helfen, Erweiterungen mit dem Visual Studio-Image Dienst zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ddb0342-eb22-429a-bdf3-ccc2719a7ceb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9988b32d693fe9d65d70543a0f3d1da9a69959db
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761126"
---
# <a name="image-service-tools"></a>Tools für Bilddienste
Das vs SDK umfasst mehrere Tools, mit denen Erweiterungs Generatoren den Visual Studio-Image Dienst verwenden können.

- Das [Manifest from Resources](../../extensibility/internals/manifest-from-resources.md) Tool führt eine Liste der Bild Ressourcen (PNG-oder XAML-Dateien) aus und generiert eine bildmanifesteindatei.

- Das [Manifest to Code](../../extensibility/internals/manifest-to-code.md) Tool nimmt eine bildmanifesteindatei an und generiert eine Wrapper Datei zur Verwendung in C++-, c#-, VB-oder vsct-Dateien.

- Der [Bild Bibliotheks-Viewer](../../extensibility/internals/image-library-viewer.md) kann Bild Manifeste laden, bearbeiten und durchsuchen.
