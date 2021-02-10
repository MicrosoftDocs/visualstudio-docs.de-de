---
title: Kombinieren von VBA und Anpassungen auf Dokument Ebene
description: Erfahren Sie, wie Sie Visual Basic for Applications-Code (VBA) in einem Dokument verwenden können, das Teil einer Anpassung auf Dokument Ebene für Microsoft Office Word oder Excel ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1c5f66042dad7051c856aa6158ea0a666a81e9b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938524"
---
# <a name="combine-vba-and-document-level-customizations"></a>Kombinieren von VBA und Anpassungen auf Dokument Ebene
  Sie können VBA-Code (Visual Basic for Applications) in einem Dokument verwenden, das Teil einer Dokumentebenenanpassung für Microsoft Office Word oder Microsoft Office Excel ist. Sie können VBA-Code im Dokument über die Anpassungsassembly aufrufen, oder Sie können für Ihr Projekt die Aktivierung des VBA-Codes im Dokument konfigurieren, um Code in der Anpassungsassembly aufzurufen.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Verhalten von VBA-Code in einer Anpassung auf Dokument Ebene
 Wenn Sie Ihr Projekt in Visual Studio öffnen, wird das Dokument im Entwurfsmodus geöffnet. Der VBA-Code wird nicht ausgeführt, wenn sich das Dokument im Entwurfsmodus befindet, damit Sie am Dokument und Code arbeiten können, ohne den VBA-Code auszuführen.

 Beim Ausführen der Projektmappe wählen Ereignishandler in VBA und in der Anpassungsassembly Ereignisse aus, die im Dokument ausgelöst werden, und beide Codesätze werden ausgeführt. Sie können nicht im Voraus bestimmen, welcher Code zuerst ausgeführt wird. Sie müssen dies durch Tests in jedem Einzelfall ermitteln. Es können unerwartete Ergebnisse auftreten, wenn zwei Codesätze nicht sorgfältig koordiniert und getestet werden.

## <a name="call-vba-code-from-the-customization-assembly"></a>VBA-Code aus der Anpassungsassembly abrufen
 Sie können Makros in Word-Dokumenten aufrufen, und Sie können Makros und Funktionen in Excel-Arbeitsmappen aufrufen. Hierzu können Sie eine der folgenden Methoden verwenden:

- Nennen Sie für Word die- <xref:Microsoft.Office.Interop.Word._Application.Run%2A> Methode der- <xref:Microsoft.Office.Interop.Word.Application> Klasse.

- Rufen Sie für Excel die <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Application> -Klasse auf.

  Bei jeder Methode wird mit dem ersten Parameter der Name des Makros oder der Funktion identifiziert, das bzw. die Sie aufrufen möchten, und mit den restlichen optionalen Parametern werden die Parameter angegeben, die an das Makro oder die Funktion übergeben werden. Der erste Parameter kann für Word und Excel verschiedene Formate haben:

- Für Word ist der erste Parameter eine Zeichenfolge, bei der es sich um eine Kombination aus Vorlage, Modul und Makroname handeln kann. Wenn Sie den Dokumentnamen angeben, kann Ihr Code nur Makros in Dokumenten ausführen, die sich auf den aktuellen Kontext beziehen – kein beliebiges Makro in einem beliebigen Dokument.

- Für Excel kann der erste Parameter eine Zeichenfolge sein, mit dem der Makroname, ein <xref:Microsoft.Office.Interop.Excel.Range> -Element zum Angeben der Funktion oder eine registrierte ID für eine registrierte DLL-Funktion (XLL) angegeben wird. Wenn Sie eine Zeichenfolge übergeben, wird die Zeichenfolge im Kontext des aktiven Blatts ausgewertet.

  Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein Makro mit dem Namen `MyMacro` aus einem Projekt auf Dokumentebene für Excel aufrufen. In diesem Beispiel wird vorausgesetzt, dass `MyMacro` in `Sheet1`definiert ist.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Informationen zur Verwendung der globalen `missing` Variablen anstelle von optionalen Parametern in Visual c# finden Sie unter [Schreiben von Code in Office](../vsto/writing-code-in-office-solutions.md)-Projektmappen.

