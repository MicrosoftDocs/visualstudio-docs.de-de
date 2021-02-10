---
title: Arbeiten mit Shaders
description: Erfahren Sie, wie Sie mit dem diagrammbasierten Shader-Designer in Visual Studio benutzerdefinierte Shadereffekte entwerfen. Sie können Shader in DirectX-basierten Spielen oder Apps verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bff5aee4337a464498fc4ac027eb05b2da912b61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844891"
---
# <a name="work-with-shaders"></a>Arbeiten mit Shadern

Sie können den diagrammbasierten Shader-Designer in Visual Studio verwenden, um benutzerdefinierte Shadereffekte zu entwerfen. Diese Shader finden in Ihren DirectX-basierten Spielen oder Apps Verwendung.

## <a name="shaders"></a>Shader

Ein *Shader* ist ein Programm, das Grafikberechnungen durchführt, z.B. Vertextransformationen oder Pixelfarben, und üblicherweise auf dem Grafikprozessor (Graphics Processing Unit; GPU) statt auf der CPU ausgeführt wird. Da die meisten Phasen der herkömmlichen Grafikpipeline mit festen Funktionen nun durch Shaderprogramme ausgeführt werden, können Sie diese verwenden, um eine Pipeline zu erstellen, die an die Anforderungen Ihrer App angepasst ist.

Die häufigsten Shader sind *Vertexshader*, die Berechnungen pro Vertex durchführen und die Transformation mit festen Funktionen sowie die Beleuchtungsszenarios von nicht programmierbarer Grafikhardware ersetzt, und *Pixelshader*, die Berechnungen pro Pixel durchführen, um die Farbe eines Pixels zu bestimmen, und die Farbmischerschaltung mit festen Funktionen in nicht programmierbarer Grafikhardware ersetzt. Für moderne Grafikhardware sind weitere Shader möglich: *Hüllenshader*, *Domänenshader* und *Geometrieshader* für Grafikberechnungen sowie *Computeshader* für nicht-grafische Berechnungen. Keine dieser Phasen ist in nicht programmierbarer Grafikhardware verfügbar. Shaders wurden ursprünglich mithilfe einer Assembly-ähnlichen Sprache erstellt, die datenparallele (SIMD) und grafikzentrierte (Skalarprodukt) Anweisungen bereitstellt. Mittlerweile werden Shader üblicherweise mithilfe von C-ähnlichen Sprachen auf hoher Ebene wie HLSL (High Level Shader Language) erstellt.

Sie können den Shader-Designer verwenden, um Pixelshader interaktiv statt durch das Eingeben und Kompilieren von Code zu erstellen. Im Shader-Designer wird ein Shader durch eine Anzahl von Knoten definiert, der Daten und Vorgänge darstellt, sowie durch Verbindungen zwischen Knoten, die den Fluss von Datenwerten und Zwischenergebnisse über den Shader darstellen. Durch diesen Ansatz und die Echtzeitvorschau im Shader-Designer können Sie die Ausführung des Shaders einfacher visualisieren und durch Experimente interessante Shadervariationen entdecken.

## <a name="dgsl-documents"></a>DGSL-Dokumente

Der Shader-Designer speichert Shader im DGSL-Format (Directed Graph Shader Language). Dabei handelt es sich um ein XML-Format, das auf DGML (Directed Graph Markup Language) basiert. Sie können DGSL-Shader direkt auf 3D-Modelle im Modell-Editor anwenden. Bevor Sie einen DGSL-Shader in Ihrer App verwenden können, müssen Sie diesen in ein Format exportieren, das DirectX verarbeiten kann (z.B. HLSL).

Da DGSL mit DGML kompatibel ist, können Sie Tools verwenden, die für das Analysieren von DGML-Dokumenten entwickelt wurden, um Ihre DGSL-Shader zu analysieren. Weitere Informationen zu DGML finden Sie unter [Grundlegendes zu Directed Graph Markup Language (DGML)](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Shader-Designer](../designers/shader-designer.md)|Beschreibt die Verwendung des Shader-Designers von Visual Studio zur Arbeit mit Shadern.|
|[Shader-Designer-Knoten](../designers/shader-designer-nodes.md)|Beschreibt die Arten von Shader-Designer-Knoten, die Sie verwenden können, um die Grafikeffekte zu erzielen.|
|[Beispiele für den Shader-Designer](../designers/how-to-create-a-basic-color-shader.md)|Enthält Links zu Artikeln, die die Verwendung des Shader-Designers zum Erzielen von allgemeinen Grafikeffekten veranschaulicht.|
