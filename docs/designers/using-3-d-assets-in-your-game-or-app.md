---
title: Verwenden von 3D-Objekten in Spielen oder Apps
description: Erfahren Sie, wie Sie Visual Studio zum Verarbeiten von 3D-Objekten und zum Einschließen dieser Objekte in Builds verwenden. Visual Studio stellt Buildanpassungen für jedes generierte Objekt bereit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee9dff2cd6b762b2f81581963de6186cdd36e3ab
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134739"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Vorgehensweise: Verwenden von 3D-Objekten in Spielen oder Apps

In diesem Artikel wird beschrieben, wie Sie Visual Studio verwenden können, um 3D-Objekte zu verarbeiten und in Ihre Builds zu integrieren.

Nachdem Sie 3D-Objekte mit den Tools von Visual Studio erstellt haben, besteht der nächste Schritt darin, sie in Ihrer App zu verwenden. Bevor Sie sie jedoch verwenden können, müssen sie in ein Format umgewandelt werden, das von DirectX unterstützt wird. Um Sie bei der Transformation Ihrer Objekte zu unterstützen, stellt Visual Studio Buildanpassungen für jede Art von Objekt bereit, die dieser Dienst erzeugen kann. Um die Ressourcen in Ihrem Build zu integrieren, müssen Sie einfach nur Ihr Projekt für die Verwendung der Buildanpassungen konfigurieren, die Ressourcen dem Projekt hinzufügen und die Ressourcen so konfigurieren, dass die richtige Buildanpassung verwendet wird. Danach können Sie die Ressourcen in die App laden und sie verwenden. Dazu erstellen und füllen Sie DirectX-Ressourcen so, wie Sie es in jeder anderen DirectX-App tun würden.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Bevor Sie die 3D-Objekte als Teil des Builds bereitstellen können, muss Visual Studio mitgeteilt werden, welche Arten von Objekten Sie bereitstellen möchten. Visual Studio kennt bereits viele gängige Dateitypen. Da aber nur bestimmte Arten von Apps 3D-Objekten verwenden, kann Visual Studio nicht wissen, dass ein Projekt mit diesen Arten von Dateien erstellt wird. Sie können Visual Studio mitteilen, dass die App diese Arten von Objekten verwendet, indem Sie die *Buildanpassungen* nutzen, die für jeden Objekttyp bereitgestellt werden. Buildanpassungen sind Dateien, die Visual Studio darüber informieren, wie die verschiedenen Dateitypen sinnvoll verarbeitet werden. Da diese Anpassungen projektweise angewendet werden, müssen Sie einfach nur die entsprechenden Anpassungen dem Projekt hinzufügen.

### <a name="to-add-the-build-customizations-to-your-project"></a>So fügen Sie die Buildanpassungen dem Projekt hinzu

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Buildabhängigkeiten** > **Buildanpassungen** aus.

   Das Dialogfeld **Buildanpassungsdateien in Visual C++** wird angezeigt.

2. Aktivieren Sie unter **Verfügbare Buildanpassungsdateien** die Kontrollkästchen für die in der folgenden Tabelle beschriebenen Ressourcentypen, die Sie im Projekt verwenden möchten:

    |Ressourcentyp|Name der Buildanpassung|
    |----------------| - |
    |Texturen und Bilder|**ImageContentTask(.targets, .props)**|
    |3D-Modelle|**MeshContentTask(.targets, .props)**|
    |Shader|**ShaderGraphContentTask(.targets, .props)**|

3. Klicken Sie auf die Schaltfläche **OK** .

## <a name="include-assets-in-your-build"></a>Integrieren der Objekte in den Build

Nachdem dem Projekt nun die verschiedenen Arten von 3D-Objekten mitgeteilt wurden, die Sie verwenden möchten, besteht der nächste Schritt darin, Informationen darüber zu liefern, welche Dateien 3D-Objekte sind und um welche Art von Objekten es sich handelt.

