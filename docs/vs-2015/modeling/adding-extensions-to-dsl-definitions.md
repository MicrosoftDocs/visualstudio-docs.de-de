---
title: Hinzufügen von Erweiterungen zu DSL-Definitionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919060"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Hinzufügen von Erweiterungen zu DSL-Definitionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die DSL-Definitions Erweiterung ermöglicht es Ihnen, ein Paket mit Erweiterungen für eine domänenspezifische Sprache (DSL) zu erstellen. Die DSL-Erweiterung, die in einer Visual Studio-Integrations Erweiterung (VSIX) enthalten ist, kann auf dem Computer eines Benutzers auf die gleiche Weise wie eine DSL installiert werden. Die zusätzlichen Features können zur Laufzeit dynamisch aktiviert und deaktiviert werden. DSLs müssen nicht explizit für Erweiterungen entworfen werden, und Erweiterungen können später oder von Drittanbietern entworfen werden, ohne die erweiterte DSL zu ändern.

 Die zusätzlichen Features können Folgendes umfassen:

- Eigenschaften für Modell-und Präsentationselemente

- Decorators für Formen und Connectors

- Klassen, Beziehungen, Formen und Connectors

- Validierungs Einschränkungen

- Toolbox Elemente und Registerkarten

  Ein Benutzer einer erweiterten DSL kann ein Modell erstellen und speichern, das Instanzen der zusätzlichen Funktionen enthält. Diese können von anderen Benutzern gelesen werden, die die entsprechende Erweiterung installiert haben. Benutzer, die die Erweiterung nicht installiert haben, können die zusätzlichen Features nicht verwenden, aber Sie können ein Modell aktualisieren und speichern, ohne die zusätzlichen Features zu verlieren.

  Beispielcode und weitere Informationen zu diesem Feature finden Sie auf der [Visual Studio-Website zum Visualisieren und modellieren von SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148) .

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio Visualization and Modeling SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
