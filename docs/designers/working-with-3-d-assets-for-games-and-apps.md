---
title: Arbeiten mit 3D-Objekten für Spiele und Apps
description: Erfahren Sie mehr über die Visual Studio-Tools, mit denen Sie 3D-Modelle, Texturen und Shader für DirectX-basierte Spiele und Apps erstellen oder bearbeiten können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b622200832e42aa3900061125fe08271f5f3458
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896350"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Arbeiten mit 3D-Objekten für Spiele und Apps

In diesem Artikel werden die Visual Studio-Tools beschrieben, die Sie verwenden können, um 3D-Modelle, Texturen und Shader für DirectX-basierte Spiele und Apps zu erstellen oder zu ändern.

## <a name="directx-app-development-in-visual-studio"></a>DirectX-App-Entwicklung in Visual Studio

In einer DirectX-App werden normalerweise Programmierlogik, die DirectX-API und HLSL-Programme (High Level Shading Language) mit Audio- und visuellen 3D-Objekten kombiniert. So können Sie von vielfältigen Multimediafunktionen profitieren. Visual Studio enthält Tools, die Sie verwenden können, um mit Bildern und Texturen, 3D-Modellen und Shadern zu arbeiten, ohne die IDE verlassen zu müssen. Visual Studio-Tools sind insbesondere für Folgendes geeignet: zum Erstellen von *Platzhalter*-Objekten, mit denen Sie Code testen oder Prototypen erstellen können, bevor Sie produktionsbereite Objekte in Auftrag geben, und zum Prüfen und Ändern produktionsbereiter Objekte, wenn Sie Ihre Anwendung debuggen.

Im Folgenden finden Sie weitere Informationen über die Objektarten, mit denen Sie in Visual Studio arbeiten können.

### <a name="images-and-textures"></a>Bilder und Texturen

Bilder und Texturen stellen Farb- und visuelle Details in Spielen und Apps bereit. In 3D-Grafiken stehen Texturen in einer Vielzahl von Formaten, Typen und Geometrien zur Verfügung, um unterschiedliche Verwendungen zu unterstützen. Beispielsweise bieten Normalmaps pixelbasierte Oberflächennormale für eine detailliertere Beleuchtung von 3D-Modellen, und Cubemaps bieten Texturen in alle Richtungen zur Verwendung für z.B. Himmel, Reflektionen und kugelförmige Texturzuordnungen. Texturen können Mipmaps bereitstellen, um effizientes Rendering für verschiedene Detailgrade zu unterstützen und können verschiedene Farbkanäle und Farbsysteme unterstützen. Texturen können in einer Vielzahl von komprimierten Formaten gespeichert werden, die weniger dedizierten Grafikspeicher belegen und den Zugriff auf Texturen für GPUs effizienter gestalten.

Sie können die Visual Studio-Bildbearbeitung verwenden, um mit Bildern und Texturen in vielen gängigen Typen und Formaten zu arbeiten.

### <a name="3d-models"></a>3D-Modelle

3D-Modelle erzeugen Raum und Formen in Spielen und Apps. In den Modellen werden die Positionen von Punkten im 3D-Raum, die als *Scheitelpunkte* bezeichnet werden, zusammen mit Indizierungsdaten codiert, um Linien oder Dreiecke zu definieren, die die Form des Modells darstellen. Diesen Vertices können weitere Daten zugeordnet werden, zum Beispiel Farbinformationen, Normalenvektoren oder anwendungsspezifische Attribute. Jedes Modell kann auch objektweite Attribute definieren, z. B. welcher Shader verwendet wird, um die Darstellung der Oberfläche des Objekts zu berechnen, oder welche Textur darauf angewendet wird.

Sie können den Visual Studio-Modell-Editor verwenden, um mit 3D-Modellen in verschiedenen gängigen Formaten zu arbeiten.

### <a name="shaders"></a>Shader

Shader sind kleine, domänenspezifische Programme, die im Grafikprozessor (Graphics Processing Unit, GPU) ausgeführt werden. Shader bestimmen, wie 3D-Modelle in Formen auf dem Bildschirm transformiert werden und wie jedes Pixel in diesen Formen gefärbt ist. Wenn Sie einen Shader erstellen und ihn auf ein Objekt in Ihrem Spiel oder in Ihrer App anwenden, können Sie dem Objekt dadurch eine unverwechselbare Darstellung verleihen.

Sie können mit dem Visual Studio-Shader-Designer (ein graphenbasiertes Shader-Design-Tool) benutzerdefinierte visuelle Effekte ohne Kenntnisse der HLSL-Programmierung erstellen.

> [!NOTE]
> Weitere Informationen über die ersten Schritte mit der DirectX-Programmierung finden Sie unter [DirectX](/windows/win32/directx). Weitere Informationen zum Debuggen einer auf DirectX basierenden Anwendung finden Sie unter [Graphics diagnostics (debugging DirectX graphics) (Grafikdiagnose (Debuggen von DirectX-Grafiken))](../debugger/graphics/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>DirectX-Versionskompatibilität

Visual Studio verwendet DirectX, um 2D- und 3D-Objekte zu rendern. Sie können entweder den DirectX 11-Renderer oder den Windows Advanced Rasterization Platform (WARP)-Softwarerenderer auswählen. Der DirectX 11-Renderer stellt leistungsfähiges, hardwarebeschleunigtes Rendering für DirectX 11- und DirectX 10-GPUs bereit. Mit dem WARP-Renderer wird sichergestellt, dass die Objekte von einer großen Bandbreite an Computern unterstützt werden; dies umfasst auch Computer, die keine moderne Grafikhardware aufweisen, und Computer mit integrierter Grafikhardware. Weitere Informationen zu WARP finden Sie unter [Windows Advanced Rasterization Platform (WARP) Guide (Windows Advanced Rasterization Platform-Handbuch)](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Arbeiten mit Texturen und Bildern](../designers/working-with-textures-and-images.md)|Beschreibt, wie Visual Studio verwendet wird, um mit Bildern und Texturen zu arbeiten.|
|[Arbeiten mit 3D-Modellen](../designers/working-with-3-d-models.md)|Beschreibt, wie Visual Studio verwendet wird, um mit 3D-Modellen zu arbeiten.|
|[Arbeiten mit Shadern](../designers/working-with-shaders.md)|Beschreibt, wie der Visual Studio-Shader-Designer verwendet wird, um benutzerdefinierte Shadereffekte zu erstellen und zu ändern.|
|[Verwenden von 3D-Objekten in Spielen oder Apps](../designers/using-3-d-assets-in-your-game-or-app.md)|Beschreibt, wie Objekte verwendet werden, die Sie mit dem Bild-Editor, Modell-Editor oder Shader-Designer in Ihrem Spiel oder Ihrer App erstellt haben.|
