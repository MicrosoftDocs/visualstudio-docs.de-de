---
title: Vbc-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6edc8b246055dcd8efdb32f4118f81a535635d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683830"
---
# <a name="vbc-task"></a>Vbc-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umschließt die Datei „vbc.exe“, die ausführbare Dateien (EXE), Dynamic Link Libraries (DLL) oder Codemodule (NETMODULE) produziert. Weitere Informationen zu vbc.exe finden Sie unter [Visual Basic Befehlszeilen Compiler](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `Vbc` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Optionaler `String[]`-Parameter.<br /><br /> Gibt weitere Ordner an, in denen nach im Verweisattribut angegebenen Assemblys gesucht werden soll|  
|`AddModules`|Optionaler `String[]`-Parameter.<br /><br /> Bewirkt, dass der Compiler dem Projekt, das Sie aktuell kompilieren, sämtliche Typinformationen aus den angegebenen Dateien bereitstellt. Dieser Parameter entspricht dem Schalter [/addmodule](https://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) des vbc.exe Compilers.|  
|`BaseAddress`|Optionaler `String`-Parameter.<br /><br /> Gibt die Basisadresse einer DLL an. Dieser Parameter entspricht dem Schalter [/BaseAddress](https://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) des vbc.exe Compilers.|  
|`CodePage`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Dieser Parameter entspricht dem Schalter [/Codepage](https://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) des vbc.exe Compilers.|  
|`DebugType`|Optionaler `String[]`-Parameter.<br /><br /> Veranlasst, dass der Compiler Debuginformationen generiert. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Der Standardwert ist `full`, wodurch ermöglicht wird, einen Debugger an ein ausgeführtes Programm anzufügen. Der Wert `pdbonly` macht das Debuggen von Quellcode möglich, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das aktive Programm an den Debugger angefügt ist. Weitere Informationen finden Sie unter [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Optionaler `String[]`-Parameter.<br /><br /> Definiert Konstanten für die bedingte Kompilierung. Symbol-Wert-Paare werden durch Semikolons getrennt und mit der folgenden Syntax angegeben:<br /><br /> *Symbol1* `=` *Wert1* `;` *Symbol2* `=` *Wert2*<br /><br /> Dieser Parameter entspricht dem Schalter [/define](https://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) des vbc.exe Compilers.|  
|`DelaySign`|Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, legt die Aufgabe den öffentlichen Schlüssel in der Assembly ab. Ist der Wert `false`, signiert die Aufgabe die Assembly vollständig. Der Standardwert ist `false`. Dieser Parameter hat keine Auswirkung, es sei denn, er wird mit den Parametern `KeyFile` oder `KeyContainer` verwendet. Dieser Parameter entspricht dem Schalter [/delaysign](https://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) des vbc.exe Compilers.|  
|`DisabledWarnings`|Optionaler `String`-Parameter.<br /><br /> Unterdrückt die angegebenen Warnungen. Sie müssen lediglich den numerischen Teil des Warnungsbezeichners angeben. Mehrere Warnungen werden durch Semikolons getrennt. Dieser Parameter entspricht dem Schalter [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) des vbc.exe Compilers.|  
|`DocumentationFile`|Optionaler `String`-Parameter.<br /><br /> Verarbeitet Dokumentationskommentare zu der angegebenen XML-Datei. Dieser Parameter überschreibt das `GenerateDocumentation`-Attribut. Weitere Informationen finden Sie unter [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, generiert die Aufgabe Debuginformationen und platziert sie in einer Programmdatenbankdatei (PDB-Datei). Weitere Informationen finden Sie unter [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Optionaler `String`-Parameter.<br /><br /> Gibt an, wie interne Compilerfehler von der Aufgabe gemeldet werden sollen. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Wenn `prompt` angegeben ist und ein interner Compilerfehler auftritt, wird der Benutzer gefragt, ob Fehlerdaten an Microsoft gesendet werden sollen.<br /><br /> Wenn `send` angegeben ist und ein interner Compilerfehler auftritt, sendet die Aufgabe Fehlerdaten an Microsoft.<br /><br /> Der Standardwert ist `none`, der Fehler im nur als Textausgabe berichtet.<br /><br /> Dieser Parameter entspricht dem Schalter [/errorreport](https://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) des vbc.exe Compilers.|  
|`FileAlignment`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Ausrichtung der Abschnitte der Ausgabedatei in Bytes an. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Dieser Parameter entspricht dem Schalter [/filealign](https://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) des vbc.exe Compilers.|  
|`GenerateDocumentation`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` lautet, werden Dokumentationsinformationen generiert und zusammen mit dem Namen der ausführbaren Datei oder der Bibliothek, die von der Aufgabe erstellt wurde, in einer XML-Datei gespeichert. Weitere Informationen finden Sie unter [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Importiert Namespaces aus den angegebenen Auflistungen. Dieser Parameter entspricht dem Schalter [/Imports](https://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) des vbc.exe Compilers.|  
|`KeyContainer`|Optionaler `String`-Parameter.<br /><br /> Gibt den Namen des kryptografischen Schlüsselcontainers an. Dieser Parameter entspricht dem Schalter [/keycontainer](https://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) des Compilers „vbc.exe“.|  
|`KeyFile`|Optionaler `String`-Parameter.<br /><br /> Gibt den Dateinamen mit dem kryptografischen Schlüssel an. Weitere Informationen finden Sie unter [/keyfile](https://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Optionaler [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)-Parameter.<br /><br /> Gibt die Sprachversion (entweder 9 oder 10) an|  
|`LinkResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert. Dieser Parameter entspricht dem Schalter [/linkresource](https://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) des vbc.exe Compilers.|  
|`MainEntryPoint`|Optionaler `String`-Parameter.<br /><br /> Gibt die Klasse oder das Modul mit dem Speicherort der `Sub Main`-Prozedur an. Dieser Parameter entspricht dem [/main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0)-Schalter des Compilers „vbc.exe“.|  
|`ModuleAssemblyName`|Optionaler `String`-Parameter.<br /><br /> Gibt die Assembly an, zu der dieses Modul gehört.|  
|`NoConfig`|Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, dass der Compiler die Datei „vbc.rsp“ nicht verwenden soll. Dieser Parameter entspricht dem [/noconfig](https://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) -Parameter des vbc.exe Compilers.|  
|`NoLogo`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden die Compilerbannerinformationen unterdrückt. Dieser Parameter entspricht dem Schalter [/nologo](https://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) des vbc.exe Compilers.|  
|`NoStandardLib`|Optionaler `Boolean`-Parameter.<br /><br /> Bewirkt, dass der Compiler nicht auf die Standardbibliotheken verweist. Dieser Parameter entspricht dem Schalter [/nostdlib](https://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) des vbc.exe Compilers.|  
|`NoVBRuntimeReference`|Optionaler `Boolean`-Parameter.<br /><br /> Nur zur internen Verwendung. Wenn der Wert TRUE ist, wird der automatische Verweis auf Microsoft.VisualBasic.dll verhindert.|  
|`NoWarnings`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser auf `true` festgelegt ist, unterdrückt die Aufgabe alle Warnungen. Weitere Informationen finden Sie unter [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Compileroptimierungen aktiviert. Dieser Parameter entspricht dem Schalter [/optimize](https://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) des vbc.exe Compilers.|  
|`OptionCompare`|Optionaler `String`-Parameter.<br /><br /> Gibt an, wie Zeichenfolgenvergleiche durchgeführt werden. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Der Wert `binary` gibt an, dass die Aufgabe binäre Zeichenfolgenvergleiche verwendet. Der Wert `text` gibt an, dass die Aufgabe Textzeichenfolgenvergleiche verwendet. Der Standardwert dieses Parameters ist `binary`. Dieser Parameter entspricht dem Schalter [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) des vbc.exe Compilers.|  
|`OptionExplicit`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, ist die explizite Deklaration von Variablen erforderlich. Dieser Parameter entspricht dem Schalter [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) des vbc.exe Compilers.|  
|`OptionInfer`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Typrückschlüsse von Variablen zugelassen.|  
|`OptionStrict`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, erzwingt die Aufgabe eine strikte Typsemantik, um implizite Typkonvertierungen zu beschränken. Dieser Parameter entspricht dem Schalter [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) des vbc.exe Compilers.|  
|`OptionStrictType`|Optionaler `String`-Parameter.<br /><br /> Gibt an, welche strikte Typsemantik eine Warnung generiert. Derzeit wird nur „custom“ unterstützt. Dieser Parameter entspricht dem Schalter [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) des vbc.exe Compilers.|  
|`OutputAssembly`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Namen der Ausgabedatei an. Dieser Parameter entspricht dem Schalter [/out](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) des vbc.exe Compilers.|  
|`Platform`|Optionaler `String`-Parameter.<br /><br /> Gibt die Prozessorplattform an, die das Ziel der Ausgabedatei darstellen soll. Dieser Parameter kann den Wert `x86`, `x64`, `Itanium` oder `anycpu` aufweisen. Der Standardwert ist `anycpu`. Dieser Parameter entspricht dem Schalter [/Platform](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) des vbc.exe Compilers.|  
|`References`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bewirkt, dass die Aufgabe öffentliche Typinformationen aus den angegebenen Elementen in das aktuelle Projekt importiert. Dieser Parameter entspricht dem Schalter [/Reference](https://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) des vbc.exe Compilers.|  
|`RemoveIntegerChecks`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden die Fehlerüberprüfungen auf Ganzzahlüberlauf deaktiviert. Der Standardwert ist `false`. Dieser Parameter entspricht dem Schalter [/removeintchecks](https://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) des vbc.exe Compilers.|  
|`Resources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bettet eine .NET Framework-Ressource in die Ausgabedatei ein. Dieser Parameter entspricht dem Schalter [/Resource](https://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) des vbc.exe Compilers.|  
|`ResponseFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Antwortdatei an, die Befehle für den die Aufgabe enthalten. Dieser Parameter entspricht der Option [@ (Antwortdatei festlegen)](https://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) des Compilers vbc.exe.|  
|`RootNamespace`|Optionaler `String`-Parameter.<br /><br /> Gibt den Stammnamespace für alle Typdeklarationen an. Dieser Parameter entspricht dem Schalter [/RootNamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) des vbc.exe Compilers.|  
|`SdkPath`|Optionaler `String`-Parameter.<br /><br /> Gibt den Speicherort von "mscorlib.dll" und "microsoft.visualbasic.dll" an. Dieser Parameter entspricht dem Schalter [/sdkpath-Schalter](https://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) des vbc.exe Compilers.|  
|`Sources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt mindestens eine [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Quelldatei an.|  
|`TargetCompactFramework`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, richtet sich die Aufgabe an das [!INCLUDE[Compact](../includes/compact-md.md)]. Dieser Schalter entspricht dem Schalter [/netcf](https://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) des vbc.exe Compilers.|  
|`TargetType`|Optionaler `String`-Parameter.<br /><br /> Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann unterschiedliche Werte aufweisen: `library` erstellt eine Codebibliothek, `exe` erstellt eine Konsolenanwendung, `module` erstellt ein Modul, und `winexe` erstellt ein Windows-Programm. Der Standardwert ist `library`. Dieser Parameter entspricht dem Schalter [/target](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) des vbc.exe Compilers.|  
|`Timeout`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt.|  
|`ToolPath`|Optionaler `String`-Parameter.<br /><br /> Gibt den Speicherort an, von wo aus die Aufgabe die zugrunde liegende ausführbare Datei (vbc.exe) lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad, der der Version des Frameworks entspricht, das [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ausführt.|  
|`TreatWarningsAsErrors`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden alle Warnungen wie Fehler behandelt. Weitere Informationen finden Sie unter [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Optionaler `Boolean`-Parameter.<br /><br /> Weist die Aufgabe an, das prozessinterne Compilerobjekt (falls verfügbar) zu verwenden. Wird nur von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwendet.|  
|`Utf8Output`|Optionaler `Boolean`-Parameter.<br /><br /> Protokolliert die Compilerausgabe mit UTF-8-Codierung. Dieser Parameter entspricht dem Schalter [/utf8output](https://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) des vbc.exe Compilers.|  
|`Verbosity`|Optionaler `String`-Parameter.<br /><br /> Gibt den Ausführlichkeitsgrad der Ausgabe des Compilers an. Der Ausführlichkeitsgrad kann `Quiet`, `Normal` (Standard) oder `Verbose` lauten.|  
|`WarningsAsErrors`|Optionaler `String`-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Dieser Parameter überschreibt den `TreatWarningsAsErrors`-Parameter.|  
|`WarningsNotAsErrors`|Optionaler `String`-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Dieser Parameter ist nur dann nützlich, wenn der `TreatWarningsAsErrors`-Parameter auf `true` gesetzt ist.|  
|`Win32Icon`|Optionaler `String`-Parameter.<br /><br /> Fügt der Assembly eine ICO-Datei hinzu, die der Ausgabedatei im Datei-Explorer das gewünschte Aussehen verleiht. Dieser Parameter entspricht dem Schalter [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) des vbc.exe Compilers.|  
|`Win32Resources`|Optionaler `String`-Parameter.<br /><br /> Fügt eine Win32-Ressource (RES-Datei) in die Ausgabedatei ein. Dieser Parameter entspricht dem Schalter ["/win32resource"](https://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) des vbc.exe Compilers.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Projekt kompiliert.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Basic-Befehlszeilencompiler](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
