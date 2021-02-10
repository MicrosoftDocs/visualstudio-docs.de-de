---
title: Unterstützung der Navigationsleiste in einem Legacy Sprachdienst
description: Erfahren Sie, wie Sie die Navigationsleiste in einem Legacy Sprachdienst unterstützen. Die Navigationsleiste in der Editor-Ansicht zeigt die Typen und Member in der Datei an.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d33b8452f727037226a50abe6a9493ce132e9564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932578"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Unterstützen der Navigationsleiste in einem Legacysprachdienst
In der Navigationsleiste am oberen Rand der Editor-Ansicht werden die Typen und Member in der Datei angezeigt. Typen werden in der linken Dropdown-Dropdown-Anzeige angezeigt, und die Elemente werden in der rechten Dropdown-Dropdown Anzeige angezeigt. Wenn der Benutzer einen Typ auswählt, wird die Einfügemarke in die erste Zeile des Typs eingefügt. Wenn der Benutzer einen Member auswählt, wird die Einfügemarke in die Definition des Members eingefügt. Die Dropdown Felder werden aktualisiert, um die aktuelle Position der Einfügemarke widerzuspiegeln.

## <a name="displaying-and-updating-the-navigation-bar"></a>Anzeigen und Aktualisieren der Navigationsleiste
 Zur Unterstützung der Navigationsleiste müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> -Klasse ableiten und die- <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode implementieren. Wenn Ihr Sprachdienst ein Code Fenster erhält, <xref:Microsoft.VisualStudio.Package.LanguageService> instanziiert die Basisklasse den <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , der das-Objekt enthält, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> das das Code Fenster darstellt. Dem- <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Objekt wird dann ein neues- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt zugewiesen. Die- <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode ruft ein-Objekt ab <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . Wenn Sie eine Instanz der-Klasse zurückgeben <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> , <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Ruft die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> -Methode auf, um die internen Listen aufzufüllen, und übergibt das <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt an den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dropdown leisten-Manager. Der Dropdown leisten-Manager ruft wiederum die-Methode für das-Objekt auf, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> um das-Objekt zu erstellen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> das die beiden Dropdown leisten enthält.

 Wenn das Caretzeichen bewegt wird, ruft die- <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Methode die- <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methode auf. Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Methode ruft die- <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse auf, um den Status der Navigationsleiste zu aktualisieren. Sie übergeben eine Reihe von- <xref:Microsoft.VisualStudio.Package.DropDownMember> Objekten an diese Methode. Jedes-Objekt stellt einen Eintrag in der Dropdown-Ablage dar.

## <a name="the-contents-of-the-navigation-bar"></a>Der Inhalt der Navigationsleiste.
 Die Navigationsleiste enthält normalerweise eine Liste von Typen und eine Liste von Membern. Die Liste der Typen umfasst alle Typen, die in der aktuellen Quelldatei verfügbar sind. Die Typnamen enthalten die Informationen zum kompletten Namespace. Im folgenden finden Sie ein Beispiel für c#-Code mit zwei Typen:

```csharp
namespace TestLanguagePackage
{
    public class TestLanguageService
    {
        internal struct Token
        {
            int tokenID;
        }
        private Tokens[] tokens;
        private string serviceName;
    }
}
```

 In der Liste Typ werden `TestLanguagePackage.TestLanguageService` und angezeigt `TestLanguagePackage.TestLanguageService.Tokens` .

 In der Liste Mitglieder werden die verfügbaren Member des Typs angezeigt, der in der Liste Typen ausgewählt ist. Bei Verwendung des obigen Code Beispiels, wenn `TestLanguagePackage.TestLanguageService` der ausgewählte Typ ist, enthält die Liste der Mitglieder die privaten Member `tokens` und `serviceName` . Die interne Struktur `Token` wird nicht angezeigt.

 Sie können die Liste der Mitglieder implementieren, um den Namen eines Elements Fett zu formatieren, wenn sich die Einfügemarke befindet. Member können auch in ausgegrauter Text angezeigt werden. Dies deutet darauf hin, dass Sie sich nicht innerhalb des Bereichs befinden, in dem die Einfügemarke aktuell positioniert ist.

