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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924509"
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
