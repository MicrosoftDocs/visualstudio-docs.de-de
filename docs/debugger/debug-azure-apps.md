---
title: Debuggen von Azure-Diensten | Microsoft-Dokumentation
description: Sie können Azure-Dienste mit Visual Studio debuggen. Klicken Sie auf die Links in diesem Artikel, um mehr über die verschiedenen Möglichkeiten zu erfahren.
ms.custom: SEO-VS-2020
ms.date: 09/14/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
ms.assetid: 3d434de3-ee5f-419d-9a94-ac4ac02d635b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: a77f1291621e84eb2e13075a791e9c6735447137
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857621"
---
# <a name="debug-azure-services-in-visual-studio"></a>Debuggen von Azure-Diensten in Visual Studio

Sie können Visual Studio zum Debuggen von Azure-Diensten in verschiedenen Szenarios verwenden:

So debuggen Sie eine Produktions-App mit den folgenden Hosts:

- Azure App Service mit Visual Studio Enterprise (weitere Informationen unter [Debuggen von aktiven ASP.NET Azure-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md))

- Azure App Service oder Service Fabric mit Application Insights (weitere Informationen unter [Debugmomentaufnahmen von Ausnahmen in .NET-Apps](/azure/application-insights/app-insights-snapshot-debugger))

- Azure-VM oder Azure-VM-Skalierungsgruppe (weitere Informationen unter [Debuggen von aktiven ASP.NET-Apps auf Azure-VMs und Azure-VMSS mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-virtual-machines.md))

- Azure Kubernetes Service (weitere Informationen unter [Debuggen von aktiven ASP.NET Azure Kubernetes Services mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md))

Remotedebuggen:

- ASP.NET in IIS (Azure App Service oder Azure-VM; weitere Informationen unter [Remotedebuggen von ASP.NET Core in IIS in Azure in Visual Studio](remote-debugging-azure.md))

- ASP.NET in Azure Service Fabric (weitere Informationen unter [Debuggen einer Service Fabric-Remoteanwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application))

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
