---
title: Filtern von Knoten
description: Erfahren Sie mehr über Filterknoten, die im Shader-Designer Eingaben wie z. B. eine Farbe oder ein Textursample in einen figurativen Farbwert umwandeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f81a51248f548ea26283dc193645ff7216eb0f
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134164"
---
# <a name="filter-nodes"></a>Filterknoten

Filterknoten wandeln im Shader-Designer Eingabe, z.B. ein Farb- oder Texturbeispiel, in einen figurativen Farbwert. Diese figurativen Farbwerte werden häufig für nicht fotorealistisches Rendering oder als Komponenten in anderen visuellen Effekten verwendet.

## <a name="filter-node-reference"></a>Referenz zu Filterknoten

|Node|Details|Eigenschaften|
|----------|-------------|----------------|
|**Blur**|Zeichnet die Pixel in einer Textur mit einer Gauß-Funktion weich.<br /><br /> Damit können Sie die Farbdetails oder das Rauschen in einer Textur reduzieren.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten für das zu testende Texel<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Der weichgezeichnete Farbwert|**Struktur**<br /> Das Texturregister, das dem Sampler zugeordnet ist, der während der Weichzeichnung verwendet wird|
|**Desaturate**|Verringert die Farbintensität der angegebenen Farbe.<br /><br /> Beim Entsättigen der Farbe nähert sich der Farbwert seinem Graustufenäquivalent.<br /><br /> **Eingabe:**<br /><br /> `RGB`: `float3`<br /> Die zu entsättigende Farbe<br /><br /> `Percent`: `float`<br /> Der Prozentsatz, um den die Farbsättigung verringert werden soll, ausgedrückt als normalisierter Wert im Bereich [0, 1].<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float3`<br /> Die entsättigte Farbe|**Sättigung**<br /> Die Gewichtungen, die den Rot-, Grün- und Blau-Farbkomponenten zugeordnet sind|
|**Edge Detection**|Erkennt Kanten in einer Textur mit dem Canny-Algorithmus. Kantenpixel werden als weiß ausgegeben, Nicht-Kantenpixel als schwarz.<br /><br /> Dadurch können Sie Kanten in einer Textur identifizieren und zusätzliche Effekte verwenden, um auf diese Kanten anzuwenden.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten für das zu testende Texel<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Die Ausgabe ist weiß, wenn sich das Texel auf einer Kante befindet, andernfalls ist sie schwarz.|**Struktur**<br /> Das Texturregister, das dem Sampler zugeordnet ist, der während der Kantenerkennung verwendet wird.|
|**Sharpen**|Zeichnet eine Textur scharf.<br /><br /> Damit können Sie genaue Details in einer Textur hervorheben.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten für das zu testende Texel<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Der weichgezeichnete Farbwert|**Struktur**<br /> Das Texturregister, das dem Sampler zugeordnet ist, der während der Scharfzeichnung verwendet wird.|