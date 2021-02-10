---
title: Verwalten von Verweisen in einem Projekt
description: Erfahren Sie, wie Sie Verweise auf externe Komponenten und verbundene Dienste in einem Projekt verwalten.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b9beb330f452ff97b7f5a81539cfc62c02404901
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909163"
---
# <a name="manage-references-in-a-project"></a>Verwalten von Verweisen in einem Projekt

Bevor Sie Code schreiben können, der sich auf eine externe Komponente oder einen verbundenen Dienst bezieht, müssen Sie zunächst einen Verweis auf diese Komponente im Projekt einrichten. Ein Verweis ist im Prinzip ein Eintrag in einer Projektdatei, der Informationen beinhaltet, die von Visual Studio zum Auffinden der Komponente oder des Diensts benötigt.

Um einen Verweis hinzuzufügen, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** oder **Abhängigkeiten**, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Hinzufügen** > **Verweis**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Verweisen](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Hinzufügen eines Verweises in Visual C++](../ide/media/vs2015_cpp_add_reference.png)

Sie können einen Verweis zu folgenden Komponenten- und Diensttypen hinzufügen:

- .NET-Klassenbibliotheken oder -Assemblys

- UWP-Apps

- COM-Komponenten

- Sonstige Assemblys oder Klassenbibliotheken von Projekten in derselben Projektmappe

- Freigegebene Projekte

- XML-Webdienste

## <a name="uwp-app-references"></a>Verweise von UWP-Apps

### <a name="project-references"></a>Projektverweise

Projekte von Universellen Windows-Plattform (UWP), können Verweise auf andere UWP-Projekte in der Projektmappe oder auf Windows 8.1-Projekte oder Binärdateien erstellen. Die Voraussetzung hierfür ist, dass diese Projekte keine APIs verwenden, die in Windows 10 nicht mehr unterstützt werden. Weitere Informationen finden Sie unter [Move from Windows Runtime 8 to UWP](/windows/uwp/porting/w8x-to-uwp-root)(Von Windows-Laufzeit zu UWP) (möglicherweise in englischer Sprache).

