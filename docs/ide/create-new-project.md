---
title: Erstellen eines neuen Projekts
description: Lernen Sie, in Visual Studio Schritt für Schritt ein neues Projekt zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 03/19/2019
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cba3c19ae939396132af8bb3c2ffee318b7007e
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006522"
---
# <a name="create-a-new-project-in-visual-studio"></a>Erstellen eines neuen Projekts in Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Öffnen des Dialogfelds „Neues Projekt“

Es gibt verschiedene Möglichkeiten, ein neues Projekt in Visual Studio 2017 zu erstellen. Auf der Startseite können Sie den Namen einer Projektvorlage in das Feld **Projektvorlagen suchen** eingeben, oder Sie klicken auf den Link **Neues Projekt erstellen**, um das Dialogfeld **Neues Projekt** zu öffnen. Abgesehen von der Startseite können Sie ebenso in der Menüleiste auf **Datei** > **Neu** > **Projekt** oder in der Symbolleiste auf die Schaltfläche **Neues Projekt** klicken.

![Startseite und „Datei“ > „Neu“ > „Projekt“](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Auswählen eines Vorlagentyps

Die verfügbaren Projektvorlagen werden im Dialogfeld **Neues Projekt** in einer Liste unter der Kategorie **Vorlagen** angezeigt. Vorlagen werden nach Programmiersprachen und Projekttypen sortiert, z.B. Visual C#, JavaScript und Azure Data Lake.

![Dialogfeld "Neues Projekt"](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Der Aufbau der Liste der verfügbaren Sprachen und Projektvorlagen hängt von der Visual Studio-Version, die Sie ausführen, und den installierten Workloads ab. Informationen zum Installieren von zusätzlichen Workloads finden Sie unter [Ändern von Visual Studio durch Hinzufügen oder Entfernen von Arbeitsauslastungen und Komponenten](../install/modify-visual-studio.md).

Zeigen Sie die Liste der Vorlagen für die Programmiersprache an, die Sie verwenden möchten, indem Sie auf das Dreieck neben dem Namen der Sprache klicken und dann eine Projektkategorie auswählen (beispielsweise Windows Desktop).

Die folgende Abbildung zeigt die Projektvorlagen, die für Visual C# .NET Core-Projekte verfügbar sind:

![Projektvorlagen](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Geben Sie in das Feld **Name** einen Namen für das neue Projekt ein. Sie können das Projekt entweder am Standardspeicherort auf Ihrem Computer speichern oder auf die Schaltfläche **Durchsuchen** klicken, um einen anderen Speicherort zu suchen. Sie können auch einen Namen für die Projektmappe wählen oder das neue Projekt einem Git-Repository hinzufügen (indem Sie **Zur Quellcodeverwaltung hinzufügen** auswählen).

Klicken Sie auf **OK**, um die Projektmappe und das Projekt zu erstellen.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Öffnen der Seite „Neues Projekt erstellen“

Es gibt verschiedene Möglichkeiten, ein neues Projekt in Visual Studio 2019 zu erstellen. Beim ersten Öffnen von Visual Studio wird das Startfenster angezeigt, und dort können Sie **Neues Projekt erstellen** auswählen.

![Erstellen eines neuen Projekts im Startfenster in VS 2019](media/vs-2019/start-window-create-new-project.png)

Wenn die Visual Studio-Entwicklungsumgebung bereits geöffnet ist, können Sie ein neues Projekt erstellen, indem Sie in der Menüleiste **Datei** > **Neu** > **Projekt** auswählen oder auf die Schaltfläche **Neues Projekt** auf der Symbolleiste klicken.

![Schaltfläche „Neues Projekt“ in Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Auswählen eines Vorlagentyps

Auf der Seite **Neues Projekt erstellen** wird links eine Liste der von Ihnen zuletzt ausgewählten Vorlagen angezeigt. Die Vorlagen sind nach den *zuletzt verwendeten* sortiert.

Wenn Sie nicht unter den zuletzt verwendeten Vorlagen auswählen, können Sie alle verfügbaren Projektvorlagen nach **Sprache** (z.B. C# oder C++), **Plattform** (z.B. Windows oder Azure) und **Projekttyp** (z.B. Desktop oder Web) filtern. Sie können außerdem Suchtext in das Suchfeld eingeben, um das Filtern der Vorlagen weiter einzugrenzen, z.B. **asp.net**.

![Filter für Projektvorlagen in Visual Studio-2019](media/vs-2019/create-new-project-filters.png)

Die Tags, die unter jeder Vorlage angezeigt werden, entsprechen den drei Dropdownfiltern (Sprache, Plattform und Projekttyp).

> [!TIP]
> Wenn Sie die gewünschte Vorlage nicht finden, fehlt möglicherweise ein Workload für Visual Studio. Um zusätzliche Workloads zu installieren, beispielsweise **Azure-Entwicklung** oder **Mobile-Entwicklung mit .NET**, klicken Sie auf den Link **Weitere Tools und Features installieren**, um den Visual Studio-Installer zu öffnen. Wählen Sie dort die Workloads, die Sie installieren möchten, und dann **Ändern** aus. Danach stehen weitere Projektvorlagen zur Wahl.
>
> ![Link „Weitere Tools und Features installieren“ in VS 2019](media/vs-2019/install-more-tools-features.png)

Wählen Sie eine Vorlage aus, und klicken Sie dann auf **Weiter**.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Die Seite **Neues Projekt konfigurieren** weist Optionen zum Benennen Ihres Projekts (und der Projektmappe), zum Auswählen eines Speicherorts auf dem Datenträger und zum Auswählen einer Framework-Version auf (sofern das auf die ausgewählte Vorlage zutrifft).

![Seite „Neues Projekt konfigurieren“ in VS 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Wenn Sie ein neues Projekt erstellen, während bereits ein Projekt oder eine Projektmappe in Visual Studio geöffnet ist, steht eine zusätzliche Konfigurationsoption zur Verfügung. Sie können sich entscheiden, eine neue Projektmappe zu erstellen oder das neue Projekt zur bereits geöffneten Projektmappe hinzuzufügen.
>
> ![Neue Projektmappe erstellen oder zu vorhandener Projektmappe hinzufügen in VS 2019](media/vs-2019/configure-new-project-solution.png)

Klicken Sie auf **Erstellen**, um das neue Projekt zu erstellen.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Hinzufügen weiterer Projekte zu einer Projektmappe

Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Projektmappenknoten, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus, um einer Projektmappe ein weiteres Projekt hinzuzufügen.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von Projektmappen und Projekten](creating-solutions-and-projects.md)
