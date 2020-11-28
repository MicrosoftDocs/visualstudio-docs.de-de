---
title: Aktualisieren vorhandener Projektelementvorlagen
description: Erfahren Sie, wie Sie mithilfe des Assistenten zum Exportieren von Vorlagen und anderer manueller Prozesse Projektelementvorlagen, die Sie bereits erstellt haben, aktualisieren.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e3a709070d777ebaf600fc05abf0e651eaef5b1a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596884"
---
# <a name="how-to-update-existing-templates"></a>Vorgehensweise: Aktualisieren vorhandener Vorlagen

Nachdem Sie eine Vorlage erstellt und die Dateien in eine *ZIP*-Datei komprimiert haben, sollten Sie die Vorlage ändern. Dazu können Sie die Dateien in der Vorlage manuell ändern oder aber eine neue Vorlage aus einem Projekt exportieren, das auf der Vorlage basiert.

## <a name="use-the-export-template-wizard"></a>Verwenden des Assistenten zum Exportieren von Vorlagen

Visual Studio stellt den **Assistenten zum Exportieren von Vorlagen** bereit, der zum Aktualisieren einer vorhandenen Vorlage verwendet werden kann:

1. Wählen Sie **Datei** > **Neu** > **Projekt** aus der Menüleiste aus.

1. Wählen Sie die Vorlage aus, die Sie aktualisieren möchten, und führen Sie die Schritte zum Erstellen eines neuen Projekts aus.

1. Bearbeiten Sie das Projekt in Visual Studio. Ändern Sie beispielsweise den Ausgabetyp, oder fügen Sie dem Projekt eine neue Datei hinzu.

1. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.

    Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.

1. Befolgen Sie die Anweisungen im Assistenten, um die Vorlage als *ZIP*-Datei zu exportieren.

1. (Optional) Speichern Sie die *ZIP*-Datei im folgenden Verzeichnis: *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*, um es zur Auswahl verfügbar zu machen. Sie müssen diesen Schritt ausführen, wenn Sie im **Assistenten zum Exportieren von Vorlagen** nicht die Option **Vorlage automatisch in Visual Studio importieren** ausgewählt haben.

1. Löschen Sie die alte *ZIP*-Vorlagendatei.

## <a name="manually-update-an-existing-template"></a>Manuelles Aktualisieren einer vorhandenen Vorlage

Sie können eine vorhandene Vorlage ohne den **Assistenten zum Exportieren von Vorlagen** aktualisieren, indem Sie die in der komprimierten *ZIP*-Datei enthaltenen Dateien ändern.

### <a name="to-manually-update-an-existing-template"></a>So aktualisieren Sie eine vorhandene Vorlage manuell

1. Suchen Sie die *ZIP*-Datei, die die Vorlage enthält. Benutzerprojektvorlagen werden in der Regel unter *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates* gespeichert.

1. Extrahieren Sie die *ZIP*-Datei.

1. Ändern oder löschen Sie die aktuellen Vorlagendateien, oder fügen Sie der Vorlage neue Dateien hinzu.

1. Öffnen, ändern und speichern Sie die XML-Datei mit der Erweiterung *.vstemplate*, damit das geänderte Verhalten bzw. neue Dateien berücksichtigt werden.

    Weitere Informationen zum *VSTEMPLATE*-Schema finden Sie unter Visual Studio [Template Schema Reference (Extensibility) (Schemareferenz zu Vorlagen für Visual Studio (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md). Weitere Informationen darüber, welche Elemente in den Quelldateien parametrisiert werden können, finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

1. Wählen Sie die Dateien in Ihrer Vorlage aus, führen Sie einen Rechtsklick durch, oder klicken Sie auf das Kontextmenü, und wählen Sie **Senden an** > **ZIP-komprimierter Ordner** aus.

    Die ausgewählten Dateien werden in eine *ZIP*-Datei komprimiert.

1. Fügen Sie die neue *ZIP*-Datei in das Verzeichnis ein, in dem sich auch die alte *ZIP*-Datei befand.

1. Löschen Sie die extrahierten Vorlagendateien und die alte *ZIP*-Datei der Vorlage.

## <a name="see-also"></a>Siehe auch

- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Vorlagenparameter](../ide/template-parameters.md)
