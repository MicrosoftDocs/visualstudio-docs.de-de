---
title: -LCID („devenv.exe“)
description: Hier erfahren Sie, wie Sie mithilfe der devenv-Befehlszeilenoption „LCID“ die Standardsprache festlegen, die für Text, Währungen und andere Werte in der IDE verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e5aad581babafe882fccc13e8594aa60437d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852140"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Legt die Standardsprache für Text, Währungen und andere Werte in der IDE fest.

## <a name="syntax"></a>Syntax

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumente

- *LocaleID*

  Erforderlich. Die Gebietsschema-ID der Sprache, die Sie angeben.

## <a name="remarks"></a>Bemerkungen

Lädt die IDE und legt die natürliche Standardsprache für die Umgebung fest. Diese Änderung wird zwischen den Sitzungen beibehalten, und die IDE zeigt diese Änderung in **Tools** > **Optionen** > **Umgebung** > **Internationale Einstellungen** > **Sprache** an.

Wenn die angegebene Sprache in Ihrem System nicht vorhanden ist, wird der `/LCID`-Schalter ignoriert.

In der folgenden Tabelle sind die LCIDs der von Visual Studio unterstützten Sprachen aufgeführt.

|Sprache|LCID|
|--------------|----------|
|Chinesisch (vereinfacht)|2052|
|Chinesisch (traditionell)|1028|
|Tschechisch|1029|
|Englisch|1033|
|Französisch|1036|
|Deutsch|1031|
|Italienisch|1040|
|Japanisch|1041|
|Koreanisch|1042|
|Polnisch|1045|
|Portugiesisch (Brasilien)|1046|
|Russisch|1049|
|Spanisch|3082|
|Türkisch|1.055

## <a name="example"></a>Beispiel

In diesem Beispiel wird die IDE mit englischen Ressourcenzeichenfolgen geladen.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Internationale Einstellungen, Umgebung, Dialogfeld „Optionen“](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)
