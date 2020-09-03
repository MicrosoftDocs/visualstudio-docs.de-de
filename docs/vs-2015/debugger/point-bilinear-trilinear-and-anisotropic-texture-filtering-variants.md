---
title: Punkt-, bilineare, drei lineare und anisotrope Textur Filter Varianten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c53f3b0633ec8938de210cb518d9fae1937eb2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185403"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Überschreibt den Filterungsmodus auf passenden Textursamplern.  
  
## <a name="interpretation"></a>Interpretation  
 Verschiedene Textursampling-Methoden bringen verschiedene Leistungskosten und Bildqualitäten. Folgende Filtermodi sind mit steigenden Kosten und höherer Bildqualität verbunden:  
  
1. Punktfilterung (am günstigen, schlechteste visuelle Qualität)  
  
2. Bilineare Filterung  
  
3. Trilineare Filterung  
  
4. Anisotrope Filterung (am teuersten, höchste visuelle Qualität)  
  
   Wenn die Leistungskosten jeder Variante mit intensiveren Filterungsmodi deutlich steigen, können Sie die Kosten gegen die höhere Bildqualität abwägen. Anhand dieser Bewertung können Sie dann höhere Leistungskosten für eine höhere visuelle Qualität oder eine niedrigere visuelle Qualität für eine höhere Rahmenrate oder für eine Leistung, die auf andere Weise nicht zu erreichen ist, akzeptieren.  
  
   Wenn die Leistungskosten keine Rolle spielen oder unabhängig vom Filtermodus gleich bleiben – z. B., wenn die GPU, die Sie anzielen, einen redundant hohen Shader-Durchsatz und eine hohe Bandbreite hat –, können Sie die anisotrope Filterung verwenden, um die beste Bildqualität in Ihrer App zu erreichen.  
  
## <a name="remarks"></a>Hinweise  
 Diese Varianten überschreiben die Samplerstatus in Aufrufen von `ID3D11DeviceContext::PSSetSamplers`, in denen eine der folgenden Filtermethoden für den von der Anwendung bereitgestellten Sampler verwendet wird:  
  
- `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_ANISOTROPIC`  
  
  In der Variante **Punkttexturfilterung** wird der von der Anwendung bereitgestellte Filtermodus durch `D3D11_FILTER_MIN_MAG_MIP_POINT` ersetzt, in der Variante **Bilineare Texturfilterung** wird er durch `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` ersetzt, und in der Variante **Trilineare Texturfilterung** wird er durch `D3D11_FILTER_MIN_MAG_MIP_LINEAR` ersetzt.  
  
  In der **anisotropen Texturfilterung** wird der von der Anwendung bereitgestellte Filtermodus durch `D3D11_FILTER_ANISOTROPIC` ersetzt, und die maximale Anisotropie wird auf 16 gesetzt.  
  
## <a name="restrictions-and-limitations"></a>Einschränkungen  
 In Direct3D bedeutet die Funktionsebene 9.1 eine maximale Anisotropie von 2x. Da die Variante **Anisotrope Texturfilterung** versucht, die 16-fache Anisotropie exklusiv zu verwenden, ist die Wiedergabe nicht möglich, wenn die Frameanalyse auf einem Gerät mit dem Funktionslevel 9.1 durchgeführt wird. Zu den heutigen Geräten, die von dieser Einschränkung betroffen sind, gehören die ARM-basierten Windows-Tablets Surface RT und Surface 2. Ältere GPUs, die auf einigen Computern immer noch zu finden sind, können ebenso betroffen sein, aber dies gilt hauptsächlich für Computer, die als veraltet betrachtet werden und immer weniger in Gebrauch sind.  
  
## <a name="example"></a>Beispiel  
 Die Variante **Punkttexturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die Variante **Bilineare Texturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die Variante **Trilineare Texturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die Variante **Anisotrope Texturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```
