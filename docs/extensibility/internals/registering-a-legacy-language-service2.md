---
title: Registrieren einer Legacy Sprache Service2 | Microsoft-Dokumentation
description: In diesem Artikel werden die Registrierungseinträge für die verschiedenen Sprachdienst Optionen aufgeführt, die in Visual Studio verfügbar sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08b9e88440fcb7b488e479e4188279d82a526e4c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875179"
---
# <a name="registering-a-legacy-language-service-2"></a>Registrieren eines Legacy sprach Dienstanbieter 2
In den folgenden Abschnitten finden Sie Listen der Registrierungseinträge für die verschiedenen Sprachdienst Optionen, die unter verfügbar sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 In der folgenden Liste von Registrierungs Einträgen ist *vs reg root* gleich HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *X. y*, wobei *X. y* die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Versionsnummer ist.

## <a name="registry-entries-for-language-service-options"></a>Registrierungseinträge für Sprachdienst Optionen
 Der Schlüssel " *vs reg root*\Languages\Language Services \\ *sprach Name* " kann die folgenden Werte enthalten.

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|*\<GUID>*|GUID des sprach Dienstanbieter.|
|Langresid|REG_DWORD|0x0-0xFFFF|Zeichen folgen Ressourcen Bezeichner (Resid) für den lokalisierten Textnamen der Sprache.|
|Paket|REG_SZ|*\<GUID>*|GUID des VSPackages.|
|Showcompletion|REG_DWORD|0-1|Gibt an, ob die **Anweisungs Vervollständigungs** Optionen im Dialogfeld **Optionen** aktiviert sind.|
|Showsmartindent|REG_DWORD|0-1|Gibt an, ob die Option zum Auswählen von **intelligentem** Einzug im Dialogfeld **Optionen** aktiviert ist.|
|RequestStockColors|REG_DWORD|0-1|Gibt an, ob benutzerdefinierte oder Standardfarben verwendet werden, um Schlüsselwörter zu färben.|
|Showhoturls|REG_DWORD|0-1|Gibt an, ob der Benutzer auf URLs klicken kann.|
|Standardmäßige nicht-Hot-URLs|REG_DWORD|0-1|Gibt die anfängliche Einstellung für die **Navigations Option "Single-Click-URL aktivieren** " im Dialogfeld " **Optionen** " an.|
|Defaultdeinsertspaces|REG_DWORD|0-1|Gibt an, ob der Sprachdienst als Standard Registerkarten Option "Leerzeichen einfügen" aufweist.|
|Showdropdownbaroption|REG_DWORD|0-1|Aktiviert oder deaktiviert die **Navigations** leisten Option im Dialogfeld **Optionen** , das die **Navigationsleiste** anzeigt oder ausblendet.|
|Nur ein Code Fenster|REG_DWORD|0-1|Aktiviert oder deaktiviert die **neue Fenster** Auswahl im Menü **Fenster** für einen Sprachdienst.|
|Enableadvancedmitgliedsoption|REG_DWORD|0-1|Aktiviert oder deaktiviert die Dialogfeld Einstellung **Optionen** für **Erweiterte Member ausblenden**.|
|Support CF_HTML|REG_DWORD|0-1|Gibt an, ob der Editor das Kopieren und Einfügen von HTML-Daten ermöglicht.|
|Enablelinenumbersoption|REG_DWORD|0-1|Gibt an, ob die Optionen für **Zeilennummern** im Dialogfeld **Optionen** für einen Sprachdienst aktiviert sind.|
|Hideadvancedmitgliedsbydefault|REG_DWORD|0-1|Gibt an, ob erweiterte Member wie private Felder in Vervollständigungs Listen ausgeblendet werden.|
|Showbracecompletion|REG_DWORD|0-1|Gibt an, ob die Option zum Abschließen der geschweifter **Klammer** im Dialogfeld **Optionen** aktiviert ist.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Registrierungseinträge für Optionen für debuggersprachen
 Der Schlüssel " *vs reg root*\Languages\Language Services \\ *Language Name*\Debugger Languages \\ *GUID*\" kann die folgenden Werte enthalten.

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|text|Der Standardwert kann verwendet werden, um den Namen der Sprache zu dokumentieren. Der Name dieses Schlüssels ist eine GUID einer Ausdrucks Auswertung, die über einen entsprechenden Eintrag in *\<VS Reg Root>* \ad7metrics\expression Auswertung verfügt.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Registrierungseinträge für Editor-Tool Optionen
 Sie können Registrierungsschlüssel unter dem Schlüssel Editor ToolsOptions für Eigenschaften Seiten und Eigenschafts Knoten hinzufügen. Mit diesen Schlüsseln und ihren Werten werden Eigenschaften Seiten im Dialogfeld **Optionen** ( **im Menü Extras** ) identifiziert, die zum Konfigurieren des sprach Dienstanbieter verwendet werden. Im folgenden Beispiel ist *Page Name* der Name einer Eigenschaften Seite und *Knoten Name* der Name eines Knotens in der Struktur im Dialogfeld **Optionen** . Der Seiten Eintrag und der Knoten Eintrag müssen separat angegeben werden.

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|Resid|Der lokalisierte Anzeige Name der Optionsseite. Der Name kann ein Literaltext oder # sein, `nnn` wobei `nnn` eine Zeichen folgen Ressourcen-ID in der Satelliten-DLL des angegebenen VSPackages ist.|
|Paket|REG_SZ|*GUID*|Der GUID des VSPackage, das diese Optionsseite implementiert.|
|Seite|REG_SZ|*GUID*|Der GUID der Eigenschaften Seite, die vom VSPackage angefordert werden soll, indem die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> . Wenn dieser Registrierungs Eintrag nicht vorhanden ist, beschreibt der Registrierungsschlüssel einen Knoten, nicht eine Seite.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Registrierungseinträge für Dateinamen-Erweiterungsoptionen
 Der Eintrag für die Dateierweiterung sollte den führenden Zeitraum enthalten, z. b. ". myext".

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|*GUID*|Dienst-GUID für den Standard Sprachdienst für diesen Dateinamen-Erweiterungstyp.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Registrierungseinträge für Editor Optionen
 Der Schlüssel " *vs reg root*\editoren" kann die folgenden Werte enthalten:

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ|""|Genutzt Sie können hier Ihren Namen für die Dokumentation eingeben.|
|DefaultToolboxTab|REG_SZ|""|Der Name der Toolbox Registerkarte, die standardmäßig aktiviert wird, wenn der Editor aktiv ist.|
|DisplayName|REG_SZ|Resid|Der Name, der im Dialogfeld **Öffnen mit** angezeigt werden soll. Der Name ist die Zeichen folgen Ressourcen-ID oder ein Name im Standardformat.|
|Excludedeftexteditor|REG_DWORD|0-1|Wird für den Befehl **Öffnen mit** Menü verwendet. Wenn Sie den Standardtext-Editor nicht in der Liste der verfügbaren Editoren für einen bestimmten Dateityp auflisten möchten, legen Sie diesen Wert auf 1 fest.|
|Linkededitor GUID|REG_SZ|*\<GUID>*|Wird für alle Sprachdienste verwendet, die eine Datei mit Codepage-Unterstützung öffnen können. Wenn Sie z. b. eine txt-Datei mit dem Befehl **Öffnen mit** öffnen, werden Optionen für die Verwendung des Quell Code-Editors mit und ohne Codierung bereitgestellt.<br /><br /> Die im Namen des unter Schlüssels angegebene GUID ist für die Codepage-Editor-Factory. die in diesem Registrierungs Eintrag angegebene verknüpfte GUID ist für die reguläre Editorfactory. Der Zweck dieses Eintrags ist, dass die IDE den nächsten Editor in der Liste verwendet, wenn die IDE eine Datei nicht mithilfe des Standard-Editors öffnet. Der nächste Editor sollte nicht die Codepage-Editor-Factory sein, da diese Editorfactory im Grunde der Editor-Factory entspricht, bei der ein Fehler aufgetreten ist.|
|Paket|REG_SZ|*\<GUID>*|VSPackage-GUID für die Größe des anzeigen Amens des anzeigen Amens.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Registrierungseinträge für logische Ansichtsoptionen
 Der Schlüssel " *vs reg root*\editoren \\ *Editor GUI>* \logicalviews" kann die folgenden Werte enthalten.

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ||Nicht verwendet.|
|*\<GUID>*|REG_SZ|""|Der Schlüssel für die unterstützten logischen Ansichten. Sie können beliebig viele von Ihnen benötigen. Der Name des Registrierungs Eintrags ist wichtig, nicht der Wert, der immer eine leere Zeichenfolge ist.|

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Registrierungseinträge für Editor-Erweiterungsoptionen
 Der Schlüssel " *vs reg root*\editoren \\ *Editor GUID*\extensions" kann die folgenden Werte enthalten. Die Dateinamenerweiterung enthält nicht den führenden Zeitraum.

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|(Standardwert)|REG_SZ||Nicht verwendet.|
|*\<ext>*|REG_DWORD|0-0xFFFFFFFF|Relative Priorität von Erweiterungen. Wenn mindestens zwei Sprachen dieselbe Erweiterung verwenden, wird die Sprache mit höherer Priorität ausgewählt.|

 Außerdem wird die Standardauswahl des aktuellen Benutzers für einen Editor in HKEY_CURRENT_USER \software\microsoft\visualstudio \\ *X. Y*\Default Editoren \\ *ext* gespeichert. Der GUID des ausgewählten sprach Dienstanbieter befindet sich im benutzerdefinierten Eintrag. Dies hat Vorrang vor dem aktuellen Benutzer.