## <a name="call-code-in-document-level-customizations-from-vba"></a>Aufrufe von Code in Anpassungen auf Dokument Ebene aus VBA
 Sie können ein Projekt auf Dokumentebene für Word oder Excel konfigurieren, damit VBA-Code (Visual Basic for Applications) im Dokument Code in der Anpassungsassembly aufrufen kann. Dies ist in den folgenden Szenarien nützlich:

- Sie möchten vorhandenen VBA-Code in einem Dokument erweitern, indem Sie Features in einer Anpassung auf Dokumentebene verwenden, die demselben Dokument zugeordnet ist.

- Sie möchten Dienste, die Sie in einer Anpassung auf Dokumentebene entwickeln, für Endbenutzer verfügbar machen. Die Endbenutzer können auf die Dienste zugreifen, indem im Dokument VBA-Code geschrieben wird.

  Die Office-Entwicklungs Tools in Visual Studio bieten eine ähnliche Funktion für VSTO-Add-Ins. Wenn Sie ein VSTO-Add-in entwickeln, können Sie Code in Ihrem VSTO-Add-in aus anderen Microsoft Office-Lösungen abrufen. Weitere Informationen finden Sie unter [Aufrufe von Code in VSTO-Add-Ins aus anderen Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)-Projektmappen.

> [!NOTE]
> Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden. Sie kann nur in Word-Dokument-, Excel-Arbeitsmappen- oder Excel-Vorlagenprojekten verwendet werden.

## <a name="requirements"></a>Anforderungen
 Bevor Sie VBA-Code zum Aufrufen aus der Anpassungsassembly aktivieren können, muss das Projekt die folgenden Anforderungen erfüllen:

- Das Dokument muss eine der folgenden Dateinamenerweiterungen haben:

  - Für Word: *. docm* oder *. doc*

  - Für Excel: *. xlsm*, *. xltm*, *. xls* oder *. xlt*

- Das Dokument muss bereits ein VBA-Projekt mit VBA-Code enthalten.

- Für den VBA-Code im Dokument muss die Ausführung zulässig sein, ohne dass der Benutzer zum Aktivieren von Makros aufgefordert wird. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.

- Das Office-Projekt muss mindestens eine öffentliche Klasse mit einem oder mehreren öffentlichen Membern enthalten, die Sie für VBA verfügbar machen.

     Sie können Methoden, Eigenschaften und Ereignisse für VBA verfügbar machen. Bei der Klasse, die Sie verfügbar machen können, kann es sich um eine Hostelementklasse (z. B. `ThisDocument` für Word oder `ThisWorkbook` und `Sheet1` für Excel) oder eine andere Klasse handeln, die Sie in Ihrem Projekt definieren. Weitere Informationen zu Host Elementen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Aktivieren von VBA-Code zum Abrufen der Anpassungsassembly
 Es gibt zwei unterschiedliche Möglichkeiten, wie Sie Member in einer Anpassungsassembly für VBA-Code im Dokument verfügbar machen können:

- Sie können Member einer Hostelementklasse in einem [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] -Projekt für VBA verfügbar machen. Legen Sie hierzu im Fenster **Eigenschaften** die **EnableVbaCallers** -Eigenschaft des Hostelements auf **True** fest, während das Hostelement (also Dokument, Arbeitsblatt oder Arbeitsmappe) im Designer geöffnet ist. Visual Studio führt automatisch alle Schritte aus, die erforderlich sind, um für VBA-Code das Aufrufen von Membern der Klasse zu ermöglichen.