### <a name="to-add-an-asset-to-your-build"></a>So fügen Sie eine Ressource dem Build hinzu

1. Öffnen Sie im **Projektmappen-Explorer** in Ihrem Projekt das Kontextmenü für eine Ressource, und wählen Sie **Eigenschaften** aus.

   Das Dialogfeld **Eigenschaftenseite** für die Ressource wird angezeigt.

2. Stellen Sie sicher, dass die Eigenschaften **Konfiguration** und **Plattform** auf die Werte festgelegt werden, für die Ihre Änderungen gelten sollen.

3. Wählen Sie unter **Konfigurationseigenschaften** die Option **Allgemein** aus. Legen Sie dann im Eigenschaftenraster unter **Allgemein** die Eigenschaft **Elementtyp** auf den entsprechenden Inhaltspipeline-Elementtyp fest. Wählen Sie z.B. für eine Bild- oder Texturdatei **Pipeline für Bildinhalte** aus.

    > [!IMPORTANT]
    > Standardmäßig geht Visual Studio davon aus, dass viele unterschiedliche Bilddateitypen anhand des Elementtyps **Bild** kategorisiert werden sollen, der in Visual Studio integriert ist. Deshalb müssen Sie die Eigenschaft **Elementtyp** jedes Bilds ändern, das durch die Bildinhaltspipeline verarbeitet werden soll. Für andere Typen von Quelldateien der Inhaltspipeline für 3D-Modelle und visuelle Shadergrafiken wird standardmäßig der richtige **Elementtyp** vorgeschlagen.

4. Klicken Sie auf die Schaltfläche **OK** .

Nachstehend sind die drei Elementtypen für die Inhaltspipeline und ihre zugeordneten Quell- und Ausgabedateitypen aufgeführt.

|Elementtyp|Typen der Quelldatei|Format der Ausgabedatei|
|---------------| - | - |
|**Bildinhaltspipeline**|Portable Network Graphics ( *.png* )<br /><br /> JPEG ( *.jpg* , *.jpeg* , *.jpe* , *.jfif* )<br /><br /> Direct Draw Surface ( *.dds* )<br /><br /> Graphics Interchange Format ( *.gif* )<br /><br /> Bitmap ( *.bmp* , *.dib* )<br /><br /> Tagged Image File Format ( *.tif* , *.tiff* )<br /><br /> Targa ( *.tga* )|DirectDraw Surface ( *.dds* )|
|**Meshinhaltspipeline**|AutoDesk FBX-Austauschdatei ( *.fbx* )<br /><br /> Collada DAE-Datei ( *.dae* )<br /><br /> Wavefront OBJ-Datei ( *.obj* )|3D-Mesh-Datei ( *.cmo* )|
|**Shaderinhaltspipeline**|Visual Shader-Diagramm ( *.dgsl* )|Compiled Shader Output ( *.cso* )|

## <a name="configure-asset-content-pipeline-properties"></a>Konfigurieren der Eigenschaften von Objektinhaltspipelines

Sie können die Eigenschaften der Inhaltspipeline für jede Ressourcendatei festlegen, sodass diese auf eine bestimmte Weise erstellt wird.

### <a name="to-configure-content-pipeline-properties"></a>So konfigurieren Sie Inhaltspipelineeigenschaften

1. Öffnen Sie im **Projektmappen-Explorer** in Ihrem Projekt das Kontextmenü für die Ressourcendatei, und wählen Sie **Eigenschaften** aus.

   Das Dialogfeld **Eigenschaftenseite** für die Ressource wird angezeigt.

2. Stellen Sie sicher, dass die Eigenschaften **Konfiguration** und **Plattform** auf die Werte festgelegt werden, für die Ihre Änderungen gelten sollen.

