---
title: Private Galerien | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Steuerelemente, Vorlagen und Tools freigeben, die Sie im Visual Studio SDK entwickeln, indem Sie Sie in einem privaten Katalog veröffentlichen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ec7390acf753af20bc0edbe20194ba17c2d9d80
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863504"
---
# <a name="private-galleries"></a>Private Kataloge
Sie können die Steuerelemente, Vorlagen und Tools, die Sie entwickeln, freigeben, indem Sie Sie wie folgt in einem *privaten* Katalog im Intranet für Ihre Organisation veröffentlichen:

- Erstellen Sie einen Atom-Feed (RSS) an einem entsprechend konfigurierten zentralen Speicherort (Repository) im Intranet. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines Atom-Feeds für einen privaten](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)Katalog.

- Verteilen Sie eine *pkgdef* -Datei, in der die private Galerie beschrieben wird. Wir empfehlen diese Konfiguration für Administratoren, die eine private Galerie gleichzeitig mit vielen Computern verbinden möchten.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Hinzufügen einer privaten Galerie zu Erweiterungen und Updates in Visual Studio
 Wenn ein privater Katalog verfügbar ist, können Sie ihn zu **Erweiterungen und Updates** in Visual Studio hinzufügen.

 ![Erweiterungs-Manager – Dialogfeld „Hinzufügen“](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>So fügen Sie Erweiterungen und Updates eine private Galerie hinzu

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**.

2. Wählen Sie im Knoten **Umgebung** die Option **Erweiterungen und Updates** aus.

3. Wählen Sie die Schaltfläche **Hinzufügen** aus.

4. Geben Sie im Feld **Name** einen Namen für die private Galerie ein, z. b `My Gallery` ..

5. Geben Sie im Feld **URL** die URL des Atom-Feeds oder der SharePoint-Website ein, auf der die private Galerie gehostet wird.

    1. Wenn es sich bei dem Host um einen Atom-Feed handelt, der eine Verbindung mit dem privaten Katalog herstellt, ähnelt die URL der folgenden URL: `http://www.mywebsite/mygallery/atom.xml` .  Diese URL kann auf eine Datei oder einen Netzwerkpfad verweisen.

    2. Wenn es sich bei dem Host um eine SharePoint-Website handelt, ähnelt die URL der folgenden URL: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Private Galerien verwalten
 Ein Administrator kann einen privaten Katalog auf mehreren Computern gleichzeitig zur Verfügung stellen, indem er die Systemregistrierung auf jedem Computer ändert. Um dies zu erreichen, erstellen Sie eine *pkgdef* -Datei, die die neuen Registrierungsschlüssel und deren Werte beschreibt.  Das Format dieser Datei lautet wie folgt.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Weitere Informationen finden Sie unter Gewusst [wie: Verwalten einer privaten Galerie mithilfe von Registrierungs Einstellungen](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Installieren von Erweiterungen aus einem privaten Katalog
 Sie können Visual Studio-Erweiterungen in einer privaten Galerie in **Erweiterungen und Updates** suchen und installieren. In den folgenden Schritten wird eine private Galerie namens verwendet `My Gallery` .

 ![Erweiterungs-Manager – Installieren der privaten Galerie](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>So suchen und installieren Sie Erweiterungen aus einem privaten Katalog

1. Wählen **Sie in** der Menüleiste Extras  >  **Erweiterungen und Updates** aus.

2. Klicken Sie im linken Bereich auf **Online Erweiterungen**, und wählen Sie dann **meine Galerie** aus.

3. Wählen Sie im rechten Bereich eine Erweiterung aus, und klicken Sie dann auf die Schaltfläche **herunterladen** .

## <a name="update-extensions-from-a-private-gallery"></a>Aktualisieren von Erweiterungen aus einem privaten Katalog
 Wenn neue Versionen von Visual Studio-Erweiterungen im privaten Katalog veröffentlicht werden, können Sie die Erweiterungen aktualisieren, die Sie installiert haben. In den folgenden Schritten wird eine private Galerie namens verwendet `My Repository` .

 ![Erweiterungs-Manager – Aktualisierung der privaten Galerie](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>So aktualisieren Sie eine installierte Erweiterung aus einem privaten Katalog

1. Wählen **Sie in** der Menüleiste Extras  >  **Erweiterungen und Updates** aus.

2. Klicken Sie im linken Bereich auf **Updates**, und wählen Sie dann **mein Repository** aus.

3. Wählen Sie im rechten Bereich eine Erweiterung aus, und klicken Sie dann auf die Schaltfläche **Aktualisieren** .

## <a name="see-also"></a>Weitere Informationen
- [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
- [Lieferumfang von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
