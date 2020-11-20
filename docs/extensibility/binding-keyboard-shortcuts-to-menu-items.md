---
title: Binden von Tastenkombinationen an Menü Elemente | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einer benutzerdefinierten Schaltfläche, einem Menü Element oder einem Symbolleisten Befehl für den Standard Editor oder einen benutzerdefinierten Editor eine Tastenkombination in Visual Studio zuordnen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 112089581965b96133f2160341a13efe23329934
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974618"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Binden von Tastenkombinationen an Menü Elemente
Fügen Sie der *vsct* -Datei für das Paket einfach einen Eintrag hinzu, um eine Tastenkombination an einen benutzerdefinierten Menübefehl zu binden. In diesem Thema wird erläutert, wie einer benutzerdefinierten Schaltfläche, einem Menü Element oder einem Symbolleisten Befehl eine Tastenkombination zugeordnet wird und wie die Tastatur Zuordnung im Standard-Editor angewendet oder auf einen benutzerdefinierten Editor beschränkt wird.

 Informationen zum Zuweisen von Tastenkombinationen zu vorhandenen Visual Studio-Menü Elementen finden Sie unter [identifizieren und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Tastenkombination auswählen
 Viele Tastenkombinationen werden bereits in Visual Studio verwendet. Sie sollten nur einem Befehl dieselbe Verknüpfung zuweisen, weil doppelte Bindungen schwer zu erkennen sind und möglicherweise zu unvorhersehbaren Ergebnissen führen. Daher empfiehlt es sich, die Verfügbarkeit einer Verknüpfung vor der Zuweisung zu überprüfen.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>So überprüfen Sie die Verfügbarkeit einer Tastenkombination

1. **Tools**  >  Wählen Sie im Fenster Extras **Optionen**  >  **Umgebung** die Option **Tastatur** aus.

2. Stellen Sie sicher, dass **Use New Shortcut in** auf **Global** festgelegt ist.

3. Geben Sie im Feld Tasten **Kombination drücken** die Tastenkombination ein, die Sie verwenden möchten.

    Wenn die Verknüpfung bereits in Visual Studio verwendet wird, zeigt die Verknüpfung, die **derzeit von Box verwendet** wird, den Befehl an, den die Verknüpfung aktuell aufruft.

4. Probieren Sie verschiedene Tastenkombinationen aus, bis Sie eine gefunden haben, die nicht zugeordnet ist.

   > [!NOTE]
   > Tastenkombinationen, die **alt** verwenden, können ein Menü öffnen und keinen Befehl direkt ausführen. Daher kann die **derzeit von Box verwendete Verknüpfung** leer sein, wenn Sie eine Verknüpfung eingeben, die **alt** enthält. Sie können überprüfen, ob die Verknüpfung ein Menü öffnet, indem Sie das Dialogfeld **Optionen** schließen und dann die Tasten drücken.

   Bei der folgenden Prozedur wird davon ausgegangen, dass Sie über ein vorhandenes VSPackage mit einem Menübefehl verfügen. Wenn Sie Hilfe benötigen, sehen Sie sich die Schritte zum [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)an.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>So weisen Sie einem Befehl eine Tastenkombination zu

1. Öffnen Sie die *vsct* -Datei für das Paket.

2. Erstellen Sie einen leeren `<KeyBindings>` Abschnitt nach dem, `<Commands>` Wenn er nicht bereits vorhanden ist.

   > [!WARNING]
   > Weitere Informationen zu Tastenbindungen finden Sie unter [KeyBinding](../extensibility/keybinding-element.md).

    Erstellen Sie im `<KeyBindings>` Abschnitt einen `<KeyBinding>` Eintrag.

    Legen `guid`  Sie das-Attribut und das-  `id` Attribut auf die des Befehls fest, den Sie aufrufen möchten.

    Legen Sie das- `mod1` Attribut auf **Control**, **alt** oder **Shift** fest.

    Der Abschnitt "KeyBinding" sollte in etwa wie folgt aussehen:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Wenn die Tastenkombination mehr als zwei Schlüssel erfordert, legen Sie das `mod2` -Attribut und das- `key2` Attribut fest.

   In den meisten Fällen sollte **Shift** nicht ohne einen zweiten Modifizierer verwendet werden, da durch das Drücken der Zeichen bereits ein Großbuchstabe oder ein Symbol für die meisten alphanumerischen Schlüssel verwendet wird.

   Mit virtuellen Schlüsselcodes können Sie auf spezielle Schlüssel zugreifen, denen kein Zeichen zugeordnet ist, z. b. Funktionstasten und die **RÜCKTASTE** . Weitere Informationen finden Sie unter [virtuelle Schlüsselcodes](/windows/desktop/inputdev/virtual-key-codes).

   Um den Befehl im Visual Studio-Editor verfügbar zu machen, legen `editor` Sie das-Attribut auf fest `guidVSStd97` .

   Damit der Befehl nur in einem benutzerdefinierten Editor verfügbar ist, legen `editor` Sie das-Attribut auf den Namen des benutzerdefinierten Editors fest, der von der Paket Vorlage generiert wurde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] als Sie das VSPackage erstellt haben, das den benutzerdefinierten Editor enthält. Um den namens Wert zu finden, suchen Sie im `<Symbols>` Abschnitt nach einem `<GuidSymbol>` Knoten, dessen `name` Attribut auf " `editorfactory` ." endet. Dies ist der Name des benutzerdefinierten Editors.

## <a name="example-1"></a>Beispiel 1
 In diesem Beispiel wird die Tastenkombination **STRG** + **alt** + **C** an einen Befehl `cmdidMyCommand` mit dem Namen in einem Paket mit dem Namen gebunden `MyPackage` .

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example-2"></a>Beispiel 2
 In diesem Beispiel wird die Tastenkombination **STRG** + **B** an einen Befehl `cmdidBold` mit dem Namen in einem Projekt mit dem Namen gebunden `TestEditor` . Der Befehl ist nur im benutzerdefinierten Editor und nicht in anderen Editoren verfügbar.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Weitere Informationen:
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
