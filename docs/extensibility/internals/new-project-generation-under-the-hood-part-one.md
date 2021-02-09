---
title: 'Neue Projektgenerierung: unter der Haube, Teil 1 | Microsoft-Dokumentation'
description: Sehen Sie sich an, was in der integrierten Entwicklungsumgebung (IDE) von Visual Studio passiert, wenn Sie Ihren eigenen Projekttyp erstellen (Teil 1 von 2).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98a305e4e3188131b2ee3c6e2ecb82dc8d4537b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895777"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Neue Projektgenerierung: Einblick in die Hintergründe, Teil 1
Haben Sie schon einmal gedacht, wie Sie Ihren eigenen Projekttyp erstellen? Fragen Sie sich, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen? Werfen wir einen Blick auf die Praxis, und sehen wir uns an, was tatsächlich passiert.

 Visual Studio koordiniert verschiedene Aufgaben:

- Es wird eine Struktur aller verfügbaren Projekttypen angezeigt.

- Es zeigt eine Liste der Anwendungs Vorlagen für jeden Projekttyp an und ermöglicht Ihnen die Auswahl eines.

- Es sammelt Projektinformationen für die Anwendung, z. b. Projektname und Pfad.

- Diese Informationen werden an die projektfactory weitergeleitet.

- Es generiert Projekt Elemente und Ordner in der aktuellen Projekt Mappe.

## <a name="the-new-project-dialog-box"></a>Dialog Feld "Neues Projekt"
 Alles beginnt, wenn Sie einen Projekttyp für ein neues Projekt auswählen. Klicken Sie zunächst im Menü **Datei** auf **Neues Projekt** . Das Dialogfeld **Neues Projekt** wird angezeigt und sieht in etwa wie folgt aus:

 ![Screenshot: Dialogfeld „Neues Projekt“](../../extensibility/internals/media/newproject.gif)

 Das sehen wir uns etwas genauer an. Die **Projekttypen** Struktur listet die verschiedenen Projekttypen auf, die Sie erstellen können. Wenn Sie einen **Projekttyp wie Visual c#-Fenster** auswählen, wird eine Liste mit Anwendungs Vorlagen angezeigt, die Ihnen den Einstieg erleichtern. **Installierte Vorlagen von Visual Studio** werden von Visual Studio installiert und sind für alle Benutzer des Computers verfügbar. Neue Vorlagen, die Sie erstellen oder sammeln, können **meinen Vorlagen** hinzugefügt werden und sind nur für Sie verfügbar.

 Wenn Sie eine Vorlage wie die **Windows-Anwendung** auswählen, wird im Dialogfeld eine Beschreibung des Anwendungs Typs angezeigt. in diesem Fall **ein Projekt zum Erstellen einer Anwendung mit einer Windows-Benutzeroberfläche**.

 Am unteren Rand des Dialog Felds **Neues Projekt** sehen Sie mehrere Steuerelemente, die weitere Informationen sammeln. Die Steuerelemente, die angezeigt werden, hängen vom Projekttyp ab, aber im Allgemeinen enthalten Sie ein Textfeld für den Projekt **Namen** , ein Textfeld für den **Speicherort** und eine zugehörige Schaltfläche **zum** **Durchsuchen** , das Textfeld Projektmappenname und das zugehörige 

## <a name="populating-the-new-project-dialog-box"></a>Auffüllen des Dialog Felds "Neues Projekt"
 Wo erhält das Dialogfeld " **Neues Projekt** " seine Informationen? An dieser Stelle gibt es zwei Mechanismen, von denen eine als veraltet markiert ist. Im Dialogfeld **Neues Projekt** werden die von beiden Mechanismen erhaltenen Informationen kombiniert und angezeigt.

 Bei der älteren (veralteten) Methode werden System Registrierungseinträge und VSDIR-Dateien verwendet. Dieser Mechanismus wird ausgeführt, wenn Visual Studio geöffnet wurde. Bei der neueren Methode werden VSTEMPLATE-Dateien verwendet. Dieser Mechanismus wird bei der Initialisierung von Visual Studio ausgeführt, z. b. durch Ausführen von

