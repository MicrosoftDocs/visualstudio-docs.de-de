---
title: Mipmap-Generierungsvariante | Microsoft-Dokumentation
description: Wenn die Mipmap-Generierung zu einer deutlichen Leistungssteigerung führt, zeigt dies an, dass Sie Texturen ohne Aktivierung von Mipmaps verwenden und den Texturcache nicht optimal nutzen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc2e377c0313fffda88bf14c0c7304ff084f3275
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904443"
---
# <a name="mip-map-generation-variant"></a>Mipmap-Generierungsvariante
Aktiviert Mipmaps auf Texturen, die keine Renderziele sind.

## <a name="interpretation"></a>Interpretation
Mipmaps werden hauptsächlich zur Eliminierung von Aliasing-Artefakten in Texturen verwendet, die gerade verkleinert werden, indem Sie kleinere Versionen der Textur vorausberechnen. Obwohl diese zusätzlichen Texturen GPU-Speicher verbrauchen – ca. 33 % mehr als die Originaltextur –, sind sie effizienter, da mehr von ihrem Oberflächenbereich in den GPU-Texturcache passt und ihre Inhalte eine höhere Verwendung erreichen.

Für 3D-Szenen empfehlen wir Mipmaps, wenn Speicher verfügbar ist, um die zusätzlichen Texturen zu speichern, da sie sowohl die Renderingleistung als auch die Bildqualität erhöhen.

Wenn diese Variante zu einer deutlichen Leistungssteigerung führt, zeigt dies an, dass Sie Texturen ohne Aktivierung von Mipmaps verwenden und deshalb den Texturcache nicht optimal nutzen.

## <a name="remarks"></a>Hinweise
Die Mipmap-Erzeugung wird bei jedem Aufruf von `ID3D11Device::CreateTexture2D` erzwungen, der eine Quelltextur erstellt. Die Mipmap-Erzeugung wird insbesondere dann erzwungen, wenn das in `pDesc` übergebene Objekt D3D11_TEXTURE2D_DESC eine nicht veränderliche Shaderressource beschreibt. Das bedeutet:

- Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_RESOURCE gesetzt.

- Das Usage-Member ist entweder auf D3D11_USAGE_DEFAULT oder auf D3D11_USAGE_IMMUTABLE gesetzt.

- Das CPUAccessFlags-Member ist auf 0 (kein Zugriff auf die CPU) gesetzt.

- Das Count-Member des SampleDesc-Members ist auf 1 (kein Multi-Sample Anti-Aliasing (MSAA)) gesetzt.

- Das MipLevels-Member ist auf 1 (keine existierende Mipmap) gesetzt.

  Wenn die Anwendung die ursprünglichen Daten ausgibt, muss das Texturformat – wie durch D3D11_FORMAT_SUPPORT_MIP_AUTOGEN festgelegt – die automatische Mipmap-Erzeugung unterstützen, außer wenn das Format BC1, BC2 oder BC3 ist; andernfalls wird die Textur nicht verändert, und bei Ausgabe der ursprünglichen Daten werden keine Mipmaps erzeugt.

  Wenn Mipmaps für eine Textur automatisch erzeugt worden sind, werden Aufrufe von `ID3D11Device::CreateShaderResourceView` während der Wiedergabe modifiziert, um während des Textursamplings die Mip-Kette zu verwenden.

## <a name="example"></a>Beispiel
Die Variante **Mipmap-Erzeugung** lässt sich durch Verwendung eines ähnlichen Codes wie dem folgenden reproduzieren:

```cpp
D3D11_TEXTURE2D_DESC texture_description;

// ...

texture_description.MipLevels = 0; // generate a full mipchain

std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);

for (auto&& mip_level : initial_data)
{
    // fill mip_level with the application-supplied initial data
}

d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)
```

Wenn Sie eine Textur mit einer vollständigen Mip-Kette erstellen möchten, setzen Sie `D3D11_TEXTURE2D_DESC::MipLevels` auf 0. Die Anzahl der Mip-Ebenen in einer vollständigen Mip-Kette ist floor(log2(n) + 1), wobei n die größte Dimension der Textur ist.

Bitte bedenken Sie, dass bei einer Bereitstellung der ursprünglichen Daten auf `CreateTexture2D` ein D3D11_SUBRESOURCE_DATA-Objekt für jede Mip-Ebene erstellt werden muss.

> [!NOTE]
> Wenn Sie Ihre eigenen Inhalte auf Mip-Ebene bereitstellen möchten, anstatt sie automatisch zu erzeugen, müssen Sie Ihre Texturen mithilfe eines Bildeditors erstellen, der Mipmap-Texturen unterstützt, und dann die Datei laden und die Mip-Ebenen an `CreateTexture2D` übergeben.

## <a name="see-also"></a>Siehe auch
[Halb-/Viertel-Texturdimensionsvariante](half-quarter-texture-dimensions-variant.md)
