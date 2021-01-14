---
title: Legacy Sprachdienst-Grundlagen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die wesentlichen Features, die in Legacy Sprachdiensten zur Verfügung stehen, mit denen Sie eine Programmiersprache in Visual Studio integrieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa21b619ef17be3fa649732a2b6e3bcd700dda6
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205137"
---
# <a name="legacy-language-service-essentials"></a>Grundlagen zu Legacysprachdiensten
Sie müssen einen Sprachdienst bereitstellen, um eine Programmiersprache in Visual Studio zu integrieren. In diesem Thema werden die in den Legacy Sprachdiensten verfügbaren Features erläutert.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren eines sprach Dienstanbieter finden Sie unter [Editor-und Sprachdienst Erweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

 Legacy Sprachdienste bieten die folgenden Features:

|Funktion|Beschreibung|
|-------------|-----------------|
|Farben für Syntax|Bewirkt, dass in der Editor-Ansicht verschiedene Farben und Schriftarten für die verschiedenen Elemente einer Sprache angezeigt werden. Diese Differenzierung erleichtert das Lesen und Bearbeiten von Dateien.<br /><br /> Allgemeine Informationen finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informationen zu diesem Feature im Managed Package Framework (MPF) finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Anweisungsvervollständigung|Schließt eine-Anweisung oder ein-Schlüsselwort ab, mit der der Benutzer begonnen hat. Mit der Anweisungs Vervollständigung können Benutzer schwierige Anweisungen leichter eingeben, mit weniger Typisierung und weniger Fehler Chancen.<br /><br /> Allgemeine Informationen finden Sie unter [Anweisungs Vervollständigung in einem Legacy Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informationen zu diesem Feature im MPF finden Sie unter [Wortvervollständigung in einem Legacy Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Klammernabgleich (zugehörige Klammer)|Hebt die Hervorhebung von paarweise paarweise Verknüpfungs Zeichen Wenn der Benutzer ein Schließ Endes Zeichen, z. b. "}", eingibt, wird das entsprechende öffnende Zeichen, wie z. b. "{", durch die Klammer Wenn mehrere Ebenen von einschließenden Zeichen vorhanden sind, können Benutzer mit dieser Funktion bestätigen, dass die einschließenden Zeichen ordnungsgemäß gekoppelt werden.<br /><br /> Weitere Informationen zu diesem Feature im MPF finden Sie unter [Abgleichen von Klammern in einem Legacy Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Tooltipps für Parameter Informationen|Zeigt eine Liste möglicher Signaturen für die überladene Methode an, die der Benutzer gerade eingibt.<br /><br /> Allgemeine Informationen finden Sie unter [Parameter Informationen in einem Legacy Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informationen zu diesem Feature im MPF finden Sie unter [Parameter Info in einem Legacy Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Fehler Marker|Zeigt eine wellenförmige rote Unterstreichung, auch als Wellenlinien bezeichnet, unter Text an, der syntaktisch nicht korrekt ist. Fehler Marker werden normalerweise verwendet, um Benutzern die Kenntnis von falsch geschriebenen Schlüsselwörtern, nicht schließenden Klammern, ungültigen Zeichen und ähnlichen Fehlern zu ermöglichen.<br /><br /> In den MPF-Klassen werden Fehler Marker automatisch in der- <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode der- <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse behandelt.|

 Viele dieser Features erfordern, dass der Sprachdienst Quellcode analysiert. Sie können den tokenisierungs-und-Code für den Compiler oder den Interpreter häufig wieder verwenden.

 Die folgenden Funktionen beziehen sich auf die Unterstützung von Programmiersprachen, sind jedoch nicht Teil der Sprachdienste:

| Funktion | Beschreibung |
|-----------------------| - |
| Ausdrucks Auswertung | Unterstützt den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger durch Überprüfen von Breakpoints und Bereitstellen einer Liste von Ausdrücken, die  im Fenster Auto Debug angezeigt werden sollen.<br /><br /> Weitere Informationen finden Sie [unter Sprachdienst Unterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md). |
| Tools zum Durchsuchen von Symbolen | Unterstützt **Objektkatalog**-, **Klassenansicht**-, **Aufrufbrowser**-und Such **Symbol Ergebnisse**. |
