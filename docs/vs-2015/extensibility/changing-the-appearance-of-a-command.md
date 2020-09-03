---
title: Ändern der Darstellung eines Befehls | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4741059410e052c571d77088b9cbe109fb651642
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184504"
---
# <a name="changing-the-appearance-of-a-command"></a>Ändern der Darstellung eines Befehls
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihrem Benutzer Feedback geben, indem Sie die Darstellung eines Befehls ändern. Beispielsweise kann es sein, dass ein Befehl anders aussieht, wenn er nicht verfügbar ist. Sie können Befehle verfügbar oder nicht verfügbar machen, Sie ausblenden oder anzeigen oder im Menü aktivieren oder deaktivieren.  
  
 Um das Aussehen eines Befehls zu ändern, führen Sie eine der folgenden Aktionen aus:  
  
- Geben Sie die entsprechenden Flags in der Befehls Definition in der Befehls Tabellen Datei an.  
  
- Verwenden Sie den- <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Dienst.  
  
- Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, und ändern Sie die rohbefehls Objekte.  
  
  Die folgenden Schritte zeigen, wie Sie die Darstellung eines Befehls mithilfe des Managed Package Framework (MPF) suchen und aktualisieren.  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>So ändern Sie die Darstellung eines Menübefehls  
  
1. Befolgen Sie die Anweisungen unter [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) , um ein Menü Element mit dem Namen zu erstellen `New Text` .  
  
2. Fügen Sie in der Datei ChangeMenuText.cs die folgende using-Anweisung hinzu:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3. Fügen Sie in der Datei ChangeMenuTextPackageGuids.cs die folgende Zeile hinzu:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4. Ersetzen Sie in der Datei ChangeMenuText.cs den Code in der ShowMessageBox-Methode durch Folgendes:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5. Rufen Sie den Befehl, den Sie aktualisieren möchten, aus dem <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> -Objekt ab, und legen Sie dann die entsprechenden Eigenschaften für das Command-Objekt fest. Mit der folgenden Methode wird z. b. der angegebene Befehl aus einem VSPackage-Befehlssatz verfügbar oder nicht verfügbar. Der folgende Code bewirkt, dass das Menü Element mit dem Namen nicht verfügbar ist, `New Text` nachdem darauf geklickt wurde.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
7. Klicken Sie **im Menü Extras auf den Befehl** **changemenutext aufrufen** . An diesem Punkt lautet der Befehls Name " **changemenutext**", sodass der Befehls Handler "changemycommand ()" nicht aufruft.  
  
8. **Im Menü Extras** sollte nun **neuer Text**angezeigt werden. Klicken Sie auf **neuer Text**. Der Befehl sollte nun abgeblendet sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