```
devenv /setup
```

 oder

```
devenv /installvstemplates
```

### <a name="project-types"></a>Projekttypen
 Die Position und die Namen der **Projekttypen** Stamm Knoten, wie z. b. **Visual c#** und **andere Sprachen**, werden durch System Registrierungseinträge bestimmt. Die Organisation der untergeordneten Knoten, z. b. **Datenbank** und **intelligentes Gerät**, spiegelt die Hierarchie der Ordner wider, die die entsprechenden VSTEMPLATE-Dateien enthalten. Sehen wir uns zuerst die Stamm Knoten an.

#### <a name="project-type-root-nodes"></a>Projekttyp-Stamm Knoten
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] initialisiert wird, werden die untergeordneten Schlüssel des System Registrierungsschlüssels durchlaufen, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs, die Stamm Knoten der **Projekttypen** Struktur zu erstellen und zu benennen. Diese Informationen werden für die spätere Verwendung zwischengespeichert. Sehen Sie sich den Schlüssel templatedirs \\ {FAE04EC1-301F-11d3-BF4B-00C04F79EFBC} \\ /1 an. Jeder Eintrag ist eine VSPackage-GUID. Der Name des unter Schlüssels (/1) wird ignoriert, aber sein vorhanden sein weist darauf hin, dass es sich hierbei um einen **Projekttypen** Stamm Knoten handelt. Ein Stamm Knoten kann wiederum mehrere Unterschlüssel aufweisen, die seine Darstellung in der **Projekttypen** Struktur steuern. Sehen wir uns einige davon an.

##### <a name="default"></a>(Standardwert)
 Dies ist die Ressourcen-ID der lokalisierten Zeichenfolge, die den Stamm Knoten benennt. Die Zeichen folgen Ressource befindet sich in der von der VSPackage-GUID ausgewählten Satelliten-DLL.

 Im Beispiel lautet die VSPackage-GUID.

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 und die Ressourcen-ID (Standardwert) des Stamm Knotens (/1) ist #2345

 Wenn Sie die GUID im Schlüssel "in der Nähe von Paketen" nachschlagen und den Unterschlüssel "satellitedll" untersuchen, finden Sie den Pfad der Assembly, die die Zeichen folgen Ressource enthält:

 \<Visual Studio installation path>\VC # \VCSPackages\1033\csprojui.dll

 Um dies zu überprüfen, öffnen Sie den Datei-Explorer, und ziehen Sie csprojui.dll in das Visual Studio-Verzeichnis. Die Zeichen folgen Tabelle zeigt, dass das Ressourcen #2345 über die Beschriftung **Visual c#** verfügt.

##### <a name="sortpriority"></a>SortPriority
 Dadurch wird die Position des Stamm Knotens in der **Projekttypen** Struktur bestimmt.

 SortPriority REG_DWORD 0x00000014 (20)

 Je niedriger die Zahl der Priorität ist, desto höher ist die Position in der Struktur.

##### <a name="developeractivity"></a>Developeractivity
 Wenn dieser Unterschlüssel vorhanden ist, wird die Position des Stamm Knotens über das Dialogfeld Entwicklereinstellungen gesteuert. Beispiel:

 Developeractivity REG_SZ VC #

 Gibt an, dass Visual c# ein Stamm Knoten sein wird, wenn Visual Studio für die Entwicklung festgelegt ist [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Andernfalls wird es sich um einen untergeordneten Knoten **anderer Sprachen** handeln.

