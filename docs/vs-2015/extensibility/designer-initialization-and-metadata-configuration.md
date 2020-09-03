---
title: Initialisierungs-und Metadatenkonfiguration des Designers | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703067"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Designer-Initialisierung und Metadatenkonfiguration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch die Bearbeitung der Metadaten und Filter Attribute, die einem Designer oder einer Designer Komponente zugeordnet sind, können Anwendungen definieren, welche Tools von einem bestimmten Designer verwendet werden, um unterschiedliche <xref:System.Type> Objekte (z. b. Datenstrukturen, Klassen oder grafische Entitäten) zu verarbeiten, wann der Designer verfügbar ist und wie die Visual Studio-IDE für die unter **Toolbox** Stützung des Designers konfiguriert ist (z. b  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Bietet mehrere Mechanismen, um die Steuerung der Initialisierung eines Designers oder der Designer Komponente und die Bearbeitung der zugehörigen Metadaten durch ein VSPackage zu vereinfachen.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Metadaten und Konfigurationsinformationen werden initialisiert.  
 Da Sie bei Bedarf geladen werden, wurden VSPackages möglicherweise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vor der Instanziierung eines Designers von der Umgebung nicht geladen. Daher können VSPackages nicht den Standardmechanismus zum Konfigurieren eines Designers oder einer Designer Komponente bei der Erstellung verwenden, um ein- <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Ereignis zu behandeln. Stattdessen implementiert ein VSPackage eine Instanz der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> -Schnittstelle und registriert sich für Anpassungen, die als Entwurfs Oberflächen Erweiterungen bezeichnet werden.  
  
### <a name="customizing-initialization"></a>Anpassen der Initialisierung  
 Das Anpassen eines Designers, einer Komponente oder einer Designer Oberfläche umfasst Folgendes:  
  
1. Ändern der Designer Metadaten und Ändern der Art und Weise, wie auf eine bestimmte <xref:System.Type> zugegriffen wird.  
  
     Dies erfolgt in der Regel über den- <xref:System.Drawing.Design.UITypeEditor> Mechanismus oder den- <xref:System.ComponentModel.TypeConverter> Mechanismus.  
  
     Wenn <xref:System.Windows.Forms> -basierte Designer beispielsweise initialisiert werden, ändert die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umgebung die <xref:System.Drawing.Design.UITypeEditor> für Objekte, die <xref:System.Web.UI.WebControls.Image> mit dem Designer verwendet werden, um den Ressourcen-Manager zum Abrufen von Bitmaps anstelle des Dateisystems zu verwenden.  
  
2. Integration in die Umgebung, z. b. durch Abonnieren von Ereignissen oder Abrufen von Projekt Konfigurationsinformationen. Sie können Projekt Konfigurationsinformationen abrufen und Ereignisse abonnieren, indem Sie die- <xref:System.ComponentModel.Design.ITypeResolutionService> Schnittstelle abrufen.  
  
3. Änderung der Benutzerumgebung durch Aktivieren entsprechender **Toolbox** Kategorien oder durch Einschränken der Anwendbarkeit des Designers durch Anwenden einer Instanz der- <xref:System.ComponentModel.ToolboxItemFilterAttribute> Klasse auf den Designer.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Initialisierung des Designers durch ein VSPackage  
 Ein VSPackage sollte die Designer Initialisierung wie folgt behandeln:  
  
1. Erstellen eines Objekts, das die- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse implementiert.  
  
   > [!NOTE]
   > Die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse sollte nie für dasselbe Objekt wie die Klasse implementiert werden <xref:Microsoft.VisualStudio.Shell.Package> .  
  
2. Registrieren Sie die-Klasse, die implementiert <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> , als Unterstützung für die Designer Erweiterungen des VSPackages durch Anwenden von Instanzen von  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf die-Klasse, die die Implementierung von VSPackage bereitstellt <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Wenn ein Designer oder eine Designer Komponente erstellt wird, ist die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umgebung:  
  
3. Greift auf jeden registrierten Entwurfs Oberflächen-Erweiterungs Anbieter zu.  
  