### <a name="example"></a>Beispiel

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Registrierungseinträge für die Optionen für das verwaltete Paket Framework Language Service
 Die folgenden Registrierungseinträge sind spezifisch für die MPF-Sprachdienst Klassen (Managed Package Framework). Diese Registrierungseinträge weisen auf die Unterstützung im Sprachdienst für verschiedene IntelliSense-Features und andere erweiterte Bearbeitungsfunktionen hin.

 Auf diese Registrierungseinträge wird über die- <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse zugegriffen.

|Name|Typ|Bereich|BESCHREIBUNG|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Unterstützung für IntelliSense-Vorgänge.|
|Matchgeschweifte Klammern|REG_DWORD|0-1|Unterstützung für übereinstimmende Sprachpaare, z. b. geschweifte Klammern, Klammern und eckige Klammern.|
|QuickInfo|REG_DWORD|0-1|Unterstützung für den IntelliSense-Quick Info-Vorgang.|
|Showmatchingbrace|REG_DWORD|0-1|Unterstützung für das Anzeigen des entsprechenden sprach Paars in der Statusleiste.|
|Matchbracesatcaret|REG_DWORD|0-1|Unterstützung für das Anzeigen übereinstimmender Sprachpaare, normalerweise durch Hervorheben der beiden Elemente.|
|Maxerrormessages|REG_DWORD|0-n|Die maximale Anzahl von Fehlern, die im **Fehlerliste** Fenster angezeigt werden können.|
|Codesenydelay|REG_DWORD|0-n|Die Anzahl der Millisekunden, die verzögert werden muss, bevor eine Hintergrundverarbeitung für einen IntelliSense-Vorgang initiiert wird.|
|EnableAsyncCompletion|REG_DWORD|0-1|Unterstützung für die Hintergrundverarbeitung.|
|Enablekommentieren|REG_DWORD|0-1|Unterstützung für das auskommentieren ausgewählter Textblöcke und impliziert auch die Unterstützung für das Auskommentieren von ausgewähltem Text.|
|Enableformatselection|REG_DWORD|0-1|Unterstützung für das Formatieren von Text wie dem automatischen Einzug oder das Anpassen der Position von geschweiften Klammern.|
|Automatische Gliederung|REG_DWORD|0-1|Unterstützung für die Gliederung (Bereiche, die reduziert werden können).|
|Maxregions|REG_DWORD|0-n|Die maximale Anzahl ausgeblendeter Regionen pro Datei.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
