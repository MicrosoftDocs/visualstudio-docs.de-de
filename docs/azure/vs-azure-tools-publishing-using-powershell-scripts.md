---
title: Verwenden von PowerShell zum Veröffentlichen in Entwicklungs-und Testumgebungen
description: Erhalten Sie Informationen zum Veröffentlichen für Entwicklungs- und Testumgebungen mithilfe von Windows PowerShell-Skripts in Visual Studio.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e0486e3a13b1c6b6ba421c5c0a97788f514413e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843955"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Veröffentlichung in Entwicklungs- und Testumgebungen mithilfe von Windows PowerShell-Skripts

Wenn Sie eine Webanwendung in Visual Studio erstellen, können Sie ein Windows PowerShell-Skript generieren. Mit diesem können Sie später die Veröffentlichung Ihrer Website in Azure als Web-App im Azure App Service oder als virtueller Computer automatisieren. Sie können das Windows PowerShell-Skript im Visual Studio-Editor entsprechend Ihren Anforderungen bearbeiten und erweitern oder das Skript in vorhandene Build-, Test- und Veröffentlichungsskripts integrieren.

Mithilfe dieser Skripts können Sie angepasste Versionen Ihrer Website (auch als Entwicklungs- und Testumgebungen bezeichnet) zur vorübergehenden Verwendung bereitstellen. Sie können z. B. eine bestimmte Version Ihrer Website auf einem virtuellen Azure-Computer oder auf dem Stagingslot einer Website einrichten, um eine Testsuite auszuführen, einen Bug zu reproduzieren, einen Bugfix zu testen, eine vorgeschlagene Änderung zu prüfen oder eine benutzerdefinierte Umgebung für eine Demonstration oder eine Präsentation einzurichten. Nachdem Sie ein Skript zum Veröffentlichen Ihres Projekts erstellt haben, können Sie identische Umgebungen erstellen, indem Sie das Skript bei Bedarf erneut ausführen. Sie können das Skript auch mit Ihrem eigenen Build Ihrer Webanwendung ausführen, um eine benutzerdefinierte Umgebung für Testzwecke zu erstellen.

## <a name="prerequisites"></a>Voraussetzungen

* Visual Studio 2015 oder höher mit installierter **Azure-Workload** oder Visual Studio 2013 und Azure SDK 2.3 oder höher. Siehe [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads). (Sie benötigen das Azure SDK nicht, um die Skripts für Webprojekte zu generieren. Dieses Feature bezieht sich auf Webprojekte, nicht auf Webrollen in Clouddiensten.)
* Azure PowerShell 0.7.4 oder höher. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)) oder höher.

## <a name="additional-tools"></a>Weitere Tools

