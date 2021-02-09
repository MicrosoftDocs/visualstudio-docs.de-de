---
title: Unterstützung für Benutzereinstellungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Persistenz von Einstellungs Kategorien mithilfe der Settings-APIs im Visual Studio SDK aktivieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06cd22ec933e72344ab743372fe30c1a3ddf5fbf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901598"
---
# <a name="support-for-user-settings"></a>Unterstützung für Benutzereinstellungen
Ein VSPackage kann eine oder mehrere Einstellungs Kategorien definieren, die Gruppen von Zustandsvariablen sind, die beibehalten werden, wenn ein Benutzer **im Menü Extras den Befehl** **Einstellungen importieren/exportieren** auswählt. Um diese Persistenz zu aktivieren, verwenden Sie die Einstellungs-APIs in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Ein Registrierungs Eintrag, der als benutzerdefinierter Einstellungs Punkt und GUID bezeichnet wird, definiert die Einstellungs Kategorie des VSPackages. Ein VSPackage kann mehrere Einstellungs Kategorien unterstützen, die jeweils durch einen benutzerdefinierten Einstellungs Punkt definiert werden.

- Implementierungen von Einstellungen, die auf Interop-Assemblys basieren (mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Schnittstelle), sollten einen benutzerdefinierten Einstellungs Punkt erstellen, indem Sie entweder die Registrierung bearbeiten oder ein Registrierungs Skript (RGS-Datei) verwenden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Code, der das Managed Package Framework (MPF) verwendet, sollte benutzerdefinierte Einstellungs Punkte erstellen <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> , indem für jeden benutzerdefinierten Einstellungs Punkt ein an das VSPackage angefügt wird.

     Wenn ein einzelnes VSPackage mehrere benutzerdefinierte Einstellungs Punkte unterstützt, wird jeder benutzerdefinierte Einstellungs Punkt durch eine separate Klasse implementiert, und jede wird durch eine eindeutige Instanz der- <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse registriert. Folglich können von der Klasse implementierende Einstellungen mehr als eine Einstellungs Kategorie unterstützt werden.

## <a name="custom-settings-point-registry-entry-details"></a>Details zur Registrierung der Registrierungseinträge für benutzerdefinierte Einstellungen
 Benutzerdefinierte Einstellungs Punkte werden in einem Registrierungs Eintrag am folgenden Speicherort erstellt: hklm\software\microsoft\visualstudio \\ *\<Version>* \usersettings \\ `<CSPName>` , wobei `<CSPName>` der Name des benutzerdefinierten Einstellungs Punkts ist, den das VSPackage unterstützt *\<Version>* , und die Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , z. b. 8,0.

> [!NOTE]
> Der Stammpfad von HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* kann mit einem alternativen Stamm überschrieben werden, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) initialisiert wird. Weitere Informationen finden Sie unter [Befehls Zeilenschalter](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Die Struktur des Registrierungs Eintrags wird im folgenden veranschaulicht:

 Hklm\software\microsoft\visualstudio \\ *\<Version>* \usersettings\

 `<CSPName`>= s ' #12345 '

 Package = ' {xxxxxx xxxx xxxx xxxx xxxxxxxxx} '

 Category = ' {YYYYYY yyyy yyyy yyyy yyyyyyyyy} '

 Resourcepackage = "{zzzzzz zzzz zzzz zzzz zzZZZZzzz}"

 Alternativen Parent = CategoryName

| Name | Typ | Daten | BESCHREIBUNG |
|-----------------|--------| - | - |
| (Standardwert) | REG_SZ | Name des benutzerdefinierten Einstellungs Punkts | Der Name des Schlüssels, `<CSPName`>, ist der nicht lokalisierte Name des benutzerdefinierten Einstellungs Punkts.<br /><br /> Bei Implementierungen, die auf MPF basieren, wird der Name des Schlüssels durch Kombinieren der `categoryName` `objectName` Argumente und des <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Konstruktors in abgerufen `categoryName_objectName` .<br /><br /> Der Schlüssel kann leer sein oder die Verweis-ID für die lokalisierte Zeichenfolge in einer Satelliten-DLL enthalten. Dieser Wert wird vom- `objectNameResourceID` Argument für den- <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Konstruktor abgerufen. |
| Paket | REG_SZ | GUID | Der GUID des VSPackage, das den benutzerdefinierten Einstellungs Punkt implementiert.<br /><br /> Auf MPF basierende Implementierungen mithilfe der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> -Klasse verwenden das-Argument des Konstruktors, `objectType` das die Reflektion des VSPackages enthält, <xref:System.Type> um diesen Wert zu erhalten. |
| Category | REG_SZ | GUID | GUID, die die Einstellungs Kategorie identifiziert.<br /><br /> Bei Implementierungen, die auf Interop-Assemblys basieren, kann dieser Wert eine beliebig ausgewählte GUID sein, die die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> -Methode und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> Methode übergibt. Alle Implementierungen dieser zwei Methoden sollten ihre GUID-Argumente überprüfen.<br /><br /> Für auf MPF basierende Implementierungen wird diese GUID vom der Klasse abgerufen, die <xref:System.Type> den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Einstellungs Mechanismus implementiert. |
| ResourcePackage | REG_SZ | GUID | Dies ist optional.<br /><br /> Pfad zur Satelliten-DLL, die lokalisierte Zeichen folgen enthält, wenn das implementierende VSPackage diese nicht bereitstellt.<br /><br /> MPF verwendet Reflektion, um das richtige Ressourcen-VSPackage zu erhalten, sodass die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse dieses Argument nicht festgelegt hat. |
| Alternative übergeordnete Elemente | REG_SZ | Name des Ordners auf der Options Seite Extras, die diesen benutzerdefinierten Einstellungs Punkt enthält. | Dies ist optional.<br /><br /> Dieser Wert muss nur festgelegt werden, wenn eine Einstellungs Implementierung **Tool Options** Seiten unterstützt, von denen der Persistenzmechanismus in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] anstelle des Mechanismus im Automatisierungs Modell zum Speichern des Zustands verwendet wird.<br /><br /> In diesen Fällen ist der Wert im alternativen übergeordneten Schlüssel der `topic` Abschnitt der `topic.sub-topic` Zeichenfolge, der zum Identifizieren der jeweiligen **ToolsOptions** -Seite verwendet wird. Beispielsweise würde für die Seite **ToolsOptions** `"TextEditor.Basic"` der Wert von alternativen Parent lauten `"TextEditor"` .<br /><br /> Wenn <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> den benutzerdefinierten Einstellungs Punkt generiert, entspricht er dem Kategorienamen. |
