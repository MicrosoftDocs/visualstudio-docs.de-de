---
title: Erstellen wiederverwendbarer Gruppen von Schaltflächen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Befehlsgruppe erstellen, bei der es sich um eine Auflistung von Befehlen handelt, die in einem Menü oder einer Symbolleiste angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62873d57da04f94ce1cdda16c5fe4801af5d19c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884922"
---
# <a name="create-reusable-groups-of-buttons"></a>Erstellen wiederverwendbarer Gruppen von Schaltflächen
Eine Befehlsgruppe ist eine Auflistung von Befehlen, die immer in einem Menü oder einer Symbolleiste angezeigt werden. Alle Befehls Gruppen können wieder verwendet werden, indem Sie im Abschnitt commandplacement der *vsct* -Datei anderen übergeordneten Menüs zugewiesen werden.

 Befehls Gruppen enthalten in der Regel Schaltflächen, Sie können jedoch auch andere Menüs oder Kombinations Felder enthalten.

## <a name="to-create-a-reusable-group-of-buttons"></a>So erstellen Sie eine wiederverwendbare Gruppe von Schaltflächen

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `ReusableButtons` . Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **reusablecommand** hinzu. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *ReusableCommand.cs*.

3. Wechseln Sie in der *vsct* -Datei zum Abschnitt "Symbole", und suchen Sie das Element "guidsymbol", das Gruppen und Befehle für das Projekt enthält. Der Name sollte "guidre-ablecommandpackagecmdset" lauten.

4. Fügen Sie ein idsymbol für jede Schaltfläche hinzu, die Sie der Gruppe hinzufügen, wie im folgenden Beispiel gezeigt.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Standardmäßig erstellt die Befehls Element Vorlage eine Gruppe mit dem Namen **mymenugroup** und eine Schaltfläche mit dem Namen, den Sie angegeben haben, sowie einen idsymbol-Eintrag für jeden.

5. Erstellen Sie im Gruppenabschnitt ein Group-Element, das über die gleichen GUID-und ID-Attribute wie die im Abschnitt "Symbole" angegebenen Attribute verfügt. Sie können auch eine vorhandene Gruppe verwenden oder den von der Befehls Vorlage bereitgestellten Eintrag verwenden, wie im folgenden Beispiel gezeigt. Diese Gruppe wird **im Menü Extras angezeigt.**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>So erstellen Sie eine Gruppe von Schaltflächen für die Wiederverwendung

1. Sie können einen Befehl oder ein Menü in eine Gruppe einfügen, indem Sie die Gruppe als übergeordnetes Element in der Definition des Befehls oder Menüs verwenden oder indem Sie den Befehl oder das Menü mithilfe des Abschnitts commandplacement in die Gruppe einfügen.

     Definieren Sie im Schaltflächen Abschnitt eine Schaltfläche, bei der die Gruppe als übergeordnetes Element angezeigt wird, oder verwenden Sie die Schaltfläche, die von der-Paket Vorlage bereitgestellt wird, wie im folgenden Beispiel gezeigt.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Wenn eine Schaltfläche in mehr als einer Gruppe angezeigt werden muss, erstellen Sie im Abschnitt commandplacement einen Eintrag, der nach dem Abschnitt Befehle platziert werden muss. Legen Sie die GUID-und ID-Attribute des commandplacement-Elements so fest, dass Sie mit denen der Schaltfläche, die Sie positionieren möchten, abgeglichen werden, und legen Sie dann die GUID und die ID des übergeordneten Elements auf die der Zielgruppe fest, wie im folgenden Beispiel gezeigt.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Der Wert des Felds Priorität bestimmt die Position des Befehls in der neuen Befehlsgruppe. Die im commandplacement-Element festgelegten Prioritäten überschreiben jene, die in der Element Definition festgelegt sind. Befehle, die niedrigere Prioritätswerte aufweisen, werden vor Befehlen angezeigt, die höhere Prioritätswerte aufweisen. Doppelte Prioritätswerte sind zulässig, aber die relative Position von Befehlen mit dem gleichen Prioritätswert kann nicht garantiert werden, da die Reihenfolge, in der der **Devenv/Setup** -Befehl die endgültige Schnittstelle aus der Registrierung erstellt, möglicherweise nicht konsistent ist.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>So legen Sie eine wiederverwendbare Gruppe von Schaltflächen in einem Menü ab

1. Erstellen Sie einen Eintrag im- `CommandPlacements` Abschnitt. Legen Sie die GUID und die ID des `CommandPlacement` Elements auf die der Gruppe fest, und legen Sie die übergeordnete GUID und die ID auf die des Zielspeicher Orts fest.

    Der Abschnitt commandplacement sollte direkt nach dem Abschnitt Befehle platziert werden:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Eine Befehlsgruppe kann in mehr als einem Menü enthalten sein. Das übergeordnete Menü kann ein von Ihnen erstelltes Element sein, das von bereitgestellt wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (wie in *shellcmddef. vsct* oder *sharedcmddef. vsct* beschrieben), oder ein Element, das in einem anderen VSPackage definiert ist. Die Anzahl der Ebenen für die übergeordnete Ebene ist unbegrenzt, solange das übergeordnete Menü schließlich mit oder mit einem Kontextmenü verbunden ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , das von einem VSPackage angezeigt wird.

    Im folgenden Beispiel wird die-Gruppe auf der **Projektmappen-Explorer** Symbolleiste rechts neben den anderen Schaltflächen abgelegt.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
