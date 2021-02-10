---
title: Erweitern von Abhängigkeitsdiagrammen
description: Erfahren Sie, wie Sie Code schreiben können, um Abhängigkeits Diagramme zu erstellen und zu aktualisieren, und wie Sie die Struktur Ihres Programmcodes mit Abhängigkeits Diagrammen in Visual Studio validieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10e0e07b6a8ee4245e19628e03bfdf484f94d34c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935143"
---
# <a name="extend-dependency-diagrams"></a>Erweitern von Abhängigkeitsdiagrammen

Sie können Code schreiben, um Abhängigkeits Diagramme zu erstellen und zu aktualisieren und die Struktur Ihres Programmcodes mit Abhängigkeits Diagrammen in Visual Studio zu validieren. Sie können Befehle hinzufügen, die im Kontextmenü der Diagramme angezeigt werden, Drag & Drop-Gesten anpassen und über Textvorlagen auf das Ebenenmodell zugreifen. Sie können diese Erweiterung in einer Visual Studio Integration Extension (VSIX) verpacken und sie an andere Visual Studio-Benutzer verteilen.

## <a name="requirements"></a>Anforderungen

Auf dem Computer, auf dem Sie die Ebenenerweiterungen entwickeln möchten, muss Folgendes installiert sein:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modellierungs-SDK für Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Auf dem Computer, auf dem Sie die Ebenenerweiterungen ausführen möchten, muss eine passende Edition von Visual Studio installiert sein. Welche Editionen von Visual Studio Abhängigkeits Diagramme unterstützen, erfahren Sie unter [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Weitere Informationen

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)
- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)
