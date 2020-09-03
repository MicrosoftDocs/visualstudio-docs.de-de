---
title: BC-Texturkomprimierungsvariante | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0758d9eb5a003b0353ceb4fee21996d90685fa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161704"
---
# <a name="bc-texture-compression-variant"></a>BC-Texturkomprimierungsvariante
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aktiviert die Blockkomprimierung von Texturen mit einem Pixelformat, das eine Variation von B8G8R8X8, B8G8R8A8 oder R8G8B8A8 ist.  
  
## <a name="interpretation"></a>Interpretation  
 Blockkomprimierungsformate wie BC1, BC2 und BC3 belegen weitaus weniger Speicherplatz als unkomprimierte Bildformate und verbrauchen deshalb auch weniger Speicherbandbreite. Verglichen mit einem unkomprimierten Format, das 32 Bit pro Pixel verwendet, erreicht BC1 (zuvor bekannt als DXT1) eine Komprimierung von 8:1 und BC3 (zuvor bekannt als DXT5) 4:1. Der Unterschied zwischen BC1 und BC3 ist, dass BC1 keinen Alpha-Kanal unterstützt, während BC3 einen blockkomprimierten Alpha-Kanal unterstützt. Trotz der hohen Komprimierungsverhältnisse wird bei normalen Texturen die Bildqualität nur wenig beeinträchtigt. Die Blockkomprimierung bestimmter Texturarten – z. B. solcher mit größeren Farbvariationen in einem kleinen Bereich – kann zu nicht akzeptablen Ergebnissen führen.  
  
 Wenn Ihre Texturen für eine Blockkomprimierung geeignet sind und die Farben nicht perfekt wiedergegeben werden müssen, können Sie ein blockkomprimiertes Format verwenden, um den Speicherverbrauch zu reduzieren und weniger Bandbreite in Anspruch zu nehmen.  
  
## <a name="remarks"></a>Hinweise  
 Die Komprimierung von Texturen mit einem Blockkomprimierungsformat geschieht bei jedem Aufruf von `ID3DDevice::CreateTexture2D`, mit dem eine Quelltextur erstellt wird. Texturen werden vor allem in folgenden Fällen komprimiert:  
  
- Das in `D3D11_TEXTURE2D_DESC` übergebene `pDesc`-Objekt beschreibt eine nicht geänderte Shaderressource. Das bedeutet:  
  
  - Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_RESOURCE gesetzt.  
  
  - Das Usage-Member ist entweder auf D3D11_USAGE_DEFAULT oder auf D3D11_USAGE_IMMUTABLE gesetzt.  
  
  - Das CPUAccessFlags-Member ist auf 0 (kein Zugriff auf die CPU) gesetzt.  
  
  - Das Count-Member des SamplerDesc-Members ist auf 1 (kein Multi-Sample Anti-Aliasing (MSAA)) gesetzt.  
  
- Die ursprünglichen Daten werden beim Aufruf von `CreateTexture2D` bereitgestellt.  
  
  Im Folgenden finden Sie die unterstützten Quellformate und die entsprechenden Blockkomprimierungsformate.  
  
|Originalformat (aus)|Komprimiertes Format (in)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (früher DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (früher DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 Wenn Ihre Textur ein nicht aufgeführtes Format hat, wird sie nicht verändert.  
  
## <a name="restrictions-and-limitations"></a>Einschränkungen  
 Manchmal verwenden Texturen, die mit einer Variation des Bildformats B8G8R8A8 oder R8G8B8A8 erstellt werden, den Alpha-Kanal nicht, aber für die Variante gibt es keinen Weg, zu erkennen, ob der Kanal verwendet wird oder nicht. Um die korrekte Ausführung sicherzustellen, falls der Alpha-Kanal verwendet wird, kodiert die Variante diese Formate immer in das weniger effizientere BC3-Format. Sie können dafür sorgen, dass die Grafikframe-Analyse die potentielle Renderingleistung Ihrer App mit dieser Variation besser versteht, indem Sie eine Variante des Bildformats B8G8R8X8 verwenden (wenn Sie nicht den Alpha-Kanal verwenden), sodass die Variante das effizientere Format BC1 verwenden kann.  
  
## <a name="example"></a>Beispiel  
 Diese Variante blockkomprimiert Texturen zur Laufzeit vor dem Aufruf von `CreateTexture2D`. Wir empfehlen bei diesem Ansatz die Verwendung eines Produktionscodes, da die unkomprimierten Texturen mehr Speicherplatz verbrauchen und der zusätzliche Schritt die Ladezeiten in Ihrer App bedeutend in die Länge ziehen kann, da die Blockkomprimierung zur Kodierung beträchtliche Computerressourcen erfordert. Wir empfehlen, Ihre Texturen stattdessen mithilfe eines Bildeditors oder Bildprozessors, der Teil Ihrer Erstellungspipeline ist, offline zu komprimieren. Diese Ansätze reduzieren die Speicheranforderungen, eliminieren den Laufzeit-Overhead in Ihrer App und wenden mehre Bearbeitungszeit auf, sodass Sie die beste Bildqualität erreichen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Halb-/Viertel-Texturdimensionsvariante](../debugger/half-quarter-texture-dimensions-variant.md)
