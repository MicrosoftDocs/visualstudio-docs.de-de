---
title: CodeIndex-Befehl
description: Erfahren Sie, wie Sie den CodeIndex-Befehl verwenden können, um die Codeindizierung auf Azure DevOps Server (früher als Team Foundation Server bezeichnet) zu verwalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece3916f0af442b67bb5cdd0999ad37159e53448
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901179"
---
# <a name="codeindex-command"></a>CodeIndex-Befehl

Mit dem **CodeIndex**-Befehl können Sie die Codeindizierung für Team Foundation Server verwalten. Beispielsweise können Sie den Index zurücksetzen, um CodeLens-Informationen zu korrigieren, oder die Indizierung deaktivieren, um Probleme mit der Serverleistung zu untersuchen.

## <a name="required-permissions"></a>Erforderliche Berechtigungen

Zum Verwenden des **CodeIndex**-Befehls müssen Sie Mitglied der Sicherheitsgruppe **Team Foundation-Administratoren** sein. Weitere Informationen finden Sie unter [Permissions and groups defined for Azure DevOps Services and TFS (Für Azure DevOps Services und TFS definierte Berechtigungen und Gruppen)](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true).

> [!NOTE]
> Sie müssen auch dann ein Fenster für die Eingabeaufforderung mit erhöhten Rechten öffnen, wenn Sie sich mit Administratoranmeldeinformationen anmelden, um diesen Befehl auszuführen. Sie müssen diesen Befehl außerdem auf der Logikschicht für Team Foundation ausführen.

## <a name="syntax"></a>Syntax

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parameter

|**Argument**|**Beschreibung**|
|------------------| - |
|`CollectionName`|Gibt den Namen der Projektsammlung an. Wenn der Name Leerzeichen enthält, setzen Sie ihn in Anführungszeichen, z.B. „Fabrikam Website“.|
|`CollectionId`|Gibt die ID der Projektsammlung an.|
|`ServerPath`|Gibt den Pfad zu einer Codedatei an.|

|**Option**|**Beschreibung**|
|----------------| - |
|**/indexingStatus**|Zeigen Sie den Status und die Konfiguration des Codeindexdiensts an.|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: Indizierung aller Changesets beginnen.<br />-   **off**: Indizierung aller Changesets beenden.<br />-   **keepupOnly**: Indizierung zuvor erstellter Changesets beenden und mit der Indizierung nur der neuen Changesets beginnen.|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Sie können das Platzhalterzeichen (*) am Anfang, am Ende oder an beiden Enden des Serverpfads verwenden.|Gibt eine Liste mit Codedateien und ihren Pfaden an, die nicht indiziert werden sollen.<br /><br /> -   **add**: Die Datei, die Sie nicht indizieren möchten, zur Liste der ignorierten Dateien hinzufügen.<br />-   **remove**: Die Datei, die Sie indizieren möchten, aus der Liste der ignorierten Dateien entfernen.<br />-   **removeAll**: Die Liste der ignorierten Dateien wird geleert und die Indizierung aller Dateien begonnen.<br />-   **view**: Alle Dateien anzeigen, die nicht indiziert werden.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Zeigt die angegebene Anzahl der Dateien an, die die angegebene Größe in KB überschreitet. Sie können dann mithilfe der Option **/ignoreList** diese Dateien von der Indizierung ausschließen.|
|**/reindexAll**|Zuvor indizierte Daten werden gelöscht, und die Indizierung wird neu gestartet.|
|**/destroyCodeIndex [/noPrompt]**|Der Codeindex wird gelöscht, und alle indizierten Daten werden entfernt. Erfordert keine Bestätigung, wenn Sie die Option **/noPrompt** verwenden.|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Steuern Sie, wie viele temporäre Daten CodeLens bei der Verarbeitung von Changesets erstellt. Die Standardgrenze ist 2 GB.<br /><br /> -   **view**: Die aktuelle Größenbeschränkung anzeigen.<br />-   `SizeInGBs`: Die Größenbeschränkung ändern.<br />-   **disable**: Die Größenbeschränkung entfernen.<br /><br /> Diese Grenze wird überprüft, bevor CodeLens ein neues Changeset verarbeitet. Wenn die temporären Daten diese Grenze überschreiten, hält CodeLens die Verarbeitung vergangener und nicht neuer Changesets an. CodeLens beginnt wieder mit der Verarbeitung, nachdem die Daten bereinigt wurden und unter diese Grenze fallen. Die Bereinigung wird automatisch einmal pro Tag ausgeführt. Das bedeutet, dass temporäre Daten diese Grenze möglicherweise überschreiten, bis die Bereinigung ausgeführt wird.|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Steuern, wie lange der Änderungsverlauf indiziert werden soll. Dies beeinflusst, wie viel Verlauf von CodeLens gezeigt wird. Die Standardgrenze beträgt 12 Monate. Das bedeutet, dass CodeLens Ihren Änderungsverlauf nur aus den vergangenen 12 Monaten anzeigt.<br /><br /> -   **view**: Die aktuelle Anzahl Monate anzeigen.<br />-   **all**: Gesamten Änderungsverlauf indizieren.<br />-   `NumberOfMonths`: Anzahl der Monate ändern, für die der Änderungsverlauf indiziert wird.|
|**/collectionName:** `CollectionName`|Gibt den Namen der Projektsammlung an, für die der **CodeIndex**-Befehl ausgeführt werden soll. Erforderlich, wenn Sie **/CollectionId** nicht verwenden.|
|**/collectionId:** `CollectionId`|Gibt die ID der Projektsammlung an, für die der **CodeIndex**-Befehl ausgeführt werden soll. Erforderlich, wenn Sie **/CollectionName** nicht verwenden.|

## <a name="examples"></a>Beispiele

> [!NOTE]
> Die in den Beispielen genannten Unternehmen, Organisationen, Produkte, Domänennamen, E-Mail-Adressen, Logos, Personen, Orte und Ereignisse sind frei erfunden.  Jede Ähnlichkeit mit tatsächlichen Firmen, Organisationen, Produkten, Domänen, Personen, Orten, Ereignissen, E-Mail-Adressen und Logos ist rein zufällig.

So zeigen Sie den Status und die Konfiguration der Codeindizierung an:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

So starten Sie die Indizierung aller Changesets:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

So beenden Sie die Indizierung zuvor erstellter Changesets und starten die Indizierung nur neuer Changesets:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

So finden Sie bis zu 50 Dateien, die größer als 10 KB sind

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

So schließen Sie eine bestimmte Datei aus der Indizierung aus und fügen Sie der Liste ignorierter Dateien hinzu:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

So zeigen Sie alle Dateien an, die nicht indiziert werden

```cmd
TFSConfig CodeIndex /ignoreList:view
```

So löschen Sie zuvor indizierte Daten und starten die Indizierung neu:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

So speichern Sie den gesamten Changeset-Verlauf:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

So entfernen Sie die Größenbeschränkung für temporäre CodeLens-Daten und fahren mit der Indizierung unabhängig von der Größe der temporären Daten fort:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

So löschen Sie den Codeindex mit Bestätigung:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Weitere Informationen

- [Ermitteln von Änderungen am Code und anderer Verläufe mit CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Managing server configuration with TFSConfig (Verwalten der Serverkonfiguration mit TFSConfig)](/azure/devops/server/command-line/tfsconfig-cmd)
