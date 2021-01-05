---
title: Ändern der F1-Hilfetaste
description: Beschreibt, wie die F1-Tastenzuordnung geändert oder entfernt wird.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jillfra
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: d9add6996949a97d6140ab6d063f13e02b677e79
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684079"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Ändern der F1-Hilfetaste in Visual Studio

Wenn Sie die F1-Taste für eine andere Funktion als den F1-Hilfedienst verwenden oder die Hilfe mit F1 einfach deaktivieren möchten, können Sie die Tastenzuordnung entfernen oder ändern.

> [!IMPORTANT]
> Wenn Sie die F1-Hilfe aufgrund von Leistungsproblemen deaktivieren möchten, sollten Sie die Tastenzuordnung temporär ändern, sodass Sie Verbesserungen des F1-Hilfediensts in Visual Studio-Updates testen können. In den meisten Szenarien ist F1 eine einfache Möglichkeit zum Öffnen von Verweisseiten für Sprachschlüsselwörter und APIs aus dem Code-Editor oder zum Öffnen von Hilfeseiten, die mit Windows- oder Benutzeroberflächenelementen in der IDE verknüpft sind. Wenn Sie dies deaktivieren, gilt die Deaktivierung für alle Verwendungszwecke in Visual Studio.

**So deaktivieren Sie die F1-Hilfe:**

1. Wählen Sie in Visual Studio **Tools** > **Optionen** und dann unter **Umgebung** die Option **Tastatur** aus.

1. Geben Sie im Textfeld **Befehle mit folgendem Inhalt anzeigen** **Help.f1** ein, um die Ansicht der Befehle zu filtern.

   ![Deaktivieren von F1-Hilfe](../not-in-toc/media/disable-f1-help-key.png)

1. Wählen Sie **Entfernen** aus, um die Tastenzuordnung zu entfernen.

1. Wählen Sie das Textfeld **Tastenkombination** drücken aus.

1. Drücken Sie auf der Tastatur eine neue Taste oder Tastenkombination für die F1-Hilfe, z. B. **Alt + F1**, wählen Sie **Zuweisen** und dann **OK** aus.

Weitere Informationen zur Einstellung von Tastenkombinationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
