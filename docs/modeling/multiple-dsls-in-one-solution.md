---
title: Mehrere DSLs in einer Projektmappe
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2eef29db24da3be0a9376ea76a9a1a551af9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542596"
---
# <a name="multiple-dsls-in-one-solution"></a>Mehrere DSLs in einer Projektmappe

Sie können mehrere DSLs als Bestandteil einer Projektmappe packen, damit sie zusammen installiert werden.

Sie können verschiedene Techniken für die Integration mehrerer DSLs nutzen. Weitere Informationen finden Sie unter [integrieren von Modellen mithilfe von Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) und Gewusst [wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md) und [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Erstellen Sie mehr als eine DSL in derselben Projekt Mappe

1. Erstellen Sie ein neues **VSIX-Projekt** Projekt.

2. Erstellen Sie zwei oder mehr DSL-Projekte im VSIX-Projektmappenverzeichnis.

   - Öffnen Sie für jede DSL eine neue Instanz von Visual Studio. Erstellen Sie die neue DSL, und geben Sie den gleichen Projektmappenordner wie für die VSIX-Projektmappe an.

   - Achten Sie darauf, dass Sie jede DSL mit einer anderen Dateinamenerweiterung erstellen.

   - Ändern Sie die Namen der **DSL** -und **dslpackage** -Projekte, sodass Sie sich alle unterscheiden. Beispiel: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Aktualisieren Sie diese Zeile in jedem **dslpackage \* \ Source.Extension.tt**auf den richtigen DSL-Projektnamen:

      `string dslProjectName = "Dsl2";`

   - Fügen Sie in der VSIX-Projekt Mappe die Projekte "DSL *" und "dslpackage" hinzu \* . Sie sollten jedes Paar in einem eigenen Projektmappenordner platzieren.

2. Kombinieren Sie die VSIX-Manifeste der DSLs:

   1. Öffnen Sie _yourvsixproject_**\source.Extension.Manifest**.

   2. Wählen Sie für jede DSL **Inhalt hinzufügen** und hinzufügen aus:

       - `Dsl*` Projekt als **MEF-Komponente**

       - `DslPackage*` Projekt als **MEF-Komponente**

       - `DslPackage*` Projekt als **vs-Paket**

3. Erstellen Sie die Projektmappe.

   Die resultierende VSIX installiert beide DSLs. Sie können Sie mit F5 testen oder _yourvsixproject_**\bin\debug \\ \* . vsix**bereitstellen.

## <a name="see-also"></a>Weitere Informationen

- [Integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Gewusst wie: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)