---
title: Registrieren und Aufheben der Registrierung von VSPackages | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ihre VSPackages registrieren und die Registrierung aufheben, einschließlich der von Ihnen verwendeten Attribute und der pkgdef-Datei.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b60844826387c2807eedcb47fe24c11a58af80f
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97862881"
---
# <a name="register-and-unregister-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages
Sie verwenden Attribute, um ein VSPackage zu registrieren, aber

## <a name="register-a-vspackage"></a>Ein VSPackage registrieren
 Mithilfe von Attributen können Sie die Registrierung verwalteter VSPackages steuern. Alle Registrierungsinformationen sind in einer *pkgdef* -Datei enthalten. Weitere Informationen zur dateibasierten Registrierung finden Sie unter dem [Hilfsprogramm](../extensibility/internals/createpkgdef-utility.md)"|".

 Der folgende Code zeigt, wie Sie das VSPackage mit den standardmäßigen Registrierungs Attributen registrieren.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Aufheben der Registrierung einer Erweiterung
 Wenn Sie viele verschiedene VSPackages ausprobiert haben und diese aus der experimentellen Instanz entfernen möchten, können Sie einfach den **Reset** -Befehl ausführen. Suchen Sie auf der Startseite des Computers nach **Zurücksetzen der experimentellen Instanz von Visual Studio** , oder führen Sie den folgenden Befehl über die Befehlszeile aus:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Wenn Sie eine Erweiterung deinstallieren möchten, die Sie in Ihrer Entwicklungs Instanz von Visual Studio installiert haben, wechseln **Sie zu Extras**  >  **Erweiterungen und Updates**, suchen Sie die Erweiterung, und klicken Sie auf **deinstallieren**.

 Wenn die Erweiterung der Erweiterung aus irgendeinem Grund von keiner dieser Methoden erfolgreich deinstalliert wird, können Sie die Registrierung der VSPackage-Assembly wie folgt von der Befehlszeile aus aufheben:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Verwenden eines benutzerdefinierten Registrierungs Attributs zum Registrieren einer Erweiterung

In bestimmten Fällen müssen Sie möglicherweise ein neues Registrierungs Attribut für die Erweiterung erstellen. Mit Registrierungs Attributen können Sie neue Registrierungsschlüssel hinzufügen oder vorhandenen Schlüsseln neue Werte hinzufügen. Das neue Attribut muss von abgeleitet sein <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , und es muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> -Methode und die-Methode überschreiben <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>Erstellen eines benutzerdefinierten Attributs

Der folgende Code zeigt, wie ein neues Registrierungs Attribut erstellt wird.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Der <xref:System.AttributeUsageAttribute> wird für Attribut Klassen verwendet, um das Programmelement (Klasse, Methode usw.) anzugeben, auf das sich das Attribut bezieht, ob es mehrmals verwendet werden kann und ob es vererbt werden kann.

### <a name="create-a-registry-key"></a>Registrierungsschlüssel erstellen

Im folgenden Code erstellt das benutzerdefinierte Attribut unter dem Schlüssel für das VSPackage, das registriert wird, einen **benutzerdefinierten** Unterschlüssel.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Erstellen Sie einen neuen Wert unter einem vorhandenen Registrierungsschlüssel.

Sie können einem vorhandenen Schlüssel benutzerdefinierte Werte hinzufügen. Der folgende Code zeigt, wie Sie einen neuen Wert zu einem VSPackage-Registrierungsschlüssel hinzufügen.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
