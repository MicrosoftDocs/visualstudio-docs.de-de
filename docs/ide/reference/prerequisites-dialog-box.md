---
title: Dialogfeld "Erforderliche Komponenten"
description: Im Dialogfeld Erforderliche Komponenten wird angegeben, welche erforderlichen Komponenten installiert werden, wie die Installation ausgeführt wird, und in welcher Reihenfolge die Pakete installiert werden.
ms.custom: SEO-VS-2020
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7384bad2096f98a646487d5d97eed3d387c7de1
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349229"
---
# <a name="prerequisites-dialog-box"></a>Dialogfeld "Erforderliche Komponenten"

Im Dialogfeld **Erforderliche Komponenten** wird angegeben, welche erforderlichen Komponenten installiert werden, wie die Installation ausgeführt wird, und in welcher Reihenfolge die Pakete installiert werden.

![Dialogfeld „Erforderliche Komponenten“ in Visual Studio](media/prerequisites-dialog-box.png)

Wählen Sie zum Aufrufen des Dialogfelds im **Projektmappen-Explorer** einen Projektknoten aus, und klicken Sie anschließend auf **Projekt** > **Eigenschaften**. Wenn der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen** und dann auf **Erforderliche Komponenten**. Klicken Sie bei Setupprojekten im Menü **Projekt** auf **Eigenschaften**. Wenn das Dialogfeld **Eigenschaftenseiten** angezeigt wird, klicken Sie auf **Erforderliche Komponenten**.

## <a name="uielement-list"></a>UIElement-Liste

