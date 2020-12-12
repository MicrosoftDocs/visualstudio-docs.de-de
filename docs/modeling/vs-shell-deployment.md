---
title: VS Shell-Bereitstellung
description: Erfahren Sie, wie eine isolierte Shell Ihnen ermöglicht, zu bestimmen, welche Visual Studio-Funktionalität Sie benötigen, um mit ihrer DSL zu interagieren und wie diese Lösung angezeigt werden sollte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361260"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung

Mithilfe einer isolierten Shell können Sie feststellen, welche Visual Studio-Funktionalität Sie benötigen, um mit ihrer domänenspezifischen Sprache zu interagieren und wie diese Lösung angezeigt werden soll. Weitere Informationen zur isolierten Visual Studio-Shell finden Sie unter [Anpassen der isolierten Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

So legen Sie eine Visual Studio-Shell als Bereitstellungs Ziel fest:

1. Öffnen Sie im **dslpackage** -Projekt **Source.Extension.tt**.

2. Unter `<SupportedProducts>` einfügen:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Ersetzen Sie *myisolatedshell* durch den Namen des isolierten shellpakets.