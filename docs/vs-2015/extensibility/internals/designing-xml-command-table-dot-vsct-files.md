---
title: Entwerfen der XML-Befehls Tabelle (. Vsct-Dateien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196847"
---
# <a name="designing-xml-command-table-vsct-files"></a>Entwerfen von Dateien für XML-Befehlstabellen (VSCT)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine XML-Befehls Tabellen Datei (vsct) beschreibt das Layout und die Darstellung von Befehls Elementen für ein VSPackage. Befehls Elemente enthalten Schaltflächen, Kombinations Felder, Menüs, Symbolleisten und Gruppen von Befehls Elementen. In diesem Thema werden XML-Befehls Tabellen Dateien, deren Auswirkungen auf Befehls Elemente und Menüs und deren Erstellung beschrieben.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Befehle, Menüs, Gruppen und die vsct-Datei  
 vsct-Dateien werden um Befehle, Menüs und Befehls Gruppen organisiert. XML-Tags in der vsct-Datei stellen jedes dieser Elemente zusammen mit anderen zugeordneten Elementen (z. b. Befehls Schaltflächen, Befehls Platzierung und Bitmaps) dar.  
  
 Wenn Sie ein neues VSPackage erstellen, indem Sie die- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Paket Vorlage ausführen, generiert die Vorlage abhängig von Ihrer Auswahl eine vsct-Datei mit den erforderlichen Elementen für einen Menübefehl, ein Tool Fenster oder einen benutzerdefinierten Editor. Diese vsct-Datei kann dann geändert werden, um die Anforderungen eines bestimmten VSPackages zu erfüllen. Beispiele zum Ändern einer vsct-Datei finden Sie in den Beispielen unter Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Informationen zum Erstellen einer neuen, leeren vsct-Datei finden Sie unter Gewusst [wie: Erstellen einer. Vsct-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Nach der Erstellung fügen Sie der Datei XML-Elemente,-Attribute und-Werte hinzu, um das Layout des Befehls Elements zu beschreiben. Ein ausführliches XML-Schema finden Sie in der [vsct-XML-Schema Referenz](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Unterschiede zwischen CTC-und vsct-Dateien  
 Obwohl die Bedeutung der XML-Tags in einer vsct-Datei mit denen im veralteten CTC-Dateiformat identisch ist, ist Ihre Implementierung etwas anders.  
  
- Mit dem neuen **\<extern>** Tag verweisen Sie auf andere zu kompilierende h-Dateien, z. b. die für die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Symbolleiste.  
  
- Während vsct-Dateien die **/include** -Anweisung unterstützen, wie CTC-Dateien, bietet Sie auch ein neues \<**import> * *-Element. Der Unterschied besteht darin, dass **/include** **alle** Informationen liefert, aber \<**import> * * nur die Namen.  
  
- CTC-Dateien erfordern zwar eine Header Datei, in der Sie die Präprozessordirektiven definieren, eine ist für vsct-Dateien jedoch nicht erforderlich. Platzieren Sie stattdessen die-Direktiven in der Symboltabelle, die sich in den **\<Symbol>** Elementen unten in der vsct-Datei befindet.  
  
- vsct-Dateien verfügen **\<Annotation>** über ein Tag, mit dem Sie beliebige Informationen, wie Notizen oder Bilder, einbetten können.  
  
- Werte werden als Attribute für das Element gespeichert.  
  
- Befehlsflags können einzeln oder gestapelt gespeichert werden.  IntelliSense funktioniert jedoch nicht bei gestapelten Befehlsflags. Weitere Informationen zu Befehlsflags finden Sie unter dem [Befehlsflag-Element](../../extensibility/command-flag-element.md).  
  
- Sie können mehrere Typen angeben, z. b. getrennte Dropdowns, Combos usw.  
  
- GUIDs werden nicht überprüft.  
  
- Jedes Benutzeroberflächen Element verfügt über eine Zeichenfolge, die den Text darstellt, der mit dem Element angezeigt wird.  
  
- Das übergeordnete Element ist optional. Wenn der Wert nicht weggelassen wird, wird der Wert "Gruppe unbekannt" verwendet.  
  
- Das Icon-Argument ist optional.  
  
- Der bitmapabschnitt (identisch mit einer CTC-Datei), mit dem Unterschied, dass Sie jetzt einen Dateinamen über href angeben können, der zur Kompilierzeit vom vsct.exe Compiler abgerufen wird.  
  
- Resid: die alte Bitmap-Ressourcen-ID kann verwendet werden und funktioniert weiterhin genauso wie in CTC-Dateien.  
  
- Href: eine neue Methode, die es Ihnen ermöglicht, einen Dateinamen für die Bitmap-Ressource anzugeben. Dabei wird davon ausgegangen, dass alle verwendet werden, sodass Sie den verwendeten Abschnitt weglassen können. Der Compiler sucht zuerst nach lokalen Ressourcen für die Datei, dann auf allen Netzwerkfreigaben und allen Ressourcen, die durch den Schalter/I definiert werden.  
  
- KeyBinding: Sie müssen keinen Emulator mehr angeben. Wenn Sie einen angeben, geht der Compiler davon aus, dass der Editor und der Emulator identisch sind.  
  
- Keychord--wurde gelöscht. Das neue Format lautet key1, MOD1, key2, MOD2.  Sie können entweder eine Zeichen-, eine hexadezimale oder eine VK-Konstante angeben.  
  
  Der neue Compiler, vsct.exe, kompiliert sowohl CTC-als auch vsct-Dateien. Der alte ctc.exe Compiler kann jedoch keine vsct-Dateien erkennen und nicht kompilieren.  
  
  Sie können den vsct.exe Compiler verwenden, um eine vorhandene CTO-Datei in eine vsct-Datei zu konvertieren. Weitere Informationen hierzu finden Sie unter Vorgehens [Weise: Erstellen einer. Vsct-Datei aus einer vorhandenen. CTO-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Die vsct-Dateielemente  
 Die Befehls Tabelle enthält die folgende Hierarchie und Elemente:  
  
 [Commandtable-Element](../../extensibility/commandtable-element.md) – stellt alle Befehle, Menü Gruppen und Menüs dar, die dem VSPackage zugeordnet sind.  
  
 [Extern-Element](../../extensibility/extern-element.md) – verweist auf externe h-Dateien, die Sie mit der vsct-Datei zusammenführen möchten.  
  
 [Include-Element](../../extensibility/include-element.md) – verweist auf alle zusätzlichen Header Dateien (. h), die zusammen mit der vsct-Datei kompiliert werden sollen. Eine vsct-Datei kann h-Dateien enthalten, die Konstanten enthalten, die Befehle, Menü Gruppen und Menüs definieren, die die IDE oder ein anderes VSPackage bereitstellt.  
  
 [Commands-Element](../../extensibility/commands-element.md) – stellt alle einzelnen Befehle dar, die ausgeführt werden können. Jeder Befehl verfügt über die folgenden vier untergeordneten Elemente:  
  
 [Menüs-Element](../../extensibility/menus-element.md) – stellt alle Menüs und Symbolleisten im VSPackage dar. Menüs sind Container für Gruppen von Befehlen.  
  
 [Groups-Element](../../extensibility/groups-element.md) – stellt alle Gruppen im VSPackage dar. Gruppen sind Sammlungen einzelner Befehle.  
  
 [Buttons-Element](../../extensibility/buttons-element.md) – stellt alle Befehls Schaltflächen und Menü Elemente im VSPackage dar. Schaltflächen sind visuelle Steuerelemente, die Befehlen zugeordnet werden können.  
  
 [Bitmaps-Element](../../extensibility/bitmaps-element.md) – stellt alle Bitmaps für alle Schaltflächen im VSPackage dar. Bitmaps sind Bilder, die je nach Kontext neben oder in den Befehls Schaltflächen angezeigt werden.  
  
 [Commandplacement-Element](../../extensibility/commandplacements-element.md) – gibt zusätzliche Speicherorte an, an denen die einzelnen Befehle in den Menüs des VSPackage positioniert werden sollen.  
  
 [Visibilityeinschränkungseinschränkungs-Element](../../extensibility/visibilityconstraints-element.md) – gibt an, ob ein Befehl immer oder nur in bestimmten Kontexten angezeigt wird, z. b. Wenn ein bestimmtes Dialogfeld oder Fenster angezeigt wird. Menüs und Befehle, die über einen Wert für dieses Element verfügen, werden nur angezeigt, wenn der angegebene Kontext aktiv ist. Das Standardverhalten besteht darin, den Befehl jederzeit anzuzeigen.  
  
 [KeyBinding-Element](../../extensibility/keybindings-element.md) – gibt alle Schlüsselbindungen für die Befehle an. Das heißt, eine oder mehrere Tastenkombinationen, die zum Ausführen des Befehls gedrückt werden müssen, z. b. **STRG + S**.  
  
 [Usedcommands-Element](../../extensibility/usedcommands-element.md) – informiert die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung, dass der angegebene Befehl zwar durch anderen Code implementiert wird, wenn das aktuelle VSPackage aktiv ist, aber die Befehls Implementierung bereitstellt.  
  
 `Symbols Element` – Enthält die Symbolnamen und GUID-IDs für alle Befehle im Paket.  
  
## <a name="vsct-file-design-guidelines"></a>. Richtlinien zum Entwerfen von vsct-Dateien  
 Befolgen Sie diese Richtlinien, um eine vsct-Datei erfolgreich zu entwerfen.  
  
- Befehle können nur in Gruppen platziert werden, Gruppen können nur in Menüs platziert werden, und Menüs können nur in Gruppen platziert werden. In der IDE werden nur Menüs angezeigt, Gruppen und Befehle nicht.  
  
- Untermenüs können nicht direkt einem Menü zugewiesen werden, sondern müssen einer Gruppe zugewiesen werden, die wiederum einem Menü zugewiesen wird.  
  
- Befehle, Untermenüs und Gruppen können mithilfe des übergeordneten Felds ihrer definierenden Direktive einer Gruppe oder einem anderen Menü zugewiesen werden.  
  
- Das Organisieren einer Befehls Tabelle allein durch die übergeordneten Felder in den Direktiven hat eine bedeutende Einschränkung. Die-Anweisungen, die-Objekte definieren, können nur ein übergeordnetes Argument annehmen.  
  
- Die Wiederverwendung von Befehlen, Gruppen oder Untermenüs erfordert, dass eine neue-Direktive verwendet wird, um eine neue Instanz des-Objekts mit einem eigenen paar zu erstellen `GUID:ID` .  
  
- Jedes `GUID:ID` Paar muss eindeutig sein. Die Wiederverwendung eines Befehls, der z. b. in einem Menü, einer Symbolleiste oder in einem Kontextmenü angezeigt wird, wird von der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle behandelt.  
  
- Befehle und Untermenüs können auch mehreren Gruppen zugewiesen werden, und Gruppen können mit dem [Commands-Element](../../extensibility/commands-element.md)mehreren Menüs zugewiesen werden.  
  
## <a name="vsct-file-notes"></a>. Vsct-Datei Hinweise  
 Wenn Sie Änderungen an einer vsct-Datei vornehmen, nachdem Sie sie kompiliert und in einer nativen Satelliten-DLL abgelegt haben, sollten Sie **devenv.exe/Setup/nosetupvstemplates**ausführen. Dadurch wird erzwungen, dass die in der experimentellen Registrierung angegebenen VSPackage-Ressourcen erneut registriert werden und die interne Datenbank, die beschreibt, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] neu erstellt werden soll.  
  
 Während der Entwicklung ist es möglich, mehrere VSPackage-Projekte in der experimentellen Registrierungs Struktur zu erstellen und zu registrieren, die zu einem verwirrenden Cluster in der IDE führen kann. Um dieses Problem zu beheben, können Sie die experimentelle Struktur auf die Standardeinstellungen zurücksetzen, um alle registrierten VSPackages und alle Änderungen, die Sie möglicherweise an der IDE vorgenommen haben, zu entfernen. Verwenden Sie zum Zurücksetzen der experimentellen Struktur das CreateExpInstance.exe Tool, das im Visual Studio SDK verfügbar ist. Sie finden es unter  
  
 **% Program Files (x86)% \ Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Führen Sie das Tool mit der Befehlszeile " **/Reset**" aus. Beachten Sie, dass dieses Tool alle registrierten VSPackages, die normalerweise nicht mit installiert wurden, aus der experimentellen Hive entfernt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)
