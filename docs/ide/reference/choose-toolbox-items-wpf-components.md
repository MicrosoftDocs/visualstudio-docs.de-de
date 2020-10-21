---
title: Toolboxelemente auswählen, WPF-Komponenten
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28576fab1ed4b39810b6f4cc32fb2955a7a44039
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099348"
---
# <a name="choose-toolbox-items-wpf-components"></a>Toolboxelemente auswählen, WPF-Komponenten

Auf dieser Registerkarte des Dialogfelds **Toolboxelemente auswählen** wird eine Liste der Windows Presentation Foundation (WPF)-Steuerelemente angezeigt, die auf dem lokalen Computer verfügbar sind. Um diese Liste anzuzeigen, wählen Sie im Menü **Extras** die Option **Toolboxelemente auswählen** aus, um das Dialogfeld **Toolboxelemente auswählen** aufzurufen. Wählen Sie anschließend die Registerkarte **WPF-Komponenten** aus. Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.

- Wenn das Kontrollkästchen neben einer Komponente aktiviert wird, wird für diese Komponente in der **Toolbox** ein Symbol aufgeführt.

    > [!TIP]
    > Um zu einem projektspezifischen Dokument, das zur Bearbeitung geöffnet ist, ein WPF-Steuerelement hinzuzufügen, ziehen Sie dessen Symbol **Toolbox** auf die Designansichtsoberfläche. Standardmarkup und Code für die Komponente werden in das Projekt eingefügt und können bearbeitet werden. Weitere Informationen finden Sie unter [Toolbox](../../ide/reference/toolbox.md).

- Wenn das Kontrollkästchen neben einer Komponente deaktiviert wird, wird das zugehörige Symbol aus **Toolbox** entfernt.

    > [!NOTE]
    > Die auf dem Computer installierten .NET-Komponenten bleiben verfügbar, und zwar unabhängig davon, ob für sie Symbole in der **Toolbox** angezeigt werden.

Die Spalten auf der Registerkarte **WPF-Komponenten** enthalten die folgenden Informationen:

**Name**

Listet die Namen der WPF-Steuerelemente auf, für die Einträge in der Registrierung des Computers vorhanden sind.

**Namespace**

Zeigt die Hierarchie des [.NET-API](/dotnet/api/?view=netframework-4.7&preserve-view=true)-Namespaces an, der die Struktur der Komponente definiert. Wenn Sie nach dieser Spalte sortieren, werden die verfügbaren Komponenten innerhalb der einzelnen auf dem Computer installierten .NET-Namespaces aufgeführt.

**Assemblyname**

Zeigt den Namen der .NET-Assembly an, die den Namespace der einzelnen Komponenten enthält. Wenn Sie nach dieser Spalte sortieren, werden die Namespaces innerhalb der einzelnen auf dem Computer installierten .NET-Assemblys aufgeführt.

**Verzeichnis**

Zeigt den Speicherort der .NET-Assembly an. Der Standardspeicherort für alle Assemblys ist der globale Assemblycache. Weitere Informationen über den globalen Assemblycache finden Sie unter [Arbeiten mit Assemblys und dem globalen Assemblycache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>UIElement-Liste

### <a name="filter"></a>Filter

Filtert die Liste der WPF-Steuerelemente auf Grundlage der Zeichenfolge, die Sie im Textfeld bereitstellen. Alle Übereinstimmungen aus den vier Spalten werden angezeigt.

**Clear** (Löschen)

Löscht die Filterzeichenfolge.

**Browse** (Durchsuchen)

Öffnet das Dialogfeld **Öffnen**, mit dem Sie zu Assemblys navigieren können, die WPF-Steuerelemente enthalten. Hier können Sie Assemblys laden, die sich nicht im globalen Assemblycache befinden.

**Sprache**

Zeigt die lokalisierte Sprache der Assembly an, die das ausgewählte WPF-Steuerelement enthält.

## <a name="limitations"></a>Einschränkungen

Beim Hinzufügen eines benutzerdefinierten Steuerelements oder <xref:System.Windows.Controls.UserControl> zur Toolbox gibt es folgende Einschränkungen:

- Es funktioniert nur bei benutzerdefinierten Steuerelementen, die außerhalb des aktuellen Projekts definiert sind.

- Es wird nicht ordnungsgemäß aktualisiert, wenn die Konfiguration der Projektmappe vom Debugmodus in den Releasemodus oder vom Releasemodus in den Debugmodus geändert wird. Der Grund hierfür ist, dass der Verweis nicht auf ein Projekt, sondern auf die Assembly auf der Festplatte verweist. Wenn das Steuerelement Teil der aktuellen Projektmappe ist und vom Debugmodus in den Releasemodus gewechselt wird, verweist das Projekt weiterhin auf die Debugversion des Steuerelements.

Wenn Entwurfszeit-Metadaten auf das benutzerdefinierte Steuerelement angewendet werden und diese Metadaten angeben, dass [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) auf `false` festgelegt ist, wird das Steuerelement nicht in der Toolbox angezeigt.

Sie können direkt in der XAML-Ansicht auf die Steuerelemente verweisen, indem Sie den Namespace und die Assembly für das Steuerelement zuordnen.

## <a name="see-also"></a>Siehe auch

- [Werkzeugkasten](../../ide/reference/toolbox.md)
- [Erste Schritte mit WPF](../../designers/getting-started-with-wpf.md)