|Element|BESCHREIBUNG|
|-------------|-----------------|
|**Setupprogramm zur Installation erforderlicher Komponenten erstellen**|Dies schließt die erforderlichen Komponenten im Setupprogramm ( *Setup.exe* ) der Anwendung ein, die je nach Abhängigkeit vor der Anwendung installiert werden. Diese Option ist standardmäßig ausgewählt. Wenn die Option nicht ausgewählt wurde, wird *Setup.exe* nicht erstellt.|
|**Auswählen der für die Installation erforderlichen Komponenten**|Gibt an, ob Komponenten wie .NET Framework- und C++-Laufzeitbibliotheken installiert werden sollen.<br /><br />Indem Sie das Kontrollkästchen neben **SQL Server 2012 Express** aktivieren, legen Sie z.B. fest, dass vom Setupprogramm überprüft werden muss, ob diese Komponente auf dem Zielcomputer installiert ist. Außerdem installiert es die Komponente, wenn diese noch nicht vorhanden ist.<br /><br />Ausführliche Informationen über die einzelnen erforderlichen Pakete finden Sie unter [Informationen über erforderliche Komponenten](#prerequisites-information).|
|**Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**|Dies gibt an, dass die erforderlichen Komponenten von der Website des Herstellers installiert werden müssen. Dies ist die Standardoption.|
|**Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**|Dies gibt an, dass die erforderlichen Komponenten vom gleichen Speicherort wie die Anwendung installiert werden müssen. Dadurch werden alle erforderlichen Pakete an den Speicherort für die Veröffentlichung kopiert. Damit diese Option funktioniert, müssen sich die erforderlichen Pakete auf dem Entwicklungscomputer befinden.|
|**Erforderliche Komponenten von folgendem Speicherort herunterladen**|Dadurch wird angegeben, dass die erforderlichen Komponenten vom ausgewählten Speicherort aus installiert werden müssen. Mithilfe der Schaltfläche **Durchsuche** n können Sie einen Speicherort auswählen.|

> [!NOTE]
> Weitere Informationen zu den Voraussetzungen finden Sie unter [Erstellen von Bootstrapperpaketen](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informationen über erforderliche Komponenten

Die im Dialogfeld **Erforderliche Komponenten** aufgeführten erforderlichen Komponenten können von den in der folgenden Liste genannten abweichen. Die im Dialogfeld **Erforderliche Komponenten** aufgelisteten Pakete mit erforderlichen Komponenten werden automatisch festgelegt, wenn Sie das Dialogfeld zum ersten Mal öffnen. Wenn im Nachhinein Änderungen am Zielframework des Projekts vorgenommen werden, müssen die erforderlichen Komponenten manuell ausgewählt werden, um dem neuen Zielframework zu entsprechen.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Mit diesem Paket wird Folgendes installiert:<br /><br /> – .NET Framework-Versionen 2.0, 3.0 und 3.5.<br />– Unterstützung für alle .NET Framework-Versionen auf 32-Bit- und 64-Bit-Betriebssystemen (x86 und x64).<br />– Sprachpakete für jede .NET Framework-Version, die mit dem Paket installiert wird.<br />– Service Packs für .NET Framework 2.0 und 3.0.<br /><br /> .NET Framework 3.0 ist im Lieferumfang von Windows Vista enthalten, und .NET Framework 3.5 ist in Visual Studio enthalten. .NET Framework 3.5 ist für alle Visual Basic- und C#-Projekte erforderlich, die explizit für 32-Bit-Betriebssysteme kompiliert werden und für die das Zielframework auf **.NET Framework 3.5** festgelegt ist, sowie für alle Visual Basic- und C#-Projekte, die für 64-Bit-Betriebssysteme kompiliert werden. (IA64 wird nicht unterstützt) Beachten Sie, dass Visual Basic-Projekte und C#-Projekte standardmäßig für jede CPU-Architektur kompiliert sind. Weitere Informationen finden Sie unter [Übersicht über Frameworkziele](../../ide/visual-studio-multi-targeting-overview.md) und [Bereitstellen der erforderlichen Komponenten für 64-Bit-Apps](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Mit dem Paket wird .NET Framework 4 sowohl für die x86- als auch die x64-Plattform installiert.|
|**Microsoft-System-CLR-Typen für SQL Server 2014 (x64 und x86)**|Mit diesem Paket werden Microsoft-System-CLR-Typen für SQL Server 2014 für x64 oder x86 installiert.|
|**SQL Server 2008 R2 Express**|Mit diesem Paket wird Microsoft SQL Server 2008 R2 Express installiert, eine kostenlose Edition von Microsoft SQL Server 2008 R2. Diese Datenbank ist für kleine Web-, Server- oder Desktopanwendungen ideal. Es kann kostenlos für Entwicklung und Produktion verwendet werden.|
|**SQL Server 2012 Express**|Mit diesem Paket wird Microsoft SQL Server 2012 Express installiert.|
|**SQL Server 2012 Express LocalDB**|Mit diesem Paket wird Microsoft SQL Server 2012 Express LocalDB installiert.|
|**Visual C++ "14"-Laufzeitbibliotheken (ARM)**|Mit diesem Paket wird die Visual C++-Laufzeitbibliotheken für die Itanium-Architektur, die die Routinen für die Programmierung für das Betriebssystem Microsoft Windows bereitstellen, installiert. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die von den Programmiersprachen C# und C++ nicht bereitgestellt werden.<br /><br /> Weitere Informationen finden Sie unter [C-Laufzeitbibliotheksreferenz](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14"-Laufzeitbibliotheken (x64)**|Mit diesem Paket werden die Visual C++-Laufzeitbibliotheken für x64-Betriebssysteme, die die Routinen für die Programmierung für das Betriebssystem Microsoft Windows bereitstellen, installiert. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die von den Programmiersprachen C# und C++ nicht bereitgestellt werden.<br /><br /> Weitere Informationen finden Sie unter [C-Laufzeitbibliotheksreferenz](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14"-Laufzeitbibliotheken (x86)**|Mit diesem Paket werden die Visual C++-Laufzeitbibliotheken für x86-Betriebssysteme, die die Routinen für die Programmierung für das Betriebssystem Microsoft Windows bereitstellen, installiert. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die von den Programmiersprachen C# und C++ nicht bereitgestellt werden.<br /><br /> Weitere Informationen finden Sie unter [C-Laufzeitbibliotheksreferenz](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Siehe auch

- [Seite "Veröffentlichen", Projekt-Designer](../../ide/reference/publish-page-project-designer.md)
- [Vorbedingungen für die Anwendungsbereitstellung](../../deployment/application-deployment-prerequisites.md)
- [Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Übersicht über Frameworkziele](../../ide/visual-studio-multi-targeting-overview.md)