3. Wählen Sie unter **Konfigurationseigenschaften** den Inhaltspipelineknoten aus (z.B. **Bildinhaltspipeline** für Textur- und Bildressourcen), und legen Sie dann im Eigenschaftenraster die Eigenschaften auf die entsprechenden Werte fest. Um beispielsweise Mipmaps für eine Texturressource zum Zeitpunkt der Erstellung zu generieren, legen Sie die Eigenschaft **MIPS generieren** auf **Ja** fest.

4. Klicken Sie auf die Schaltfläche **OK** .

### <a name="image-content-pipeline-configuration"></a>Konfiguration der Bildinhaltspipeline

Wenn Sie zur Erstellung einer Texturressource das Tool für Bildinhaltspipelines verwenden, können Sie die Textur auf verschiedene Arten komprimieren. Und Sie können angeben, ob MIP-Ebenen zum Zeitpunkt der Erstellung generiert werden sollen, und den Namen der Ausgabedatei angeben.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Komprimieren**|Gibt den Komprimierungstyp an, der für die Ausgabedatei verwendet wird.<br /><br /> Verfügbare Optionen:<br /><br /> -   **Keine Komprimierung**<br />-   **BC1_UNORM-Komprimierung**<br />-   **BC1_UNORM_SRGB-Komprimierung**<br />-   **BC2_UNORM-Komprimierung**<br />-   **BC2_UNORM_SRGB-Komprimierung**<br />-   **BC3_UNORM-Komprimierung**<br />-   **BC3_UNORM_SRGB-Komprimierung**<br />-   **BC4_UNORM-Komprimierung**<br />-   **BC4_SNORM-Komprimierung**<br />-   **BC5_UNORM-Komprimierung**<br />-   **BC5_SNORM-Komprimierung**<br />-   **BC6H_UF16-Komprimierung**<br />-   **BC6H_SF16-Komprimierung**<br />-   **BC7_UNORM-Komprimierung**<br />-   **BC7_UNORM_SRGB-Komprimierung**<br /><br /> Informationen darüber, welche Komprimierungsformate von den verschiedenen Versionen von DirectX unterstützt werden, finden Sie unter [Programmierhandbuch für DXGI](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews).|
|Konvertieren in ein vorab multipliziertes Alphaformat.|**Ja** , um das Bild in ein vorab multipliziertes Alphaformat in der Ausgabedatei zu konvertieren, andernfalls **Nein**. Nur die Ausgabedatei wird geändert, das Quellbild bleibt unverändert.|
|**MIPS generieren**|**Ja** , um eine vollständige MIP-Kette zum Zeitpunkt der Erstellung zu generieren und in die Ausgabedatei einzuschließen; andernfalls **Nein**. Falls Sie **Nein** auswählen und die Quelldatei bereits eine Mipmap-Kette enthält, verfügt die Ausgabedatei über eine MIP-Kette; andernfalls hat die Ausgabedatei keine MIP-Kette.|
|**Inhaltsausgabe**|Gibt den Namen der Ausgabedatei an. **Wichtig:** Das Ändern des Ausgabedateisuffixes hat keine Auswirkungen auf das Dateiformat.|

### <a name="mesh-content-pipeline-configuration"></a>Konfiguration der Mesh-Inhaltspipeline

Wenn Sie das Tool für Mesh-Inhaltspipelines verwenden, um eine Meshressource zu erstellen, können Sie den Namen der Ausgabedatei ändern.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Inhaltsausgabe**|Gibt den Namen der Ausgabedatei an. **Wichtig:** Das Ändern des Ausgabedateisuffixes hat keine Auswirkungen auf das Dateiformat.|

### <a name="shader-content-pipeline-configuration"></a>Konfiguration der Shader-Inhaltspipeline

Wenn Sie das Tool für Shader-Inhaltspipelines verwenden, um eine Shader-Ressource zu erstellen, können Sie den Namen der Ausgabedatei ändern.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Inhaltsausgabe**|Gibt den Namen der Ausgabedatei an. **Wichtig:** Das Ändern des Ausgabedateisuffixes hat keine Auswirkungen auf das Dateiformat.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Laden und verwenden von 3D-Objekten zur Laufzeit

