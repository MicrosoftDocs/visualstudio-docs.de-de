---
title: Workflow-Designer-Shellfunktionen
description: Erfahren Sie, wie die Workflow-Designer Shellfeatures eine Reihe von Schaltflächen zum Verwalten der aktuellen Ansicht enthalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 239a879fbffe67bf54149ba29e98edcd3428410d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433647"
---
# <a name="workflow-designer-shell-features"></a>Workflow-Designer-Shellfunktionen

Workflow-Designer besteht aus drei Hauptbereichen der Benutzeroberfläche: der Designer Oberfläche, der Breadcrumb-Leiste oberhalb und der darunter liegenden Shell. Die Breadcrumb-Leiste am oberen Fensterrand dient zur Anzeige der Vorgängerliste für die aktuelle Stammaktivität. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden der Breadcrumb-Navigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). Die Designeroberfläche im mittleren Bereich dient zum Erstellen von Workflows. Die Shell am unteren Fensterrand enthält eine Reihe von Schaltflächen zum Verwalten der aktuellen Ansicht.

## <a name="shell-features"></a>Shell-Funktionen
 Auf der rechten Seite der Shell-Leiste befinden sich Schaltflächen zum Vergrößern bzw. Verkleinern der Workflowgrafik, zum Anpassen des Workflowinhalts an die Bildschirmgröße und zum Einblenden bzw. Ausblenden der Übersichtskarte. Sie können die Workflowgrafik auch mit den Tastenkombinationen STRG++ und STRG+- vergrößern bzw. verkleinern.

## <a name="overview-map"></a>Übersichtskarte
 Die Übersichtskarte zeigt eine kleine Version der gesamten Aktivität des aktuellen Breadcrumb-Stamms an, einschließlich aller untergeordneten Elemente mit erweiterten untergeordneten Elementen. Der aktuell im Editor angezeigte Teil der Aktivität wird in einem Ansichtsfenster, einem Rechteck mit orangefarbenem Rahmen, hervorgehoben. Durch Ziehen des Rechtecks auf der Übersichtskarte können Sie im Workflow-Designer einen Bildlauf durchführen und die Ansicht des Editors ändern.

> [!NOTE]
> Die Workflow-Designer-Benutzeroberfläche ist virtualisiert. Die Aktivitätsdesigner werden nur nach Bedarf gerendert. Die Teile des Workflows, die auf der Designeroberfläche nicht gezeichnet wurden, werden in der Übersichtskarte weiß angezeigt. Um den Workflow vollständig zu zeichnen, führen Sie einen Bildlauf auf der Übersichtskarte durch.

## <a name="copying-or-saving-workflows-as-images"></a>Kopieren und Speichern von Workflows als Bilder
 Workflows können im Bitmapformat kopiert und im Bitmap- oder Vektorformat gespeichert werden. Das Kopieren bzw. Speichern eines Bilds bietet die Möglichkeit, eine Ansicht der gesamten Aktivität des aktuellen Breadcrumb-Stamms in ein anderes Programm zu exportieren, einschließlich aller untergeordneten Elemente und zugehörigen erweiterten untergeordneten Elemente.

 Zum Kopieren als Bild klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Designer, und wählen Sie **als Bild kopieren** aus. Zum Speichern als Bild klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Designer, und wählen Sie **als Bild speichern** aus. Workflows können in den Formaten JPG, PNG, GIF und XPS gespeichert werden. Das Format wird im Dialogfeld **Speichern** unter im Dropdown-Listenfeld **Dateityp:** am unteren Rand des Fensters ausgewählt.

## <a name="fonts-and-colors"></a>Schriftarten und Farben

Die Schriftarten, die in Workflow-Designer in Visual Studio verwendet werden, werden durch die Schriftart der Umgebung gesteuert. Die in Workflow-Designer angezeigten Farben ändern sich, wenn Sie ein Farbschema mit hohem Kontrast für das Betriebssystemdesign verwenden. Sie müssen Visual Studio neu starten, nachdem Sie die Schriftart-oder Farbeinstellungen geändert haben, bevor die Änderungen in Workflow-Designer wirksam werden.