---
title: Projekte | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Möglichkeiten, wie VSPackages das Visual Studio-Projekt System erweitern können, einschließlich Projekttypen, Projekt Untertypen und benutzerdefinierter Tools.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cacd00339dbf6e9507b8bf4c81be27b4c45fa80b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970074"
---
# <a name="projects"></a>Projekte
In Visual Studio sind Projekte die Container, die Entwickler zum Organisieren von Quell Code Dateien und anderen Ressourcen verwenden, die in **Projektmappen-Explorer** angezeigt werden. In der Regel handelt es sich bei Projekten um Dateien (z. b. eine CSPROJ-Datei für ein c#-Projekt), in der Verweise auf Quell Code Dateien und Ressourcen wie Bitmapdateien gespeichert werden. Mit Projekten können Sie Quellcode, Verweise auf Webdienste und Datenbanken sowie andere Ressourcen organisieren, erstellen, Debuggen und bereitstellen. VSPackages können das Visual Studio-Projekt System auf drei Arten erweitern: *Projekttypen*, *Projekt Untertypen* und *benutzerdefinierte Tools*.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Projekttypen](../../extensibility/internals/project-types.md)

 *Projekttypen* fügen Unterstützung für neue Arten von Projekten hinzu, z. b. Programmiersprachen. Beispielsweise verfügt jede Sprache, die Visual Studio unterstützt, über einen eigenen Projekttyp, und das IronPython-Integrations Beispiel enthält einen Projekttyp für die IronPython-Sprache. Sie müssen einen Projekttyp für andere Sprachen als c# erstellen oder Visual Basic, um anzupassen, wie Elemente erstellt, gedeppt, bereitgestellt und in **Projektmappen-Explorer** angezeigt werden. Weitere Informationen finden Sie unter [Projekttypen](../../extensibility/internals/project-types.md).

- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)

 *Projekt Untertypen* basieren auf Projekttypen und können verwendet werden, um die Art und Weise anzupassen, wie Projekte erstellt, gedeppt und bereitgestellt werden. Visual Studio verwendet Projekt Untertypen mit Projekten für intelligente Geräte. Sie passen die Bereitstellung an, indem Sie ein neu erstelltes Programm von einem Entwicklungs Computer auf das Zielgerät kopieren. Die c#-und Visual Basic-Projekttypen können als Grundlage für Projekt Untertypen verwendet werden. C++-Projekttypen können nicht. Ihre eigenen Projekttypen können auch als Grundlage für Projekt Untertypen verwendet werden. Weitere Informationen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).

- [Webprojekte](../../extensibility/internals/web-projects.md)

 Erläutert das Webprojekt, das wiederum Webanwendungen erstellt.

- [Neue Projektgenerierung: im Hintergrund Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) und [neue Projektgenerierung: Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Erläutert, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen.

- [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Enthält die Beispiele im VSSDK, die Projekte und Projektmappen behandeln.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Im Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Erläutert verschiedene Aspekte der Visual Studio-Erweiterbarkeit.
