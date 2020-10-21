---
title: Unterstützte Visual Studio-Editionen für Visualisierungs-und Modellierungs-SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 908a224feb9f6ad463ae14812b3a8550bf932e35
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "92298558"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Unterstützte Visual Studio-Versionen für das Visualisierungs- und Modellierungs-SDK

Im folgenden finden Sie Listen der Visual Studio-Editionen, die von [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in den Erstellungs-und Bereitstellungs Umgebungen unterstützt werden. Weitere Informationen zu diesen Editionen finden Sie im Microsoft Visual Studio [Developer Center](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Erstellungsedition

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|Produkt|Downloadlink|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Bereitstellungseditionen

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] von werden die folgenden Konfigurationen für die Bereitstellung der domänenspezifischen Sprachen unterstützt, die Sie erstellen:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrierter Modus), verteilbares Paket

- Visual Studio Shell (isolierter Modus), verteilbares Paket

> [!NOTE]
> Damit eine DSL in einem shellprodukt ausgeführt werden kann, müssen Sie das **unterstützte vs Edition** -Feld im Erweiterungs Manifest festlegen. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Weitere Informationen

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))