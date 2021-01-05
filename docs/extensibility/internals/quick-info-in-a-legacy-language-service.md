---
title: Quick Infos in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Unterstützung für den IntelliSense-schnell Info Vorgang zum Anzeigen von Informationen zu einem Bezeichner.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 255022c2722104d3790d1c417eee644730ddc1e8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875075"
---
# <a name="quick-info-in-a-legacy-language-service"></a>QuickInfo in einem Legacysprachdienst
IntelliSense-QuickInfo zeigt Informationen zu einem Bezeichner in der Quelle an, wenn der Benutzer entweder die Einfügemarke im Bezeichner platziert und im **IntelliSense** -Menü die **QuickInfo** auswählt oder den Mauszeiger über dem Bezeichner hält. Dies bewirkt, dass eine QuickInfo mit Informationen zum Bezeichner angezeigt wird. Diese Informationen bestehen normalerweise aus dem Bezeichnertyp. Wenn die Debug-Engine aktiv ist, können diese Informationen den aktuellen Wert enthalten. Die Debug-Engine liefert Ausdrucks Werte, während der Sprachdienst nur Bezeichner verarbeitet.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von Quick Infos für QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

 Die Dienst Klassen für das Managed Package Framework (MPF) bieten vollständige Unterstützung für die Anzeige der QuickInfo-QuickInfo für IntelliSense. Sie müssen lediglich den anzuzeigenden Text angeben und das QuickInfo-Feature aktivieren.

 Der anzuzeigende Text wird abgerufen, indem der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methoden Parser mit einem analysieren Reason-Wert von aufgerufen wird <xref:Microsoft.VisualStudio.Package.ParseReason> . Dieser Grund weist den Parser an, die Typinformationen (oder das, was für die QuickInfo-QuickInfo geeignet ist) für den Bezeichner an der im-Objekt angegebenen Position abzurufen <xref:Microsoft.VisualStudio.Package.ParseRequest> . Das <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt wird an die-Methode übermittelt <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> .

 Der Parser muss alles bis zur Position im Objekt analysieren, um <xref:Microsoft.VisualStudio.Package.ParseRequest> die Typen aller Bezeichner zu ermitteln. Dann muss der Parser den Bezeichner am Speicherort der Analyse Anforderung erhalten. Schließlich muss der Parser die QuickInfo-Daten, die diesem Bezeichner zugeordnet sind, an das-Objekt übergeben, damit das- <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt den Text aus der-Methode zurückgeben kann <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .

## <a name="enabling-the-quick-info-feature"></a>Aktivieren der QuickInfo-Funktion
 Um das QuickInfo-Feature zu aktivieren, müssen Sie den `CodeSense` -Parameter und den `QuickInfo` benannten Parameter von festlegen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Diese Attribute legen die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> -Eigenschaft und die-Eigenschaft fest <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> .

## <a name="implementing-the-quick-info-feature"></a>Implementieren der Quick Info-Funktion
 Die- <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse verarbeitet den IntelliSense-Quick Info-Vorgang. Wenn die- <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse den- <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl empfängt, ruft die-Klasse die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode mit dem Analyse Grund und dem Speicherort der Einfügemarke <xref:Microsoft.VisualStudio.Package.ParseReason> zum Zeitpunkt der Befehls Erstellung auf <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> . Der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methoden Parser muss dann die Quelle bis zum angegebenen Speicherort analysieren und dann den Bezeichner an der angegebenen Position analysieren, um zu bestimmen, was in der QuickInfo-QuickInfo angezeigt werden soll.

 Die meisten Parser führen eine anfängliche Analyse der gesamten Quelldatei durch und speichern die Ergebnisse in einer Analyse Struktur. Die vollständige Analyse wird ausgeführt, wenn <xref:Microsoft.VisualStudio.Package.ParseReason> an die- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode übergeben wird. Andere Arten der Analyse können dann die Analyse Struktur verwenden, um die gewünschten Informationen zu erhalten.

 Beispielsweise kann der Wert für die Analyse Ursache von <xref:Microsoft.VisualStudio.Package.ParseReason> den Bezeichner am Quell Speicherort finden und in der Analyse Struktur nachschlagen, um die Typinformationen zu erhalten. Diese Typinformationen werden dann an die <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Klasse weitergegeben und von der- <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> Methode zurückgegeben.
