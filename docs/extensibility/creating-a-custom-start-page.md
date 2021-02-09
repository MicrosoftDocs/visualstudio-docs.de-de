---
title: Erstellen einer benutzerdefinierten Start Seite | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine benutzerdefinierte Start Seite erstellen. Beginnen Sie mit einer leeren Startseite, fügen Sie dem leeren UserControl-Element Steuerelemente hinzu, und testen Sie dann die Seite.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 65415c22da2815650278ac1190e7d19f54b96063
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853084"
---
# <a name="creating-a-custom-start-page"></a>Erstellen einer benutzerdefinierten Start Seite

Sie können eine benutzerdefinierte Start Seite erstellen, indem Sie die Schritte in diesem Dokument ausführen.

## <a name="create-a-blank-start-page"></a>Erstellen einer leeren Start Seite

Erstellen Sie zunächst eine leere Start Seite, indem Sie eine *XAML* -Datei mit einer Tagstruktur erstellen, die von Visual Studio erkannt wird. Fügen Sie dann Markup und Code Behind hinzu, um die gewünschte Darstellung und Funktionalität zu schaffen.

1. Erstellen Sie ein neues Projekt des Typs **WPF-Anwendung** (**Visual c#**  >  **-Windows-Desktop**).

2. Fügen Sie einen Verweis auf `Microsoft.VisualStudio.Shell.14.0` hinzu.

3. Öffnen Sie die XAML-Datei im XML-Editor, und ändern Sie das Element der obersten Ebene in \<Window> ein- \<UserControl> Element, ohne die Namespace Deklarationen zu entfernen.

4. Entfernen Sie die `x:Class` Deklaration aus dem Element der obersten Ebene. Dadurch ist der XAML-Inhalt mit dem Visual Studio-Tool Fenster kompatibel, das die Start Seite hostet.

5. Fügen Sie dem Element der obersten Ebene die folgenden Namespace Deklarationen hinzu \<UserControl> .

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Mit diesen Namespaces können Sie auf Visual Studio-Befehle,-Steuerelemente und-Benutzeroberflächen Einstellungen zugreifen. Weitere Informationen finden Sie unter [Hinzufügen von Visual Studio-Befehlen zu einer Start Seite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Das folgende Beispiel zeigt das Markup in der *. XAML* -Datei für eine leere Start Seite. Jeder benutzerdefinierte Inhalt sollte in das innere <xref:System.Windows.Controls.Grid> Element gelangen.

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Fügen Sie dem leeren Element Steuerelemente hinzu \<UserControl> , um die benutzerdefinierte Start Seite auszufüllen. Weitere Informationen zum Hinzufügen von Funktionen, die für Visual Studio spezifisch sind, finden [Sie unter Hinzufügen von Visual Studio-Befehlen zu einer Start Seite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Start Seite

Legen Sie die primäre Instanz von Visual Studio nicht so fest, dass die benutzerdefinierte Start Seite ausgeführt wird, bis Sie überprüfen, ob Visual Studio nicht abstürzt. Testen Sie Sie stattdessen in der experimentellen Instanz.

### <a name="to-test-a-manually-created-custom-start-page"></a>So testen Sie eine manuell erstellte benutzerdefinierte Start Seite

1. Kopieren Sie die XAML-Datei und alle unterstützenden Textdateien oder Markup Dateien in den Ordner *%UserProfile%\My Documents\Visual Studio 2015 \ \\ StartPages* .

2. Wenn Ihre Startseite auf Steuerelemente oder Typen in Assemblys verweist, die nicht von Visual Studio installiert werden, kopieren Sie die Assemblys, und fügen Sie Sie in *{Visual Studio-Installationsordner} \\ \common7\ide\privateassemblys* ein.

3. Geben Sie an einer Visual Studio-Eingabeaufforderung **devenv/rootsuffix Exp** ein, um eine experimentelle Instanz von Visual Studio zu öffnen.

4. Wechseln Sie in der experimentellen Instanz zur Seite Extras  >  **Optionen**  >  **Umgebung**  >  **Start** , und wählen Sie die XAML-Datei aus der Dropdown Liste **Start Seite anpassen** aus.

5. Klicken Sie im Menü **Ansicht** auf **Startseite**.

     Die benutzerdefinierte Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, die Änderungen durchführen, die geänderten Dateien kopieren und einfügen und dann die experimentelle Instanz erneut öffnen, um die Änderungen anzuzeigen.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>So wenden Sie die benutzerdefinierte Startseite in der primären Instanz von Visual Studio an

- Nachdem Sie die Startseite getestet und als stabil festgestellt haben, verwenden Sie im Dialogfeld **Optionen** die Option **Startseite anpassen** , um Sie in der primären Instanz von Visual Studio als Startseite auszuwählen.

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Start Seite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Hinzufügen eines Benutzer Steuer Elements zur Start Seite](../extensibility/adding-user-control-to-the-start-page.md)
- [Hinzufügen von Visual Studio-Befehlen zu einer Start Seite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Start Seite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Bereitstellen von benutzerdefinierten Start Seiten](../extensibility/deploying-custom-start-pages.md)
