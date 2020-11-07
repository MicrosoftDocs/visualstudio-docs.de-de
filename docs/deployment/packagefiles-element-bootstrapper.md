---
title: '&lt;PackageFiles- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
description: Erfahren Sie mehr über das PackageFiles-Element, das PackageFile-Elemente enthält, die die Installationspakete definieren, die als Ergebnis des Command-Elements ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60d6491101bef33f1d8c91d4f7640be9d7277da0
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349541"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles- &gt; Element (Boots Trapper)
Das- `PackageFiles` Element enthält- `PackageFile` Elemente, die die Installationspakete definieren, die als Ergebnis des-Elements ausgeführt werden `Command` .

## <a name="syntax"></a>Syntax

```xml
<PackageFiles
    CopyAllPackageFiles
>
    <PackageFile
        Name
        HomeSite
        CopyOnBuild
        PublicKey
        Hash
    />
</PackageFiles>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `PackageFiles` -Element hat das folgende Attribut.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`CopyAllPackageFiles`|Optional. Wenn der Wert auf festgelegt `false` ist, lädt der Installer nur Dateien herunter, auf die vom-Element verwiesen wird `Command` Wenn diese Einstellung auf festgelegt `true` ist, werden alle Dateien heruntergeladen.<br /><br /> Wenn der Wert auf festgelegt `IfNotHomesite` ist, verhält sich das Installationsprogramm wie `False` , wenn `ComponentsLocation` auf festgelegt ist `HomeSite` , und andernfalls verhält sich wie if `True` . Diese Einstellung kann nützlich sein, um zu ermöglichen, dass Pakete, die selbst Bootstrapper sind, Ihr eigenes Verhalten in einem HomeSite-Szenario ausführen.<br /><br /> Der Standardwert ist `true`.|

## <a name="packagefile"></a>PackageFile
 Das- `PackageFile` Element ist ein untergeordnetes `PackageFiles` Element des-Elements. Ein- `PackageFiles` Element muss über mindestens ein- `PackageFile` Element verfügen.

 `PackageFile` weist die folgenden Attribute auf.

| attribute | BESCHREIBUNG |
|---------------| - |
| `Name` | Erforderlich. Der Name der Paketdatei. Dies ist der Name, auf den das `Command` Element verweist, wenn es die Bedingungen definiert, unter denen ein Paket installiert wird. Dieser Wert wird auch als Schlüssel in der Tabelle verwendet `Strings` , um den lokalisierten Namen abzurufen, den Tools wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Beschreiben des Pakets verwenden. |
| `HomeSite` | Optional. Der Speicherort des Pakets auf dem Remote Server, wenn es nicht im Installationsprogramm enthalten ist. |
| `CopyOnBuild` | Optional. Gibt an, ob der Boots Trapper die Paketdatei zur Buildzeit auf den Datenträger kopieren soll. Der Standardwert ist "True". |
| `PublicKey` | Der verschlüsselte öffentliche Schlüssel des Zertifikats Signatur Gebers des Pakets. Erforderlich `HomeSite` , wenn verwendet wird, andernfalls optional. |
| `Hash` | Optional. Ein SHA1-Hash der Paketdatei. Hiermit wird die Integrität der Datei zur Installationszeit überprüft. Wenn der identische Hash nicht aus der Paketdatei berechnet werden kann, wird das Paket nicht installiert. |

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel werden Pakete für das .NET Framework verteilbaren Paket und seine Abhängigkeiten definiert, wie z. b. die Windows Installer.

```xml
<PackageFiles>
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetchk.exe"/>
</PackageFiles>
```

## <a name="see-also"></a>Weitere Informationen
- [\<Product> gewisses](../deployment/product-element-bootstrapper.md)
- [\<Package> gewisses](../deployment/package-element-bootstrapper.md)
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)