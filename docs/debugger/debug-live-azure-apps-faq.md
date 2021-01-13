---
title: Häufig gestellte Fragen zum Debuggen von Momentaufnahmen | Microsoft-Dokumentation
description: Hier finden Sie eine Liste häufig gestellter Fragen (FAQ), die beim Debuggen aktiver Azure-Anwendungen mit dem Momentaufnahmedebugger in Visual Studio aufkommen können.
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5276127f0d6755b9fdabdfa965b5c1b8c4d94823
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727202"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio

Hier ist eine Liste der Fragen, die beim Debuggen aktiver Azure-Anwendungen mit dem Momentaufnahmedebugger aufkommen könnten.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Wie hoch sind die Leistungseinbußen bei einer Momentaufnahme?

Wenn der Momentaufnahmedebugger eine Momentaufnahme Ihrer App erfasst, verzweigt er den Prozess der App und setzt die verzweigte Kopie aus. Wenn Sie eine Momentaufnahme debuggen, debuggen Sie die verzweigte Kopie des Prozesses. Dieser Vorgang dauert nur 10 bis 20 Millisekunden, kopiert aber nicht den vollständigen Heap der App. Stattdessen kopiert er nur die Seitentabelle und legt Seiten für das Kopieren beim Schreibvorgang fest. Wenn einige Ihrer App-Objekte auf dem Heap geändert werden, werden die entsprechenden Seiten kopiert. Darum beansprucht jede Momentaufnahme etwas Arbeitsspeicher (bei den meisten Apps in der Größenordnung von ein paar hundert Kilobytes).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Was geschieht, wenn ich einen horizontal hochskalierten Azure App Service habe (mehrere Instanzen meiner App)?

Wenn Sie mehrere Instanzen Ihrer App haben, werden die Andockpunkte auf jede einzelne Instanz angewendet. Nur der erste mit den angegebenen Bedingungen zu erreichende Andockpunkt erstellt eine Momentaufnahme. Wenn Sie mehrere Andockpunkte haben, stammen spätere Momentaufnahmen von der gleichen Instanz, die die erste Momentaufnahme erstellt hat. An das Ausgabefenster gesendete Protokollpunkte zeigen nur Meldungen von einer Instanz an, während an Anwendungsprotokolle gesendete Protokollpunkte Meldungen von jeder Instanz senden.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Wie lädt der Momentaufnahmedebugger Symbole?

Der Momentaufnahmedebugger erfordert, dass Sie die entsprechenden Symbole für Ihre Anwendung entweder lokal oder für Ihren Azure App Service bereitgestellt haben. (Eingebettete PDB-Dateien werden derzeit nicht unterstützt.) Der Momentaufnahmedebugger lädt automatisch Symbole von Ihrem Azure App Service. Ab Visual Studio 2017 Version 15.2 werden mit der Bereitstellung für Azure App Service auch die Symbole Ihrer App bereitgestellt.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Arbeitet der Momentaufnahmedebugger mit Releasebuilds meiner Anwendung?

Ja, der Momentaufnahmedebugger soll mit Releasebuilds arbeiten. Wenn ein Andockpunkt in einer Funktion platziert wird, wird die Funktion zu einer Debugversion neu kompiliert und damit debugfähig. Beim Beenden des Momentaufnahmedebuggers werden die Funktionen auf die Version des Releasebuilds zurückgesetzt.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Können Protokollpunkte in meiner Produktionsanwendung Nebeneffekte verursachen?

Nein – jegliche Meldungen, die Sie Ihrer App hinzufügen, werden virtuell ausgewertet. Sie können keine Nebeneffekte in Ihrer Anwendung auslösen. Allerdings ist der Zugriff auf einige native Eigenschaften mit Protokollpunkten vielleicht nicht möglich.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funktioniert der Momentaufnahmedebugger, wenn mein Server unter Last steht?

