---
title: Erstellen von Options Seiten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Options Seite im Menü Extras in Visual Studio erstellen, indem Sie eine DialogPage-Klasse aus dem Managed Package Framework implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4759b3590fcde116e6f106ac326ff875e9566c43
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328638"
---
# <a name="create-options-pages"></a>Erstellen von Options Seiten
Im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Managed Package Framework erweitern die von abgeleiteten Klassen <xref:Microsoft.VisualStudio.Shell.DialogPage> die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE durch Hinzufügen von **options** Seiten **Tools** im Menü Extras.

 Ein Objekt, das eine bestimmte **Tool Options** Seite implementiert, ist bestimmten VSPackages durch das- <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt zugeordnet.

 Da die Umgebung das Objekt instanziiert, das eine bestimmte **Tool Options** Seite implementiert, wenn diese bestimmte Seite von der IDE angezeigt wird:

- Eine **options** Seite für Extras sollte auf Ihrem eigenen Objekt implementiert werden, nicht auf dem Objekt, das ein VSPackage implementiert.

- Ein Objekt kann nicht mehrere **Tool Options** Seiten implementieren.

## <a name="register-as-a-tools-options-page-provider"></a>Als Tool Options Seiten Anbieter registrieren
 Ein VSPackage, das die Benutzerkonfiguration über Extras **options** Seiten unterstützt, zeigt die Objekte an, die diese **Tools-Options** Seiten bereitstellen <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.Package>

 Es muss eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> für jeden <xref:Microsoft.VisualStudio.Shell.DialogPage> abgeleiteten Typ vorhanden sein, der eine Extras **options** Seite implementiert.

 Jede Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet den Typ, der die **options** Seite "Tools" implementiert, Zeichen folgen, die die Kategorie und die Unterkategorie enthalten, die zum Identifizieren einer Extras **Optionen** -Seite verwendet werden, und Ressourcen Informationen, um den Typ als Bereitstellung einer Extras **Optionen** -Seite zu registrieren.

## <a name="persist-tools-options-page-state"></a>Status der Options Seite für persistente Tools
 Wenn eine **Tools-Optionen** -Seiten Implementierung bei aktivierter Automatisierungsunterstützung registriert ist, speichert die IDE den Status der Seite zusammen mit allen anderen Extras- **options** Seiten.

 Ein VSPackage kann seine eigene Persistenz mithilfe von verwalten <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Es sollte nur eine oder die andere Persistenzmethode verwendet werden.

## <a name="implement-dialogpage-class"></a>Implementieren der DialogPage-Klasse
 Ein Objekt, das eine VSPackage-Implementierung eines von <xref:Microsoft.VisualStudio.Shell.DialogPage> abgeleiteten Typs bereitstellt, kann die folgenden geerbten Features nutzen:

- Ein Standardfenster für die Benutzeroberfläche.

- Ein standardmäßiger Persistenzmechanismus <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ist verfügbar, wenn auf die Klasse angewendet wird, oder, wenn die- <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> Eigenschaft `true` für den auf <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> die Klasse angewendeten festgelegt ist.

- Automatisierungsunterstützung.

  Die Mindestanforderung für ein Objekt, das eine Extras **options** Seite mithilfe von implementiert, <xref:Microsoft.VisualStudio.Shell.DialogPage> ist das Hinzufügen von öffentlichen Eigenschaften.

  Wenn die Klasse ordnungsgemäß als **options** Seiten Anbieter für Extras registriert ist, sind ihre öffentlichen Eigenschaften im Abschnitt **Optionen** **des Menüs Extras** in Form eines Eigenschaften Rasters verfügbar.

  Alle diese Standard Features können überschrieben werden. Zum Erstellen einer anspruchsvolleren Benutzeroberfläche ist es z. b. erforderlich, dass nur die Standard Implementierung von überschrieben wird <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .

## <a name="example"></a>Beispiel
 Im folgenden finden Sie eine einfache "Hello World"-Implementierung einer Optionsseite. Wenn Sie den folgenden Code zu einem Standard Projekt hinzufügen, das von der Visual Studio-Paket Vorlage erstellt wurde, und die **Menübefehls** Option ausgewählt ist, wird die Option Seiten Funktionalität ordnungsgemäß

### <a name="description"></a>BESCHREIBUNG
 Die folgende Klasse definiert eine minimale "Hello World"-Optionsseite. Beim Öffnen kann der Benutzer die Public- `HelloWorld` Eigenschaft in einem Eigenschaften Raster festlegen.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>BESCHREIBUNG
 Wenn Sie das folgende Attribut auf die Paket Klasse anwenden, ist die Seite Optionen verfügbar, wenn das Paket geladen wird. Die Zahlen sind beliebige Ressourcen-IDs für die Kategorie und die Seite, und der boolesche Wert am Ende gibt an, ob die Seite die Automatisierung unterstützt.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>BESCHREIBUNG
 Der folgende Ereignishandler zeigt ein Ergebnis an, abhängig vom Wert der Eigenschaft, die auf der Seite Optionen festgelegt ist. Dabei wird die- <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Methode verwendet, wobei das Ergebnis explizit in den benutzerdefinierten Options Seitentyp umgewandelt wird, um auf die von der Seite verfügbar gemachten Eigenschaften zuzugreifen.

 Bei einem Projekt, das von der Paket Vorlage generiert wird, wird diese Funktion von der-Funktion aufgerufen, `MenuItemCallback` um Sie an den Standardbefehl anzufügen **, der** dem Menü Extras hinzugefügt wird.

### <a name="code"></a>Code
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Siehe auch
- [Erweitern von Benutzereinstellungen und-Optionen](../../extensibility/extending-user-settings-and-options.md)
- [Automatisierungsunterstützung für options Seiten](../../extensibility/internals/automation-support-for-options-pages.md)
