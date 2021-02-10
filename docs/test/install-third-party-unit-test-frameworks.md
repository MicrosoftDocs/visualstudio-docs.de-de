---
title: Installieren von Frameworks für Komponententests von Drittanbietern
description: Der Visual Studio-Test-Explorer kann Tests aus beliebigen Frameworks für Komponententests ausführen, für die eine Adapterschnittstelle entwickelt wurde.
ms.custom: SEO-VS-2020
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c59a9d9055dd6a5788eec4d4904d9ec41262dae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879500"
---
# <a name="install-unit-test-frameworks"></a>Installieren von Komponententestframeworks

Der Visual Studio-Test-Explorer kann Tests aus beliebigen Frameworks für Komponententests ausführen, für die eine Adapterschnittstelle entwickelt wurde. Beim Installieren des Frameworks werden die Binärdateien kopiert und die Visual Studio-Projektvorlagen für die unterstützten Sprachen werden hinzugefügt. Wenn Sie ein Projekt mit der Vorlage erstellen, wird das Framework beim Test-Explorer registriert.

Eine Visual Studio-Projektmappe kann Komponententestprojekte enthalten, die verschiedene Frameworks verwenden und verschiedene Zielsprachen aufweisen.

::: moniker range=">=vs-2019"
Für .NET sind [MSTest, NUnit und xUnit](getting-started-with-unit-testing.md) die von Visual Studio bereitgestellten und standardmäßig installierten Testframeworks. Für C++ werden andere Testframeworks bereitgestellt, z. B. CTest.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md) ist das Testframework von Visual Studio und wird standardmäßig installiert.
::: moniker-end

## <a name="acquire-frameworks"></a>Herunterladen von Frameworks

Installieren Sie Drittanbieterframeworks für Komponententests mithilfe des **NuGet-Paket-Managers**.

1. Klicken Sie mit der rechten Maustaste auf das Projekt, das Ihren Testcode enthalten soll, und wählen Sie die Option **NuGet-Pakete verwalten** aus.

2. Suchen Sie im **NuGet-Paket-Manager** nach dem Testframework, das Sie installieren möchten, und klicken Sie dann auf **Installieren**.

   ![NuGet-Paket-Manager in Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Aktualisieren auf die neuesten Testadapter

Aktualisieren Sie auf den neuesten stabilen Testadapter, um eine bessere Testermittlung und Ausführung zu erzielen. Weitere Informationen über Updates für MSTest-, NUnit- und xUnit-Testadapter finden Sie im [Visual Studio-Blog](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>So aktualisieren Sie auf die neueste stabile Testadapterversion

1. Öffnen Sie den NuGet-Paket-Manager für Ihre Projektmappe, indem Sie zu **Extras** > **NuGet-Paket-Manager** > **NuGet-Pakete für Projektmappe verwalten** navigieren.

2. Klicken Sie auf die Registerkarte **Updates**, und suchen Sie nach installierten MSTest-, NUnit- oder xUnit-Testadaptern.

3. Wählen Sie erst alle Testadapter und dann im Dropdownmenü die neueste stabile Version aus.

4. Wählen Sie die Schaltfläche **Installieren** aus.

   ![Aktualisieren des Testadapters](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
