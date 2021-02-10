---
title: Verwenden von Visual Studio auf einem virtuellen Azure-Computer
titleSuffix: ''
description: Erfahren Sie, wie Visual Studio auf einem virtuellen Azure-Computer verwendet wird
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7111c53a498fe10710ec2b328600052a7d4de0cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935637"
---
# <a name="visual-studio-images-on-azure"></a><a id="top"> </a> Visual Studio-Images in Azure

Die Verwendung von Visual Studio in einem vorkonfigurierten virtuellen Azure-Computer (VM) ist eine einfache, schnelle Möglichkeit, von Null zu einer ausführbereiten Entwicklungsumgebung zu gelangen. Systemimages mit verschiedenen Visual Studio-Konfigurationen sind im [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure) verfügbar.

Neu bei Azure? [Kostenloses Azure-Konto erstellen](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Welche Konfigurationen und Versionen sind verfügbar?

Images für die letzten Hauptversionen, Visual Studio 2019 und Visual Studio 2017 und Visual Studio 2015, finden Sie im Azure Marketplace.  Für jede veröffentlichte Hauptversion werden die ursprünglich im Web veröffentlichte Version (released to web, RTW) und die letzten aktualisierten Versionen aufgeführt.  Jede dieser Versionen bietet die Editionen „Visual Studio Enterprise“ und „Visual Studio Community“.  Diese Images werden mindestens einmal monatlich aktualisiert, um die neuesten Visual Studio- und Windows-Updates einzuschließen.  Jede Imagebeschreibung enthält die Produktinstallationsversion und das Erstellungsdatum des Image, während die Namen der Images unverändert bleiben.

| Releaseversion                                                                                                                                          | Editionen              |    Produktversion    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------:|:-----------------------:|
| [Visual Studio 2019: Neueste Version (Version 16.8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | Version 16.8.0    |
| [Visual Studio 2019: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Enterprise            | Version 16.0.20    |
| [Visual Studio 2017: Aktuellste Version (Version 15.9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | Version 15.9.29   |
| [Visual Studio 2017: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, Community | Version 15.0.28   |
| [Visual Studio 2015: Aktuellste Version (Update 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | Version 14.0.25431.01 |

> [!NOTE]
> Im Einklang mit der Microsoft-Wartungsrichtlinie ist die ursprünglich veröffentlichte Version („RTW“) von Visual Studio 2015 für die Wartung abgelaufen. Visual Studio 2015 Update 3 ist die einzige verbleibende Version, die für die Visual Studio 2015-Produktlinie angeboten wird.

Weitere Informationen finden Sie in der [Visual Studio-Wartungsrichtlinie](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Welche Features werden installiert?

Jedes Image enthält die empfohlenen Features für diese Edition von Visual Studio. Im Allgemeinen umfasst die Installation:

* Alle verfügbaren Workloads, einschließlich der jeweils empfohlenen optionalen Komponenten für eine Workload
* SDKs, unterstützte Pakete und Entwicklertools für .NET 4.6.2 und .NET 4.7
* Visual F#
* GitHub-Erweiterung für Visual Studio
* LINQ zu SQL-Tools

Wir verwenden beim Erstellen der Images folgende Befehlszeile zum Installieren von Visual Studio:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Wenn die Images ein Visual Studio-Feature nicht enthalten, das Sie benötigen, geben Sie uns entsprechendes Feedback mithilfe des Feedbacktools in der oberen rechten Ecke der Seite.

## <a name="what-size-vm-should-i-choose"></a>Welche VM-Größe sollte ich auswählen?

Azure bietet eine umfassende Palette von Größen für virtuelle Computer. Da Visual Studio eine leistungsstarke Multithread-Anwendung ist, sollten Sie eine Größe für den virtuellen Computer auswählen, die mindestens zwei Prozessoren und 7 GB Arbeitsspeicher umfasst. Für Visual Studio-Images werden folgende Größen für virtuelle Computer empfohlen:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

Weitere Informationen zu den aktuellen VM-Größen finden Sie unter [Größen für virtuelle Windows-Computer in Azure](/azure/virtual-machines/windows/sizes).

Mit Azure können Sie die Größe des virtuellen Computers ändern, um einen erneuten Abgleich Ihrer ursprünglichen Wahl vorzunehmen. Sie können einen neuen virtuellen Computer mit einer besser geeigneten Größe bereitstellen oder die Größe des vorhandenen virtuellen Computers an verschiedene zugrunde liegende Hardware anpassen. Weitere Informationen finden Sie unter [Ändern der Größe eines virtuellen Windows-Computers](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Wie geht es weiter, wenn der virtuelle Computer ausgeführt wird?

Visual Studio folgt in Azure dem Modell „Verwendung Ihrer eigenen Lizenz“. Wie bei einer Installation auf proprietärer Hardware besteht einer der ersten Schritte in der Lizenzierung Ihrer Visual Studio-Installation. Visual Studio lässt sich mit einer der folgenden Methoden entsperren:
- Anmelden mit einem Microsoft-Konto, das einem Visual Studio-Abonnement zugeordnet ist
- Entsperren von Visual Studio mit den Product Key, den Sie bei Ihren ursprünglichen Kauf erhalten haben

Weitere Informationen finden Sie unter [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md) und [Entsperren von Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Wie wird der virtuelle Entwicklungscomputer zur späteren Verwendung oder zur Verwendung durch das Team gespeichert?

Das Spektrum der Entwicklungsumgebungen ist unüberschaubar, und für den Ausbau einer komplexeren Umgebung fallen hohe Kosten an. Unabhängig von der Konfiguration Ihrer Umgebung können Sie Ihren konfigurierten virtuellen Computer als „Basisimage“ zur späteren Verwendung oder für andere Mitglieder Ihres Teams speichern oder erfassen. Sie stellen dann einen neuen virtuellen Computer beim Starten vom Basisimage bereit und nicht vom Azure Marketplace-Image.

Kurze Zusammenfassung: Verwenden Sie das Tool für die Systemvorbereitung (Sysprep), und fahren Sie die ausgeführte VM herunter. Erfassen Sie die VM *(Abbildung 1)* anschließend über die Benutzeroberfläche des Azure-Portals als Image. Azure speichert die Datei `.vhd` mit dem Image im Speicherkonto Ihrer Wahl. Anschließend wird das neue Image als Imageressource in der Ressourcenliste Ihres Abonnements angezeigt.

![Erfassen eines Images über die Benutzeroberfläche des Azure-Portals](media/capture-vm.png)

*(Abbildung 1) Erfassen eines Images über die Benutzeroberfläche des Azure-Portals*

Weitere Informationen finden Sie unter [Erstellen eines verwalteten Images eines generalisierten virtuellen Computers in Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Vergessen Sie nicht, den virtuellen Computer mithilfe von Sysprep vorzubereiten. Wenn Sie diesen Schritt auslassen, kann Azure keinen virtuellen Computer aus dem Image bereitstellen.

> [!NOTE]
> Für das Speichern der Images können weiterhin gewisse Kosten anfassen, diese inkrementellen Kosten fallen jedoch im Vergleich zu den Gemeinkosten für die Neuerstellung eines virtuellen Computers von Grund auf – für jedes Teammitglied, der einen benötigt – wahrscheinlich nicht ins Gewicht. Beispielsweise kostet es wenige Euro, ein Image von 127 GB zu erstellen und einen Monat lang zu speichern, das von Ihrem gesamten Team wiederverwendet werden kann. Diese Kosten sind jedoch im Vergleich zu den Stunden, die jeder Mitarbeiter für das Ausbauen und Überprüfen einer ordnungsgemäß konfigurierten Entwicklungsumgebung für den eigenen Gebrauch investiert, geringfügig.

Darüber hinaus müssen Ihre Entwicklungsaufgaben oder Technologien möglicherweise weiter skaliert werden, etwa in Form von Varianten von Entwicklungskonfigurationen oder der Konfiguration mehrerer Computer. Mit Azure DevTest Labs können Sie _Rezepte_ erstellen, welche die Erstellung eines für Ihre Zwecke optimierten Images („Golden Image“) automatisieren. Außerdem können Sie mit DevTest Labs Richtlinien für die ausgeführten virtuellen Computer Ihres Teams verwalten. [Verwenden von Azure DevTest Labs für Entwickler](/azure/devtest-lab/devtest-lab-developer-lab) ist die beste Quelle für weitere Informationen zu DevTest Labs.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie sich mit vorkonfigurierten Visual Studio-Images beschäftigt haben, besteht der nächste Schritt im Erstellen eines neuen virtuellen Computers:

* [Erstellen eines virtuellen Computers über das Azure-Portal](/azure/virtual-machines/windows/quick-create-portal)
* [Übersicht über virtuelle Windows-Computer](/azure/virtual-machines/windows/overview)
