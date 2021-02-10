---
title: Automatisches Anwenden von Product Keys
description: Erfahren Sie, wie Produktschlüssel bei der Bereitstellung von Visual Studio programmgesteuert angewendet werden.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 029c2829e1a31f3fc5329e38d1f369afafa17f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868711"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio

Sie können Ihren Product Key programmgesteuert als Teil eines Skripts anwenden, mit dem die Bereitstellung von Visual Studio automatisiert wird. Sie haben die Möglichkeit, einen Product Key während der Installation von Visual Studio oder nach der abgeschlossenen Installation auf einem Gerät programmgesteuert festzulegen.

## <a name="apply-the-license-after-installation"></a>Anwenden der Lizenz nach der Installation

::: moniker range="vs-2017"

Sie können eine installierte Version von Visual Studio mit einem Product Key aktivieren, indem Sie das Hilfsprogramm `StorePID.exe` auf den Zielcomputern im automatischen Modus verwenden. `StorePID.exe` ist ein Hilfsprogramm im Installationsumfang von Visual Studio 2017, das am folgenden Standardspeicherort installiert wird: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Sie können eine installierte Version von Visual Studio mit einem Product Key aktivieren, indem Sie das Hilfsprogramm `StorePID.exe` auf den Zielcomputern im automatischen Modus verwenden. `StorePID.exe` ist ein Hilfsprogramm im Installationsumfang von Visual Studio 2019, das am folgenden Standardspeicherort installiert wird: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Führen Sie `StorePID.exe` mit erhöhten Rechten entweder mithilfe eines System Center-Agents oder einer Eingabeaufforderung mit erhöhten Rechten aus. Geben Sie dahinter den Product Key und den Microsoft-Produktcode (Microsoft Product Code, MPC) ein.

>[!IMPORTANT]
> Schließen Sie unbedingt die Gedankenstriche in den Product Key mit ein.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

Im folgenden Beispiel wird eine Beispielbefehlszeile für die Anwendung der Lizenz für Visual Studio 2017 Enterprise mit dem MPC 08860 und dem Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` gezeigt. Es wird angenommen, dass die Installation an einem Standardspeicherort erfolgt:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Im folgenden Beispiel wird eine Beispielbefehlszeile für die Anwendung der Lizenz für Visual Studio 2019 Enterprise mit dem MPC 09260 und dem Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` gezeigt. Es wird angenommen, dass die Installation an einem Standardspeicherort erfolgt:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 In der folgenden Tabelle werden die MPC-Codes für jede Edition von Visual Studio aufgelistet:

| Visual Studio-Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio-Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

Wenn der Product Key im Hilfsprogramm `StorePID.exe` erfolgreich angewendet wurde, wird als Wert von `%ERRORLEVEL%` 0 zurückgegeben. Wenn Fehler auftreten, wird einer der folgenden Codes entsprechend der Fehlerbedingung zurückgegeben:

| Fehler                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Wenn Sie eine virtuelle Instanz von Visual Studio ausführen, stellen Sie sicher, dass Sie auch den lokalen AppData-Ordner und die Registrierung virtualisieren. Führen Sie `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe` aus, um Probleme bei virtuellen Instanzen zu beheben.  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Installieren von Visual Studio](../install/install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
