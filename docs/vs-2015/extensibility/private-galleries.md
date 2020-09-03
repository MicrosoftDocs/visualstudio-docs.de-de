---
title: Private Galerien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444920"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Steuerelemente, Vorlagen und Tools, die Sie entwickeln, freigeben, indem Sie Sie wie folgt in einem *privaten* Katalog im Intranet für Ihre Organisation veröffentlichen:  
  
- Erstellen Sie einen Atom-Feed (RSS) an einem entsprechend konfigurierten zentralen Speicherort (Repository) im Intranet. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines Atom-Feeds für einen privaten](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)Katalog.  
  
- Verteilen Sie eine pkgdef-Datei, in der die private Galerie beschrieben wird. Wir empfehlen diese Konfiguration für Administratoren, die eine private Galerie gleichzeitig mit vielen Computern verbinden möchten.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Hinzufügen einer privaten Galerie zu Erweiterungen und Updates in Visual Studio  
 Wenn ein privater Katalog verfügbar ist, können Sie ihn zu **Erweiterungen und Updates** in Visual Studio hinzufügen.  
  
 ![Erweiterungs-Manager – Dialogfeld „Hinzufügen“](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>So fügen Sie Erweiterungen und Updates eine private Galerie hinzu  
  
1. **Wählen Sie**in der Menüleiste Extras, **Optionen**aus.  
  
2. Wählen Sie im Knoten **Umgebung** die Option **Erweiterungen und Updates**aus.  
  
3. Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
4. Geben Sie im Feld **Name** einen Namen für die private Galerie ein, z. b `My Gallery` ..  
  
5. Geben Sie im Feld **URL** die URL des Atom-Feeds oder der SharePoint-Website ein, auf der die private Galerie gehostet wird.  
  
    1. Wenn es sich bei dem Host um einen Atom-Feed handelt, der eine Verbindung mit dem privaten Katalog herstellt, ähnelt die URL der folgenden URL: `http://www.mywebsite/mygallery/atom.xml` .  Diese URL kann auf eine Datei oder einen Netzwerkpfad verweisen.  
  
    2. Wenn es sich bei dem Host um eine SharePoint-Website handelt, ähnelt die URL der folgenden URL: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .  
  
### <a name="managing-private-galleries"></a>Verwalten von privaten Galerien  
 Ein Administrator kann einen privaten Katalog auf mehreren Computern gleichzeitig zur Verfügung stellen, indem er die Systemregistrierung auf jedem Computer ändert. Um dies zu erreichen, erstellen Sie eine pkgdef-Datei, die die neuen Registrierungsschlüssel und deren Werte beschreibt.  Das Format dieser Datei lautet wie folgt.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Weitere Informationen finden Sie unter Gewusst [wie: Verwalten einer privaten Galerie mithilfe von Registrierungs Einstellungen](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Installieren von Erweiterungen aus einem privaten Katalog  
 Sie können Visual Studio-Erweiterungen in einer privaten Galerie in **Erweiterungen und Updates**suchen und installieren. In den folgenden Schritten wird eine private Galerie namens verwendet `My Gallery` .  
  
 ![Erweiterungs-Manager – Installieren der privaten Galerie](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>So suchen und installieren Sie Erweiterungen aus einem privaten Katalog  
  
1. Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.  
  
2. Klicken Sie im linken Bereich auf **Online Erweiterungen**, und wählen Sie dann **meine Galerie**aus.  
  
3. Wählen Sie im rechten Bereich eine Erweiterung aus, und klicken Sie dann auf die Schaltfläche **herunterladen** .  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Aktualisieren von Erweiterungen aus einem privaten Katalog  
 Wenn neue Versionen von Visual Studio-Erweiterungen im privaten Katalog veröffentlicht werden, können Sie die Erweiterungen aktualisieren, die Sie installiert haben. In den folgenden Schritten wird eine private Galerie namens verwendet `My Repository` .  
  
 ![Erweiterungs-Manager – Aktualisierung der privaten Galerie](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>So aktualisieren Sie eine installierte Erweiterung aus einem privaten Katalog  
  
1. Wählen Sie auf der Menüleiste **Tools**, **Erweiterungen und Updates** aus.  
  
2. Klicken Sie im linken Bereich auf **Updates**, und wählen Sie dann **mein Repository**aus.  
  
3. Wählen Sie im rechten Bereich eine Erweiterung aus, und klicken Sie dann auf die Schaltfläche **Aktualisieren** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)   
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
