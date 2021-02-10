---
title: Erstellen eines neuen Projekts
description: In diesem Artikel erfahren Sie, wie Sie ein neues Projekt in Visual Studio erstellen.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 97d585f8c484f1ef8b4cbd0514585d6f328af67c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956879"
---
# <a name="create-a-new-project-in-visual-studio"></a>Erstellen eines neuen Projekts in Visual Studio

In diesem Artikel erfahren Sie, wie Sie schnell ein neues Projekt in Visual Studio erstellen.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Öffnen des Dialogfelds „Neues Projekt“

Es gibt verschiedene Möglichkeiten, ein neues Projekt in Visual Studio 2017 zu erstellen. Auf der Startseite können Sie den Namen einer Projektvorlage in das Feld **Projektvorlagen suchen** eingeben, oder klicken Sie auf den Link **Neues Projekt erstellen**, um das Dialogfeld **Neues Projekt** zu öffnen. Abgesehen von der Startseite können Sie ebenso in der Menüleiste auf **Datei**  >  **Neu**  >  **Projekt** oder in der Symbolleiste auf **Neues Projekt** klicken.

![Screenshot: Menüleiste in Visual Studio mit den Optionen „Datei“ > „Neu“ > „Projekt“ ausgewählt](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Auswählen eines Vorlagentyps

Die verfügbaren Projektvorlagen werden im Dialogfeld **Neues Projekt** in einer Liste unter der Kategorie **Vorlagen** angezeigt. Vorlagen werden nach Programmiersprachen und Projekttypen sortiert, z.B. Visual C#, JavaScript und Azure Data Lake.

![Screenshot: Dialogfeld „Neues Projekt“ mit einer Liste der installierten Vorlagen](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Der Aufbau der Liste der verfügbaren Sprachen und Projektvorlagen hängt von der Visual Studio-Version, die Sie ausführen, und den installierten Workloads ab. Informationen zum Installieren von zusätzlichen Workloads finden Sie unter [Ändern von Visual Studio durch Hinzufügen oder Entfernen von Arbeitsauslastungen und Komponenten](../install/modify-visual-studio.md).

Zeigen Sie die Liste der Vorlagen für die Programmiersprache an, die Sie verwenden möchten, indem Sie auf das Dreieck neben dem Namen der Sprache klicken und dann eine Projektkategorie auswählen (beispielsweise Windows Desktop).

Die folgende Abbildung zeigt die Projektvorlagen, die für Visual C# .NET Core-Projekte verfügbar sind:

![Screenshot: Dialogfeld „Neues Projekt“ mit einer Liste der auswählbaren Projektvorlagen](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Geben Sie in das Feld **Name** einen Namen für das neue Projekt ein. Sie können das Projekt entweder am Standardspeicherort auf Ihrem Computer speichern oder auf die Schaltfläche **Durchsuchen** klicken, um einen anderen Speicherort zu suchen. Sie können auch einen Namen für die Projektmappe wählen oder das neue Projekt einem Git-Repository hinzufügen (indem Sie auf **Zur Quellcodeverwaltung hinzufügen** klicken).

Klicken Sie auf **OK**, um die Projektmappe und das Projekt zu erstellen.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Öffnen der Seite „Neues Projekt erstellen“

Es gibt verschiedene Möglichkeiten, ein neues Projekt in Visual Studio 2019 zu erstellen. Beim ersten Öffnen von Visual Studio wird das Startfenster angezeigt, und dort können Sie **Neues Projekt erstellen** auswählen.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Screenshot: Dialogfeld „Neues Projekt erstellen“ im Startfenster von Visual Studio 2019":::

Wenn die Visual Studio-Entwicklungsumgebung bereits geöffnet ist, können Sie ein neues Projekt erstellen, indem Sie in der Menüleiste **Datei** > **Neu** > **Projekt** auswählen. Sie können auch in der Symbolleiste auf **Neues Projekt** klicken oder **STRG** + **UMSCHALT** + **N** drücken.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Screenshot: Schaltfläche „Neues Projekt“ in Visual Studio 2019":::

## <a name="select-a-template-type"></a>Auswählen eines Vorlagentyps

Auf der Seite **Neues Projekt erstellen** wird links eine Liste der von Ihnen zuletzt ausgewählten Vorlagen angezeigt. Die Vorlagen sind nach den *zuletzt verwendeten* sortiert.

Wenn Sie nicht unter den zuletzt verwendeten Vorlagen auswählen, können Sie alle verfügbaren Projektvorlagen nach **Sprache** (z.B. C# oder C++), **Plattform** (z.B. Windows oder Azure) und **Projekttyp** (z.B. Desktop oder Web) filtern. Sie können außerdem Suchtext in das Suchfeld eingeben, um das Filtern der Vorlagen weiter einzugrenzen, z.B. **asp.net**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Screenshot: Projektvorlagenfilter in Visual Studio 2019":::

Die Tags, die unter jeder Vorlage angezeigt werden, entsprechen den drei Dropdownfiltern (Sprache, Plattform und Projekttyp).

> [!TIP]
> Wenn Sie die gewünschte Vorlage nicht finden, fehlt möglicherweise ein Workload für Visual Studio. Um zusätzliche Workloads zu installieren, beispielsweise **Azure-Entwicklung** oder **Mobile-Entwicklung mit .NET**, klicken Sie auf den Link **Weitere Tools und Features installieren**, um den Visual Studio-Installer zu öffnen. Wählen Sie dort die Workloads aus, die Sie installieren möchten, und klicken Sie dann auf **Ändern**. Danach stehen weitere Projektvorlagen zur Wahl.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Screenshot: Link „Weitere Tools und Features installieren“ in Visual Studio 2019":::

Wählen Sie eine Vorlage aus, und klicken Sie dann auf **Weiter**.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Auf der Seite **Neues Projekt konfigurieren** finden Sie Optionen zum Benennen Ihres Projekts (und der Projektmappe), zum Auswählen eines Speicherorts auf dem Datenträger und zum Auswählen einer Frameworkversion (sofern dies für die ausgewählte Vorlage möglich ist).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Screenshot: Seite „Neues Projekt konfigurieren“ in Visual Studio 2019":::

> [!NOTE]
> Wenn Sie ein neues Projekt erstellen, während bereits ein Projekt oder eine Projektmappe in Visual Studio geöffnet ist, steht eine zusätzliche Konfigurationsoption zur Verfügung. Sie können sich entscheiden, eine neue Projektmappe zu erstellen oder das neue Projekt zur bereits geöffneten Projektmappe hinzuzufügen.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Screenshot: Dialogfeld „Neue Projektmappe erstellen“ oder „Zu Projektmappe hinzufügen“ in Visual Studio 2019":::

Klicken Sie auf **Erstellen**, um das neue Projekt zu erstellen.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Hinzufügen weiterer Projekte zu einer Projektmappe

Wenn Sie ein zusätzliches Projekt zu einer Projektmappe hinzufügen möchten, klicken Sie mit der rechten Maustaste auf den Projektmappenknoten im **Projektmappen-Explorer**, und wählen Sie dann **Hinzufügen**  >  **Neues Projekt** aus.

> [!TIP]
> Ein Beispiel für die Erstellung eines Projekts und einer Projektmappe von Grund auf mit exemplarischen Anweisungen und Beispielcode finden Sie in der [Einführung in Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Weitere Informationen

- [Einführung in Projekte und Projektmappen](../get-started/tutorial-projects-solutions.md)
- [Arbeiten mit Projektmappen und Projekten](creating-solutions-and-projects.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)
- [Erstellen von Projekten (Visual Studio für Mac)](/visualstudio/mac/create-new-projects)