##### <a name="folder"></a>Ordner
 Wenn dieser Unterschlüssel vorhanden ist, wird der Stamm Knoten zu einem untergeordneten Knoten des angegebenen Ordners. Unter dem Schlüssel wird eine Liste möglicher Ordner angezeigt.

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Der Eintrag Datenbankprojekte enthält z. b. einen Ordner Schlüssel, der mit dem anderen Projekttypen Eintrag in pseudofolders übereinstimmt. Daher sind **Datenbankprojekte** in der **Projekttypen** Struktur ein untergeordneter Knoten **anderer Projekttypen**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Projekttypen untergeordneter Knoten und vstdir-Dateien
 Die Position der untergeordneten Knoten in der **Projekttypen** Struktur folgt der Hierarchie der Ordner in den ProjectTemplates-Ordnern. Für Computer Vorlagen (**installierte Vorlagen in Visual Studio**) lautet der typische Speicherort "\Programme\Microsoft Visual Studio 14,0 \ Common7\IDE\ProjectTemplates\". für Benutzervorlagen (**Meine Vorlagen**) lautet der typische Speicherort "\my Documents\Visual Studio 14,0 \ templates\projecttemplates" \\ . Die Ordner Hierarchien aus diesen beiden Speicherorten werden zusammengeführt, um die **Projekttypen** Struktur zu erstellen.

 Für Visual Studio mit c#-Entwicklereinstellungen sieht die **Projekttypen** Struktur etwa wie folgt aus:

 ![Screenshot der Projekttypen-Ordnerstruktur in Visual Studio mit c#-Entwicklereinstellungen.](../../extensibility/internals/media/projecttypes.png)

 Der entsprechende ProjectTemplates-Ordner sieht wie folgt aus:

 ![Screenshot der Projektvorlagen-Ordnerstruktur in Visual Studio mit c#-Entwicklereinstellungen.](../../extensibility/internals/media/projecttemplates.png)

 Wenn das Dialogfeld **Neues Projekt** geöffnet wird, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durchläuft den Ordner ProjectTemplates und erstellt seine Struktur in der **Projekttypen** Struktur mit einigen Änderungen neu:

- Der Stamm Knoten in der **Projekttypen** Struktur wird durch die Anwendungs Vorlage bestimmt.

- Der Knoten Name kann lokalisiert werden und kann Sonderzeichen enthalten.

- Die Sortierreihenfolge kann geändert werden.

##### <a name="finding-the-root-node-for-a-project-type"></a>Suchen des Stamm Knotens für einen Projekttyp
 Wenn Visual Studio die Ordner ProjectTemplates durchläuft, werden alle ZIP-Dateien geöffnet, und alle VSTEMPLATE-Dateien werden extrahiert. Eine VSTEMPLATE-Datei verwendet XML, um eine Anwendungs Vorlage zu beschreiben. Weitere Informationen finden Sie [unter New Project Generation: at the Hood, Part Two](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Das- \<ProjectType> Tag bestimmt den Projekttyp für die Anwendung. Die \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip Datei enthält beispielsweise eine emptyproject. VSTEMPLATE-Datei mit diesem Tag:

```
<ProjectType>CSharp</ProjectType>
```

 Das \<ProjectType> -Tag und nicht der Unterordner im Ordner ProjectTemplates bestimmt den Stamm Knoten einer Anwendung in der **Projekttypen** Struktur. Im Beispiel werden Windows CE Anwendungen unter dem **Visual c#** -Stamm Knoten angezeigt, und auch wenn Sie den Ordner "WindowsCE" in den Ordner "VisualBasic" verschieben würden, werden Windows CE Anwendungen weiterhin unter dem **Visual c#** -Stamm Knoten angezeigt.

##### <a name="localizing-the-node-name"></a>Lokalisieren des Knoten namens
 Wenn Visual Studio die Ordner ProjectTemplates durchläuft, werden alle gefundenen vstdir-Dateien untersucht. Bei einer vstdir-Datei handelt es sich um eine XML-Datei, mit der die Darstellung des Projekt Typs im Dialogfeld **Neues Projekt** gesteuert wird. Verwenden Sie in der vstdir-Datei das- \<LocalizedName> Tag, um den **Projekttypen** Knoten zu benennen.

 Beispielsweise enthält die Datei \csharp\database\templateindex.vstdir dieses Tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Dadurch werden die Satelliten-DLL und die Ressourcen-ID der lokalisierten Zeichenfolge bestimmt, die den Stamm Knoten benennt, in diesem Fall " **Database**". Der lokalisierte Name kann Sonderzeichen enthalten, die für Ordnernamen, wie z. b. **.net**, nicht verfügbar sind.

 Wenn kein \<LocalizedName> Tag vorhanden ist, wird der Projekttyp durch den Ordner selbst benannt, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Suchen der Sortierreihenfolge für einen Projekttyp
 Zum Bestimmen der Sortierreihenfolge für den Projekttyp verwenden vstdir-Dateien das- \<SortOrder> Tag.

 Beispielsweise enthält die Datei \csharp\windows\windows.vstdir dieses Tag:

```
<SortOrder>5</SortOrder>
```

 Die Datei \csharp\database\templateindex.vstdir verfügt über ein Tag mit einem größeren Wert:

```
<SortOrder>5000</SortOrder>
```

 Je niedriger die Zahl im \<SortOrder> Tag ist, desto höher ist die Position in der Struktur, sodass der **Windows** -Knoten größer als der **Daten Bank** Knoten in der **Projekttypen** Struktur ist.

 Wenn \<SortOrder> für einen Projekttyp kein Tag angegeben ist, wird es in alphabetischer Reihenfolge nach allen Projekttypen angezeigt, die \<SortOrder> Spezifikationen enthalten.

 Beachten Sie, dass sich in den Ordnern eigene Dateien (**Meine Vorlagen**) keine vstdir-Dateien befinden. Die Projekttypen Namen von Benutzer Anwendungen werden nicht lokalisiert und in alphabetischer Reihenfolge angezeigt.

#### <a name="a-quick-review"></a>Eine schnell Überprüfung
 Ändern Sie das Dialogfeld **Neues Projekt** , und erstellen Sie eine neue Benutzer Projektvorlage.

1. Fügen Sie den Unterordner "myprojectnode" dem Ordner "\Programme\Microsoft Visual Studio 14,0 \ Common7\IDE\ProjectTemplates\CSharp" hinzu.

2. Erstellen Sie mit einem beliebigen Text-Editor die Datei "MyProject. vstdir" im Ordner "myprojectnode".

3. Fügen Sie die folgenden Zeilen zur vstdir-Datei hinzu:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Speichern und schließen Sie die vstdir-Datei.

5. Erstellen Sie unter Verwendung eines beliebigen Text-Editors eine MyProject. VSTEMPLATE-Datei im Ordner "myprojectnode".

6. Fügen Sie die folgenden Zeilen der VSTEMPLATE-Datei hinzu:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Speichern Sie die VSTEMPLATE-Datei, und schließen Sie den Editor.

8. Senden Sie die VSTEMPLATE-Datei an einen neuen komprimierten MyProjectNode\MyProject.zip Ordner.

9. Geben Sie im Visual Studio-Befehlsfenster Folgendes ein:

    ```
    devenv /installvstemplates
    ```

   Öffnen Sie Visual Studio.

10. Öffnen Sie das Dialogfeld **Neues Projekt** , und erweitern Sie den **Visual c#** -Projekt Knoten.

    ![Screenshot der Projekttypen-Ordnerstruktur im Dialogfeld "Neues Projekt", wobei "myprojectnode" unter dem erweiterten Visual c#-Projekt Knoten hervorgehoben ist.](../../extensibility/internals/media/myprojectnode.png)

    **Myprojectnode** wird als untergeordneter Knoten von Visual c# direkt unterhalb des Windows-Knotens angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Neue Projektgenerierung: Einblick in die Hintergründe, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
