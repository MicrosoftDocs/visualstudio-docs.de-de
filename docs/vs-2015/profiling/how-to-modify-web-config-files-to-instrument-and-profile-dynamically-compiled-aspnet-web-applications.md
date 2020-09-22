---
title: 'Vorgehensweise: Bearbeiten von Web.Config-Dateien zur Instrumentierung und Profilerstellung für dynamisch kompilierte ASP.NET-Webanwendungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9e4fc4dfdff336b9ddcbd04bd031b48a8acc4dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840935"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Gewusst wie: Bearbeiten von Web.Config-Dateien zur Instrumentierung und Profilerstellung für dynamisch kompilierte ASP.NET-Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungs-Instrumentierungsmethode verwenden, um detaillierte Zeitsteuerdaten, .NET-Speicherbelegungsdaten und .NET-Objektlebensdauerdaten von dynamisch kompilierten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen zu sammeln.  
  
 In diesem Thema wird beschrieben, wie die Konfigurationsdatei „web.config“ zum Aktivieren der Instrumentierung und Profilerstellung von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen geändert werden kann.  
  
> [!NOTE]
> Wenn Sie die Profilerstellungsmethode durch Sampling verwenden oder Sie ein vorkompiliertes Modul [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] instrumentieren möchten, brauchen Sie die web.config-Datei nicht zu ändern.  
  
 Der Stamm einer web.config-Datei ist das Element **configuration**. Sie müssen zum Instrumentieren und Erstellen eines Profils von einer dynamisch kompilierten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung folgende Elemente ändern oder hinzufügen:  
  
- Ein Element **configuration/runtime/assemblyBinding/dependentAssembly**, das das Microsoft.VisualStudio.Enterprise.ASPNetHelper-Assembly identifiziert, das die Profilerstellung steuert. Das Element **dependentAssembly** enthält zwei untergeordnete Elemente: **assemblyIdentity** und **codeBase**.  
  
- Ein Element **configuration/system.web/compilation**, das den Schritt der Profilernachbearbeitungskompilierung für die Ziel-Assembly identifiziert.  
  
- Zwei Elemente **add**, die den Speicherort der Tools „Profilerstellungstools“ identifizieren, werden zum Abschnitt **configuration/appSettings** hinzugefügt.  
  
  Sie sollten eine Kopie der originalen web.config-Datei erstellen, mit der Sie die Konfiguration der Anwendung wiederherstellen können.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>So fügen Sie die ASPNetHelper-Assembly als Element „configuration/runtime/assemblyBinding/dependentAssembly“ ein  
  
1. Fügen Sie, wenn notwendig, das Element **Runtime** als untergeordnetes Element des Elements **configuration** ein. Ansonsten fahren Sie mit dem nächsten Schritt fort.  
  
     Das Element **Runtime** weist keine Attribute auf. Das Element **configuration** kann nur ein untergeordnetes Element **Runtime** haben.  
  
2. Fügen Sie, wenn notwendig, das Element **assemblyBinding** als untergeordnetes Element des Elements **Runtime** ein. Ansonsten fahren Sie mit dem nächsten Schritt fort.  
  
     Das Element **Runtime** kann nur ein Element **assemblyBinding** haben.  
  
3. Fügen Sie den folgenden Attributnamen und -wert zum Element **assemblyBinding** hinzu:  
  
    |Attributname|Attributwert|  
    |--------------------|---------------------|  
    |**Xmlns**|**urn:schemas-microsoft-com:asm.v1**|  
  
4. Fügen Sie ein Element **dependentAssembly** als untergeordnetes Element des Elements **assemblyBinding** ein.  
  
     Das Element **dependentAssembly** weist keine Attribute auf.  
  
5. Fügen Sie ein Element **assemblyIdentity** als untergeordnetes Element des Elements **dependentAssembly** ein.  
  
6. Fügen Sie den folgenden Attributnamen und -wert zum Element **assemblyIdentity** hinzu:  
  
    |Attributname|Attributwert|  
    |--------------------|---------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7. Fügen Sie ein Element **codeBase** als untergeordnetes Element des Elements **dependentAssembly** ein.  
  
8. Fügen Sie den folgenden Attributnamen und -wert zum Element **codeBase** hinzu:  
  
    |Attributname|Attributwert|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` ist die Datei-URL von Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Wenn [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] am Standardspeicherort installiert ist, sollte der Wert **href**`C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL` entsprechen  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>So fügen Sie den Profilernachbearbeitungsschritt zum Element „configuration/system.web/compilation“ hinzu  
  
1. Fügen Sie, wenn notwendig, das Element **system.web** als untergeordnetes Element des Elements **configuration** ein. Ansonsten fahren Sie mit dem nächsten Schritt fort.  
  
     Das Element **system.web** weist keine Attribute auf. Das Element **configuration** kann nur ein untergeordnetes Element **system.web** haben.  
  
2. Fügen Sie, wenn notwendig, das Element **compilation** als untergeordnetes Element des Elements **system.web** ein. Ansonsten fahren Sie mit dem nächsten Schritt fort.  
  
     Das Element **system.web** kann nur ein untergeordnetes Element **compilation** haben.  
  
3. Entfernen Sie alle vorhandenen Attribute aus dem Element **compilation**, und fügen Sie den folgenden Attributnamen und -wert hinzu:  
  
    |Attributname|Attributwert|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>So fügen Sie Profiler-Speicherorteinstellungen zum Element „configuration/appSettings“ hinzu  
  
1. Fügen Sie, wenn notwendig, das Element **appSettings** als untergeordnetes Element des Elements **configuration** ein. Ansonsten fahren Sie mit dem nächsten Schritt fort.  
  
     Das Element **appSettings** weist keine Attribute auf. Das Element **configuration** kann nur ein untergeordnetes Element **appSettings** haben.  
  
2. Fügen Sie ein Element **add** als untergeordnetes Element des Elements **appSettings** hinzu.  
  
3. Fügen Sie den folgenden Attributnamen und -wert zum Element **add** hinzu:  
  
    |Attributname|Attributwert|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\VSInstr.Exe**|  
  
4. Fügen Sie ein weiteres Element **add** als untergeordnetes Element des Elements **appSettings** hinzu.  
  
5. Fügen Sie den folgenden Attributnamen und -wert zu diesem Element **add** hinzu:  
  
    |Attributname|Attributwert|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` ist der Pfad der ausführbaren Profilerdatei. Wenn [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installiert ist im Standardspeicherort installiert ist, entspricht der Wert **C:\Program Files\Microsoft Visual Studio 10.0 \Team Tools\Performance Tools**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>Beispiel  
 Im Folgenden finden Sie eine vollständige web.config-Datei, die die Instrumentierung und Profilerstellung von dynamisch kompilierten [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen ermöglicht. In diesem Beispiel wird davon ausgegangen, dass es keine anderen Einstellungen in der Datei vor der Änderung gab.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET-Anwendung und Sammeln ausführlicher Zeit Steuerungsdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET-Anwendung und Sammeln von Speicherdaten](/visualstudio/profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data?view=vs-2015)
