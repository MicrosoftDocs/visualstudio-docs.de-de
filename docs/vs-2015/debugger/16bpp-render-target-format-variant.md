---
title: 16 bpp-Renderzielformat-Variante | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b315c7ab9bb10d039e81ba26b1beb9c4447a205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157570"
---
# <a name="16bpp-render-target-format-variant"></a>16bpp-Renderzielformat-Variante
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Setzt das Pixelformat für alle Renderziele und Hintergrundpuffer auf DXGI_FORMAT_B5G6R5_UNORM.  
  
## <a name="interpretation"></a>Interpretation  
 Ein Renderziel oder ein Hintergrundpuffer verwendet ein 32bpp (Bits per Pixel)-Format wie B8G8R8A8_UNORM. 32bpp-Formate können eine Menge Speicherbandbreite in Anspruch nehmen. Da das Format B5G6R5_UNORM ein 16bpp-Format ist, das die halbe Größe des 32bpp-Formats hat, kann seine Verwendung den Druck von der Speicherbandbreite nehmen, aber dies um den Preis reduzierter Farbtreue.  
  
 Wenn diese Variante zu einer Leistungssteigerung führt, kann dies ein Zeichen dafür sein, dass Ihre App zu viel Speicherbandbreite verbraucht. Leistungssteigerungen können besonders betont werden, wenn der profilierte Rahmen unter einer deutlichen Überzeichnung leidet oder eine Menge Alphablendings enthält.  
  
 Wenn die Arten von Szenen, die durch Ihre App dargestellt werden, keine Wiedergabe mit hoher Farbtreue erfordern, muss das Renderziel nicht über einen Alpha-Kanal verfügen und enthält häufig keine weichen Gradienten – die anfällig für das Banding von Artefakten unter reduzierter Farbtreue sind. Also können Sie ein 16bpp-Renderzielformat verwenden, um den Speicherbandbreitenverbrauch zu senken.  
  
 Wenn die Szenen, die durch Ihre App gerendert werden, eine Wiedergabe mit hoher Farbtreue oder einen Alpha-Kanal erfordern oder wenn weiche Gradienten gelten, bedenken Sie andere Strategien zur Reduzierung der Bandbreitennutzung – z. B. reduziertes Überzeichnen oder Alphablending, Reduzierung der Größe des Framepuffers oder Modifikation von Texturressourcen, um weniger Speicherbandbreite zu verbrauchen, indem Sie eine Komprimierung aktivieren oder ihre Größen reduzieren. Wie gewohnt müssen Sie die Kompromisse bei der Bildqualität bedenken, die mit jeder dieser Optimierungen einhergehen.  
  
 Wenn Ihre App von einem Umschalten auf einen 16bpp-Hintergrundpuffer profitiert, aber Teil Ihrer Swapkette ist, müssen Sie zusätzliche Schritte ausführen, da DXGI_FORMAT_B5G6R5_UNORM kein unterstütztes Hintergrundpufferformat für Swapketten ist, die mit `D3D11CreateDeviceAndSwapChain` oder `IDXGIFactory::CreateSwapChain` erstellt wurden. Stattdessen müssen Sie ein Renderziel im Format B5G6R5_UNORM erstellen, indem Sie `CreateTexture2D` verwenden. Kopieren Sie dann, bevor Sie "Vorhanden" auf Ihrer Swapkette aufrufen, das Renderziel in den Hintergrundpuffer der Swapkette, indem Sie ein Quadrat über den kompletten Bildschirm mit dem Renderziel als Quelltextur zeichnen. Obwohl dies ein zusätzlicher Schritt ist, der eine gewisse Speicherbandbreite beansprucht, verbrauchen die meisten Renderingvorgänge weniger Bandbreite, da Sie sich auf das 16bpp renderzielformat-Renderziel auswirken Wenn dadurch mehr Bandbreite eingespart wird, als durch Kopieren des Renderziels in den Hintergrund Puffer der Austausch Kette verbraucht wird, wird die Renderingleistung verbessert.  
  
 GPU-Architekturen, die Kachel-Rendering-Techniken verwenden, können große Leistungssteigerungen erfahren, wenn Sie ein 16bpp-Framepuffer-Format verwenden, da ein größerer Teil des Framepuffers in den lokalen Framepuffer-Cache jeder Kachel passt. Kachel-Rendering-Architekturen sind manchmal in GPUs in mobilen Handsets und Tablet-Computern zu finden; außerhalb dieser Nische kommen sie selten vor.  
  
## <a name="remarks"></a>Hinweise  
 Das Renderzielfomat wird mit jedem Aufruf von `ID3D11Device::CreateTexture2D`, der ein Renderziel erstellt, auf DXGI_FORMAT_B5G6R5_UNORM zurückgesetzt. Vor allem wird das Format überschrieben, wenn das in pDesc übergebene D3D11_TEXTURE2D_DESC-Objekt eines der folgenden Renderziele beschreibt:  
  
- Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_TARGET gesetzt.  
  
- Für das BindFlags-Member ist das Flag D3D11_BIND_DEPTH_STENCIL gelöscht.  
  
- Das Usage-Member ist auf D3D11_USAGE_DEFAULT gesetzt.  
  
## <a name="restrictions-and-limitations"></a>Einschränkungen  
 Da das Format B5G6R5 über keinen Alpha-Kanal verfügt, werden Alpha-Inhalte von dieser Variante nicht beibehalten. Wenn das Rendering Ihrer App einen Alpha-Kanal in Ihrem Renderziel erfordert, können Sie nicht einfach zum Format B5G6R5 wechseln.  
  
## <a name="example"></a>Beispiel  
 Die Variante **16bpp renderzielformat-renderzielformat** kann für Renderziele, die mithilfe von erstellt wurden, mithilfe `CreateTexture2D` von Code wie dem folgenden reproduziert werden:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
