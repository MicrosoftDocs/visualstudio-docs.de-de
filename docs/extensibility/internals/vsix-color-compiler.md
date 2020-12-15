---
title: VSIX-Farb Compiler | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Visual Studio-Erweiterungs Farb Compiler-Tool, bei dem es sich um eine Konsolenanwendung handelt, die Farben in Visual Studio-Designs in eine pkgdef-Datei umschließt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50cd1f1c8c3ff7f86cd00e4b384f548c7ec9d21
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487997"
---
# <a name="vsix-color-compiler"></a>VSIX-Farbcompiler
Das Visual Studio-Erweiterungs Farben-Compilertool ist eine Konsolenanwendung, die eine XML-Datei verwendet, die Farben für vorhandene Visual Studio-Designs darstellt, und Sie in eine pkgdef-Datei konvertiert, sodass diese Farben in Visual Studio verwendet werden können. Da es einfach ist, Unterschiede zwischen XML-Dateien zu vergleichen, ist dieses Tool nützlich, um benutzerdefinierte Farben in der Quell Code Verwaltung zu verwalten. Sie kann auch in Buildumgebungen eingebunden werden, sodass die Ausgabe des Builds eine gültige pkgdef-Datei ist.

 **Design-XML-Schema**

 Eine komplette Datei "Theme. xml" sieht wie folgt aus:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Design**

 Das- \<Theme> Element definiert ein gesamtes Design. Ein Design muss mindestens ein Element enthalten \<Category> . Designelemente werden wie folgt definiert:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Attribut**|**Definition**|
|-|-|
|Name|Benötigten Der Name des Designs.|
|GUID|Benötigten Die GUID des Designs (muss mit der GUID-Formatierung identisch sein)|

 Beim Erstellen benutzerdefinierter Farben für Visual Studio müssen diese Farben für die folgenden Themen definiert werden. Wenn für ein bestimmtes Design keine Farben vorhanden sind, versucht Visual Studio, die fehlenden Farben aus dem Design "Hell" zu laden.

|**Design Name**|**Design-GUID**|
|-|-|
|Hell|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Dunkel|{1endd0138-47ce-435e-84ef-9ec1f 439b749}|
|Blau|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Hoher Kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategorie**

 Das- \<Category> Element definiert eine Auflistung von Farben in einem Design. Kategorienamen stellen logische Gruppierungen bereit und sollten so eng wie möglich definiert werden. Eine Kategorie muss mindestens ein Element enthalten \<Color> . Kategorieelemente werden wie folgt definiert:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Attribut**|**Definition**|
|-|-|
|Name|Benötigten Der Name der Kategorie.|
|GUID|Benötigten Die GUID der Kategorie (muss mit der GUID-Formatierung identisch sein).|

 **Farbe**

 Das- \<Color> Element definiert eine Farbe für eine Komponente oder einen Status der Benutzeroberfläche. Das bevorzugte Benennungs Schema für eine Farbe ist [UI-Typ] [State]. Verwenden Sie das Wort "Color" nicht, da es redundant ist. Eine Farbe sollte eindeutig den Elementtyp und die Situationen oder "State" angeben, für die die Farbe angewendet wird. Eine Farbe darf nicht leer sein und muss entweder ein \<Background> -Element oder ein-Element und ein- \<Foreground> Element enthalten. Farbelemente werden wie folgt definiert:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Attribut**|**Definition**|
|-|-|
|Name|Benötigten Der Name der Farbe.|

 **Hintergrund und/oder Vordergrund**

 Das \<Background> -Element und das- \<Foreground> Element definieren den Wert und den Typ einer Farbe für den Hintergrund oder den Vordergrund eines UI-Elements. Diese Elemente haben keine untergeordneten Elemente.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Attribut**|**Definition**|
|-|-|
|Typ|Benötigten Der Typ der Farbe. Folgende Werte sind möglich:<br /><br /> *CT_INVALID:* Die Farbe ist ungültig oder nicht festgelegt.<br /><br /> *CT_RAW:* Ein unformatierten ARGB-Wert.<br /><br /> *CT_COLORINDEX:* Verwenden Sie nicht.<br /><br /> *CT_SYSCOLOR:* Eine Windows-System Farbe aus syscolor.<br /><br /> *CT_VSCOLOR:* Eine Visual Studio-Farbe aus __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Die automatische Farbe.<br /><br /> *CT_TRACK_FOREGROUND:* Verwenden Sie nicht.<br /><br /> *CT_TRACK_BACKGROUND:* Verwenden Sie nicht.|
|`Source`|Benötigten Der Wert der in Hexadezimal Darstellung dargestellten Farbe.|

 Alle Werte, die von der __VSCOLORTYPE-Enumeration unterstützt werden, werden vom Schema im Type-Attribut unterstützt. Es wird jedoch empfohlen, nur CT_RAW und CT_SYSCOLOR zu verwenden.

 **Alles zusammen**

 Dies ist ein einfaches Beispiel für eine gültige Datei "Theme. xml":

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Verwenden des Tools
 **Syntax**

 Vsixcolorcompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Argumente**

|**SwitchName**|**Notizen**|**Erforderlich oder optional**|
|-|-|-|
|Unbenannte Datei (XML-Datei)|Dies ist der erste unbenannte Parameter und der Pfad zur XML-Datei, die konvertiert werden soll.|Erforderlich|
|Unbenannte Datei (pkgdef-Datei)|Dies ist der zweite unbenannte Parameter und der Ausgabepfad für die generierte pkgdef-Datei.<br /><br /> Standard: \<XML Filename> . pkgdef|Optional|
|/noLogo|Wenn Sie dieses Flag festlegen, werden die Produkt-und Copyright Informationen nicht gedruckt.|Optional|
|/?|Ausdrucken von Hilfe Informationen.|Optional|
|/help|Ausdrucken von Hilfe Informationen.|Optional|

 **Beispiele**

- Vsixcolorcompiler D:\xml\colors.xml d:\pkgdef\colors.pkgdef

- Vsixcolorcompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>Notizen

- Dieses Tool erfordert, dass die aktuelle Version der VC + +-Laufzeit installiert ist.

- Nur einzelne Dateien werden unterstützt. Die Massen Konvertierung über Ordner Pfade wird nicht unterstützt.

## <a name="sample-output"></a>Beispielausgabe
 Die vom Tool generierte pkgdef-Datei ähnelt den folgenden Schlüsseln:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