## <a name="enabling-support-for-the-navigation-bar"></a>Aktivieren der Unterstützung für die Navigationsleiste
 Um die Unterstützung für die Navigationsleiste zu aktivieren, müssen Sie den- `ShowDropdownBarOption` Parameter des- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attributs auf festlegen `true` . Dieser Parameter legt die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>-Eigenschaft fest. Zur Unterstützung der Navigationsleiste müssen Sie das- <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Objekt in der-Methode der- <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse implementieren.

 Wenn die-Eigenschaft in der Implementierung der- <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Methode <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> auf festgelegt ist `true` , können Sie ein-Objekt zurückgeben <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . Wenn Sie das-Objekt nicht zurückgeben, wird die Navigationsleiste nicht angezeigt.

 Die Option zum Anzeigen der Navigationsleiste kann vom Benutzer festgelegt werden. Daher ist es möglich, dass dieses Steuerelement zurückgesetzt wird, während die Editor Ansicht geöffnet ist. Der Benutzer muss das Editor Fenster schließen und erneut öffnen, bevor die Änderung stattfindet.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementieren der Unterstützung für die Navigationsleiste
 Die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> -Methode nimmt zwei Listen (jeweils eine für jede Dropdown Liste) und zwei Werte an, die die aktuelle Auswahl in jeder Liste darstellen. Die Listen und Auswahl Werte können aktualisiert werden. in diesem Fall muss die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode zurückgeben, `true` um anzugeben, dass die Listen geändert wurden.

 Wenn sich die Auswahl in der Dropdown Liste "Typen" ändert, muss die Liste der Mitglieder aktualisiert werden, um den neuen Typ widerzuspiegeln. In der Liste der Mitglieder kann Folgendes angezeigt werden:

- Die Liste der Elemente für den aktuellen Typ.

- Alle Elemente, die in der Quelldatei verfügbar sind, aber alle Elemente, die sich nicht im aktuellen Typ befinden, werden in ausgegrauter Text angezeigt. Der Benutzer kann immer noch die abzurufenen Member auswählen, sodass Sie für die schnelle Navigation verwendet werden können, aber die Farbe gibt an, dass Sie nicht Teil des aktuell ausgewählten Typs sind.

  Eine Implementierung der- <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode führt in der Regel die folgenden Schritte aus:

1. Eine Liste der aktuellen Deklarationen für die Quelldatei erhalten.

     Es gibt eine Reihe von Möglichkeiten, die Listen aufzufüllen. Ein Ansatz besteht darin, eine benutzerdefinierte Methode für Ihre Version der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse zu erstellen, die die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode mit einem benutzerdefinierten Analyse Grund aufruft, der eine Liste aller Deklarationen zurückgibt. Eine andere Möglichkeit besteht darin, die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode direkt aus der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode mit dem Grund für die benutzerdefinierte Analyse aufzurufen. Ein Dritter Ansatz besteht darin, die Deklarationen in der Klasse zwischenzuspeichern, die <xref:Microsoft.VisualStudio.Package.AuthoringScope> durch den letzten vollständigen Prozess der Verarbeitung in der-Klasse zurückgegeben wurde <xref:Microsoft.VisualStudio.Package.LanguageService> , und diese aus der- <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode abzurufen

2. Füllt die Liste der Typen auf oder aktualisiert sie.

     Der Inhalt der Liste Typen kann aktualisiert werden, wenn sich die Quelle geändert hat, oder wenn Sie die Textformatierung der Typen basierend auf der aktuellen Position der Einfügemarke ändern möchten. Beachten Sie, dass diese Position an die-Methode übermittelt wird <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .

3. Bestimmen Sie den Typ, der in der Liste Typen basierend auf der aktuellen Position der Einfügemarke ausgewählt werden soll.

     Sie können die in Schritt 1 erhaltenen Deklarationen durchsuchen, um den Typ zu finden, der die aktuelle Position der Einfügemarke einschließt, und dann die Liste der Typen nach diesem Typ durchsuchen, um den Index in der Liste der Typen zu ermitteln.

4. Füllt die Liste der Elemente auf der Grundlage des ausgewählten Typs auf oder aktualisiert sie.

     Die Liste Mitglieder gibt an, was momentan in der Dropdown Liste **Mitglieder** angezeigt wird. Der Inhalt der Liste Mitglieder muss möglicherweise aktualisiert werden, wenn sich die Quelle geändert hat oder wenn Sie nur die Elemente des ausgewählten Typs anzeigen und der ausgewählte Typ geändert wurde. Wenn Sie alle Elemente in der Quelldatei anzeigen möchten, muss die Textformatierung der einzelnen Elemente in der Liste aktualisiert werden, wenn sich der aktuell ausgewählte Typ geändert hat.

5. Bestimmen Sie den Member, der basierend auf der aktuellen Position der Einfügemarke in der Liste Mitglieder ausgewählt werden soll.

     Durchsuchen Sie die in Schritt 1 abgenommenen Deklarationen für den Member, der die aktuelle Position der Einfügemarke enthält, und suchen Sie dann in der Liste der Member nach diesem Element, um den Index in der Elementliste zu ermitteln.

6. Gibt zurück `true` , wenn Änderungen an den Listen oder der Auswahl in der Liste vorgenommen wurden.
