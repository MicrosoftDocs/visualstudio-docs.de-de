---
title: Problembehandlung bei Projekt- und Elementvorlagen
description: Erfahren Sie, wie Sie Probleme mit Vorlagen beheben, wenn sie nicht in die Entwicklungsumgebung geladen werden.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 842e34ce18767f5d16cc55d16b8346369fe6cef9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869114"
---
# <a name="how-to-troubleshoot-templates"></a>Vorgehensweise: Problembehandlung bei Vorlagen

Wenn keine Vorlage in der Entwicklungsumgebung geladen werden kann, gibt es einige Möglichkeiten, das Problem zu erfassen.

## <a name="validate-the-vstemplate-file"></a>Überprüfen der VSTEMPLATE-Datei

::: moniker range="vs-2017"

Wenn die *VSTEMPLATE*-Datei in einer Vorlage nicht dem Visual Studio-Vorlagenschema folgt, wird die Vorlage möglicherweise nicht im Dialogfeld **Neues Projekt** angezeigt.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn die *VSTEMPLATE*-Datei in einer Vorlage nicht dem Visual Studio-Vorlagenschema folgt, wird die Vorlage möglicherweise nicht dem Dialogfeld angezeigt, in dem Sie neue Projekte erstellen.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>So überprüfen Sie die VSTEMPLATE-Datei

1. Suchen Sie die *ZIP*-Datei, die die Vorlage enthält.

1. Extrahieren Sie die *ZIP*-Datei.

1. Klicken Sie im Menü **Datei** in Visual Studio auf **Öffnen** > **Datei**.

1. Wählen Sie die *VSTEMPLATE*-Datei für die Vorlage aus, und klicken Sie auf **Öffnen**.

1. Stellen Sie sicher, dass das XML-Format der *VSTEMPLATE*-Datei dem Vorlagenschema folgt. Weitere Informationen zum *VSTEMPLATE*-Schema finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Fügen Sie dem `VSTemplate`-Element ein `xmlns`-Attribut hinzu, und weisen Sie diesem einen Wert von `http://schemas.microsoft.com/developer/vstemplate/2005` zu, um die IntelliSense-Unterstützung während der Erstellung der *VSTEMPLATE*-Datei zu nutzen.

1. Speichern und schließen Sie die *VSTEMPLATE*-Datei.

1. Wählen Sie die Dateien in Ihrer Vorlage aus, klicken Sie mit der rechten Maustaste, und klicken Sie auf **Senden an** > **ZIP-komprimierten Ordner**. Die ausgewählten Dateien werden in eine *ZIP*-Datei komprimiert.

1. Platzieren Sie die neue *ZIP*-Datei in dem Verzeichnis, in dem sich auch die alte *ZIP*-Datei befand.

1. Löschen Sie die extrahierten Vorlagendateien und die alte *ZIP*-Datei der Vorlage.

## <a name="enable-diagnostic-logging"></a>Aktivieren der Diagnoseprotokollierung

Sie können die Diagnoseprotokollierung für die Ermittlung von Vorlagen aktivieren, indem Sie die Schritte unter [Troubleshooting template discovery (Extensibility) (Problembehandlung bei der Ermittlung von Vorlagen (Erweiterbarkeit))](../extensibility/troubleshooting-template-discovery.md) beschrieben befolgen.

## <a name="see-also"></a>Weitere Informationen

- [Troubleshooting template discovery (Extensibility) (Problembehandlung bei der Ermittlung von Vorlagen (Erweiterbarkeit))](../extensibility/troubleshooting-template-discovery.md)
- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
