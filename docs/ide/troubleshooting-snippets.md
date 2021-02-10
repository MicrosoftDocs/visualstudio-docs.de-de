---
title: Problembehandlung bei Codeausschnitten
description: Hier erfahren Sie, wie Sie Probleme mit IntelliSense-Codeausschnitten beheben, die häufig auf eine fehlerhafte oder beschädigte Codeausschnittdateien zurückzuführen sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d18e65fe14d231fa7cc9ea515eddaf89fc5c2b81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971478"
---
# <a name="troubleshoot-snippets"></a>Problembehandlung bei Codeausschnitten

Probleme bei IntelliSense-Codeausschnitten sind häufig auf eine beschädigte Ausschnittsdatei oder auf fehlerhafte Inhalte in der Datei zurückzuführen.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Der Codeausschnitt lässt sich nicht vom Datei-Explorer in eine Visual Studio-Quelldatei ziehen

- Der XML-Code in der Ausschnittsdatei ist möglicherweise fehlerhaft. Probleme mit der XML-Struktur können mithilfe des **XML-Editors** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermittelt werden.

- Die Ausschnittsdatei entspricht nicht dem Ausschnittsschema. Probleme mit der XML-Struktur können mithilfe des **XML-Editors** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermittelt werden.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Im Code befinden sich Compilerfehler, die nicht hervorgehoben werden

- Möglicherweise ist ein Projektverweis nicht vorhanden. Lesen Sie die Dokumentation zu dem Codeausschnitt. Wenn der Verweis nicht auf dem Computer gefunden wird, müssen Sie diesen installieren. Durch das Einfügen eines Codeausschnitts sollten dem Projekt alle erforderlichen Verweise hinzugefügt werden. Wenn die Verweisinformationen nicht im Codeausschnitt vorhanden sind, kann dieser Fehler dem Ausschnittsersteller gemeldet werden.

- Eine Variable wurde möglicherweise nicht definiert. Nicht definierte Variablen in einem Ausschnitt sollten hervorgehoben werden. Wenn dies nicht der Fall ist, kann dieser Fehler dem Ausschnittsersteller gemeldet werden.

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)
