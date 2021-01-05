---
title: Angeben von Datei Handlern für Dateinamen Erweiterungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von OpenWithList und OpenWithProgIds ermitteln, welche Anwendung eine Dateierweiterung im Visual Studio SDK behandelt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421244cd88af43e7602298e7384a632c8aa51833
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715599"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Angeben von Dateihandlern für Dateierweiterungen
Es gibt verschiedene Möglichkeiten, die Anwendung zu bestimmen, die eine Datei mit einer bestimmten Dateierweiterung verarbeitet. Die Verben OpenWithList und OpenWithProgIds sind zwei Methoden zum Angeben von Datei Handlern unter dem Registrierungs Eintrag für die Dateierweiterung.

## <a name="openwithlist-verb"></a>OpenWithList-Verb
 Wenn Sie mit der rechten Maustaste auf eine Datei in Windows-Explorer klicken, wird der Befehl **Öffnen** angezeigt. Wenn mehr als ein Produkt einer Erweiterung zugeordnet ist, wird das Untermenü **Öffnen mit** angezeigt.

 Sie können verschiedene Anwendungen registrieren, um eine Erweiterung zu öffnen, indem Sie den OpenWithList-Schlüssel für die Dateierweiterung in HKEY_CLASSES_ROOT festlegen. Die unter diesem Schlüssel für eine Dateierweiterung aufgeführten Anwendungen werden im Dialogfeld **Öffnen mit** unter der Überschrift **Empfohlene Programme** angezeigt. Das folgende Beispiel zeigt die registrierten Anwendungen zum Öffnen der Dateierweiterung. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Die Schlüssel zum Angeben von Anwendungen stammen aus der Liste unter HKEY_CLASSES_ROOT\Applications.

 Wenn Sie einen OpenWithList-Schlüssel hinzufügen, deklarieren Sie, dass Ihre Anwendung eine Dateierweiterung unterstützt, auch wenn eine andere Anwendung den Besitz der Erweiterung übernimmt. Dabei kann es sich um eine zukünftige Version der Anwendung oder eine andere Anwendung handeln.

## <a name="openwithprogids"></a>OpenWithProgIds
 Programmgesteuerte Bezeichner (ProgIDs) sind benutzerfreundliche Versionen von Klassifizierungen, mit denen eine Version einer Anwendung oder eines COM-Objekts identifiziert wird. Jedes gemeinsam erbare Objekt sollte über eine eigene ProgID verfügen. VisualStudio. DTE. 7.1 startet z. b. Visual Studio .NET 2003, während VisualStudio. DTE. 10.0 gestartet wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Als Besitzer eines Projekt Typs oder Projekt Elementtyps müssen Sie eine versionsspezifische ProgID für die Dateierweiterung erstellen. Diese ProgIDs sind möglicherweise redundant, da mehrere ProgID möglicherweise dieselbe Anwendung starten. Weitere Informationen finden Sie unter [Registrieren von Verben für Dateinamen Erweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md).

 Verwenden Sie die folgende Benennungs Konvention für Datei ProgIDs mit Versions Angabe, um eine Duplizierung bei der Registrierung von anderen Anbietern zu vermeiden:

|Dateierweiterung|Versionierte ProgID|
|--------------------|----------------------|
|Erweiterung|ProductName. Erweiterung. VersionMajor. VersionMinor|

 Sie können verschiedene Anwendungen registrieren, die eine bestimmte Dateierweiterung öffnen können, indem Sie dem HKEY_CLASSES_ROOT \\ \openwithprogids-Schlüssel versionierte ProgIDs als Werte hinzufügen *\<extension>* . Dieser Registrierungsschlüssel enthält eine Liste der alternativen ProgIDs, die der Dateierweiterung zugeordnet sind. Die den aufgelisteten ProgIDs zugeordneten Anwendungen werden im Untermenü mit dem _Produktnamen_ **Öffnen** angezeigt. Wenn die gleiche Anwendung in den `OpenWithList` Schlüsseln und angegeben ist `OpenWithProgids` , führt das Betriebssystem die Duplikate zusammen.

> [!NOTE]
> Der `OpenWithProgids` Schlüssel wird nur in Windows XP unterstützt. Da andere Betriebssysteme diesen Schlüssel ignorieren, sollten Sie ihn nicht als einzige Registrierung für Datei Handler verwenden. Verwenden Sie diesen Schlüssel, um eine bessere Benutzer Leistung in Windows XP bereitzustellen.

 Fügen Sie die gewünschten ProgIDs als Werte des Typs REG_NONE hinzu. Der folgende Code enthält ein Beispiel für das Registrieren von ProgIDs für eine Dateierweiterung (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 Die als Standardwert für die Dateierweiterung angegebene ProgID ist der Standarddatei Handler. Wenn Sie die ProgID für eine Dateierweiterung ändern, die mit einer früheren Version von ausgeliefert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurde oder die von anderen Anwendungen übernommen werden kann, müssen Sie den `OpenWithProgids` Schlüssel für die Dateierweiterung registrieren und die neue ProgID in der Liste zusammen mit den alten ProgIDs, die Sie unterstützen, angeben. Zum Beispiel:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Wenn der alten ProgID Verben zugeordnet sind, werden diese Verben auch unter **mit** *Produkt Name* öffnen im Kontextmenü angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Informationen zu Dateierweiterungen](../extensibility/about-file-name-extensions.md)
- [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)
