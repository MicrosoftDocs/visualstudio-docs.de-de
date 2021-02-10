---
title: Wortvervollständigung in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Die Wortvervollständigung kann für einen Legacy Sprachdienst im Visual Studio SDK unterstützt werden. Erfahren Sie, wie Legacy Sprachdienste in einem VSPackage implementiert werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3625719987afc94deda314fa61d7a8cc2c1c843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943367"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Wortvervollständigung in einem Legacysprachdienst
Die Wortvervollständigung füllt die fehlenden Zeichen für ein teilweise typisiertes Wort aus. Wenn nur ein möglicher Abschluss vorhanden ist, wird das Wort abgeschlossen, wenn das Abschluss Zeichen eingegeben wird. Wenn das partielle Wort mit mehr als einer Möglichkeit übereinstimmt, wird eine Liste der möglichen Vervollständigungen angezeigt. Bei einem Abschluss Zeichen kann es sich um ein beliebiges Zeichen handeln, das nicht für Bezeichner verwendet wird.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="implementation-steps"></a>Implementierungs Schritte

1. Wenn der Benutzer im **IntelliSense** -Menü die Option **Wort vervollständigen** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> auswählt, wird der Befehl an den Sprachdienst gesendet.

2. Die <xref:Microsoft.VisualStudio.Package.ViewFilter> -Klasse fängt den Befehl ab und ruft die- <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode mit der Analyse Ursache von auf <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. Die <xref:Microsoft.VisualStudio.Package.Source> -Klasse ruft dann die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode auf, um die Liste der möglichen Wort Vervollständigungen zu erhalten, und zeigt dann die Wörter in einer QuickInfo-Liste mithilfe der- <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse an.

    Wenn nur ein Wort übereinstimmt, schließt die <xref:Microsoft.VisualStudio.Package.Source> Klasse das Wort ab.

   Wenn der Scanner den Wert des Auslösers zurückgibt <xref:Microsoft.VisualStudio.Package.TokenTriggers> , wenn das erste Zeichen eines Bezeichners eingegeben wird, <xref:Microsoft.VisualStudio.Package.Source> erkennt die Klasse dies, und ruft die- <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode mit der Analyse Grund von auf <xref:Microsoft.VisualStudio.Package.ParseReason> . In diesem Fall muss der Parser das vorhanden sein eines Elementauswahl Zeichens erkennen und eine Liste von Membern bereitstellen.

## <a name="enabling-support-for-the-complete-word"></a>Aktivieren der Unterstützung für das Wort "Complete"
 Um die Unterstützung für die Wortvervollständigung zu aktivieren, wird der `CodeSense` benannte Parameter an das Benutzer Attribut übergeben, das <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dem Sprachpaket zugeordnet ist. Dadurch wird die- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft für die-Klasse festgelegt <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

 Der Parser muss eine Liste von Deklarationen als Reaktion auf den Wert der analysieren-Ursache zurückgeben <xref:Microsoft.VisualStudio.Package.ParseReason> , damit die Wortvervollständigung ausgeführt werden kann.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementieren von Complete Word in der Methode "Parser ource"
 Für die Wortvervollständigung <xref:Microsoft.VisualStudio.Package.Source> Ruft die-Klasse die- <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode für die- <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse auf, um eine Liste möglicher Wort Übereinstimmungen abzurufen. Sie müssen die Liste in einer Klasse implementieren, die von der- <xref:Microsoft.VisualStudio.Package.Declarations> Klasse abgeleitet wird. Weitere <xref:Microsoft.VisualStudio.Package.Declarations> Informationen zu den Methoden, die Sie implementieren müssen, finden Sie in der-Klasse.

 Wenn die Liste nur ein einzelnes Wort enthält, fügt die <xref:Microsoft.VisualStudio.Package.Source> Klasse dieses Wort anstelle des partiellen Worts automatisch ein. Wenn die Liste mehr als ein Wort enthält, zeigt die Klasse eine QuickInfo- <xref:Microsoft.VisualStudio.Package.Source> Liste an, aus der der Benutzer die geeignete Auswahl treffen kann.

 Sehen Sie sich auch das Beispiel einer <xref:Microsoft.VisualStudio.Package.Declarations> Klassen Implementierung in der Element [Vervollständigung in einem Legacy Sprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)an.
