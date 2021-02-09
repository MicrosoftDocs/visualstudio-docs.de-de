---
title: Befehlsflag-Element | Microsoft-Dokumentation
description: Das Befehlsflag-Element ändert das übergeordnete Element. Überprüfen Sie die übergeordneten Elemente und untergeordneten Elemente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f328f2112073c082e276683d32d6ca06276b9829
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848194"
---
# <a name="command-flag-eelement"></a>Eelement für Befehlsflag
Ändert das übergeordnete Element.

## <a name="syntax"></a>Syntax

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 Im folgenden Abschnitt werden gültige Element Werte beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Wert|Beschreibung|
|-----------|-----------------|
|Allowparametriams|Gibt an, dass Benutzer Befehlsparameter im **Befehls** Fenster eingeben können, wenn Sie den kanonischen Namen des Befehls eingeben.<br /><br /> Gültig für: `Button`|
|AlwaysCreate|Das Menü wird auch dann erstellt, wenn es keine Gruppen oder Schaltflächen enthält.<br /><br /> Gültig für: `Menu`|
|CaseSensitive|Bei Benutzer Einträgen wird die Groß-/Kleinschreibung beachtet.<br /><br /> Gültig für: `Combo`|
|Commandwellonly|Wenden Sie dieses Flag an, wenn der Befehl nicht im Menü der obersten Ebene angezeigt wird und Sie für zusätzliche Shellanpassungen verfügbar machen möchten, z. b. für die Bindung an eine Tastenkombination. Nachdem das VSPackage installiert wurde, können Sie diese Befehle anpassen, indem Sie das Dialogfeld **Optionen** öffnen und dann die Befehls Platzierung unter der Kategorie **Tastatur Umgebung** bearbeiten. Dieses Flag wirkt sich nicht auf die Platzierung von Kontextmenüs, Symbolleisten, Menü Controllern oder Untermenüs aus.<br /><br /> Gültig für: `Button` , `Combo`|
|Defaultdeaktiviert|Standardmäßig ist der Befehl deaktiviert, wenn das VSPackage, das es implementiert, nicht geladen wurde oder die `QueryStatus` Methode nicht aufgerufen wurde.<br /><br /> Gültig für: `Button` , `Combo`|
|Defaultangedockt|Standardmäßig angedockt. Diese Einstellung gilt nicht mehr für Symbolleisten, da Sie immer angedockt sind.|
|Defaultinvisible|Standardmäßig ist der Befehl unsichtbar, wenn das VSPackage, das es implementiert, nicht geladen wurde oder die- `QueryStatus` Methode nicht aufgerufen wurde.<br /><br /> Es wird empfohlen, dies mit dem-Flag zu kombinieren `DynamicVisibility` .<br /><br /> Gültig für: `Button` , `Combo` , `Menu`|
|DontCache|Die- `QueryStatus` Methoden Ergebnisse für diesen Befehl werden von der Entwicklungsumgebung nicht zwischengespeichert.<br /><br /> Bei einem Menü wird einem Menü Controller mitgeteilt, dass er den Text seiner Menü Elemente nicht zwischenspeichern soll. Verwenden Sie dieses Flag, wenn das Menü dynamische Elemente oder Elemente mit dynamischem Text enthält.<br /><br /> Gültig für: `Button` , `Menu`|
|Dynamicitemstart|Gibt den Anfang einer dynamischen Liste an. Dadurch kann die Umgebung eine Liste erstellen, indem Sie die- `QueryStatus` Methode für Listenelemente nacheinander aufrufen, bis das OLECMDERR_E_UNSUPPORTED-Flag zurückgegeben wird. Dies funktioniert gut für Elemente wie z. b. die zuletzt verwendeten (MRU) Listen und Fenster Listen.<br /><br /> Gültig für: `Button`|
|Dynamicvisibility|Die Sichtbarkeit des Befehls kann durch die- `QueryStatus` Methode oder durch eine Kontext-GUID, die im-Abschnitt enthalten ist, geändert werden `VisibilityConstraints` .<br /><br /> Gilt für Befehle, die in Menüs und Tool Fenster Symbolleisten angezeigt werden, jedoch nicht für Symbolleisten der obersten Ebene, die im Hauptfenster angezeigt werden. Symbolleisten Elemente der obersten Ebene können deaktiviert, jedoch nicht ausgeblendet werden, wenn das OLECMDF_INVISIBLE-Flag von der-Methode zurückgegeben wird `QueryStatus` . Symbolleisten Befehle, die auf Symbolleisten des Tool Fensters angezeigt werden, können ausgeblendet werden.<br /><br /> In einem Menü gibt dieses Flag auch an, dass es automatisch ausgeblendet werden soll, wenn alle zugehörigen Member ausgeblendet sind. Dieses Flag wird normalerweise Untermenüs zugewiesen, da die Menüs der obersten Ebene bereits über dieses Verhalten verfügen.<br /><br /> Dieses Flag sollte mit dem-Flag kombiniert werden `DefaultInvisible` .<br /><br /> Gültig für: `Button` , `Combo` , `Menu`|
|Filter Keys|Weitere Informationen finden Sie im Thema Filtern von Schlüsseln unter "Kombinations [Element](../extensibility/combo-element.md)"<br /><br /> Gültig für: `Combo`|
|Fixmenucontroller|Wenn dieser Befehl auf einem Menü Controller positioniert ist, ist der Befehl immer der Standard. Das heißt, dass der Befehl immer dann ausgewählt wird, wenn die Menü Controller Schaltfläche selbst ausgewählt ist. Wenn für den Menü Controller das `TextIsAnchorCommand` Flag festgelegt ist, übernimmt der Menü Controller auch seinen Text aus dem Befehl, der über das `FixMenuController` Flag verfügt.<br /><br /> Nur ein Befehl in einem Menü Controller muss über das `FixMenuController` Flag verfügen. Wenn mehr als ein Befehl so gekennzeichnet ist, wird der letzte Befehl im Menü zum Standardbefehl.<br /><br /> Gültig für: `Button`|
|Iconandtext|Symbol und Text im Menü und in der Symbolleiste anzeigen.<br /><br /> Gültig für: `Button` , `Combo` , `Menu`|
|Noautocomplete|Die Funktion zum automatischen Vervollständigen ist deaktiviert.<br /><br /> Gültig für: `Combo`|
|Nobuttoncustomize|Lassen Sie den Benutzer diese Schaltfläche nicht anpassen.<br /><br /> Gültig für: `Button` , `Combo`|
|Nokeycustomize|Aktivieren Sie keine Tastatur Anpassung.<br /><br /> Gültig für: `Button` , `Combo`|
|Noshowonmenucontroller|Wenn dieser Befehl auf einem Menü Controller positioniert ist, wird der Befehl nicht in der Dropdown Liste angezeigt.<br /><br /> Gültig für: `Button`|
|Notintblist|Wird nicht in der Liste der verfügbaren Symbolleisten angezeigt. Dies ist nur für Symbolleisten-Menü Typen gültig.<br /><br /> Gültig für: `Menu`|
|Notoolbarclose|Der Benutzer kann die Symbolleiste nicht schließen. Dies ist nur für Symbolleisten-Menü Typen gültig.<br /><br /> Gültig für: `Menu`|
|PICT|Zeigt nur ein Symbol auf einer Symbolleiste an, aber nur Text in einem Menü. Wenn kein Symbol angegeben wird, wird ein klickbarer leerer Leerraum auf einer Symbolleiste angezeigt.<br /><br /> Gültig für: `Button`|
|Postexec|Bewirkt, dass der Befehl nicht blockiert wird. Die Entwicklungsumgebung wird ausgeführt, bis alle vorab verarbeiteten Abfragen abgeschlossen sind.<br /><br /> Gültig für: `Button`|
|Routeto docs|Der Befehl wird an das aktive Dokument weitergeleitet.<br /><br /> Gültig für: `Button`|
|Stretchhorizontal|Wenn dieses Flag festgelegt ist, wird die Breite zur minimalen Breite für das Kombinations Feld. wenn auf der Symbolleiste Platz vorhanden ist, wird das Kombinations Feld gestreckt, um den verfügbaren Platz auszufüllen. Dies tritt nur dann auf, wenn die Symbolleiste horizontal angedockt ist und nur ein Kombinations Feld auf der Symbolleiste das Flag verwenden kann (das Flag wird ignoriert, außer das erste Kombinations Feld).<br /><br /> Gültig für: `Combo`|
|Textchanges Befehlsflag|Der Befehl oder Menütext kann zur Laufzeit geändert werden, in der Regel über die- `QueryStatus` Methode.<br /><br /> Gültig für: `Button` , `Menu`|
|Textchangesbutton|Gültig für: `Button`|
|Textisanchorcommand|Bei einem Menü Controller wird der Text des Menüs aus dem Standardbefehl (Anker) entnommen. Ein Anker Befehl ist der letzte ausgewählte oder latchende Befehl. Wenn dieses Flag nicht festgelegt ist, verwendet der Menü Controller ein eigenes `MenuText` Feld. Wenn Sie jedoch auf den Menü Controller klicken, wird weiterhin der letzte ausgewählte Befehl von diesem Controller aktiviert.<br /><br /> Es wird empfohlen, dieses Flag mit dem-Flag zu kombinieren `TextChanges` .<br /><br /> Dieses Flag gilt nur für Menüs vom Typ menucontroller oder menucontrollerlatched.<br /><br /> Gültig für: `Menu`|
|Textmenuctrlufestmenu|Verwenden Sie das- `MenuText` Feld auf Menü Controllern. Das Standardfeld ist `ButtonText` .<br /><br /> Gültig für: `Button`|
|Textmenuusebutton|Verwenden Sie das `ButtonText` Feld für Menüs. Das Standardfeld ist, `MenuText` Wenn es angegeben wird.<br /><br /> Gültig für: `Button`|
|TextOnly|Nur Text auf einer Symbolleiste oder einem Menü, aber ohne Symbol anzeigen, auch wenn das Symbol angegeben ist.<br /><br /> Gültig für: `Button`|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Buttons-Element](../extensibility/buttons-element.md)|Stellt eine Gruppe für [Schaltflächen Element](../extensibility/button-element.md) Elemente bereit.|
|[Menüs-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die von einem VSPackage implementiert werden.|

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehls Tabelle (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
