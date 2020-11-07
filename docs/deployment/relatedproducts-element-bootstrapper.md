---
title: '&lt;RelatedProducts- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
description: Mit dem RelatedProducts-Element werden andere Produkte definiert, die entweder von oder im aktuellen Produkt enthalten sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ac9f84fa22526ed03d7a2e9b201cc9afc2f476d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350568"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts- &gt; Element (Boots Trapper)
Mit dem- `RelatedProducts` Element werden andere Produkte definiert, die entweder von abhängen oder im aktuellen Produkt enthalten sind.

## <a name="syntax"></a>Syntax

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das- `RelatedProducts` Element ist ein untergeordnetes `Product` Element des-Elements. Sie besitzt keine Attribute.

## <a name="dependsonproduct"></a>DependsOnProduct
 Das `DependsOnProduct` -Element gibt an, dass das aktuelle Produkt vom benannten Produkt abhängt und dass das benannte Produkt vor dem aktuellen Produkt installiert werden sollte. Es ist ein untergeordnetes Element des- `RelatedProducts` Elements. Ein- `RelatedProducts` Element kann ein oder mehrere- `DependsOnProduct` Elemente aufweisen.

 `DependsOnProduct` weist das folgende Attribut auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Code`|Der Codename des enthaltenen Produkts, wie durch das- `ProductCode` Attribut des- `Product` Elements angegeben. Weitere Informationen finden Sie unter [\<Product>Element](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 Das `EitherProducts` -Element definiert NULL oder mehr `DependsOnProduct` -Elemente und weist keine Attribute auf. Mindestens eine `DependsOnProduct` in diesem Satz muss vor dem aktuellen Produkt installiert werden. Ein- `RelatedProducts` Element kann NULL oder mehr- `EitherProducts` Elemente aufweisen.

## <a name="includesproduct"></a>IncludesProduct
 Das `IncludesProduct` -Element gibt an, dass ein Produkt in der aktuellen Installation enthalten ist und keine separate Installation erfordert. Es ist ein untergeordnetes Element des- `RelatedProducts` Elements. Ein- `RelatedProducts` Element kann ein oder mehrere- `IncludesProduct` Elemente aufweisen.

 `IncludesProduct` weist das folgende Attribut auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Code`|Der Codename des enthaltenen Produkts, wie durch das- `ProductCode` Attribut des- `Product` Elements angegeben. Weitere Informationen finden Sie unter [\<Product>Element](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird angegeben, dass das Microsoft Installer mit dem .NET Framework installiert wird und daher keine separate Installation erforderlich ist.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Weitere Informationen
- [\<Product> gewisses](../deployment/product-element-bootstrapper.md)