### <a name="use-textures-and-images"></a>Verwenden von Texturen und Bildern

Direct3D stellt Funktionen zum Erstellen von Texturressourcen bereit. In Direct3D 11 bietet die Dienstbibliothek D3DX11 zusätzliche Funktionen für das Erstellen von Texturressourcen und Ressourcenansichten direkt aus Bilddateien. Weitere Informationen über die Erstellung einer Texturressource in Direct3D 11 finden Sie unter [Texturen](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures). Weitere Informationen darüber, wie Sie die Bibliothek „D3DX11“ verwenden, um eine Texturressource oder Ressourcenansicht aus einer Bilddatei zu erstellen, finden Sie unter [Vorgehensweise: Initialisieren einer Textur aus einer Datei](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to).

### <a name="use-3d-models"></a>Verwenden von 3D-Modellen

Direct3D 11 bietet keine Funktionen für das Erstellen von Ressourcen aus 3D-Modellen. Stattdessen müssen Sie Code schreiben, der die 3D-Modelldatei liest sowie Vertex- und Indexpuffer erstellt, die das 3D-Modell und alle Ressourcen darstellen, die das Modell benötigt, z.B. Texturen oder Shader.

### <a name="use-shaders"></a>Verwenden von Shadern

Direct3D stellt Funktionen zum Erstellen von Shaderressourcen und deren Anbindung an die programmierbare Grafikpipeline bereit. Weitere Informationen über die Erstellung einer Shaderressource in Direct3D und ihre Anbindung an die Pipeline finden Sie unter [Programmierhandbuch für HLSL](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide).

In der programmierbaren Grafikpipeline muss jede Phase der Pipeline der nächsten Phase der Pipeline ein Ergebnis übergeben, das so formatiert ist, das es verstanden wird. Da der Shader-Designer nur Pixel-Shader erstellen kann, bedeutet dies, dass Ihre App sicherstellen muss, dass die Daten, die sie erhält, im erwarteten Format vorliegen. Einige programmierbare Shader-Phasen treten vor dem Pixel-Shader auf und führen geometrische Umwandlungen durch – darunter Vertex-Shader, Hull-Shader, Domain-Shader und Geometrie-Shader. Die nicht programmierbare Mosaikphase tritt ebenfalls vor dem Pixel-Shader auf. Unabhängig davon, welche dieser Phasen direkt vor dem Pixel-Shader stattfindet, muss sie ihr Ergebnis in diesem Format übergeben:

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

Abhängig von den Shader-Designer-Knoten, die Sie im Shader verwenden, müssen Sie möglicherweise auch zusätzliche Daten in einem Format entsprechend diesen Definitionen bereitstellen:

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Vorgehensweise: Erstellen einer Textur, die Mipmaps enthält](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Beschreibt, wie die Bildinhaltspipeline zum Exportieren einer Textur verwendet wird, die vorausberechnete Mipmaps enthält.|
|[Vorgehensweise: Exportieren einer Textur, in der integrierte Alphakanäle verwendet werden](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Beschreibt, wie die Bildinhaltspipeline zum Exportieren einer Textur verwendet wird, die prämultiplizierte Alphawerte enthält.|
|[Vorgehensweise: Exportieren einer Textur für die Verwendung mit Direct2D- oder JavaScript-Apps](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Beschreibt, wie die Bildinhaltspipeline zum Exportieren einer Textur verwendet wird, die in einer Direct2D- oder einer JavaScript-App verwendet werden kann.|
|[Arbeiten mit 3D-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Es werden die Bearbeitungstools, die Visual Studio zum Erstellen und Bearbeiten von 3D-Objekten bereitstellt, inklusive Texturen und Bildern, 3D Modellen sowie Shadern beschrieben.|
|[Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)|Das Exportieren eines Shaders vom Shader-Designer wird beschrieben.|
