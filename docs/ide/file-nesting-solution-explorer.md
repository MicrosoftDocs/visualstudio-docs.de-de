---
title: Regeln für die Dateischachtelung für den Projektmappen-Explorer
description: Erfahren Sie mehr über Dateischachtelungsregeln im Projektmappen-Explorer, Voreinstellungen und Anpassungen.
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jmartens
ms.openlocfilehash: aa3ca640fed4e32c19defd925a49369890219035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869452"
---
# <a name="file-nesting-in-solution-explorer"></a>Dateischachtelung im Projektmappen-Explorer

Der **Projektmappen-Explorer** schachtelt verwandte Dateien, damit diese besser organisiert werden können und leichter aufzufinden sind. Wenn Sie z.B. ein Windows Forms-Formular zu einem Projekt hinzufügen, wird die Codedatei für das Formular im **Projektmappen-Explorer** unterhalb des Formulars geschachtelt. In ASP.NET Core-Projekten kann die Dateischachtelung noch einen Schritt weiter geführt werden. Sie können zwischen diesen Voreinstellungen für die Dateischachtelung auswählen: **Aus**, **Standard** und **Web**. Sie können auch [die Dateischachtelung anpassen](#customize-file-nesting) oder [projektmappenspezifische und projektspezifische Einstellungen erstellen](#create-project-specific-settings).

> [!NOTE]
> Das Feature wird derzeit nur für ASP.NET Core-Projekte unterstützt.

## <a name="file-nesting-options"></a>Optionen für die Dateischachtelung

![Schaltfläche für die Aktivierung/Deaktivierung der Dateischachtelung](media/filenesting_onoff.png)

Die verfügbaren Optionen für die nicht anpassbare Dateischachtelung sind folgende:

* **Aus**: Mit dieser Option erhalten Sie eine flache Liste von Dateien ohne Schachtelung.

* **Standard**: Mit dieser Option erhalten Sie das Standardschachtelungsverhalten im **Projektmappen-Explorer**. Wenn keine Einstellungen für einen vorhanden Projekttyp existieren, werden auch keine Dateien im Projekt geschachtelt. Sollten Einstellungen vorhanden sein, z.B. für ein Webprojekt, dann wird die Schachtelung angewendet.

* **Web**: Diese Option wendet das Schachtelungsverhalten für **Webdateien** auf alle Projekte in der aktuellen Projektmappe an. Sie verfügt über zahlreiche Regeln, probieren Sie es also einfach aus, und teilen Sie uns Ihre Meinung mit. Der folgende Screenshot zeigt nur ein paar Beispiele des Dateischachtelungsverhaltens, das Sie mit dieser Option erhalten:

   ![Dateischachtelung im Projektmappen-Explorer](media/filenesting.png)

## <a name="customize-file-nesting"></a>Anpassen der Dateischachtelung

Wenn Ihnen die Ergebnisse der Standardeinstellungen nicht gefallen, können Sie Ihre eigenen benutzerdefinierten Schachtelungseinstellungen erstellen, die den **Projektmappen-Explorer** anweisen, wie Dateien geschachtelt werden sollen. Sie können so viele benutzerdefinierte Einstellungen für die Dateischachtelung hinzufügen, wie Sie möchten, und Sie können beliebig oft zwischen diesen wechseln. Um eine neue benutzerdefinierte Einstellung zu erstellen, können Sie mit einer leeren Datei beginne. Alternativ können Sie auch die **Webeinstellungen** als Startpunkt verwenden:

![Hinzufügen von benutzerdefinierten Regeln für die Dateischachtelung](media/filenesting_addcustom.png)

Die **Webeinstellungen** werden als Startpunkt empfohlen, da es einfacher ist, mit etwas zu arbeiten, das bereits funktioniert. Wenn Sie die **Webeinstellungen** als Startpunkt verwenden, sieht die Datei *.filenesting.json* der folgenden Datei ähnlich:

![Verwenden vorhandener Dateischachtelungsregeln als Basis für benutzerdefinierte Einstellungen](media/filenesting_editcustom.png)

Konzentrieren wir uns auf den Knoten **dependentFileProviders** und dessen untergeordnete Knoten. Jeder untergeordnete Knoten ist ein Regeltyp, den Visual Studio zum Schachteln von Dateien verwenden kann. Beispielsweise ist ein Regeltyp die **Verwendung des gleichen Dateinamens aber einer anderen Erweiterung**. Die verfügbaren Regeln sind:

* **extensionToExtension**: Verwenden Sie diesen Regeltyp, um *file.js* unter *file.ts* zu schachteln.

* **fileSuffixToExtension**: Verwenden Sie diesen Regeltyp, um *file-vsdoc.js* unter *file.js* zu schachteln.

* **addedExtension**: Verwenden Sie diesen Regeltyp, um *file.html.css* unter *file.html* zu schachteln.

* **pathSegment**: Verwenden Sie diesen Regeltyp, um *jquery.min.js* unter *jquery.js* zu schachteln.

* **allExtensions**: Verwenden Sie diesen Regeltyp, um *file.** unter *file.js* zu schachteln.

* **fileToFile**: Verwenden Sie diesen Regeltyp, um *bower.json* unter *.bowerrc* zu schachteln.

### <a name="the-extensiontoextension-provider"></a>Der extensionToExtension-Anbieter

Mit diesem Anbieter können Sie Dateischachtelungsregeln mithilfe bestimmter Dateierweiterungen definieren. Betrachten Sie das folgende Beispiel:

![Regeln für das extensionToExtension-Beispiel](media/filenesting_extensiontoextension.png) ![Wirkung des extensionToExtension-Beispiels](media/filenesting_extensiontoextension_effect.png)

* *cart.js* wird aufgrund der ersten **extensionToExtension**-Regel unter *cart.ts* geschachtelt.

* *cart.js* wird nicht unter *cart.tsx* geschachtelt, da **.ts** vor **.tsx** in den Regeln steht und es nur ein übergeordnetes Element geben darf.

* *light.css* wird aufgrund der zweiten **extensionToExtension**-Regel unter *light.sass* geschachtelt.

* *home.html* wird aufgrund der dritten **extensionToExtension**-Regel unter *home.md* geschachtelt.

### <a name="the-filesuffixtoextension-provider"></a>Der fileSuffixToExtension-Anbieter

Dieser Anbieter arbeitet genau so wie der **extensionToExtension**-Anbieter, mit dem einzigen Unterschied, dass die Regel das Suffix der Datei anstatt nur die Erweiterung behandelt. Betrachten Sie das folgende Beispiel:

![Regeln für das fileSuffixToExtension-Beispiel](media/filenesting_filesuffixtoextension.png) ![Wirkung des fileSuffixToExtension-Beispiels](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* wird aufgrund der **fileSuffixToExtension**-Regel unter *portal.js* geschachtelt.

* Jeder andere Aspekt der Regel arbeitet genauso wie **extensionToExtension**.

### <a name="the-addedextension-provider"></a>Der addedExtension-Anbieter

Dieser Anbieter schachtelt Dateien mit einer zusätzlichen Erweiterung unter der Datei ohne zusätzliche Erweiterung. Die zusätzliche Erweiterung kann nur am Ende des vollständigen Dateinamens auftreten.

Betrachten Sie das folgende Beispiel:

![Regeln für das addedExtension-Beispiel](media/filenesting_addedextension.png) ![Wirkung des addedExtension-Beispiels](media/filenesting_addedextension_effect.png)

* *file.html.css* wird aufgrund der **addedExtension**-Regel unter *file.html* geschachtelt.

> [!NOTE]
> Sie müssen keine Dateierweiterungen für die `addedExtension`-Regel angeben, da sie automatisch auf alle Dateierweiterungen angewendet wird. Das bedeutet Folgendes: Eine Datei mit dem gleichen Namen und der gleichen Erweiterung wie eine andere Datei plus eine weitere Erweiterung am Ende wird unter der anderen Datei geschachtelt. Sie können die Wirkung dieses Anbieters nicht auf bestimmte Dateierweiterungen einschränken.

### <a name="the-pathsegment-provider"></a>Der pathSegment-Anbieter

Dieser Anbieter schachtelt Dateien mit einer zusätzlichen Erweiterung unter einer Datei ohne zusätzliche Erweiterung. Die zusätzliche Erweiterung kann nur in der Mitte des vollständigen Dateinamens auftreten.

Betrachten Sie das folgende Beispiel:

![Regeln des pathSegment-Beispiels](media/filenesting_pathsegment.png) ![Wirkung des pathSegment-Beispiels](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* wird aufgrund der **pathSegment**-Regel unter *jquery.js* geschachtelt.

> [!NOTE]
> - Wenn Sie keine Dateierweiterungen für die `pathSegment`-Regel angeben, wird sie automatisch auf alle Dateierweiterungen angewendet. Das bedeutet Folgendes: Eine Datei mit dem gleichen Namen und der gleichen Erweiterung wie eine andere Datei plus eine weitere Erweiterung in der Mitte wird unter der anderen Datei geschachtelt.
> - Sie können die Wirkung der `pathSegment`-Regel auf bestimmte Dateierweiterungen beschränken, indem Sie diese auf folgende Weise angeben:
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>Der allExtensions-Anbieter

Mit diesem Anbieter können Sie Regeln für die Dateischachtelung ohne zusätzliche Erweiterung aber mit dem gleichen Basisdateinamen definieren. Betrachten Sie das folgende Beispiel:

![Regeln des allExtensions-Beispiels](media/filenesting_allextensions.png) ![Wirkung des allExtensions-Beispiels](media/filenesting_allextensions_effect.png)

* *template.cs* und *template.doc* werden aufgrund der **allExtensions**-Regel unter *template.tt* geschachtelt.

### <a name="the-filetofile-provider"></a>Der fileToFile-Anbieter

Mit diesem Anbieter können Sie Dateischachtelungsregeln auf Basis ganzer Dateinamen schachteln. Betrachten Sie das folgende Beispiel:

![Regel für das fileToFile-Beispiel](media/filenesting_filetofile.png) ![Wirkung des fileToFile-Beispiels](media/filenesting_filetofile_effect.png)

* *.bowerrc* wird aufgrund der **fileToFile**-Regel unter *bower.json* geschachtelt.

### <a name="rule-order"></a>Regelreihenfolge

Die Sortierung ist in jedem Teil Ihrer benutzerdefinierten Einstellungsdatei wichtig. Sie können die Reihenfolge, in der Regeln ausgeführt werden, ändern, indem Sie die Regeln im Knoten **dependentFileProvider** nach oben oder unten verschieben. Wenn Sie z.B. eine Regel besitzen, die **file.js** zum übergeordneten Element von **file.ts** macht und eine andere Regel, die **file.coffee** zum übergeordneten Element von **file.ts** macht, wird das Schachtelungsverhalten von der Reihenfolge bestimmt, in der die Elemente in der Datei angezeigt werden, wenn alle drei Dateien vorhanden sind. Da **file.ts** nur über ein übergeordnetes Element verfügen kann, gewinnt die Regel, die zuerst ausgeführt wird.

Die Sortierung ist ebenso für Regelabschnitte selbst wichtig, nicht nur für Dateien innerhalb eines Abschnitts. Sobald ein Dateipaar einer Dateischachtelungsregel zugeordnet wird, werden die anderen Regeln weiter unten in der Datei ignoriert, und das nächste Dateipaar wird verarbeitet.

### <a name="file-nesting-button"></a>Schaltfläche für die Dateischachtelung

Sie können alle Einstellungen einschließlich Ihrer eigenen benutzerdefinierten Einstellungen über die gleiche Schaltfläche im **Projektmappen-Explorer** verwalten:

![Aktivieren von benutzerdefinierten Regeln für die Dateischachtelung](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Erstellen von projektspezifischen Einstellungen

Sie können projektmappenspezifische und projektspezifische Einstellungen über das Kontextmenü jeder Projektmappe und jedes Projekts erstellen:

![Projektmappen- und projektspezifische Schachtelungsregeln](media/filenesting_solutionprojectspecific.png)

Projektmappenspezifische und projektspezifische Einstellungen werden mit den aktiven Visual Studio-Einstellungen kombiniert. Beispielsweise verfügen Sie über eine leere projektspezifische Einstellungsdatei, der **Projektmappen-Explorer** schachtelt jedoch noch immer Dateien. Das Schachtelungsverhalten stammt entweder aus den projektmappenspezifischen Einstellungen oder den Visual Studio-Einstellungen. Die Rangfolge für das Zusammenführen der Einstellungen für die Dateischachtelung ist: Visual Studio > Projektmappe > Projekt.

Sie können Visual Studio anweisen, projektmappenspezifische und projektspezifische Einstellungen zu ignorieren, auch wenn die Dateien auf dem Datenträger vorhanden sind. Aktivieren Sie dazu die Option **Ignore solution and project settings** (Projektmappen- und Projekteinstellungen ignorieren) unter **Extras** > **Optionen** > **ASP.NET Core** > **Dateischachtelung**.

Sie können das Gegenteil tun und Visual Studio anweisen, *ausschließlich* die projektmappenspezifischen oder die projektspezifischen Einstellungen zu verwenden, indem Sie den **Stammknoten** auf **TRUE** festlegen. Visual Studio beendet zu diesem Zeitpunkt das Zusammenführen von Dateien und kombiniert diese nicht mit Dateien, die sich in der Hierarchie auf einer höheren Ebene befinden.

Projektmappenspezifische und projektspezifische Einstellungen können in die Quellcodeverwaltung eingecheckt werden, und das gesamte Team, das an der Codebasis arbeitet, kann sie freigeben.

## <a name="disable-file-nesting-rules-for-a-project"></a>Deaktivieren der Dateischachtelungsregeln für ein Projekt

Sie können vorhandene globale Dateischachtelungsregeln für bestimmte Projektmappen oder Projekte deaktivieren, indem Sie die Aktion **remove** (Entfernen) anstelle von **add** (Hinzufügen) für einen Anbieter verwenden. Wenn Sie z.B. einem Projekt den folgenden Einstellungscode hinzufügen, werden alle **pathSegment**-Regeln deaktiviert, die global für dieses bestimmte Projekt existieren können.

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Siehe auch

- [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Projektmappen und Projekte in Visual Studio](solutions-and-projects-in-visual-studio.md)
