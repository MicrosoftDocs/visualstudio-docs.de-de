---
title: 'Vorgehensweise: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine VSIX-Paket Bereitstellung einrichten, mit der alle Abhängigkeiten installiert werden, die nicht bereits auf dem Zielcomputer vorhanden sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb035f9174085667eb229ab5003d8f997eaae84a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953031"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Vorgehensweise: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket

Sie können eine VSIX-Paket Bereitstellung einrichten, mit der alle Abhängigkeiten installiert werden, die nicht bereits auf dem Zielcomputer vorhanden sind. Fügen Sie hierzu die VSIX-Abhängigkeiten in die Datei " *Source. Extension. vsixmanifest* " ein.

## <a name="to-add-a-dependency"></a>So fügen Sie eine Abhängigkeit hinzu

1. Öffnen Sie die Datei " *Source. Extension. vsixmanifest* " in der **Entwurfs** Ansicht. Wechseln Sie zur Registerkarte **Abhängigkeiten** , und klicken Sie auf **neu**.

2. So fügen Sie eine installierte Erweiterung hinzu: Wählen Sie im Dialogfeld **neue Abhängigkeit hinzufügen** die Option **installierte Erweiterung** aus, und wählen Sie dann als **Name** eine Erweiterung in der Liste aus.

3. Um eine weitere VSIX hinzuzufügen, die nicht installiert ist: Wählen Sie im Dialogfeld **neue Abhängigkeit hinzufügen** die Option **Datei im Dateisystem** aus, und wählen Sie dann die VSIX mithilfe der Schaltfläche **Durchsuchen** aus.

## <a name="require-a-specific-visual-studio-release"></a>Bestimmte Visual Studio-Version erforderlich

Wenn Ihre Erweiterung eine bestimmte Version von Visual Studio 2017 erfordert, z. b. von einer in 15,3 veröffentlichten Funktion, können Sie die Buildnummer in Ihrem VSIX- **installationtarget** angeben. Release 15,3 hat z. b. die Buildnummer "15.0.26730.3". [Hier](../install/visual-studio-build-numbers-and-release-dates.md)können Sie die Zuordnung von Releases zu Buildnummern sehen. Beachten Sie, dass die Verwendung der Releasenummer "15,3" nicht ordnungsgemäß funktioniert.

Wenn Ihre Erweiterung 15,3 oder höher erfordert, deklarieren Sie die **installationtarget-Version** als [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Das vsixinstaller erkennt frühere Versionen von Visual Studio und informiert den Benutzer darüber, dass ein späteres Update erforderlich ist.

## <a name="see-also"></a>Weitere Informationen

- [VSIX-Erweiterungs Schema 1,0-Referenz](/previous-versions/dd393700(v=vs.110))
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [Vorbereiten von Erweiterungen für Windows Installer Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)