Informationen zur Neuausrichtung von Windows 8.1-Projekten auf Windows 10 finden Sie unter [Übertragung, Migration und Upgrade von Visual Studio-Projekten](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Verweise auf Erweiterungs-SDKs

In Visual Basic, C#, C++ und JavaScript für die universelle Windows-Plattform (UWP) geschriebene Apps können auf Erweiterungs-SDKs verweisen, die auf Windows 8.1 ausgerichtet sind, sofern diese Erweiterungs-SDKs keine APIs verwenden, die in Windows 10 nicht mehr unterstützt werden. Besuchen Sie die Website des Anbieters des Erweiterungs-SDKs, um festzustellen, ob UWP-Apps darauf verweisen können.

Wenn Sie feststellen, dass das Erweiterungs-SDK, auf das von Ihrer Anwendung verwiesen wird, nicht unterstützt wird, müssen Sie folgende Schritte ausführen:

1. Schauen Sie sich den Namen des Projekts an, das den Fehler verursacht. Die Plattform, auf die Ihr Projekt abzielt, steht in Klammern neben dem Projektnamen. Beispielsweise bedeutet **MyProjectName (Windows 8.1)** dass das Projekt **MyProjectName** auf die Plattformversion Windows 8.1 abzielt.

1. Wechseln Sie zur Website des Anbieters des nicht unterstützten Erweiterungs-SDKs, und installieren Sie die SDK-Version, deren Abhängigkeiten mit der Version der Plattform kompatibel sind, auf die Ihr Projekt ausgelegt ist.

    > [!NOTE]
    > Um herauszufinden, ob ein Erweiterungs-SDK von einem anderen abhängt, können Sie im **Verweis-Manager** nachsehen. Starten Sie Visual Studio neu, erstellen Sie ein neues C#-UWP-App-Projekt, klicken Sie dann mit der rechten Maustaste auf das Projekt, und wählen Sie **Verweis hinzufügen** aus. Wechseln Sie zur Registerkarte **Fenster** und dann zur Unterregisterkarte **Erweiterungen**, und wählen Sie das Erweiterungs-SDK aus. Sehen Sie sich den **Verweis-Manager** im rechten Bereich an. Wenn Abhängigkeiten bestehen, werden sie dort aufgeführt.

    > [!IMPORTANT]
    > Wenn Ihr Projekt auf Windows 10 ausgerichtet ist und das im vorherigen Schritt installierte Erweiterungs-SDK von Microsoft Visual C++ Runtime Package abhängt, lautet die mit Windows 10 kompatible Version von Microsoft Visual C++ Runtime Package 14.0 und wird mit Visual Studio installiert.

1. Wenn das im vorherigen Schritt installierte Erweiterungs-SDK von anderen Erweiterungs-SDKs abhängt, rufen Sie die Websites der entsprechenden Anbieter auf, und installieren Sie die Versionen der Abhängigkeiten, die mit der Version der Plattform kompatibel sind, auf die Ihr Projekt ausgelegt ist.

1. Starten Sie Visual Studio neu, und öffnen Sie Ihre App.

1. Klicken Sie im Projekt, das den Fehler verursacht hat, mit der rechten Maustaste auf den Knoten **Verweise** oder **Abhängigkeiten** und anschließend auf **Verweis hinzufügen**.

1. Klicken Sie auf die Registerkarte **Fenster** und anschließend auf die Unterregisterkarte **Erweiterungen**. Deaktivieren Sie dann die Kontrollkästchen für die alten Erweiterungs-SDKs, und aktivieren Sie die Kontrollkästchen für die neuen. Klicken Sie auf **OK**.

## <a name="add-a-reference-at-design-time"></a>Hinzufügen von Verweisen zur Entwurfszeit

Wenn Sie im Projekt einen Verweis auf eine Assembly erstellen, sucht Visual Studio die Assembly an den folgenden Speicherorten:

- Das aktuelle Projektverzeichnis. (Sie können die Assemblys über die Registerkarte **Durchsuchen** suchen.)

- Andere Projektverzeichnisse in der gleichen Projektmappe. (Sie finden diese Assemblys auf der Registerkarte **Projekte** .)

> [!NOTE]
> - Alle Projekte enthalten einen impliziten Verweis auf **mscorlib**.
> - Alle Projekte enthalten einen impliziten Verweis auf `System.Core`. Dies gilt auch, wenn `System.Core` aus der Liste der Verweise entfernt wird.
> - Visual Basic-Projekte enthalten einen impliziten Verweis auf <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Verweise auf freigegebene Komponenten zur Laufzeit

Zur Laufzeit müssen sich Komponenten entweder im Ausgabepfad des Projekts oder im Globalen Assemblycache (GAC) befinden. Wenn das Projekt einen Verweis auf ein Objekt enthält, der sich nicht an einem dieser Orte befindet, müssen Sie den Verweis beim Erstellen des Projekts in den Ausgabepfad des Projekts kopieren. Die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Eigenschaft gibt an, ob diese Kopie erstellt werden muss. Wenn der Wert **True** lautet, wird der Verweis beim Erstellen des Projekts in das Projektverzeichnis kopiert. Wenn der Wert **False** ist, wird der Verweis nicht kopiert.

Wenn Sie eine Anwendung bereitstellen, die einen Verweis auf eine im GAC registrierte benutzerdefinierte Komponente enthält, wird die Komponente unabhängig von der <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Einstellung nicht mit der Anwendung bereitgestellt. In früheren Versionen von Visual Studio konnten Sie die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>-Eigenschaft für einen Verweis festlegen, um sicherzustellen, dass die Assembly bereitgestellt wird. Jetzt müssen Sie die Assembly manuell dem Ordner \Bin hinzufügen. Dadurch wird der gesamte benutzerdefinierte Code einer Prüfung unterzogen, und das Risiko der Veröffentlichung von unbekanntem benutzerdefinierten Code wird vermindert.

Wenn sich die Assembly bzw. Komponente im globalen Assemblycache befindet oder eine .NET Framework-Komponente ist, wird die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Eigenschaft standardmäßig auf **False** festgelegt. Andernfalls wird der Wert auf **True** festgelegt. Verweise zwischen Projekten werden immer auf **True** festgelegt.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Verweisen auf ein Projekt oder eine Assembly, das/die auf eine andere .NET-Version ausgerichtet ist

Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf eine andere Version von .NET ausgerichtet sind. Sie können z.B. eine Anwendung für .NET Framework 4.6 erstellen, die auf eine Assembly verweist, die wiederum .NET Framework 4.5 anzielt. Wenn Sie ein Projekt für eine frühere Version von .NET erstellen, können Sie in diesem Projekt nicht auf Projekte oder Assemblys verweisen, die auf eine neuere Version ausgerichtet sind.

Weitere Informationen finden Sie unter [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Projekt-zu-Projekt-Verweise

Verweise zwischen Projekten sind Verweise auf Projekte mit Assemblys. Projektverweise weisen Sie über die Registerkarte **Projekte** im Dialogfeld „Verweis-Manager“ hinzu. Visual Studio kann anhand eines Pfads zum Projekt nach einer Assembly suchen.

Wenn Sie ein Projekt haben, das eine Assembly erstellt, müssen Sie auf das Projekt verweisen und keinen Dateiverweis verwenden (siehe unten). Der Vorteil eines Verweises zwischen Projekten liegt darin, dass eine Abhängigkeit zwischen den Projekten im Buildsystem erzeugt wird. Das abhängige Projekt wird erstellt, wenn es sich seit der letzten Erstellung des verweisenden Projekts geändert hat. Bei Dateiverweisen wird keine Buildabhängigkeit erstellt, d. h., das verweisende Projekt kann ohne Erstellen des abhänigen Projekts erstellt werden, und der Verweis kann veraltet sein. (Das heißt, das Projekt kann auf eine vorher erstellte Version des Projekts verweisen.) Dies kann dazu führen, dass im *bin*-Verzeichnis mehrere Versionen einer einzigen DLL erforderlich sind, was jedoch nicht möglich ist. Wenn dieser Konflikt auftritt, wird eine Meldung wie die folgende angezeigt: „Fehler: Die Abhängigkeit ‚Datei‘ in Projekt ‚Projekt‘ kann nicht in das Ausführungsverzeichnis kopiert werden, da sie den Verweis ‚Datei‘ überschreiben würde.“ Weitere Informationen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md) und [Vorgehensweise: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Anstelle eines Projekt-zu-Projekt-Verweises wird ein Dateiverweis erstellt, wenn die Zielversion von .NET Framework eines Projekts Version 4.5 ist und die Zielversion des anderen Projekts Version 2, 3, 3.5 oder 4.0 ist.

## <a name="shared-project-references"></a>Verweis für das freigegebene Projekt

Im Gegensatz zu den meisten anderen Projekttypen hat ein *freigegebenes Projekt* keine Binärausgabe. Stattdessen wird der Code in jedes Projekt kompiliert, das auf ihn verweist. [Mit freigegebenen Projekten](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) können Sie allgemeinen Code schreiben, auf den von einer Reihe verschiedener Anwendungsprojekte verwiesen wird. Der Code wird als Teil jedes verweisenden Projekts kompiliert und kann Compilerdirektiven beinhalten, um plattformspezifische Funktionen in die freigegebene Codebasis zu integrieren. Fügen Sie auf der **Registerkarte Freigegebene Projekte** im Dialogfeld „Verweis-Manager“ einen Verweis auf ein freigegebenes Projekt hinzu.

## <a name="file-references"></a>Dateiverweise

Dateiverweise sind direkte Verweise auf Assemblys, die sich außerhalb eines Visual Studio-Projekts befinden. Sie erstellen diese mithilfe der Registerkarte **Durchsuchen** im Dialogfeld „Verweis-Manager“. Dateiverweise bieten sich an, wenn Sie nur eine Assembly oder Komponente haben und nicht das Projekt, das sie als Ausgabe erstellt.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)
- [How to: Hinzufügen und Entfernen von Verweisen](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