Für die Arbeit mit PowerShell in Visual Studio für die Azure-Entwicklung stehen weitere Tools und Ressourcen zur Verfügung. Weitere Informationen finden Sie unter [PowerShell-Tools für Visual Studio](https://marketplace.visualstudio.com/items?itemName=AdamRDriscoll.PowerShellToolsforVisualStudio2015).

## <a name="generating-the-publish-scripts"></a>Generieren der Veröffentlichungsskripts

Sie können die Veröffentlichungsskripts für einen virtuellen Computer generieren, der Ihre Website hostet, wenn Sie ein neues Projekt anhand [dieser Anweisungen](/azure/virtual-machines/windows/classic/web-app-visual-studio) erstellen. Sie können auch [Veröffentlichungsskripts für Web-Apps in Azure App Service generieren](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Von Visual Studio generierte Skripts

Visual Studio generiert einen Ordner auf Projektebene namens **PublishScripts**, der zwei Windows PowerShell-Dateien enthält – ein Veröffentlichungsskript für Ihren virtuellen Computer oder die Website und ein Modul, das Funktionen enthält, die Sie in den Skripts verwenden können. Visual Studio generiert außerdem eine Datei im JSON-Format, die die Details des von Ihnen bereitgestellten Projekts angibt.

### <a name="windows-powershell-publish-script"></a>Windows PowerShell-Veröffentlichungsskript

Das Veröffentlichungsskript enthält spezifische Veröffentlichungsschritte für die Bereitstellung auf einer Website oder einem virtuellen Computer. Visual Studio stellt farbige Syntaxmarkierung für die Windows PowerShell-Entwicklung zur Verfügung. Hilfe zu den einzelnen Funktionen ist verfügbar, und Sie können die Funktionen im Skript frei bearbeiten und so an Ihre sich ändernden Anforderungen anpassen.

### <a name="windows-powershell-module"></a>Windows PowerShell-Modul

Das von Visual Studio generierte Windows PowerShell-Modul enthält Funktionen, die vom Veröffentlichungsskript verwendet werden. Diese Azure PowerShell-Funktionen sollten nicht geändert werden. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>JSON-Konfigurationsdatei

Die JSON-Datei wird im Ordner **Konfigurationen** erstellt und enthält die spezifischen Konfigurationsdaten, die genau angeben, welche Ressourcen in Azure bereitgestellt werden. Der Name der von Visual Studio generierten Datei lautet "projektname-WAWS-dev.json", wenn Sie eine Website erstellt haben, bzw. "projektname-VM-dev.json", wenn Sie einen virtuellen Computer erstellt haben. Das folgende Beispiel zeigt eine JSON-Konfigurationsdatei, die generiert wird, wenn Sie eine Website erstellen. Die meisten Werte sind selbsterklärend. Der Websitename wird von Azure generiert. Er stimmt daher ggf. nicht mit Ihrem Projektnamen überein.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Wenn Sie einen virtuellen Computer erstellen, sieht die JSON-Konfigurationsdatei wie im folgenden Beispiel aus. Ein Clouddienst wird als Container für den virtuellen Computer erstellt. Der virtuelle Computer enthält die üblichen Endpunkte für den Webzugriff über HTTP und HTTPS sowie Endpunkte für Web Deploy. Letzteres ermöglicht die Veröffentlichung auf der Website über Ihren lokalen Computer, Remotedesktop und Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Sie können die JSON-Konfiguration bearbeiten, um das Verhalten beim Ausführen der Veröffentlichungsskripts zu ändern. Die Abschnitte `cloudService` und `virtualMachine` sind erforderlich, der Abschnitt `databases` kann jedoch gelöscht werden, wenn er nicht benötigt wird. Die Eigenschaften, die in der von Visual Studio generierten Standardkonfigurationsdatei leer sind, sind optional. Die Eigenschaften, die in der Standardkonfigurationsdatei Werte aufweisen, sind erforderlich.

Wenn Sie eine Website mit mehreren Bereitstellungsumgebungen (als Slots bezeichnet) anstelle einer einzelnen Produktionswebsite in Azure verwenden, können Sie den Slotnamen in den Namen der Website in der JSON-Konfigurationsdatei einschließen. Wenn Sie z. B. eine Website mit dem Namen **mysite** und einen zugehörigen Slot namens **test** verwenden, lautet der URI `mysite-test.cloudapp.net`. Der richtige Name für die Verwendung in der Konfigurationsdatei ist jedoch mysite(test). Diese Vorgehensweise ist nur möglich, wenn die Website und die Slots bereits in Ihrem Abonnement vorhanden sind. Andernfalls erstellen Sie die Website, indem Sie das Skript ausführen, ohne den Slot anzugeben. Erstellen Sie den Slot dann im [Azure-Portal](https://portal.azure.com/), und führen Sie anschließend das Skript mit dem geänderten Websitenamen aus. Weitere Informationen zu den Bereitstellungsslots für Web-Apps finden Sie unter [Einrichten von Stagingumgebungen für Web-Apps in Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Ausführen der Veröffentlichungsskripts

Wenn Sie noch nie zuvor ein Windows PowerShell-Skript ausgeführt haben, müssen Sie zuerst die Ausführungsrichtlinie festlegen, damit die Ausführung von Skripts ermöglicht wird. Die Richtlinie ist eine Sicherheitsmaßnahme, die die Ausführung von Windows PowerShell-Skripts durch Benutzer verhindert, die von Schadsoftware oder Viren betroffen sein könnten, die eine Skriptausführung beinhalten.

### <a name="run-the-script"></a>Ausführen des Skripts

1. Erstellen Sie das Web Deploy-Paket für Ihr Projekt. Web Deploy-Pakete sind komprimierte Archive (ZIP-Dateien), die Dateien enthalten, die Sie auf Ihre Website oder den virtuellen Computer kopieren möchten. In Visual Studio können Sie Web Deploy-Pakete für beliebige Webanwendungen erstellen.

   ![Web Deploy-Paket erstellen](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Webbereitstellungspakets in Visual Studio](/previous-versions/aspnet/dd465323(v=vs.110)). Sie können die Erstellung Ihres Web Deploy-Pakets wie unter [Customizing and extending the publish scripts (Anpassen und Erweitern des Veröffentlichungsskripts)](#customizing-and-extending-the-publish-scripts) beschrieben automatisieren.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Skript, und wählen Sie dann **Mit PowerShell-ISE öffnen** aus.
1. Wenn Sie Windows PowerShell-Skripts erstmals auf diesem Computer ausführen, öffnen Sie ein Eingabeaufforderungsfenster mit Administratorberechtigungen, und geben Sie den folgenden Befehl ein:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Melden Sie sich mithilfe des folgenden Befehls bei Azure an.

    ```powershell
    Add-AzureAccount
    ```

    Geben Sie Ihren Benutzernamen und Ihr Kennwort ein, wenn Sie dazu aufgefordert werden.

    Beachten Sie, dass diese Methode für die Bereitstellung von Azure-Anmeldeinformationen bei einer Automatisierung des Skripts nicht funktioniert. Stattdessen sollten Sie die `.publishsettings`-Datei zum Bereitstellen von Anmeldeinformationen verwenden. Sie verwenden den Befehl **Get-AzurePublishSettingsFile** einmalig zum Herunterladen der Datei aus Azure. Danach verwenden Sie **Import-AzurePublishSettingsFile**, um die Datei zu importieren. Ausführliche Anweisungen finden Sie unter [Installieren und Konfigurieren von Azure PowerShell](/powershell/azure/overview).

1. (Optional:) Wenn Sie Azure-Ressourcen (z.B. virtuelle Computer, Datenbanken und Websites) erstellen möchten, ohne Ihre Webanwendung zu veröffentlichen, verwenden Sie den Befehl **Publish-WebApplication.ps1** mit dem Argument **-Configuration**, das auf die JSON-Konfigurationsdatei festgelegt ist. Diese Befehlszeile verwendet die JSON-Konfigurationsdatei, um zu ermitteln, welche Ressourcen erstellt werden sollen. Da sie die Standardeinstellungen für andere Befehlszeilenargumente verwendet, werden die Ressourcen erstellt, Ihre Webanwendung wird jedoch nicht veröffentlicht. Die Option "–Verbose" stellt weitere Informationen zu den Vorgängen zur Verfügung.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Verwenden Sie den Befehl **Publish-WebApplication.ps1** wie in einem der folgenden Beispiele gezeigt, um das Skript aufzurufen und Ihre Webanwendung zu veröffentlichen. Wenn Sie die Standardeinstellungen für andere Argumente (z.B. den Abonnementnamen, den Namen des Veröffentlichungspakets, die Anmeldeinformationen des virtuellen Computers oder die Anmeldeinformationen des Datenbankservers) außer Kraft setzen müssen, können Sie diese Parameter angeben. Verwenden Sie die Option **-Verbose**, um weitere Informationen zum Verlauf des Veröffentlichungsvorgangs anzuzeigen.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Wenn Sie einen virtuellen Computer erstellen, sieht der Befehl wie im folgenden Beispiel aus. Dieses Beispiel zeigt außerdem, wie die Anmeldeinformationen für mehrere Datenbanken angegeben werden. Für die virtuellen Computer, die durch diese Skripts erstellt werden, stammt das SSL-Zertifikat nicht von einer vertrauenswürdigen Stammzertifizierungsstelle. Aus diesem Grund müssen Sie die Option **–AllowUntrusted** verwenden.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Das Skript kann Datenbanken erstellen, es erstellt jedoch keine Datenbankserver. Wenn Sie einen Datenbankserver erstellen möchten, können Sie die Funktion **New-AzureSqlDatabaseServer** im Azure-Modul verwenden.

## <a name="customizing-and-extending-the-publish-scripts"></a>Anpassen und Erweitern der Veröffentlichungsskripts

Sie können das Veröffentlichungsskript und die JSON-Konfigurationsdatei anpassen. Die Funktionen im Windows PowerShell-Modul **AzureWebAppPublishModule.psm1** sollten nicht geändert werden. Wenn Sie nur eine andere Datenbank angeben oder einige Eigenschaften des virtuellen Computers ändern möchten, bearbeiten Sie die JSON-Konfigurationsdatei. Wenn Sie die Funktionen des Skripts so erweitern möchten, dass der Buildvorgang und das Testen des Projekts automatisiert werden, können Sie Funktionsstubs in **Publish-WebApplication.ps1** implementieren.

Wenn Sie den Buildvorgang Ihres Projekts automatisieren möchten, fügen Sie Code hinzu, der MSBuild für `New-WebDeployPackage` aufruft. Dies wird im folgenden Codebeispiel gezeigt. Der Pfad zum MSBuild-Befehl kann abhängig von der installierten Version von Visual Studio variieren. Zum Ermitteln des richtigen Pfads können Sie die Funktion **Get-MSBuildCmd** wie in diesem Beispiel gezeigt verwenden.

### <a name="to-automate-building-your-project"></a>So automatisieren Sie die Erstellung Ihres Projekts

1. Fügen Sie den Parameter `$ProjectFile` im Abschnitt mit den globalen Parametern hinzu.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Kopieren Sie die Funktion `Get-MSBuildCmd` in Ihre Skriptdatei.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Ersetzen Sie `New-WebDeployPackage` durch den folgenden Code, und ersetzen Sie die Platzhalter in der Zeile, mit der `$msbuildCmd` erstellt wird. Dieser Code ist für Visual Studio 2019. Wenn Sie Visual Studio 2017 verwenden, ändern Sie die **VisualStudioVersion**-Eigenschaft in `15.0` (bei Visual Studio 2015 in 14.0 und bei Visual Studio 2013 in `12.0`).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Verwenden Sie zum Erstellen Ihrer Webanwendung „MsBuild.exe“. Hilfe finden Sie unter [MSBuild Command-Line Referenz](../msbuild/msbuild-command-line-reference.md)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=16.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Starten des Buildbefehls

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Rufen Sie die Funktion `New-WebDeployPackage` vor dieser Zeile auf: `$Config = Read-ConfigFile $Configuration` für Web-Apps bzw. `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` für virtuelle Computer.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Rufen Sie das angepasste Skript über die Befehlszeile auf, und übergeben Sie das Argument `$Project`, wie im folgenden Beispiel gezeigt:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Wenn Sie das Testen Ihrer Anwendung automatisieren möchten, fügen Sie der `Test-WebApplication`Code hinzu. Stellen Sie in **Publish-WebApplication.ps1** sicher, dass die Auskommentierung der Zeilen aufgehoben wird, in denen diese Funktionen aufgerufen werden. Wenn Sie keine Implementierung bereitstellen, können Sie Ihr Projekt manuell mit Visual Studio erstellen und dann das Veröffentlichungsskript zum Veröffentlichen in Azure aufrufen.

## <a name="publishing-function-summary"></a>Zusammenfassung der Veröffentlichungsfunktion
Wenn Sie Hilfe zu Funktionen abrufen möchten, können Sie an der Windows PowerShell-Eingabeaufforderung den Befehl `Get-Help function-name`verwenden. Die Hilfe umfasst Parameterhilfe und Beispiele. Der gleiche Hilfe Text befindet sich auch in den Skript Quelldateien **azurewebapppublishmodule. psm1** und **Publish-WebApplication.ps1**. Das Skript und die Hilfe sind in Ihrer Visual Studio-Sprache lokalisiert.

**AzureWebAppPublishModule**

| Funktionsname | BESCHREIBUNG |
| --- | --- |
| Add-AzureSQLDatabase |Erstellt eine neue Azure SQL-Datenbank. |
| Add-AzureSQLDatabases |Erstellt Azure SQL-Datenbanken aus Werten in der JSON-Konfigurationsdatei, die von Visual Studio generiert wird |
| Add-AzureVM |Erstellt einen virtuellen Azure-Computer und gibt die URL des bereitgestellten virtuellen Computers zurück. Die Funktion richtet die Voraussetzungen ein und ruft dann die Funktion **New-AzureVM** (Azure-Modul) auf, um einen neuen virtuellen Computer zu erstellen. |
| Add-AzureVMEndpoints |Fügt einem virtuellen Computer neue Eingabeendpunkte hinzu und gibt den virtuellen Computer mit dem neuen Endpunkt zurück. |
| Add-AzureVMStorage |Erstellt ein neues Azure-Speicherkonto im aktuellen Abonnement. Der Name des Kontos beginnt mit "devtest", gefolgt von einer eindeutigen alphanumerischen Zeichenfolge. Die Funktion gibt den Namen des neuen Speicherkontos zurück. Geben Sie einen Speicherort oder eine Affinitätsgruppe für das neue Speicherkonto an. |
| Add-AzureWebsite |Erstellt eine Website mit dem angegebenen Namen und Speicherort. Diese Funktion ruft die Funktion **New-AzureWebsite** im Azure-Modul auf. Wenn das Abonnement noch keine Website mit dem angegebenen Namen umfasst, erstellt diese Funktion die Website und gibt ein Websiteobjekt zurück. Andernfalls wird `$null`zurückgegeben. |
| Backup-Subscription |Speichert das aktuelle Azure-Abonnement in der Variablen `$Script:originalSubscription` im Skriptbereich. Diese Funktion speichert das aktuelle Azure-Abonnement (wie durch `Get-AzureSubscription -Current` abgerufen) und das zugehörige Speicherkonto sowie das Abonnement, das von diesem Skript geändert wird (in der Variablen `$UserSpecifiedSubscription` gespeichert), und das zugehörige Speicherkonto im Skriptbereich. Da diese Werte gespeichert werden, können Sie eine Funktion (z.B. `Restore-Subscription`) zum Wiederherstellen des ursprünglichen aktuellen Abonnements und Speicherkontos im aktuellen Status verwenden, wenn sich der aktuelle Status geändert hat. |
| Find-AzureVM |Ruft den angegebenen virtuellen Azure-Computer ab. |
| Format-DevTestMessageWithTime |Stellt einer Meldung das Datum und die Uhrzeit voran. Diese Funktion bezieht sich auf Meldungen, die in die Datenströme vom Typ "Fehler" und "Ausführlich" geschrieben werden. |
| Get-AzureSQLDatabaseConnectionString |Stellt eine Verbindungszeichenfolge zum Herstellen einer Verbindung mit einer Azure SQL-Datenbank zusammen. |
| Get-AzureVMStorage |Gibt den Namen des ersten Speicher Kontos mit dem Namensmuster "devtest" (ohne Beachtung der *Groß-/Kleinschreibung) am angegebenen Speicherort oder in der affinitätsgruppe zurück. Wenn das Speicherkonto "devtest*" nicht mit dem Speicherort oder der affinitätsgruppe identisch ist, wird es von der Funktion ignoriert. Geben Sie einen Speicherort oder eine Affinitätsgruppe an. |
| Get-MSDeployCmd |Gibt einen Befehl zum Ausführen des Tools "MsDeploy.exe" zurück. |
| New-AzureVMEnvironment |Sucht oder erstellt einen virtuellen Computer im Abonnement, das mit den Werten in der JSON-Konfigurationsdatei übereinstimmt. |
| Publish-WebPackage |Verwendet "MsDeploy.exe" und eine Webveröffentlichungspaket-ZIP-Datei zum Bereitstellen von Ressourcen für eine Website. Diese Funktion generiert keine Ausgabe. Wenn beim Aufruf von "MSDeploy.exe" ein Fehler auftritt, löst die Funktion eine Ausnahme aus. Verwenden Sie die Option **-Verbose** , wenn Sie eine ausführlichere Ausgabe wünschen. |
| Publish-WebPackageToVM |Überprüft die Parameterwerte und ruft dann die Funktion **Publish-WebPackage** auf. |
| Read-ConfigFile |Überprüft die JSON-Konfigurationsdatei und gibt eine Hashtabelle ausgewählter Werte zurück. |
| Restore-Subscription |Setzt das aktuelle Abonnement auf das ursprüngliche Abonnement zurück. |
| Test-AzureModule |Gibt `$true` zurück, wenn die Version des installierten Azure-Moduls 0.7.4 oder höher ist. Gibt `$false` zurück, wenn das Modul nicht installiert ist oder in einer früheren Version vorliegt. Diese Funktion besitzt keine Parameter. |
| Test-AzureModuleVersion |Gibt `$true` zurück, wenn die Version des Azure-Moduls 0.7.4 oder höher ist. Gibt `$false` zurück, wenn das Modul nicht installiert ist oder in einer früheren Version vorliegt. Diese Funktion besitzt keine Parameter. |
| Test-HttpsUrl |Konvertiert die Eingabe-URL in ein System.Uri-Objekt. Gibt `$True` zurück, wenn die URL absolut ist und ein https-Schema verwendet. Gibt `$false` zurück, wenn die URL relativ ist und nicht das HTTPS-Schema verwendet oder die Eingabezeichenfolge nicht in eine URL konvertiert werden kann. |
| Test-Member |Gibt `$true` zurück, wenn eine Eigenschaft oder Methode ein Element des Objekts ist. Andernfalls wird `$false`zurückgegeben. |
| Write-ErrorWithTime |Schreibt eine Fehlermeldung, der die aktuelle Uhrzeit als Präfix vorangestellt ist. Diese Funktion ruft die Funktion **Format-DevTestMessageWithTime** auf, um die Uhrzeit voranzustellen, bevor die Meldung in den Fehlerdatenstrom geschrieben wird. |
| Write-HostWithTime |Schreibt eine Fehlermeldung in das Hostprogramm (**Write-Host**), der die aktuelle Uhrzeit als Präfix vorangestellt ist. Die Auswirkungen des Schreibens in das Hostprogramm sind unterschiedlich. Die meisten Programme, die Windows PowerShell hosten, schreiben diese Meldungen in die Standardausgabe. |
| Write-VerboseWithTime |Schreibt eine ausführliche Fehlermeldung, der die aktuelle Uhrzeit als Präfix vorangestellt ist. Da **Write-Verbose** aufgerufen wird, wird die Meldung nur angezeigt, wenn das Skript mit dem Parameter **Verbose** ausgeführt wird oder die Einstellung **VerbosePreference** auf **Continue** festgelegt ist. |

**Publish-WebApplication**

| Funktionsname | BESCHREIBUNG |
| --- | --- |
| New-AzureWebApplicationEnvironment |Erstellt Azure-Ressourcen, z. B. eine Website oder einen virtuellen Computer. |
| New-WebDeployPackage |Diese Funktion ist nicht implementiert. Sie können Befehle in dieser Funktion hinzufügen, um Ihr Projekt zu erstellen. |
| Publish-AzureWebApplication |Veröffentlicht eine Webanwendung in Azure. |
| Publish-WebApplication |Erstellt Web-Apps, virtuelle Computer, SQL-Datenbanken und Speicherkonten für ein Visual Studio-Webprojekt und stellt diese Elemente bereit. |
| Test-WebApplication |Diese Funktion ist nicht implementiert. Sie können Befehle in dieser Funktion hinzufügen, um Ihre Anwendung zu testen. |

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zur PowerShell-Skripterstellung finden Sie unter [Skripterstellung mit Windows PowerShell](/powershell/scripting/overview). Weitere Azure PowerShell-Skripts finden Sie im [Script Center](https://azure.microsoft.com/documentation/scripts/).