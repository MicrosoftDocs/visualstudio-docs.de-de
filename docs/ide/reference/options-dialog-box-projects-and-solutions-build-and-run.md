---
title: Dialogfeld „Optionen“, Projekte und Projektmappen, Erstellen und Ausführen
description: Sie können die maximale Anzahl von gleichzeitig erstellbaren C++- oder C#-Projekten, bestimmte Standardbuildverhaltensweisen und einige Buildprotokolleinstellungen in Visual Studio angeben.
'\ms.custom': SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c91a016d91addc4f9e4b06acb32614bd6f6a162
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136770"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Dialogfeld „Optionen“: Projekte und Projektmappen \> Erstellen und Ausführen

In diesem Dialogfeld können Sie die maximale Anzahl von C++- oder C#-Projekten, die gleichzeitig erstellt werden können, bestimmte standardmäßige Buildverhaltensweisen und einige Buildprotokolleinstellungen angeben. Klicken Sie zum Zugriff auf diese Optionen auf **Extras** > **Optionen** , erweitern Sie **Projekte und Projektmappen** , und klicken Sie auf **Erstellen und Ausführen** .

**Maximale Anzahl paralleler Projektbuilds**

Gibt die maximale Anzahl von C++- und C#-Projekten an, die gleichzeitig erstellt werden können. Zur Optimierung des Buildvorgangs wird die maximale Anzahl paralleler Projektbuilds automatisch auf die Anzahl der CPUs des Computers festgelegt. Die maximale Anzahl beträgt 32.

**Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**

Es werden nur das Startprojekt und dessen Abhängigkeiten erstellt, wenn Sie auf **F5** drücken, den Menübefehl **Debuggen** > **Debuggen starten** oder zutreffende Befehle im Menü **Erstellen** auswählen. Wenn diese Option deaktiviert ist, werden alle Projekte und Abhängigkeiten erstellt.

**Beim Ausführen, bei nicht aktuellen Projekten**

*Dies bezieht sich nur auf C++-Projekte.*

Wenn Sie ein Projekt mit **F5** oder dem Befehl **Debuggen** > **Debuggen starten** ausführen, zeigt die Standardeinstellung **Zum Erstellen auffordern** eine Meldung an, wenn eine Projektkonfiguration veraltet ist. Wählen Sie **Immer erstellen** aus, um das Projekt jedes Mal bei Ausführung zu erstellen. Wählen Sie **Nie erstellen** aus, um alle automatischen Builds zu unterdrücken, wenn das Projekt ausgeführt wird.

**Beim Ausführen, bei Build- oder Bereitstellungsfehlern**

*Dies bezieht sich nur auf C++-Projekte.*

Wenn Sie ein Projekt mit **F5** oder dem Befehl **Debuggen** > **Debuggen starten** ausführen, zeigt die Standardeinstellung **Zum Starten auffordern** eine Meldung an, wenn ein Projekt ausgeführt werden soll, auch wenn der Build fehlgeschlagen ist. Wählen Sie **Alte Version starten** aus, um automatisch den letzten guten Build zu starten, was zu Konflikten zwischen dem aufgeführten Code und dem Quellcode führen könnte. Wählen Sie **Nicht starten** aus, um die Meldung zu unterdrücken.

**Aktuell ausgewähltes Projekt als Startprojekt für neue Projektmappen verwenden**

Wenn diese Option festgelegt ist, verwenden neue Projektmappen das aktuell ausgewählten Projekt als Startprojekt.

**Ausführlichkeit der MSBuild-Projektbuildausgabe**

Bestimmt, wie viele Informationen aus dem Buildprozess im **Ausgabefenster** angezeigt werden.

**Ausführlichkeit der Protokolldatei des MSBuild-Projektbuilds**

*Dies bezieht sich nur auf C++-Projekte.*

Hiermit wird festgelegt, wie viele Informationen in die Buildprotokolldatei geschrieben werden, die sich unter *\\\<ProjectName>\Debug\\\<ProjectName>.log* befindet.

## <a name="see-also"></a>Siehe auch

- [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)
- [Optionen (Dialogfeld), Projekte und Projektmappen](projects-and-solutions-options-dialog-box.md)
- [Dialogfeld „Optionen“, Projekte und Projektmappen, Webprojekte](options-dialog-box-projects-and-solutions-web-projects.md)