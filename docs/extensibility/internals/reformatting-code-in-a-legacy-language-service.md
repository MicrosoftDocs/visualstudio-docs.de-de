---
title: Neuformatieren von Code in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Aktivieren der Unterstützung für die Neuformatierung von Quellcode für einen Visual Studio-Legacy Sprachdienst.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fcd9871cb0eeec69b98ada83af15f0daa624cb4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875361"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Neuformatieren von Code in einem Legacysprachdienst

Im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcode kann neu formatiert werden, indem die Verwendung von Einzügen und Leerzeichen normalisiert wird. Dies kann das Einfügen oder Entfernen von Leerzeichen oder Registerkarten am Anfang jeder Zeile, das Hinzufügen neuer Zeilen zwischen Zeilen oder das Ersetzen von Leerzeichen durch Tabstopps oder Tabstopps durch Leerzeichen umfassen.

> [!NOTE]
> Das Einfügen oder Löschen von Zeilen Zeilenzeichen kann Marker wie Haltepunkte und Lesezeichen beeinflussen, das Hinzufügen oder Entfernen von Leerzeichen oder Registerkarten wirkt sich jedoch nicht auf Marker aus.

Benutzer können einen neuformatierungs Vorgang starten, indem Sie im Menü **Bearbeiten** im Menü " **erweitert** " die Option **Format Auswahl** oder **Dokumentformat** auswählen. Ein neuformatiervorgang kann auch ausgelöst werden, wenn ein Code Ausschnitt oder ein bestimmtes Zeichen eingefügt wird. Wenn Sie z. b. in c# eine schließende geschweifte Klammer eingeben, wird alles zwischen der passenden öffnenden geschweifte Klammer und der schließenden geschweifte Klammer automatisch auf die richtige Ebene eingezogen.

Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Befehl **Format Auswahl** oder **formatdokument** an den Sprachdienst sendet, ruft die- <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse die- <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.Source> Klasse auf. Um die Formatierung zu unterstützen, müssen Sie die <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> -Methode überschreiben und ihren eigenen Formatierungs Code angeben.

## <a name="enabling-support-for-reformatting"></a>Aktivieren der Unterstützung für die Neuformatierung

Um die Formatierung zu unterstützen, muss der- `EnableFormatSelection` Parameter von <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> auf festgelegt werden, `true` Wenn Sie Ihr VSPackage registrieren. Dadurch wird die- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> Eigenschaft auf festgelegt `true` . Die- <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Methode gibt den Wert dieser Eigenschaft zurück. Wenn true zurückgegeben wird, <xref:Microsoft.VisualStudio.Package.ViewFilter> Ruft die-Klasse auf <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

## <a name="implementing-reformatting"></a>Implementierende Neuformatierung

Um die Neuformatierung zu implementieren, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> -Klasse ableiten und die-Methode überschreiben <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> . Das <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> -Objekt beschreibt die zu formatierende Spanne, und das- <xref:Microsoft.VisualStudio.Package.EditArray> Objekt enthält die Änderungen, die in der Spanne vorgenommen werden. Beachten Sie, dass diese Spanne das gesamte Dokument sein kann. Da jedoch wahrscheinlich mehrere Änderungen an der Spanne vorgenommen werden, sollten alle Änderungen in einer einzigen Aktion rückgängig gemacht werden. Umschließen Sie hierzu alle Änderungen in einem- <xref:Microsoft.VisualStudio.Package.CompoundAction> Objekt (Weitere Informationen finden Sie im Abschnitt "Verwenden der CompoundAction-Klasse" in diesem Thema).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird sichergestellt, dass nach jedem Komma in der Auswahl ein einzelnes Leerzeichen vorhanden ist, es sei denn, auf das Komma folgt eine Registerkarte oder befindet sich am Ende der Zeile. Nachfolgende Leerzeichen nach dem letzten Komma in einer Zeile werden gelöscht. Informationen dazu, wie diese Methode von der-Methode aufgerufen wird, finden Sie im Abschnitt "Verwenden der CompoundAction-Klasse" in diesem Thema <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>Verwenden der CompoundAction-Klasse

Alle Neuformatierung in einem Code Abschnitt sollte in einer einzigen Aktion rückgängig gemacht werden. Dies kann mithilfe einer-Klasse erreicht werden <xref:Microsoft.VisualStudio.Package.CompoundAction> . Diese Klasse umschließt eine Reihe von Bearbeitungsvorgängen für den Text Puffer in einen einzelnen Bearbeitungsvorgang.

### <a name="example"></a>Beispiel

Im folgenden finden Sie ein Beispiel für die Verwendung der- <xref:Microsoft.VisualStudio.Package.CompoundAction> Klasse. Ein Beispiel für die-Methode finden Sie im Abschnitt "Implementieren der Unterstützung für die Formatierung" in diesem Thema `DoFormatting` .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen

- [Funktionen von Legacysprachdiensten](legacy-language-service-features1.md)
