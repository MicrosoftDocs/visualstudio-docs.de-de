---
title: '&lt;TrustInfo- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
description: Das trustInfo-Element beschreibt die minimalen Sicherheits Berechtigungen, die erforderlich sind, damit die Anwendung auf dem Client Computer ausgeführt wird. Das trustInfo-Element ist erforderlich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6779471edc25435f14511cc2ebcc34e6247225ee
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349216"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt;-Element (ClickOnce-Anwendung)
Beschreibt die Mindestsicherheitsberechtigungen, die zum Ausführen der Anwendung auf dem Clientcomputer erforderlich sind.

## <a name="syntax"></a>Syntax

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `trustInfo` -Element ist erforderlich und befindet sich im `asm.v2` -Namespace. Es besitzt keine Attribute und enthält die folgenden Elemente.

## <a name="security"></a>security
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `trustInfo` -Elements. Es enthält das `applicationRequestMinimum` -Element und besitzt keine Attribute.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `security` -Elements und enthält die Elemente `PermissionSet`, `assemblyRequest`und `defaultAssemblyRequest`. Dieses Element weist keine Attribute auf.

## <a name="permissionset"></a>PermissionSet
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `applicationRequestMinimum` -Elements und enthält das `IPermission` -Element. Dieses Element weist folgende Attribute auf.

- `ID`

     Erforderlich. Bezeichnet den Berechtigungssatz. Dieses Attribut kann beliebige Werte annehmen. Auf die ID wird in den Attributen `defaultAssemblyRequest` und `assemblyRequest` verwiesen.

- `version`

     Erforderlich. Bezeichnet die Version der Berechtigung. Normalerweise ist dieser Wert `1`.

## <a name="ipermission"></a>IPermission
 Optional. Dieses Element ist ein untergeordnetes Element des `PermissionSet` -Elements. Das- `IPermission` Element identifiziert vollständig eine Berechtigungs Klasse in der .NET Framework. Das `IPermission` -Element besitzt die folgenden Attribute, kann aber zusätzliche Attribute aufweisen, die den Eigenschaften der Berechtigungsklasse entsprechen. In der Security.config-Datei finden Sie Beispiele, mit denen Sie die Syntax einer bestimmten Berechtigung ermitteln können.

- `class`

     Erforderlich. Bezeichnet die Berechtigungsklasse mit einem starken Namen. Beispielsweise identifiziert der folgende Code den Typ `FileDialogPermission` .

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     Erforderlich. Bezeichnet die Version der Berechtigung. Normalerweise ist dieser Wert `1`.

- `Unrestricted`

     Erforderlich. Bestimmt, ob für die Anwendung eine unbeschränkte Erteilung dieser Berechtigung erforderlich ist. Bei `true`ist die Erteilung der Berechtigung ohne Bedingungen. Bei `false`oder nicht definiertem Attribut erfolgt die Erteilung gemäß den berechtigungsspezifischen Attributen, die im `IPermission` -Tag definiert sind. Betrachten wir die folgenden Berechtigungen:

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     In diesem Beispiel schränkt die Deklaration für <xref:System.Security.Permissions.EnvironmentPermission> die Anwendung auf das ausschließliche Lesen der Umgebungsvariablen USERNAME ein, während die Deklaration für <xref:System.Security.Permissions.FileDialogPermission> der Anwendung die uneingeschränkte Verwendung aller <xref:System.Windows.Forms.FileDialog> -Klassen erlaubt.

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 Optional. Bezeichnet den allen Assemblys erteilten Berechtigungssatz. Dieses Element ist ein untergeordnetes Element des `applicationRequestMinimum` -Elements und weist folgende Attribute auf.

- `permissionSetReference`

     Erforderlich. Bezeichnet die ID des Berechtigungssatzes, der die Standardberechtigung bildet. Der Berechtigungssatz wird im `PermissionSet` -Element deklariert.

## <a name="assemblyrequest"></a>assemblyRequest
 Optional. Bezeichnet die Berechtigungen für eine bestimmte Assembly. Dieses Element ist ein untergeordnetes Element des `applicationRequestMinimum` -Elements und weist folgende Attribute auf.

- `Name`

     Erforderlich. Bezeichnet den Assemblynamen.

- `permissionSetReference`

     Erforderlich. Bezeichnet die ID des Berechtigungssatzes, der für diese Assembly erforderlich ist. Der Berechtigungssatz wird im `PermissionSet` -Element deklariert.

## <a name="requestedprivileges"></a>requestedPrivileges
 Optional. Dieses Element ist ein untergeordnetes Element des `security` -Elements und enthält das `requestedExecutionLevel` -Element. Dieses Element weist keine Attribute auf.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 Optional. Bezeichnet die Sicherheitsstufe, die von der Anwendung für die Ausführung angefordert wird. Dieses Element hat keine untergeordneten Elemente und weist folgende Attribute auf.

- `Level`

   Erforderlich. Bezeichnet die Sicherheitsstufe, die von der Anwendung angefordert wird. Mögliche Werte:

   `asInvoker`, es werden keine zusätzlichen Berechtigungsstufen angefordert. Für diese Stufe sind keine zusätzlichen Eingaben für die Vertrauensstellung erforderlich.

   `highestAvailable`, es werden die höchsten für den übergeordneten Prozess verfügbaren Berechtigungen angefordert.

   `requireAdministrator`, es werden vollständige Administratorberechtigungen angefordert.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungen können nur mit dem Wert `asInvoker`installiert werden. Bei der Installation mit anderen Werten tritt ein Fehler auf.

- `uiAccess`

   Optional. Gibt an, ob die Anwendung Zugriff auf geschützte Elemente der Benutzeroberfläche benötigt. Die Werte sind `true` und `false`, und der Standardwert ist „false“. Nur signierte Anwendungen sollten den Wert „true“ haben.

## <a name="remarks"></a>Hinweise
 Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mehr Berechtigungen anfordert, als der Clientcomputer standardmäßig erteilt, fragt der Trust-Manager der Common Language Runtime beim Benutzer nach, ob er der Anwendung die höhere Vertrauensstellung einräumen möchte. Wenn er ablehnt, wird die Anwendung nicht ausgeführt; andernfalls wird sie mit den angeforderten Berechtigungen ausgeführt.

 Alle mithilfe von `defaultAssemblyRequest` und `assemblyRequest` angeforderten Berechtigungen werden ohne Nachfrage beim Benutzer erteilt, wenn das Bereitstellungsmanifest eine gültige Vertrauenslizenz aufweist.

 Weitere Informationen zur Berechtigungs Erweiterung finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md). Weitere Informationen zur Bereitstellung von Richtlinien finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

## <a name="examples"></a>Beispiele
 Die folgenden drei Codebeispiele veranschaulichen `trustInfo` -Elemente für die benannten Standardsicherheitszonen – Internet, Lokales Intranet und Vertrauenswürdige Sites – für die Verwendung im Anwendungsmanifest einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Bereitstellung.

 Das erste Beispiel zeigt das `trustInfo` -Element für die in der Sicherheitszone „Internet“ verfügbaren Standardberechtigungen.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 Das zweite Beispiel zeigt das `trustInfo` -Element für die in der Sicherheitszone „Lokales Intranet“ verfügbaren Standardberechtigungen.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 Das dritte Beispiel zeigt das `trustInfo` -Element für die in der Sicherheitszone „Vertrauenswürdige Sites“ verfügbaren Standardberechtigungen.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über bereit Stellungen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)