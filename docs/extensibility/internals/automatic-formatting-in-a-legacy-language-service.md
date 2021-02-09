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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de54f43ca8abc7547609882647e014cb3695da33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906057"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatische Formatierung in einem Legacy Sprachdienst
Bei der automatischen Formatierung fügt ein Sprachdienst automatisch einen Code Ausschnitt ein, wenn ein Benutzer damit beginnt, ein bekanntes Code Konstrukt einzugeben.

## <a name="automatic-formatting-behavior"></a>Automatisches Formatierungs Verhalten
 Wenn Sie z. b. *eingeben,* fügt der Sprachdienst automatisch passende geschweifte Klammern ein, oder wenn Sie die EINGABETASTE drücken, erzwingt der Sprachdienst die Einfügemarke in der neuen Zeile auf die entsprechende Einzugs Ebene, je nachdem, ob die vorherige Zeile einen neuen Bereich öffnet.

 Der für den Rest des sprach Dienstanbieter verwendete Befehls Filter kann auch für die automatische Formatierung verwendet werden. Sie können auch passende geschweifte Klammern hervorheben, indem Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacy sprach Dienstanbieter](../../extensibility/internals/developing-a-legacy-language-service.md)
