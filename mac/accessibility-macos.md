---
title: Verwenden von macOS-Optionen für Barrierefreiheit
description: Informationen zum Verwenden von macOS-Optionen und -Features für die Barrierefreiheit, z. B. hoher Kontrast, Tastaturnavigation und VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998385"
---
# <a name="accessibility-features-of-macos"></a>Barrierefreiheitsfunktionen von macOS

macOS ist ein barrierefreies Betriebssystem, das eine Reihe von Features bietet, um Personen mit unterschiedlichen Fähigkeiten die Bedienung zu ermöglichen. Diese Features umfassen einen Modus mit hohem Kontrast, Tastaturnavigationsoptionen und VoiceOver-Funktionen (die macOS-Sprachausgabe).

## <a name="enable-accessibility-features"></a>Aktivieren von Barrierefreiheitsfunktionen

In Visual Studio für Mac ist die Unterstützung für Hilfstechnologien standardmäßig deaktiviert. So aktivieren Sie die Unterstützung der Barrierefreiheit:

1. Wechseln Sie zu **Visual Studio (Menü)**  > **Einstellungen** > **Weitere**, und wählen Sie **Barrierefreiheit** aus.

1. Aktivieren Sie das Kontrollkästchen **Barrierefreiheit aktivieren**.

   ![Screenshot der Barrierefreiheitseinstellungen, „Barrierefreiheit aktivieren“ ausgewählt](media/accessibility-preferences.png)

1. Wählen Sie **Visual Studio neu starten** aus, um die Unterstützung für die Hilfstechnologien von Apple zu aktivieren.

Alternativ dazu können Sie die Barrierefreiheitsfunktionen über die Befehlszeile aktivieren. Geben Sie im Terminal folgenden Befehl ein:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Nachdem Sie diese Einstellung über die Befehlszeile geändert haben, müssen Sie Visual Studio neu starten.

## <a name="increase-the-contrast-in-macos"></a>Erhöhen des Kontrasts unter macOS

Visual Studio für Mac unterstützt einen höheren Kontrast unter macOS, wodurch Farbkontraste für Benutzeroberflächenelemente verstärkt und Konturen besser definiert werden. So aktivieren Sie diese Einstellung:

1. Öffnen Sie die **Systemeinstellungen**.

1. Wechseln Sie zu **Barrierefreiheit**, und wählen Sie **Anzeigen** aus.

1. Aktivieren Sie das Kontrollkästchen **Kontrast erhöhen**.
