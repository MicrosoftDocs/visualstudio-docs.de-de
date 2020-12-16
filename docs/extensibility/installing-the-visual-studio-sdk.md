---
title: Installieren des Visual Studio SDK | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Optionen zum Installieren des Visual Studio Software Development Kit einschließlich der Installation von Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edab24396f5a3ae5527b76a58db90c19796c4240
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487568"
---
# <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK

Das Visual Studio SDK (Software Development Kit) ist ein optionales Feature im Visual Studio-Setup. Sie können das VS SDK auch später installieren.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren des Visual Studio SDK im Rahmen einer Visual Studio-Installation

Wenn Sie das VS SDK in Ihre Visual Studio-Installation einbeziehen möchten, installieren Sie die Workload **Visual Studio-Erweiterungsentwicklung** unter **Andere Toolsets**. Durch diese Workload werden das Visual Studio SDK und die erforderlichen Voraussetzungen installiert. Sie können die Installation weiter optimieren, indem Sie Komponenten in der Ansicht **Zusammenfassung** aktivieren oder deaktivieren.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren des Visual Studio SDK nach der Installation von Visual Studio

Um das Visual Studio SDK nach Abschluss der Visual Studio-Installation zu installieren, führen Sie das Visual Studio-Installationsprogramm erneut aus und wählen die Workload **Visual Studio-Erweiterungsentwicklung** aus.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installieren des Visual Studio SDK aus einer Projektmappe

Wenn Sie eine Projektmappe mit einem Erweiterbarkeitsprojekt öffnen, ohne zuvor das VS SDK installiert zu haben, werden Sie von einem Dialogfeld **Fehlendes Feature installieren** aufgefordert, die Workload **Visual Studio-Erweiterungsentwicklung** zu installieren:

![Installieren der Erweiterungsentwicklung](../extensibility/media/install-extension-development.png "Installieren der Erweiterungsentwicklung")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installieren des Visual Studio SDK über die Befehlszeile

Wie bei jeder Visual Studio-Workload oder -Komponente können Sie auch die Workload **Visual Studio-Erweiterungsentwicklung** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) über die Befehlszeile installieren. Ausführliche Informationen zu den entsprechenden Befehlszeilenschaltern und allgemeine Anweisungen zum Ermitteln von Workload- oder Komponentenbezeichnern finden Sie unter [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).

Beachten Sie, dass Sie das Visual Studio-Installationsprogramm verwenden müssen, der mit der installierten Version von Visual Studio übereinstimmt. Wenn Sie z. B. Visual Studio Enterprise auf dem Computer installiert haben, müssen Sie das Visual Studio Enterprise-Installationsprogramm (*vs_enterprise.exe*) ausführen.
