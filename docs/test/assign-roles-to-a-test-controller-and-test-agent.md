---
title: Testcontroller- und Test-Agent-Rollen
description: Lernen Sie, eine Testeinstellung zu erstellen und zu konfigurieren, in der mithilfe eines Testcontrollers und eines Test-Agents Tests auf mehrere Computer verteilt werden, die Visual Studio verwenden.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 163cb3d541b054d22dc46df0b8e1e4735ac3fd50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964666"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Zuweisen von Rollen an einen Testcontroller und einen Test-Agent

In diesem Artikel werden außerdem die Erstellung und Konfiguration einer Testeinstellung veranschaulicht, in der mithilfe eines Testcontrollers und eines Test-Agents Tests auf mehrere Computern verteilt werden, die Visual Studio verwenden. Darüber hinaus wird erläutert, wie der Testeinstellung Diagnose- und Datenadapter hinzugefügt werden.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Voraussetzungen

- Erstellen Sie Komponententests oder Tests der codierten UI, die mit der Testeinstellung ausgeführt werden.

- Installieren Sie einen Testcontroller und Test-Agents. Weitere Informationen zum Installieren eines Testcontrollers und von Test-Agents finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>So erstellen und konfigurieren Sie eine Testeinstellung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Projektmappenelemente**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie im Bereich **Installierte Vorlagen** die Option **Testeinstellungen** aus.

3. Geben Sie im Feld **Name** den Namen **TestSettingDistributedTestWalkthrough** ein.

4. Wählen Sie **Hinzufügen** aus.

     Die neue Testdatei *TestSettingDistributedTestWalkthrough.testsettings* wird im **Projektmappen-Explorer** im Ordner **Projektmappenelemente** angezeigt.

     Das Dialogfeld **Testeinstellungen** wird angezeigt. Die Seite **Allgemein** ist ausgewählt.

     Sie können die Testeinstellungswerte jetzt bearbeiten und speichern.

5. Geben Sie unter **Name** den Namen für die Testeinstellungen ein.

6. Geben Sie unter **Beschreibung** **Distributed test settings** (Einstellungen für verteilte Tests) ein.

7. Lassen Sie das **Standardbenennungsschema** aktiviert.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>So weisen Sie einem Testcontroller und Test-Agents Rollen zu

1. Klicken Sie auf **Rollen**.

     Die Seite **Rollen** wird angezeigt.

2. Wenn Sie den Test remote ausführen möchten, wählen Sie in der Dropdownliste **Testausführungsmethode** die Option **Remoteausführung** aus.

3. Geben Sie in der Dropdownliste **Controller** den Computernamen [Ihres Testcontrollers](../test/lab-management/install-configure-test-agents.md) ein.

    > [!NOTE]
    > Wenn Sie zum ersten Mal einen Controller hinzufügen, enthält die Dropdownliste keine Controller. Die Liste wird mit vorherigen Controllern aufgefüllt, die Sie in anderen Testeinstellungen angegeben haben.

4. Klicken Sie unter **Rollen** auf die Option **Hinzufügen**.

5. Geben Sie in der markierten Zeile in der Spalte **Name** **Verteilter Test** ein.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>So weisen Sie der Testeinstellung einen Diagnose- und Datenadapter zu

1. Klicken Sie auf **Daten und Diagnose**.

     Die Seite **Daten und Diagnose** wird angezeigt.

2. Überprüfen Sie unter **Rolle**, ob die Rolle **Verteilter Test** ausgewählt ist.

3. Wählen Sie unter **Data and Diagnostic for select role** (Daten und Diagnosen für ausgewählte Rolle) die Adapter **IntelliTrace** und **Systeminformationen** aus.

     Informationen zu diesen und anderen Adaptern, die in einer Testeinstellung verwendet werden können, finden Sie unter [Configure unit tests (Konfigurieren von Komponententests)](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Klicken Sie auf **Hosts**.

5. (Optional) Wenn der Computer unter einer 64-Bit-Version von Microsoft Windows ausgeführt wird, und Sie den Test mit der Konfiguration **Any CPU** (Beliebige CPU) kompiliert haben, klicken Sie in der Dropdownliste **Run test in 32 bit or 64 bit process** (Test als 32-Bit- oder 64-Bit-Prozess ausführen) auf die Option **Run tests in 64-bit process on 64-bit machine** (Tests als 64-Bit-Prozess auf einem 64-Bit-Computer ausführen).

    > [!TIP]
    > Maximale Flexibilität erhalten Sie, wenn Sie die Testprojekte mit der Konfiguration **Beliebige CPU** kompilieren. Die Ausführung ist dann sowohl auf 32- als auch auf 64-Bit-Agents möglich. Das Kompilieren von Testprojekten mit der **64-Bit**-Konfiguration bietet keinen Vorteil.

6. Klicken Sie zum Speichern der neuen Testeinstellungen auf **Anwenden**.

7. Klicken Sie auf **Schließen**.

::: moniker range="vs-2017"

8. Klicken Sie im Menü **Test** auf **Testeinstellungen** > **Datei für Testeinstellungen auswählen**, und wählen Sie die Datei *TestSettingDistributedTestWalkthrough.testsettings* aus.

::: moniker-end

::: moniker range=">=vs-2019"

8. Klicken Sie im Menü **Test** auf **Einstellungsdatei auswählen**. Navigieren Sie zur Datei *TestSettingDistributedTestWalkthrough.testsettings*, und wählen Sie sie aus.

::: moniker-end

9. Führen Sie den Test wie gewohnt aus.

     Wenn der Testcontroller Komponententests und Tests der codierten UI verarbeitet, unterteilt er die Tests in Gruppen von je 100 und sendet diese an einen Test-Agent-Computer. Beispielsweise werden bei 250 Komponententests und drei Test-Agents die ersten 100 Komponententests an agent1 gesendet, die nächsten 100 Komponententests an agent2 und die verbleibenden 50 Komponententests an agent3.

## <a name="see-also"></a>Weitere Informationen

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
