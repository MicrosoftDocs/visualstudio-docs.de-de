---
title: Erstellen von Stubs für Komponententestmethoden
description: Lernen Sie, den Befehl „Komponententests erstellen“ zu verwenden, der die leichte Konfiguration von Testprojekten, Testklassen und des darin enthaltenen Testmethodenstubs ermöglicht.
ms.custom: SEO-VS-2020
ms.date: 04/24/2020
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9bdbd545a3509927dd13a800e22b9aaaab2cb2b
ms.sourcegitcommit: 4e28314dc2be59b4c5fd44545c0653f625e74489
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97756629"
---
# <a name="create-unit-test-method-stubs-from-code"></a>Erstellen von Stubs für Komponententestmethoden aus Code

Mit dem Befehl **Komponententests erstellen** werden Stubs für Komponententestmethoden erstellt. Diese Funktion ermöglicht die leichte Konfiguration von Testprojekten, Testklassen und des darin enthaltenen Testmethodenstubs.

::: moniker range="vs-2017"
> [!NOTE]
> Der Menübefehl **Komponententests erstellen** steht nur für C#-Code für .NET Framework (aber nicht für .NET Core oder .NET Standard) zur Verfügung.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Der Menübefehl **Komponententests erstellen** ist nur für C#-Code verfügbar.
::: moniker-end

Der Menübefehl **Komponententests erstellen** ist erweiterbar und kann zum Generieren von Tests für MSTest, MSTest V2, NUnit und xUnit verwendet werden.

## <a name="get-started"></a>Erste Schritte

Beginnen Sie, indem Sie eine Methode, einen Typ oder einen Namespace im Code-Editor im zu testenden Projekt auswählen, klicken Sie mit der rechten Maustaste auf diesen, und wählen Sie dann **Komponententests erstellen** aus. Das Dialogfeld **Komponententests erstellen** wird geöffnet. Dort können Sie konfigurieren, wie die Tests erstellt werden sollen.

![Verwenden des Befehls „Unittests erstellen“](media/createunittestcommand.png)

Wenn Sie keine Optionen für Frameworks für Komponententests für NUnit oder xUnit sehen, finden Sie weitere Informationen unter [Verwenden von Frameworks für Komponententests von Drittanbietern](#use-third-party-unit-test-frameworks).

## <a name="set-unit-test-traits"></a>Festlegen der Merkmale von Komponententests

Wenn Sie diese Tests im Rahmen des Testautomatisierungsprozesses ausführen möchten, ziehen Sie in Erwägung, den Test in einem anderen Testprojekt zu erstellen (die zweite Option ist das oben stehende Dialogfeld) und Merkmale für den Komponententest festzulegen. So können Sie diese Tests leichter als Teil der Continuous Integration- und Continuous Deployment-Pipeline ein- oder ausschließen. Sie können die Merkmale festlegen, indem Sie Metadaten direkt in den Unittest einfügen, wie unten dargestellt.

![Festlegen der Merkmale eines Unittests](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Verwenden von Frameworks für Komponententests von Drittanbietern

Installieren Sie eine der folgenden Testframeworkerweiterungen aus dem Visual Studio Marketplace, um automatisch Komponententests für NUnit oder xUnit zu generieren:

* [NUnit-Erweiterung für Testgeneratoren](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [xUnit.net-Erweiterung für Testgeneratoren](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Wann ist diese Funktion sinnvoll?

Verwenden Sie dieses Feature, wenn Sie Komponententests erstellen müssen, insbesondere wenn Sie vorhandenen Code testen, der wenig oder keine Testabdeckung und keine Dokumentation aufweist. Also dort, wo es sehr eingeschränkte oder gar keine Codespezifikationen gibt. Im Prinzip implementiert es einen Ansatz, der den [intelligenten Komponententests](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) ähnelt, die das beobachtete Verhalten des Codes charakterisieren.

Dieses Feature kann jedoch auch angewendet werden, wenn ein Entwickler Code schreibt und diesen anschließend nutzt, um Bootstraps für Komponententests auszuführen. Es kann sein, dass der Entwickler beim Codieren schnell einen Stub für Komponententestmethoden für einen bestimmten Codeteil erstellen möchte (mit einer entsprechenden Testklasse und einem entsprechenden Testprojekt).

## <a name="see-also"></a>Siehe auch

- [Creating unit test method stubs with "Create Unit Tests" (Erstellen von Stubs für Unittestmethoden mit "Unittests erstellen")](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Blogbeiträge zu Komponententests](https://devblogs.microsoft.com/devops/?s=unit+testing)
