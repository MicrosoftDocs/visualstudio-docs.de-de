---
title: 16 bpp-Renderzielformat-Variante | Microsoft-Dokumentation
description: Wenden Sie die 16 bpp-Renderzielformat-Variante an, indem Sie das Pixelformat für alle Renderziele und Hintergrundpuffer auf DXGI_FORMAT_B5G6R5_UNORM festlegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa73637244469d781ac77acba362886b5656f8d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728043"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp-Renderzielformat-Variante
Setzt das Pixelformat für alle Renderziele und Hintergrundpuffer auf DXGI_FORMAT_B5G6R5_UNORM.

## <a name="interpretation"></a>Interpretation
 Ein Renderziel oder ein Hintergrundpuffer verwendet normalerweise ein 32 bpp-Format (32 Bit pro Pixel) wie B8G8R8A8_UNORM. 32 bpp-Formate können eine große Menge an Speicherbandbreite in Anspruch nehmen. Da das Format B5G6R5_UNORM ein 16 bpp-Format ist, das die halbe Größe des 32 bpp-Formats aufweist, kann seine Verwendung den Druck auf die Speicherbandbreite verringern, dies jedoch zum Preis einer reduzierten Farbtreue.

 Wenn diese Variante zu einer Leistungssteigerung führt, kann dies ein Zeichen dafür sein, dass Ihre App zu viel Speicherbandbreite verbraucht. Sie können eine deutliche Leistungsverbesserung erzielen, insbesondere dann, wenn der profilierte Frame eine beträchtliche Menge an Überzeichnung oder Alphablending aufweist.

Ein 16 bpp-Renderzielformat kann die Auslastung der Speicherbandbreite verringern, wenn Ihre Anwendung die folgenden Bedingungen erfüllt:
- Erfordert keine High-Fidelity-Farbreproduktion.
- Erfordert keinen Alphakanal.
- Weist nur wenige glatte Farbverläufe auf (die anfällig für Bandingartefakte unter reduzierter Farbtreue sind).

Weitere Strategien zum Verringern der Speicherbandbreite sind:
- Verringern der Menge von Überzeichnung oder Alphablending
- Verringern der Größe des Framepuffers
- Verringern der Größe von Texturressourcen
- Verringern von Komprimierungen der Texturressourcen

Wie gewohnt müssen Sie die Kompromisse bei der Bildqualität bedenken, die mit jeder dieser Optimierungen einhergehen.

Anwendungen, die Teil einer Swapchain sind, weisen ein Hintergrundpufferformat (DXGI_FORMAT_B5G6R5_UNORM) auf, das 16 bpp nicht unterstützt. Diese Swapchains werden mithilfe von `D3D11CreateDeviceAndSwapChain` oder `IDXGIFactory::CreateSwapChain` erstellt. Führen Sie die folgenden Schritte aus, um diese Einschränkung zu umgehen:
1. Erstellen Sie ein Renderziel im Format B5G6R5_UNORM, indem Sie `CreateTexture2D` verwenden.
2. Kopieren Sie das Renderziel in den Hintergrundpuffer der Swapchain, indem Sie ein Quadrat über den kompletten Bildschirm mit dem Renderziel als Quelltextur zeichnen.
3. Rufen Sie Present in der Swapchain auf.

   Wenn diese Strategie mehr Bandbreite spart, als durch Kopieren des Renderziels in den Hintergrundpuffer der Swapchain beansprucht wird, verbessert dies die Renderingleistung.

   GPU-Architekturen, die gekachelte Renderingtechniken verwenden, können durch die Verwendung eines 16 bpp-Framepufferformats bedeutende Leistungsvorteile erzielen. Diese Verbesserung liegt daran, dass ein größerer Teil des Framepuffers in den lokalen Framepuffercache jeder Kachel passt. Kachel-Rendering-Architekturen sind manchmal in GPUs in mobilen Handsets und Tablet-Computern zu finden; außerhalb dieser Nische kommen sie selten vor.

## <a name="remarks"></a>Hinweise
 Das Renderzielfomat wird mit jedem Aufruf von `ID3D11Device::CreateTexture2D`, der ein Renderziel erstellt, auf DXGI_FORMAT_B5G6R5_UNORM zurückgesetzt. Vor allem wird das Format überschrieben, wenn das in pDesc übergebene D3D11_TEXTURE2D_DESC-Objekt eines der folgenden Renderziele beschreibt:

- Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_TARGET gesetzt.

- Für das BindFlags-Member ist das Flag D3D11_BIND_DEPTH_STENCIL gelöscht.

- Das Usage-Member ist auf D3D11_USAGE_DEFAULT gesetzt.

## <a name="restrictions-and-limitations"></a>Einschränkungen
 Da das Format B5G6R5 über keinen Alpha-Kanal verfügt, werden Alpha-Inhalte von dieser Variante nicht beibehalten. Wenn das Rendering Ihrer App einen Alpha-Kanal in Ihrem Renderziel erfordert, können Sie nicht einfach zum Format B5G6R5 wechseln.

## <a name="example"></a>Beispiel
 Die Variante **16 bpp-Renderzielformat** kann für Renderziele reproduziert werden, die mit `CreateTexture2D` unter Verwendung von Code ähnlich dem folgenden erstellt wurden:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
