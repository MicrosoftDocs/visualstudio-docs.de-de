---
title: Angeben des Speicher Orts der VSPackage-Datei für die vs-Shell | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie es Visual Studio ermöglichen können, die assemblydll zu finden, um das VSPackage zu laden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12034ef884fafda2e3e09722b9bb187ed7a1cbb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969970"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Angeben des VSPackage-Dateispeicherorts für die VS Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muss in der Lage sein, die assemblydll zu finden, um das VSPackage zu laden. Sie finden es auf verschiedene Arten, wie in der folgenden Tabelle beschrieben.

| Methode | BESCHREIBUNG |
| - | - |
| Verwenden Sie den Registrierungsschlüssel CodeBase. | Der CodeBase-Schlüssel kann verwendet werden, um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die VSPackage-Assembly von einem beliebigen voll qualifizierten Dateipfad zu laden. Der Wert des Schlüssels sollte der Dateipfad zur DLL sein. Dies ist die beste Möglichkeit, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ihre paketassembly zu laden. Diese Technik wird manchmal auch als "CodeBase/private Installation Directory-Technik" bezeichnet. Während der Registrierung wird der Wert der Codebasis über eine Instanz des Typs an die Registrierungs Attribut Klassen übermittelt <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> . |
| Platzieren Sie die dll im Verzeichnis **privateassemblys** . | Platzieren Sie die Assembly im Unterverzeichnis **privateassemblys** des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verzeichnisses. Assemblys, die sich in **privateassemblys** befinden, werden automatisch erkannt, sind aber im Dialogfeld **Verweise hinzufügen** nicht sichtbar. Der Unterschied  zwischen privateassemassemblys und **PublicAssemblies** besteht darin, dass Assemblys in **PublicAssemblies** im Dialogfeld **Verweise hinzufügen** aufgelistet werden. Wenn Sie die Methode "CodeBase/private Installation Directory" nicht verwenden möchten, sollten Sie im Verzeichnis " **privateassemblys** " installieren. |
| Verwenden Sie eine Assembly mit starkem Namen und den assemblyregistrierungsschlüssel. | Der Assemblyschlüssel kann verwendet werden, um explizit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine starke benannte VSPackage-Assembly zu laden. Der Wert des Schlüssels muss der starke Name der Assembly sein. |
| Platzieren Sie die dll im Verzeichnis **PublicAssemblies** . | Schließlich kann die Assembly auch in das Unterverzeichnis **PublicAssemblies** eingefügt werden. Assemblys, die sich in **PublicAssemblies** befinden, werden automatisch erkannt. Sie werden auch im Dialogfeld **Verweise hinzufügen** in angezeigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> VSPackage-Assemblys sollten nur im Verzeichnis **PublicAssemblies** abgelegt werden, wenn Sie verwaltete Komponenten enthalten, die von anderen VSPackage-Entwicklern wieder verwendet werden sollen. Der Großteil der Assemblys erfüllt dieses Kriterium nicht. |

> [!NOTE]
> Verwenden Sie mit starkem Namen signierte Assemblys für alle abhängigen Assemblys. Diese Assemblys sollten auch in Ihrem eigenen Verzeichnis oder im globalen Assemblycache (GAC) installiert werden. Dies schützt vor Konflikten mit Assemblys mit dem gleichen Basis Dateinamen, die als Bindung mit schwachem Namen bezeichnet werden.