Ja, das Momentaufnahmedebuggen kann bei Servern unter Last funktionieren. Wenn nur eine geringe Menge freien Arbeitsspeichers auf dem Server vorhanden ist, wird der Momentaufnahmedebugger gedrosselt und erfasst keine Momentaufnahmen.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Wie deinstalliere ich den Momentaufnahmedebugger?

Sie können die Momentaufnahmedebugger-Websiteerweiterung mit den folgenden Schritten in Ihrem App Service deinstallieren:

1. Deaktivieren Sie Ihre App Service-Instanz entweder über den Cloud-Explorer in Visual Studio oder im Azure-Portal.
1. Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zu **Websiteerweiterungen**.
1. Klicken Sie auf das X der Momentaufnahmedebugger-Websiteerweiterung, um sie zu entfernen.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Warum werden während einer Momentaufnahmedebugger-Sitzung Ports geöffnet?

Der Momentaufnahmedebugger muss einen Satz von Ports öffnen, um die in Azure erstellten Momentaufnahmen zu debuggen. Hierbei handelt es sich um die gleichen Ports, die für das Remotedebuggen erforderlich sind. [Hier finden Sie die Liste der Ports](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Wie kann ich die Erweiterung „Remotedebugger“ deaktivieren?

Für App Services:
1. Deaktivieren Sie die Erweiterung „Remotedebugger“ im Azure-Portal für Ihre App Service-Instanz.
2. Wählen Sie im Azure-Portal das Blatt für Ihre Application Service-Ressource und dann die Option *Anwendungseinstellungen* aus.
3. Navigieren Sie zum Abschnitt *Debuggen*, und klicken Sie für *Remotedebuggen* auf die Schaltfläche *Aus*.

Für AKS:
1. Aktualisieren Sie Ihre Dockerfile-Datei, um die Abschnitte für den [Visual Studio-Momentaufnahmedebugger für Docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker) zu entfernen.
2. Führen Sie für das geänderte Docker-Image die erneute Erstellung und Bereitstellung durch.

Entfernen Sie für virtuelle Computer bzw. VM-Skalierungsgruppen wie folgt die Erweiterung „Remotedebugger“, Zertifikate, Schlüsseltresore und NAT-Eingangspools:

1. Entfernen der Erweiterung „Remotedebugger“

   Es gibt mehrere Möglichkeiten, den Remotedebugger für virtuelle Computer und VM-Skalierungsgruppen zu deaktivieren:

      - Deaktivieren des Remotedebuggers per Cloud-Explorer

         - Wählen Sie im Cloud-Explorer Ihre VM-Ressource und dann die Option „Debuggen deaktivieren“ aus (für VM-Skalierungsgruppen im Cloud-Explorer nicht verfügbar).

      - Deaktivieren des Remotedebuggers mit PowerShell-Skripts/-Cmdlets

         Für virtuelle Computer:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Für VM-Skalierungsgruppen:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Deaktivieren des Remotedebuggers über das Azure-Portal
         - Wählen Sie im Azure-Portal das Blatt für Ihren virtuellen Computer bzw. Ihre VM-Skalierungsgruppe und dann die Option „Erweiterungen“ aus.
         - Deinstallieren der Erweiterung „Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger“

         > [!NOTE]
         > VM-Skalierungsgruppen: Im Portal ist das Entfernen der DebuggerListener-Ports nicht zulässig. Sie müssen Azure PowerShell verwenden. Details finden Sie weiter unten.

2. Entfernen von Zertifikaten und Azure Key Vault

   Beim Installieren der Erweiterung „Remotedebugger“ für virtuelle Computer oder VM-Skalierungsgruppen werden sowohl Client- als auch Serverzertifikate erstellt, um den Visual Studio-Client für die Ressourcen der Azure-VM bzw. der VM-Skalierungsgruppe authentifizieren zu können.

   - Clientzertifikat

      Bei diesem Zertifikat handelt es sich um ein selbstsigniertes Zertifikat unter „Cert:/CurrentUser/My/“.

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Eine Möglichkeit, dieses Zertifikat von Ihrem Computer zu entfernen, ist PowerShell.

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Serverzertifikat
      - Der entsprechende Fingerabdruck des Serverzertifikats wird als Geheimnis in Azure Key Vault bereitgestellt. Visual Studio versucht, einen Schlüsseltresor mit dem Präfix MSVSAZ* in der Region zu finden oder zu erstellen, in der sich die Ressource des virtuellen Computers oder der VM-Skalierungsgruppe befindet. Für alle Ressourcen des virtuellen Computers oder der VM-Skalierungsgruppe, die in dieser Region bereitgestellt wurden, wird daher derselbe Schlüsseltresor genutzt.
      - Navigieren Sie zum Löschen des Geheimnisses für den Serverzertifikat-Fingerabdruck zum Azure-Portal, und suchen Sie nach dem Schlüsseltresor mit „MSVSAZ*“ in derselben Region, in der Ihre Ressource gehostet wird. Löschen Sie das Geheimnis (es sollte die Bezeichnung `remotedebugcert<<ResourceName>>` haben).
      - Sie müssen auch das Servergeheimnis per PowerShell aus Ihrer Ressource löschen.

      Für virtuelle Computer:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Für VM-Skalierungsgruppen:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Entfernen Sie alle NAT-Eingangspools vom Typ „DebuggerListener“ (nur VM-Skalierungsgruppe).

   Mit dem Remotedebugger werden NAT-Eingangspools vom Typ „DebuggerListener“ eingeführt, die auf das Lastenausgleichsmodul Ihrer Skalierungsgruppe angewendet werden.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Wie kann ich den Momentaufnahmedebugger deaktivieren?

Für App Service:
1. Deaktivieren Sie den Momentaufnahmedebugger über das Azure-Portal für Ihre App Service-Instanz.
2. Wählen Sie im Azure-Portal das Blatt für Ihre Application Service-Ressource und dann die Option *Anwendungseinstellungen* aus.
3. Löschen Sie die folgenden App-Einstellungen im Azure-Portal, und speichern Sie Ihre Änderungen.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Alle Änderungen der Anwendungseinstellungen bewirken, dass ein Neustart der App initiiert wird. Weitere Informationen zu Anwendungseinstellungen finden Sie unter [Konfigurieren einer App Service-App im Azure-Portal](/azure/app-service/web-sites-configure).

Für AKS:
1. Aktualisieren Sie Ihre Dockerfile-Datei, um die Abschnitte für den [Visual Studio-Momentaufnahmedebugger für Docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker) zu entfernen.
2. Führen Sie für das geänderte Docker-Image die erneute Erstellung und Bereitstellung durch.

Für virtuelle Computer/VM-Skalierungsgruppen:

Es gibt mehrere Möglichkeiten, den Momentaufnahmedebugger zu deaktivieren:
- Navigieren Sie im Cloud-Explorer zur Ressource Ihres virtuellen Computers bzw. der VM-Skalierungsgruppe, und wählen Sie die Option „Diagnose deaktivieren“ aus.

- Navigieren Sie im Azure-Portal zum Blatt für die Ressource Ihres virtuellen Computers bzw. der VM-Skalierungsgruppe, und wählen Sie „Erweiterungen“ > „Microsoft.Insights.VMDiagnosticsSettings-Erweiterung deinstallieren“ aus.

- PowerShell-Cmdlets aus [Az PowerShell](/powershell/azure/overview)

   Virtueller Computer:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   VM-Skalierungsgruppen:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Debuggen von aktiven ASP.NET-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Debuggen von aktiven ASP.NET Azure-VMs\-VMSS, die den Momentaufnahmedebugger verwenden](../debugger/debug-live-azure-virtual-machines.md)
- [Debuggen von aktiven ASP.NET Azure Kubernetes Services mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md)
