---
title: 0x-2x-4x-MSAA-Varianten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e77c0d7b5cbba2faf73fcca85ffcd0db063d618e
ms.sourcegitcommit: 023f52f10fb91850824558478cbfd2ec965054f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94407548"
---
# <a name="0x2x4x-msaa-variants"></a>0x/2x/4x-MSAA-Varianten
Überschreibt die Multi-Sample Anti-Aliasing (MSAA)-Einstellungen auf allen Renderzielen und Swapketten.

## <a name="interpretation"></a>Interpretation
 Das Multi-Sample Anti-Aliasing erhöht die visuelle Qualität durch Entnahme von Proben an mehreren Stellen in jedem Pixel; für höhere Ebenen des MSAA werden mehr Proben benötigt, und ohne das MSAA wird nur eine Probe aus der Mitte des Pixels entnommen. Die Aktivierung des MSAA in Ihrer App hat einen moderaten, aber bemerkbaren Einfluss auf die Renderingleistung, aber unter bestimmten Arbeitsbedingungen oder auf bestimmten GPUs hat es praktisch keine Auswirkung.

 Wenn das MSAA in Ihrer App bereits aktiviert ist, dann zeigen die kleineren MSAA-Varianten die relative Leistung an, die vom vorhandenen MSAA der höheren Ebene erbracht wird. Insbesondere zeigt die Variante 0x MSAA die relative Leistung Ihrer App ohne MSAA an.

 Wenn das MSAA auf Ihrer App nicht bereits aktualisiert ist, dann zeigen die Varianten 2x MSAA und 4x MSAA die relative Auswirkung einer Aktivierung in Ihrer App auf die Leistung an. Wenn die Auswirkung in akzeptabler Weise niedrig ist, können Sie MSAA aktivieren, um die Bildqualität ihrer App zu steigern.

> [!NOTE]
> Ihre Hardware unterstützt MSAA eventuell nicht vollständig für alle Formate. Wenn für eine dieser Varianten eine Hardwarebeschränkung gilt, die nicht umgangen werden kann, wird die entsprechende Spalte in der Leistungszusammenfassungstabelle leer gelassen und eine Fehlermeldung ausgegeben.

## <a name="remarks"></a>Hinweise
 Diese Varianten überschreiben die Samplinganzahl- und die Samplingqualitäts-Argumente auf Aufrufen von `ID3DDevice::CreateTexture2D`, die Renderziele erstellen. Diese Parameter werden insbesondere überschrieben, wenn:

- Das in `D3D11_TEXTURE2D_DESC` übergebene `pDesc`-Objekt ein Renderziel mit folgenden Eigenschaften beschreibt:

  - Für das BindFlags-Member ist entweder das Flag D3D11_BIND_TARGET oder das Flag D3D11_BIND_DEPTH_STENCIL gesetzt.

  - Das Usage-Member ist auf D3D11_USAGE_DEFAULT gesetzt.

  - Das CPUAccessFlags-Member ist auf 0 gesetzt.

  - Das MipLevels-Member ist auf 1 gesetzt.

- Das Gerät unterstützt die angefragte Samplinganzahl (0, 2 oder 4) und Samplingqualität (0) für das angefragte Renderzielformat (Member D3D11_TEXTURE2D_DESC::Format), wie durch `ID3D11Device::CheckMultisampleQualityLevels` festgelegt.

  Wenn für das Member D3D11_TEXTURE2D_DESC::BindFlags das Flag D3D_BIND_SHADER_RESOURCE oder das Flag D3D11_BIND_UNORDERED_ACCESS gesetzt ist, werden zwei Versionen der Textur erstellt: In der ersten sind diese Flags für eine Verwendung als Renderziel gelöscht, und die zweite ist eine Nicht-MSAA-Textur, in der diese Flags intakt sind und die als Auflösungspuffer für die erste Version erstellt wird. Dies ist notwendig, da die Verwendung einer MSAA-Textur als Shaderressource oder für ungeordneten Zugriff wahrscheinlich nicht gültig ist - ein Shader, der auf sie einwirkt, würde unkorrekte Ergebnisse erzeugen, da er eine Nicht-MSAA-Textur erwarten würde. Wenn die Variante die sekundäre Nicht-MSAA-Textur erstellt hat, wird immer dann, wenn das MSAA-Renderziel aus dem Gerätekontext gelöst wird, sein Inhalt in die Nicht-MSAA-Textur aufgelöst. Auf ähnliche Weise wird, wenn das MSAA-Renderziel als Shaderressource gebunden werden sollte oder in einer Ansicht mit ungeordnetem Ziel verwendet wird, stattdessen die Nicht-MSAA-Textur gebunden.

  Diese Varianten überschreiben auch MSAA-Einstellungen auf allen durch Verwendung von `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition` und `ID3D11CreateDeviceAndSwapChain` erstellten Swapketten.

  Der Nettoeffekt dieser Änderungen ist, dass das gesamte Rendering in ein MSAA-Renderziel geht, aber wenn Ihre Anwendung eines dieser Renderziele oder einen dieser Swapketten-Puffer als Shaderressourcenansicht oder unsortierte Zugriffsansicht verwendet, dann werden die Daten aus der aufgelösten MSAA-Kopie des Renderziels gesampelt.

## <a name="restrictions-and-limitations"></a>Einschränkungen
 In Direct3D11 sind MSAA-Texturen mehr eingeschränkt als Nicht-MSAA-Texturen. Sie können z. B. `ID3D11DeviceContext::UpdateSubresource` nicht auf einer MSAA-Textur aufrufen, und der Aufruf von `ID3D11DeviceContext::CopySubresourceRegion` schlägt fehl, wenn die Samplinganzahl und die Samplingqualität der Quellressource und der Zielressource nicht übereinstimmen, was passieren kann, wenn die Variante die MSAA-Einstellungen einer, aber nicht der anderen Ressource überschreibt.

 Wenn bei der Wiedergabe diese Art von Konflikten erkannt wird, wird versucht, das beabsichtigte Verhalten zu replizieren, aber eventuell können nicht genau die gewünschten Ergebnisse erreicht werden. Obwohl die Leistung und die Wirkung dieser Varianten dadurch im Allgemeinen nicht beeinflusst werden, ist es möglich – z. B. wenn die Ablaufsteuerung in einem Pixelshader vom genauen Inhalt einer Textur bestimmt wird –, dass die replizierter Textur eventuell nicht den völlig gleichen Inhalt hat.

## <a name="example-1"></a>Beispiel 1
 Diese Varianten können für mit `ID3D11Device::CreateTexture2D` erstellte Renderziele mithilfe eines Codes, reproduziert werden, der dem folgenden ähnlich ist:

```cpp
D3D11_TEXTURE2D_DESC target_description;
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
target_description.SampleDesc.Quality = 0;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```

## <a name="example-2"></a>Beispiel 2
 Oder für Swapketten, die mit IDXGISwapChain::CreateSwapChain oder D3D11CreateDeviceAndSwapChain erstellt wurden, durch Verwendung eines Codes, der dem folgenden ähnlich ist:

```cpp
DXGI_SWAP_CHAIN_DESC chain_description;
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
chain_description.SampleDesc.Quality = 0;

// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.
```
