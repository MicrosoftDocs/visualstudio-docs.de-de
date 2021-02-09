---
title: Befehle, die nach der Installation ausgeführt werden müssen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Befehle, die im Rahmen der Installation einer Erweiterung ausgeführt werden müssen, die über eine MSI-Datei in Visual Studio bereitgestellt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: deca5b39701fd073b3191cf7a24d83ccf1e08794
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884727"
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden müssen
Wenn Sie die Erweiterung über eine *MSI* -Datei bereitstellen, müssen Sie **Devenv/Setup** im Rahmen der Installation ausführen, damit Visual Studio Ihre Erweiterungen ermitteln kann.

> [!NOTE]
> Die Informationen in diesem Thema gelten für die Suche nach *devenv.exe* mit Visual Studio 2008 und früher. Informationen dazu, wie Sie *devenv.exe* mit neueren Versionen von Visual Studio ermitteln, finden Sie unter [Erkennen von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Suchen devenv.exe
 Sie können die *devenv.exe* einer Version aus Registrierungs Werten suchen, die von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installationsprogrammen geschrieben werden. verwenden Sie dazu die reglocator-Tabelle und die AppSearch-Tabellen, um die Registrierungs Werte als Eigenschaften zu speichern. Weitere Informationen finden Sie unter [Erkennen von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Relocator-Tabellenzeilen, um devenv.exe aus verschiedenen Versionen von Visual Studio zu suchen

|Signatur|Root|Schlüssel|Name|type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|Software\microsoft\visualstudio\7.0\setup\vs|Umgebungs Pfad|2|
|RL_DevenvExe_2003|2|Software\microsoft\visualstudio\7,1 \setup\vs|Umgebungs Pfad|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\setup\vs|Umgebungs Pfad|2|
|RL_DevenvExe_2008|2|Software\Microsoft\VisualStudio\9.0\setup\vs|Umgebungs Pfad|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Hiermit werden Tabellenzeilen für entsprechende reglocator-Tabellenzeilen durchsucht.

|Eigenschaft|Signatur|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Der Visual Studio-Installer schreibt z. b. den Registrierungs Wert **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** als *C:\VS2008\Common7\IDE\devenv.exe*, einen kompletten Pfad zur ausführbaren Datei, die vom Installationsprogramm ausgeführt werden muss.

> [!NOTE]
> Da die Typspalte der reglocator-Tabelle 2 ist, ist es nicht erforderlich, zusätzliche Versionsinformationen in der Signatur Tabelle anzugeben.

## <a name="run-devenvexe"></a>Ausführen devenv.exe
 Nachdem die AppSearch-Standardaktion im Installationsprogramm ausgeführt wurde, weist jede Eigenschaft in der AppSearch-Tabelle einen Wert auf, der auf die *devenv.exe* Datei für die zugehörige Version von Visual Studio zeigt. Wenn einer der angegebenen Registrierungs Werte nicht vorhanden ist – da diese Version von Visual Studio nicht installiert ist – wird die angegebene Eigenschaft auf NULL festgelegt.

 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, auf die eine Eigenschaft durch den benutzerdefinierten Aktionstyp 50 zeigt. Die benutzerdefinierte Aktion sollte die in-Script-Ausführungs Optionen `msidbCustomActionTypeInScript` (1024) und `msidbCustomActionTypeCommit` (512) enthalten, um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor es in integriert wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Weitere Informationen finden Sie unter [CustomAction Table](/windows/desktop/msi/customaction-table) und [Custom Action in-Script Execution Options](/windows/desktop/msi/custom-action-in-script-execution-options).

 Benutzerdefinierte Aktionen des Typs 50 geben die Eigenschaft an, die die ausführbare Datei als Wert der Quell Spalte und Befehlszeilenargumente in der Ziel Spalte enthält.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Zu testbare CustomAction-Tabellenzeilen devenv.exe

|Aktion|type|`Source`|Ziel|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Benutzerdefinierte Aktionen müssen in der InstallExecuteSequence-Tabelle erstellt werden, um die Ausführung während der Installation zu planen. Verwenden Sie die entsprechende-Eigenschaft in jeder Zeile der Spalte Bedingung, um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt wird, wenn diese Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht auf dem System installiert ist.

> [!NOTE]
> NULL-Werte `False` werden bei der Verwendung in Bedingungen ausgewertet.

 Der Wert der Sequence-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequenz Werten im Windows Installer Paket ab. Die Sequenzwerte sollten so lauten, dass die *devenv.exe* benutzerdefinierten Aktionen so nah wie möglich ausgeführt werden, unmittelbar vor der Standardaktion InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence-Tabelle, um die devenv.exe benutzerdefinierten Aktionen zu planen

|Aktion|Bedingung|Sequenz|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
