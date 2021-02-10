---
title: 'Vorgehensweise: Konfigurieren der Sicherheit für die Aufnahme Liste'
description: Konfigurieren Sie die ClickOnce-Vertrauensstellungs-Eingabeaufforderung, um zu steuern, ob Endbenutzer Office-Projektmappen installieren können, indem Sie eine Vertrauensstellungs Entscheidung für die Aufnahme Liste
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ddbc74c00c1e1f74ce078586d624e2da4dbd8163
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954019"
---
# <a name="how-to-configure-inclusion-list-security"></a>Vorgehensweise: Konfigurieren der Sicherheit für die Aufnahme Liste
  Wenn Sie über Administrator Berechtigungen verfügen, können Sie die Vertrauensstellungs Aufforderung so konfigurieren, dass Endbenutzer die Möglichkeit haben, Office-Projektmappen [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zu installieren, indem Sie eine Vertrauensstellungs Entscheidung für die Aufnahme Liste speichern. Informationen zu Inklusions Listen finden Sie unter Vertrauen von Office-Projektmappen [mithilfe von Inklusions Listen](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Für Lösungen in den einzelnen fünf Zonen können Sie die folgenden Optionen festlegen:

- Aktivieren Sie den Schlüssel für die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Vertrauenswürdige Eingabeaufforderung und die Aufnahme Liste. Sie können Endbenutzern gestatten, Office-Projektmappen, die mit einem beliebigen Zertifikat signiert sind, Vertrauenswürdigkeit zu gewähren.

- Schränken Sie den Schlüssel für die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Vertrauenswürdigkeit und die Inklusions Liste ein. Sie können Endbenutzern die Installation von Office-Projektmappen gestatten, die mit einem Zertifikat signiert sind, das den Verleger identifiziert, der jedoch noch nicht vertrauenswürdig ist.

- Deaktivieren Sie die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Vertrauensstellungs-und Inklusions Taste. Sie können verhindern, dass Endbenutzer eine Office-Projekt Mappe installieren, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert ist.

## <a name="enable-the-inclusion-list"></a>Aktivieren der Aufnahme Liste
 Aktivieren Sie die Inklusions Liste für eine Zone, wenn Endbenutzern die Option angezeigt werden soll, eine beliebige Office-Projekt Mappe zu installieren und ausführen, die aus dieser Zone stammt.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>So aktivieren Sie die Aufnahme Liste mithilfe des Registrierungs-Editors

1. Öffnen Sie den Registrierungs-Editor:

    1. Klicken Sie im **Startmenü** auf **Ausführen**.

    2. Geben Sie im Feld **Öffnen** **regedt32.exe** ein, und klicken Sie dann auf **OK**.

2. Suchen Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichen folgen Wert** hinzu, wenn Sie noch nicht vorhanden sind, und geben Sie die zugehörigen Werte an.

    |Zeichen folgen Wert-Unterschlüssel|Wert|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**Nicht treudsites**|**Deaktiviert**|
    |**MyComputer**|**Enabled**|
    |**LocalIntranet**|**Enabled**|
    |**TrustedSites**|**Enabled**|

     Standardmäßig hat das **Internet** den Wert **AuthenticodeRequired** , und der Wert von **untreudsites** ist **deaktiviert**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>So aktivieren Sie die Aufnahme Liste Programm gesteuert

1. Erstellen Sie eine Visual Basic-oder Visual c#-Konsolenanwendung.

2. Öffnen Sie die Datei " *Program. vb* " oder " *Program.cs* " zum Bearbeiten, und fügen Sie folgenden Code hinzu.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Erstellen Sie die Anwendung, und führen Sie sie aus.

## <a name="restrict-the-inclusion-list"></a>Einschränken der Aufnahme Liste
 Schränken Sie die Aufnahme Liste ein, damit Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die eine bekannte Identität aufweisen, bevor Benutzer zur Eingabe einer Vertrauensstellungs Entscheidung aufgefordert werden.

### <a name="to-restrict-the-inclusion-list"></a>So schränken Sie die Aufnahme Liste ein

1. Öffnen Sie den Registrierungs-Editor:

    1. Klicken Sie im **Startmenü** auf **Ausführen**.

    2. Geben Sie im Feld **Öffnen** **regedt32.exe** ein, und klicken Sie dann auf **OK**.

2. Suchen Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichen folgen Wert** hinzu, wenn Sie noch nicht vorhanden sind, und geben Sie die zugehörigen Werte an.

    |Zeichen folgen Wert-Unterschlüssel|Wert|
    |-------------------------|-----------|
    |**Nicht treudsites**|**Deaktiviert**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Standardmäßig hat das **Internet** den Wert **AuthenticodeRequired** , und der Wert von **untreudsites** ist **deaktiviert**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>So schränken Sie die Aufnahme Liste Programm gesteuert ein

1. Erstellen Sie eine Visual Basic-oder Visual c#-Konsolenanwendung.

2. Öffnen Sie die Datei " *Program. vb* " oder " *Program.cs* " zum Bearbeiten, und fügen Sie folgenden Code hinzu.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Erstellen Sie die Anwendung, und führen Sie sie aus.

## <a name="disable-the-inclusion-list"></a>Deaktivieren der Aufnahme Liste
 Sie können die Aufnahme Liste deaktivieren, damit Endbenutzer nur Lösungen installieren können, die mit einem vertrauenswürdigen und bekannten Zertifikat signiert sind.

### <a name="to-disable-the-inclusion-list"></a>So deaktivieren Sie die Aufnahme Liste

1. Öffnen Sie den Registrierungs-Editor:

    1. Klicken Sie im **Startmenü** auf **Ausführen**.

    2. Geben Sie im Feld **Öffnen** **regedt32.exe** ein, und klicken Sie dann auf **OK**.

2. Erstellen Sie den folgenden Registrierungsschlüssel, wenn dieser nicht bereits vorhanden ist:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Fügen Sie die folgenden Unterschlüssel als **Zeichen folgen Wert** hinzu, wenn Sie noch nicht vorhanden sind, und geben Sie die zugehörigen Werte an.

    |Zeichen folgen Wert-Unterschlüssel|Wert|
    |-------------------------|-----------|
    |**Nicht treudsites**|**Deaktiviert**|
    |**Internet**|**Deaktiviert**|
    |**MyComputer**|**Deaktiviert**|
    |**LocalIntranet**|**Deaktiviert**|
    |**TrustedSites**|**Deaktiviert**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>So deaktivieren Sie die Aufnahme Liste Programm gesteuert

1. Erstellen Sie eine Visual Basic-oder Visual c#-Konsolenanwendung.

2. Öffnen Sie die Datei " *Program. vb* " oder " *Program.cs* " zum Bearbeiten, und fügen Sie folgenden Code hinzu.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Erstellen Sie die Anwendung, und führen Sie sie aus.

## <a name="see-also"></a>Weitere Informationen
- [Vertrauen von Office-Projektmappen mithilfe von Inklusions Listen](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
