---
title: Der DslTextTransform-Befehl
description: Erfahren Sie, dass dsltexttransform. cmd ein Skript ist, das TextTransform.exe aufruft und es mit allgemeinen Optionen ausführt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74f87f735f5ad6864082046327bc852d5d43fdb6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362716"
---
# <a name="the-dsltexttransform-command"></a>Der DslTextTransform-Befehl
Dsltexttransform. cmd ist ein Skript, das TextTransform.exe aufruft und es mit allgemeinen Optionen ausführt. Sie können dsltexttransformation. cmd verwenden, um einen nächtlichen Build ihrer Projekte zu automatisieren [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Weitere Informationen finden Sie unter [Erstellen von Dateien mit dem textTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md).

 Die Datei "dsltexttransform. cmd" befindet sich im folgenden Verzeichnis:

 **\<Visual Studio SDK Installation Path>\Visualstudiointegration\tools\bin**

 Sie können die folgenden Argumente als Eingabe für "dsltexttransform. cmd" angeben:

- Das Ausgabeverzeichnis des Domänen Modellprojekts.

- Das Ausgabeverzeichnis des Designer Definitions Projekts.

- Der Speicherort der Textvorlagen Datei.

  Dsltexttransform. cmd verarbeitet die angegebene Textvorlagen Datei mithilfe der Standard direktivenprozessoren und-Assemblys. Wenn Sie benutzerdefinierte direktivenprozessoren erstellen, können Sie eine eigene Batchdatei erstellen, die TextTransform.exe aufruft. In dieser Batchdatei können Sie die Assemblys und die zugeordneten benutzerdefinierten direktivenprozessoren angeben.