4. Instanziiert und Initialisiert eine Instanz der einzelnen-Objekte des Entwurfs Oberflächen Erweiterungs Anbieters. <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
5. Ruft die-Methode oder-Methode jedes Entwurfs Oberflächen Erweiterungs Anbieters auf <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (je nach Bedarf).  
  
   Wenn Sie das <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt als Member eines VSPackage implementieren, ist es wichtig, Folgendes zu verstehen:  
  
6. Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umgebung bietet keine Kontrolle über die Metadaten oder andere Konfigurationseinstellungen, die von einem bestimmten Anbieter geändert werden `DesignSurfaceExtension` . Es ist möglich, dass zwei oder mehr `DesignSurfaceExtension` Anbieter die gleiche Designer Funktion in widersprüchliche Weise ändern, wobei die abschließende Änderung endgültig ist. Es ist unbestimmt, welche Änderung zuletzt angewendet wurde.  
  
7. Es ist möglich, eine Implementierung des-Objekts explizit <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> auf bestimmte Designer zu beschränken, indem Sie Instanzen von <xref:System.ComponentModel.ToolboxItemFilterAttribute> auf diese Implementierung anwenden. Weitere Informationen zum Filtern von **Toolbox** Elementen finden Sie unter <xref:System.ComponentModel.ToolboxItemFilterAttribute> und <xref:System.ComponentModel.ToolboxItemFilterType> .  
  
## <a name="additional-metadata-provisioning"></a>Zusätzliche metadatenbereitstellung  
 Ein VSPackage kann die Konfiguration eines Designers oder einer Designer Komponente außer zur Entwurfszeit ändern.  
  
 Die- <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasse kann Programm gesteuert verwendet werden oder auf ein VSPackage angewendet werden, das einen Designer bereitstellt.  
  
 Eine Instanz der- <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasse wird verwendet, um die Metadaten von Komponenten zu ändern, die auf einer Entwurfs Oberfläche erstellt werden. Beispielsweise kann ein von Objekten verwendeter Standardeigenschaften Browser durch <xref:System.Windows.Forms.CommonDialog> einen benutzerdefinierten Eigenschaften Browser ersetzt werden.  
  
 Änderungen, die von einer Instanz von bereitgestellt werden <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> , die auf die Implementierung von für ein VSPackage angewendet wird, <xref:Microsoft.VisualStudio.Shell.Package> können einen von zwei Bereichen aufweisen:  
  
- Global: für alle neuen Instanzen einer bestimmten Komponente  
  
- Local: bezieht sich nur auf die Instanz der Komponente, die auf einer Entwurfs Oberfläche erstellt wurde, die vom aktuellen VSPackage bereitgestellt wird.  
  
  Die `IsGlobal` -Eigenschaft der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> -Instanz, die auf die Implementierung von VSPackage angewendet wird, <xref:Microsoft.VisualStudio.Shell.Package> bestimmt diesen Bereich.  
  
  Wenn Sie das-Attribut auf eine Implementierung von anwenden, <xref:Microsoft.VisualStudio.Shell.Package> wobei die- <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> Eigenschaft des- <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Objekts auf festgelegt `true` ist, ändert sich wie unten beschrieben der Browser für die gesamte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umgebung:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Wenn das globale Flag auf festgelegt wurde `false` , erfolgt die Metadatenänderung lokal für den aktuellen Designer, der vom aktuellen VSPackage unterstützt wird:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> Zum aktuellen Zeitpunkt unterstützt die Entwurfs Oberfläche nur das Erstellen von Komponenten, sodass nur Komponenten lokale Metadaten aufweisen können. Im obigen Beispiel haben wir versucht, eine Eigenschaft zu ändern, z. b. die- `Color` Eigenschaft eines Objekts. Wenn `false` für das globale Flag an weitergegeben wurde, wird `CustomBrowser` nie angezeigt, da der Designer nie tatsächlich eine Instanz von erstellt `Color` . Wenn das globale Flag auf festgelegt `false` wird, ist es nützlich für Komponenten, z. b. Steuerelemente, Timer und Dialogfelder.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Erweitern der Entwurfszeitunterstützung](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