- Sie können Member in einer öffentlichen Klasse in einem Visual C#-Projekt oder in einer anderen Klasse als einer Hostelementklasse in einem [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] -Projekt für VBA verfügbar machen. Bei dieser Option können Sie freier wählen, welche Klassen Sie für VBA verfügbar machen, aber es sind auch mehr manuelle Schritte erforderlich.

   Hierzu müssen Sie die folgenden Hauptschritte ausführen:

  1. Machen Sie die Klasse für COM verfügbar.

  2. Überschreiben Sie die **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt, um eine Instanz der Klasse zurückzugeben, die Sie für VBA verfügbar machen.

  3. Legen Sie die **ReferenceAssemblyFromVbaProject** -Eigenschaft einer beliebigen Hostelementklasse im Projekt auf **True** fest. Dadurch wird die Typbibliothek der Anpassungsassembly in die Assembly eingebettet, und dem VBA-Projekt im Dokument wird ein Verweis auf die Typbibliothek hinzugefügt.

  Ausführliche Anweisungen finden Sie unter Gewusst wie: verfügbar machen von [Code für VBA in einem Visual Basic Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) und Gewusst wie: verfügbar machen von [Code für VBA in einem Visual C&#35;-Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

  Die Eigenschaften **EnableVbaCallers** und **ReferenceAssemblyFromVbaProject** sind nur zur Entwurfszeit im Fenster **Eigenschaften** verfügbar. Sie können zur Laufzeit nicht verwendet werden. Öffnen Sie zum Anzeigen der Eigenschaften den Designer für ein Hostelement in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen zu den spezifischen Aufgaben, die Visual Studio ausführt, wenn Sie diese Eigenschaften festlegen, finden Sie unter [von den Host Element Eigenschaften ausgeführte Aufgaben](#PropertyTasks).

> [!NOTE]
> Wenn die Arbeitsmappe oder das Dokument nicht bereits VBA-Code enthält oder wenn die Ausführung des VBA-Codes im Dokument nicht als vertrauenswürdig eingestuft wird, erhalten Sie eine Fehlermeldung, sobald Sie die **EnableVbaCallers** - oder **ReferenceAssemblyFromVbaProject** -Eigenschaft auf **True** festlegen. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Verwenden von Membern in VBA-Code zum Abrufen der Anpassungsassembly
 Nachdem Sie im Projekt für den VBA-Code Aufrufe in der Anpassungsassembly konfiguriert haben, fügt Visual Studio dem VBA-Projekt im Dokument die folgenden Member hinzu:

- Für alle Projekte fügt Visual Studio eine globale Methode mit dem Namen `GetManagedClass`hinzu.

- Für [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Projekte, in denen Sie Member einer Host Element Klasse mithilfe der **enablevbacallzer** -Eigenschaft verfügbar machen, fügt Visual Studio `CallVSTOAssembly` dem `ThisDocument` `ThisWorkbook` Modul,, `Sheet1` , `Sheet2` oder `Sheet3` im VBA-Projekt auch eine Eigenschaft mit dem Namen hinzu.

  Sie können die `CallVSTOAssembly` -Eigenschaft oder die `GetManagedClass` -Methode verwenden, um auf öffentliche Member der Klasse zuzugreifen, die Sie für den VBA-Code im Projekt verfügbar gemacht haben.

> [!NOTE]
> Beim Entwickeln und Bereitstellen Ihrer Projektmappe sind mehrere unterschiedliche Kopien des Dokuments vorhanden, denen Sie den VBA-Code hinzufügen können. Weitere Informationen finden Sie unter [Richtlinien zum Hinzufügen von VBA-Code zum Dokument](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Verwenden der CallVSTOAssembly-Eigenschaft in einem Visual Basic Projekt
 Verwenden Sie die `CallVSTOAssembly` -Eigenschaft, um auf öffentliche Member zuzugreifen, die Sie der Hostelementklasse hinzugefügt haben. Mit dem folgenden VBA-Makro wird beispielsweise eine Methode mit dem Namen `MyVSTOMethod` aufgerufen, die in der `Sheet1` -Klasse in einem Excel-Arbeitsmappenprojekt definiert ist.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Diese Eigenschaft ist ein bequemerer Weg zum Aufrufen der Anpassungsassembly als die direkte Verwendung der `GetManagedClass` -Methode. `CallVSTOAssembly` gibt ein Objekt zurück, das für die Hostelementklasse steht, die Sie für VBA verfügbar gemacht haben. Die Member und Methodenparameter des zurückgegebenen Objekts werden in IntelliSense angezeigt.

 Die `CallVSTOAssembly` -Eigenschaft verfügt über eine Deklaration, die dem folgenden Code ähnelt. In diesem Code wird vorausgesetzt, dass Sie die `Sheet1` -Hostelementklasse in einem Excel-Arbeitsmappenprojekt mit dem Namen `ExcelWorkbook1` für VBA verfügbar gemacht haben.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Verwenden der GetManagedClass-Methode
 Übergeben Sie zum Verwenden der globalen `GetManagedClass` -Methode das VBA-Objekt, das der Hostelementklasse entspricht, in der Ihre Überschreibung der **GetAutomationObject** -Methode enthalten ist. Verwenden Sie dann das zurückgegebene Objekt zum Zugreifen auf die Klasse, die Sie für VBA verfügbar gemacht haben.

 Mit dem folgenden VBA-Makro wird beispielsweise eine Methode mit dem Namen `MyVSTOMethod` aufgerufen, die in der `Sheet1` -Hostelementklasse in einem Excel-Arbeitsmappenprojekt mit dem Namen `ExcelWorkbook1`definiert ist.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 Die `GetManagedClass` -Methode weist die folgende Deklaration auf:

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Diese Methode gibt ein Objekt zurück, das für die Klasse steht, die Sie für VBA verfügbar gemacht haben. Die Member und Methodenparameter des zurückgegebenen Objekts werden in IntelliSense angezeigt.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Richtlinien zum Hinzufügen von VBA-Code zum Dokument
 Es sind mehrere unterschiedliche Kopien des Dokuments vorhanden, denen Sie VBA-Code hinzufügen können, um Aufrufe für die Anpassung auf Dokumentebene durchführen zu können.

 Beim Entwickeln und Testen Ihrer Projektmappe können Sie VBA-Code im Dokument schreiben, das geöffnet wird, während Sie das Projekt in Visual Studio (also das Dokument im Buildausgabeordner) debuggen oder ausführen. Sämtlicher VBA-Code, den Sie diesem Dokument hinzufügen, wird beim nächsten Erstellen des Projekts überschrieben. Visual Studio ersetzt das Dokument im Buildausgabeordner durch eine Kopie des Dokuments aus dem Hauptordner des Projekts.

 Wenn Sie den VBA-Code speichern möchten, den Sie dem Dokument beim Debuggen oder Ausführen der Projektmappe hinzufügen, kopieren Sie den VBA-Code in das Dokument im Projektordner. Weitere Informationen zum Buildprozess finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

 Wenn Sie die Projektmappe bereitstellen möchten, stehen Ihnen drei Hauptspeicherorte für Dokumente zur Verfügung, an denen Sie den VBA-Code hinzufügen können.

### <a name="in-the-project-folder-on-the-development-computer"></a>Im Projektordner auf dem Entwicklungs Computer
 Dieser Speicherort ist gut geeignet, wenn Sie die vollständige Kontrolle über den VBA-Code im Dokument und den Anpassungscode haben. Da sich das Dokument auf dem Entwicklungscomputer befindet, können Sie den VBA-Code leicht ändern, wenn Sie den Anpassungscode ändern. VBA-Code, den Sie dieser Kopie des Dokuments hinzufügen, verbleibt im Dokument, wenn Sie die Projektmappe erstellen, debuggen und veröffentlichen.

 Sie können den VBA-Code dem Dokument nicht hinzufügen, während es im Designer geöffnet ist. Sie müssen das Dokument zuerst im Designer schließen und es dann direkt in Word oder Excel öffnen.

> [!CAUTION]
> Wenn Sie VBA-Code hinzufügen, der bei geöffnetem Dokument ausgeführt wird, kann es in selten Fällen dazu kommen, dass dieser Code zu einer Beschädigung des Dokuments führt oder das Öffnen im Designer verhindert.

### <a name="in-the-publish-or-installation-folder"></a>Im Veröffentlichungs-oder Installationsordner
 In einigen Fällen kann es sinnvoll sein, den VBA-Code dem Dokument im Veröffentlichungs- oder Installationsordner hinzuzufügen. Beispielsweise können Sie diese Option wählen, wenn der VBA-Code von einem anderen Entwickler auf einem Computer geschrieben und getestet wird, auf dem Visual Studio nicht installiert ist.

 Wenn Benutzer die Projektmappe direkt aus dem Veröffentlichungsordner installieren, müssen Sie den VBA-Code dem Dokument jedes Mal hinzufügen, wenn Sie die Projektmappe veröffentlichen. Visual Studio überschreibt das Dokument am Veröffentlichungsspeicherort, wenn Sie die Projektmappe veröffentlichen.

 Wenn Benutzer die Projektmappe aus einem Installationsordner installieren, der sich vom Veröffentlichungsordner unterscheidet, können Sie verhindern, dass Sie den VBA-Code dem Dokument bei jeder Veröffentlichung der Projektmappe hinzufügen müssen. Wenn ein Veröffentlichungsupdate für das Verschieben aus dem Veröffentlichungsordner in den Installationsordner bereit ist, kopieren Sie alle Dateien in den Installationsordner, mit Ausnahme des Dokuments.

### <a name="on-the-end-user-computer"></a>Auf dem Endbenutzer Computer
 Wenn es sich bei den Endbenutzern um VBA-Entwickler handelt, von denen Dienste aufgerufen werden, die Sie in der Anpassung auf Dokumentebene bereitstellen, ist Folgendes möglich: Sie können ihnen mitteilen, wie Ihr Code aufgerufen wird, indem Sie die `CallVSTOAssembly` -Eigenschaft oder die `GetManagedClass` -Methode in ihren Kopien des Dokuments verwenden. Wenn Sie Updates für die Lösung veröffentlichen, wird VBA-Code im Dokument auf dem Endbenutzer Computer nicht überschrieben, da das Dokument nicht durch Veröffentlichungs Updates geändert wird.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Von den Host Element Eigenschaften ausgeführte Aufgaben
 Wenn Sie die Eigenschaften **EnableVbaCallers** und **ReferenceAssemblyFromVbaProject** verwenden, führt Visual Studio unterschiedliche Aufgabensätze aus.

### <a name="enablevbacallers"></a>Eigenschaften
 Wenn Sie die **EnableVbaCallers** -Eigenschaft eines Hostelements in einem Visual Basic-Projekt auf **True** festlegen, führt Visual Studio die folgenden Aufgaben aus:

1. Die Attribute <xref:Microsoft.VisualBasic.ComClassAttribute> und <xref:System.Runtime.InteropServices.ComVisibleAttribute> werden der Hostelementklasse hinzugefügt.

2. Die **GetAutomationObject** -Methode der Hostelementklasse wird überschrieben.

3. Die **ReferenceAssemblyFromVbaProject** -Eigenschaft des Hostelements wird auf **True** festgelegt.

   Wenn Sie die **EnableVbaCallers** -Eigenschaft zurück auf **False** setzen, führt Visual Studio die folgenden Aufgaben aus:

4. Die Attribute <xref:Microsoft.VisualBasic.ComClassAttribute> und <xref:System.Runtime.InteropServices.ComVisibleAttribute> werden aus der `ThisDocument` -Klasse entfernt.

5. Die **GetAutomationObject** -Methode wird aus der Hostelementklasse entfernt.

   > [!NOTE]
   > Visual Studio legt die **ReferenceAssemblyFromVbaProject** -Eigenschaft nicht automatisch wieder auf **False** fest. Sie können diese Eigenschaft manuell auf **False** festlegen, indem Sie das Fenster **Eigenschaften** verwenden.

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Wenn die **ReferenceAssemblyFromVbaProject** -Eigenschaft eines beliebigen Hostelements in einem Visual Basic- oder Visual C#-Projekt auf **True** festgelegt ist, führt Visual Studio die folgenden Aufgaben aus:

1. Es wird eine Typbibliothek für die Anpassungsassembly generiert und die Typbibliothek in die Assembly eingebettet.

2. Es wird ein Verweis auf die folgenden Typbibliotheken im VBA-Projekt im Dokument hinzugefügt:

   - Die Typbibliothek für die Anpassungsassembly.

   - Die Typbibliothek „Microsoft Visual Studio-Tools für Office-Ausführungs-Engine 9.0“. Diese Typbibliothek ist in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]enthalten.

   Wenn die **ReferenceAssemblyFromVbaProject** -Eigenschaft wieder auf **False** festgelegt wird, führt Visual Studio die folgenden Aufgaben aus:

3. Die Typbibliotheksverweise werden aus dem VBA-Projekt im Dokument entfernt.

4. Die eingebettete Typbibliothek wird aus der Assembly entfernt.

## <a name="troubleshoot"></a>Problembehandlung
 Die folgende Tabelle enthält einige häufige Fehler und Vorschläge zum Beheben der Fehler.

|Fehler|Vorschlag|
|-----------|----------------|
|Nachdem Sie die **EnableVbaCallers** - oder **ReferenceAssemblyFromVbaProject** -Eigenschaft festgelegt haben, wird in einer Fehlermeldung angegeben, dass im Dokument kein VBA-Projekt enthalten ist oder dass Sie keine Berechtigung zum Zugreifen auf das VBA-Projekt im Dokument haben.|Stellen Sie sicher, dass das Dokument im Projekt mindestens ein VBA-Makro enthält, dass das VBA-Projekt vertrauenswürdig genug für die Ausführung ist und dass das VBA-Projekt nicht mit einem Kennwort geschützt ist.|
|Nachdem Sie die **Eigenschaften** - oder **ReferenceAssemblyFromVbaProject** -Eigenschaft festgelegt haben, wird in einer Fehlermeldung angegeben, dass die <xref:System.Runtime.InteropServices.GuidAttribute> -Deklaration fehlt oder beschädigt ist.|Stellen Sie sicher, dass sich die- <xref:System.Runtime.InteropServices.GuidAttribute> Deklaration in der *AssemblyInfo.cs* -oder *AssemblyInfo. vb* -Datei im Projekt befindet und dass dieses Attribut auf eine gültige GUID festgelegt ist.|
|Nachdem Sie die **Eigenschaften** - oder **ReferenceAssemblyFromVbaProject** -Eigenschaft festgelegt haben, wird in einer Fehlermeldung angegeben, dass die vom <xref:System.Reflection.AssemblyVersionAttribute> -Element angegebene Versionsnummer ungültig ist.|Stellen Sie sicher, dass die <xref:System.Reflection.AssemblyVersionAttribute> Deklaration in der *AssemblyInfo.cs* -oder *AssemblyInfo. vb* -Datei in Ihrem Projekt auf eine gültige Versionsnummer der Assembly festgelegt ist. Informationen zu gültigen Assemblyversionsnummern finden Sie unter der <xref:System.Reflection.AssemblyVersionAttribute> -Klasse.|
|Nachdem Sie die Anpassungsassembly umbenannt haben, funktioniert der VBA-Code nicht mehr, mit dem Aufrufe für die Anpassungsassembly durchgeführt werden.|Wenn Sie den Namen der Anpassungsassembly ändern, nachdem Sie diese für den VBA-Code verfügbar gemacht haben, ist der Link zwischen dem VBA-Projekt im Dokument und Ihrer Anpassungsassembly beschädigt. Um dieses Problem zu beheben, ändern Sie die **ReferenceFromVbaAssembly** -Eigenschaft im Projekt in **False** und dann zurück in **True**. Ersetzen Sie anschließend alle Verweise auf den alten Assemblynamen im VBA-Code durch den neuen Assemblynamen.|

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual Basic Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual C-&#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual Basic Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual C-&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Vergleich von VBA-und Office-Projektmappen in Visual Studio](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
