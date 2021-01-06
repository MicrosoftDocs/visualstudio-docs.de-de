---
title: Gliederung in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Gliederung durch die Implementierung von ausgeblendeten Regionen in einem Legacy Sprachdienst unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca457c32751fb1f9179a9c09b624c444efab627d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876830"
---
# <a name="outlining-in-a-legacy-language-service"></a>Gliederung in einem Legacysprachdienst
Durch Gliederung kann ein komplexes Programm in eine Übersicht oder eine Gliederung reduziert werden. In c# können z. b. alle Methoden in eine einzelne Zeile reduziert werden, die nur die Methoden Signatur anzeigt. Außerdem können Strukturen und Klassen so reduziert werden, dass nur die Namen der Strukturen und Klassen angezeigt werden. Innerhalb einer einzelnen Methode kann eine komplexe Logik reduziert werden, um den gesamten Datenfluss anzuzeigen, indem nur die erste Zeile der Anweisungen angezeigt wird, z `foreach` `if` . b., und `while` .

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [:](../../extensibility/walkthrough-outlining.md)Gliederung.

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="enabling-support-for-outlining"></a>Aktivieren der Unterstützung für Gliederung
 Der `AutoOutlining` Registrierungs Eintrag ist auf 1 festgelegt, um die automatische Gliederung zu aktivieren. Die automatische Gliederung richtet eine Analyse der gesamten Quelle ein, wenn eine Datei geladen oder geändert wird, um ausgeblendete Bereiche zu identifizieren und die Gliederungs Symbole anzuzeigen. Die Gliederung kann auch manuell vom Benutzer gesteuert werden.

 Der Wert des `AutoOutlining` Registrierungs Eintrags kann über die- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Eigenschaft der-Klasse abgerufen werden <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . Der `AutoOutlining` Registrierungs Eintrag kann mit einem benannten Parameter für das Attribut initialisiert werden <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (Weitere Informationen finden Sie unter [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service1.md) ).

## <a name="the-hidden-region"></a>Der verborgene Bereich
 Zum Bereitstellen von Gliederung muss Ihr Sprachdienst ausgeblendete Bereiche unterstützen. Dabei handelt es sich um Textabschnitte, die erweitert oder reduziert werden können. Ausgeblendete Bereiche können durch Standardsprachen Symbole (z. b. geschweifte Klammern) oder durch benutzerdefinierte Symbole begrenzt werden. C# verfügt beispielsweise über ein paar, das einen ausgeblendeten `#region` / `#endregion` Bereich begrenzt.

 Ausgeblendete Bereiche werden von einem ausgeblendeten Bereichs-Manager verwaltet, der als Schnittstelle verfügbar gemacht wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>

 Gliederung verwendet ausgeblendete Bereiche die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> Schnittstelle und enthält die Spanne des ausgeblendeten Bereichs, den aktuellen sichtbaren Zustand und das Banner, das angezeigt werden soll, wenn die Spanne reduziert wird.

 Der Sprachdienst Parser verwendet die- <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Methode, um einen neuen ausgeblendeten Bereich mit dem Standardverhalten für ausgeblendete Bereiche hinzuzufügen, während die- <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Methode Ihnen ermöglicht, die Darstellung und das Verhalten der Gliederung anzupassen. Wenn ausgeblendete Bereiche der ausgeblendeten Regions Sitzung zugewiesen werden, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwaltet die ausgeblendeten Bereiche für den Sprachdienst.

 Wenn Sie bestimmen müssen, wann die ausgeblendete Regions Sitzung zerstört wird, wird ein ausgeblendeter Bereich geändert, oder Sie müssen sicherstellen, dass ein bestimmter ausgeblendeter Bereich sichtbar ist. Sie müssen eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> -Klasse ableiten und die entsprechenden Methoden, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> , <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> und überschreiben <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> .

### <a name="example"></a>Beispiel
 Hier ist ein vereinfachtes Beispiel für das Erstellen ausgeblendeter Bereiche für alle Paare von geschweiften Klammern. Es wird davon ausgegangen, dass die Sprache geschweifte Klammern enthält und dass die geschweiften Klammern mindestens die geschweiften Klammern ({und}) enthalten. Diese Vorgehensweise dient nur zu Veranschaulichung. Eine vollständige Implementierung hätte eine vollständige Behandlung von Fällen in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Außerdem wird in diesem Beispiel gezeigt, wie die-Einstellung temporär festgelegt wird <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> `true` . Eine Alternative besteht darin, den `AutoOutlining` benannten Parameter im- `ProvideLanguageServiceAttribute` Attribut in Ihrem Sprachpaket anzugeben.

 In diesem Beispiel werden c#-Regeln für Kommentare, Zeichen folgen und Literale angenommen.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
