---
title: Automatische Formatierung in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie mehr über die automatische Formatierung in einem Legacy Sprachdienst, der automatisch einen Code Ausschnitt einfügt, wenn Sie beginnen, ein bekanntes Code Konstrukt einzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651cecb20604069c6e8ccc5a5c7b983ab43d7384
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190056"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatische Formatierung in einem Legacy Sprachdienst
Bei der automatischen Formatierung fügt ein Sprachdienst automatisch einen Code Ausschnitt ein, wenn ein Benutzer damit beginnt, ein bekanntes Code Konstrukt einzugeben.

## <a name="automatic-formatting-behavior"></a>Automatisches Formatierungs Verhalten
 Wenn Sie z. b. *eingeben,* fügt der Sprachdienst automatisch passende geschweifte Klammern ein, oder wenn Sie die EINGABETASTE drücken, erzwingt der Sprachdienst die Einfügemarke in der neuen Zeile auf die entsprechende Einzugs Ebene, je nachdem, ob die vorherige Zeile einen neuen Bereich öffnet.

 Der für den Rest des sprach Dienstanbieter verwendete Befehls Filter kann auch für die automatische Formatierung verwendet werden. Sie können auch passende geschweifte Klammern hervorheben, indem Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacy sprach Dienstanbieter](../../extensibility/internals/developing-a-legacy-language-service.md)
