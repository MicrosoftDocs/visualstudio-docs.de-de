---
title: Erkennen von System Anforderungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Microsoft Windows Installer so konfigurieren, dass Systemanforderungen, z. b. die installierte Edition von Visual Studio, erkannt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20287ba123c5736c9eb7077622623f4a739bde5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963470"
---
# <a name="detect-system-requirements"></a>Systemanforderungen erkennen
Ein VSPackage ist nicht funktionsfähig, es sei denn, Visual Studio ist installiert. Wenn Sie Microsoft Windows Installer zum Verwalten der Installation des VSPackages verwenden, können Sie den Installer so konfigurieren, dass erkannt wird, ob Visual Studio installiert ist. Sie können es auch so konfigurieren, dass das System auf andere Anforderungen, z. b. eine bestimmte Version von Windows oder eine bestimmte Größe von RAM, überprüft wird.

## <a name="detect-visual-studio-editions"></a>Erkennen von Visual Studio-Editionen
 Um zu ermitteln, ob eine Edition von Visual Studio installiert ist, vergewissern Sie sich, dass der Wert des Registrierungsschlüssels " **install** " *(REG_DWORD) 1* im entsprechenden Ordner lautet, wie in der folgenden Tabelle aufgeführt. Beachten Sie, dass es eine Hierarchie von Visual Studio-Editionen gibt:

1. Enterprise

2. Professionell

3. Community

Wenn eine neuere Edition installiert ist, werden die Registrierungsschlüssel für diese Edition sowie für frühere Editionen hinzugefügt. Das heißt, wenn die Enterprise Edition installiert ist, wird der **Installations** Schlüssel auf *1* für Unternehmen sowie für die Editionen Professional und Community festgelegt. Daher müssen Sie nur die aktuelle benötigte Edition überprüfen.

> [!NOTE]
> In der 64-Bit-Version des Registrierungs-Editors werden unter **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\** 32-Bit-Schlüssel angezeigt. Die Visual Studio-Schlüssel befinden sich unter **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Produkt|Schlüssel|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (integriert und isoliert)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Erkennen, wenn Visual Studio ausgeführt wird
 Das VSPackage kann nicht ordnungsgemäß registriert werden, wenn Visual Studio ausgeführt wird, wenn das VSPackage installiert ist. Der Installer muss erkennen, wenn Visual Studio ausgeführt wird, und dann die Installation des Programms ablehnen. Mit Windows Installer können Sie keine Tabelleneinträge verwenden, um eine solche Erkennung zu aktivieren. Stattdessen müssen Sie eine benutzerdefinierte Aktion wie folgt erstellen: Verwenden Sie die `EnumProcesses` Funktion, um den *devenv.exe* Prozess zu erkennen, und legen Sie dann entweder eine installereigenschaft fest, die in einer Startbedingung verwendet wird, oder bedingt ein Dialogfeld, in dem der Benutzer aufgefordert wird, Visual Studio zu schließen.

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
