---
title: AutoWiederherstellen, Umgebung, Dialogfeld "Optionen"
description: Erfahren Sie mehr über die Option „AutoWiederherstellen“ unter „Umgebung“ im Dialogfeld „Optionen“ und ihre Verwendung, um anzugeben, ob Dateien automatisch gesichert werden sollen.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9a90198ce4cf3dc54eedbf80bbf4ffbad634cbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836487"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoWiederherstellen, Umgebung, Dialogfeld „Optionen“

Verwenden Sie diese Seite im Dialogfeld **Optionen**, um anzugeben, ob Dateien automatisch gesichert werden sollen oder nicht. Sie können außerdem angeben, ob geänderte Dateien wiederhergestellt werden sollen, wenn Visual Studio unerwartet beendet wird.

Um dieses Dialogfeld zu öffnen, navigieren Sie zu **Extras** > **Optionen** > **Umgebung** > **AutoWiederherstellen**.

:::image type="content" source="media/autorecover-options.png" alt-text="Screenshot des Abschnitts „AutoWiederherstellen“ im Dialogfeld „Optionen“":::

**AutoWiederherstellen-Informationen speichern alle [n] Minuten**

::: moniker range="vs-2019"

Verwenden Sie diese Option, um anzupassen, wie oft eine Datei automatisch im Editor gespeichert wird. Für zuvor gespeicherte Dateien speichert Visual Studio 2019 Version 16.2 oder höher eine Kopie der Datei unter ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles\\[Projektname]***. Wenn es sich um eine neue Datei handelt und diese noch nicht gespeichert wurde, wird sie von Visual Studio mit einem zufällig generierten Dateinamen automatisch gespeichert.

> [!NOTE]
> Wenn Sie Visual Studio 2019 Version 16.1 oder früher verwenden, ist der Speicherort unter *%USERPROFILE%\Documents\Visual Studio [version]\Backup Files\\[Projektname]* . Weitere Informationen finden Sie auf der Seite [Verlauf der Versionshinweisen zu Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/).

::: moniker-end

::: moniker range="vs-2017"

Verwenden Sie diese Option, um anzupassen, wie oft eine Datei automatisch im Editor gespeichert wird. Bei zuvor gespeicherten Dateien wird eine Kopie der Datei von Visual Studio 2017 unter *%USERPROFILE%\Documents\Visual Studio [Version]\Backup Files\\[Projektname]* gespeichert. Wenn es sich um eine neue Datei handelt und diese noch nicht gespeichert wurde, wird sie von Visual Studio mit einem zufällig generierten Dateinamen automatisch gespeichert.

::: moniker-end

**Informationen für AutoWiederherstellen beibehalten für [n] Tage**

Verwenden Sie diese Option, um anzugeben, wie lange Visual Studio Dateien für die automatische Wiederherstellung beibehält.

### <a name="see-also"></a>Weitere Informationen

- [Optionen (Dialogfeld)](../../ide/reference/options-dialog-box-visual-studio.md)
