---
title: VSPackage-Setup Szenarien | Microsoft-Dokumentation
description: Erfahren Sie mehr über bewährte Methoden für die Unterstützung paralleler Installationen von Visual Studio mit freigegebenen oder parallelen Installationen des VSPackages.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81e298229bb12d906a3061e0b547553518cce204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899998"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage-Setupszenarien

Es ist wichtig, dass Sie das VSPackage-Installationsprogramm flexibel gestalten. Beispielsweise müssen Sie möglicherweise in der Zukunft einen Sicherheitspatches veröffentlichen, oder Sie können eine Geschäftsstrategie ändern, die eine gründliche Unterstützung der parallelen Versionsverwaltung erfordert.

Wenn Sie [mehrere Versionen von Visual Studio unterstützen](../../extensibility/supporting-multiple-versions-of-visual-studio.md), können Sie sich über die Vorteile und Probleme bei der Unterstützung paralleler Installationen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit freigegebenen oder parallelen Installationen Ihres VSPackage informieren. Kurz gesagt bieten Ihnen parallele VSPackages die größte Flexibilität bei der Unterstützung neuer Funktionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Die in diesem Thema erläuterten Szenarien sind nicht Ihre einzige Wahl, sondern werden als empfohlene bewährte Methoden vorgestellt.

## <a name="components-privacy-and-sharing"></a>Komponenten, Datenschutz und Freigabe

### <a name="make-your-components-independent"></a>Machen Sie Ihre Komponenten unabhängig

Nachdem Sie eine Komponente identifiziert und aufgefüllt, eine zugewiesen `GUID` und die Komponente bereitgestellt haben, können Sie deren Komposition nicht mehr ändern. Wenn Sie die Zusammensetzung einer Komponente ändern, muss die resultierende Komponente eine neue Komponente mit einem neuen sein `GUID` . Angesichts dieser Fakten wird die größte Flexibilität bei der Versionsverwaltung erzielt, indem jede Komponente unabhängig voneinander unabhängig voneinander unabhängig gemacht wird. Weitere Informationen zu Regeln, die Komponenten steuern, finden Sie unter [Ändern des Komponenten Codes](/windows/desktop/Msi/changing-the-component-code) und [Was geschieht, wenn die Komponenten Regeln beschädigt sind?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Keine Mischung aus freigegebenen und privaten Ressourcen in einer Komponente

Die Verweis Zählung erfolgt auf der Komponentenebene. Folglich ist es unmöglich, private Ressourcen (z. b. eine ausführbare Datei) zu aktualisieren, ohne auch freigegebene Ressourcen zu überschreiben, um freigegebene und private Ressourcen in einer Komponente zu mischen. Dieses Szenario stellt abwärts Kompatibilitätsprobleme dar und schränkt Sie von der Erstellung paralleler Funktionen ein.

Registrierungs Werte, die zum Registrieren des VSPackage bei verwendet werden, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sollten z. b. in einer separaten Komponente gespeichert werden, die von der zum Registrieren des VSPackage bei Visual Studio verwendeten Komponente getrennt ist. Freigegebene Dateien oder Registrierungs Werte werden in einer anderen Komponente verwendet.

## <a name="scenario-1-shared-vspackage"></a>Szenario 1: frei gegebenes VSPackage

In diesem Szenario wird ein frei gegebenes VSPackage (eine einzelne Binärdatei, die mehrere Versionen von Visual Studio unterstützt, in einem Windows Installer Paket ausgeliefert. Die Registrierung bei jeder Version von Visual Studio wird durch Benutzer auswählbare Features gesteuert. Dies bedeutet auch, dass bei Zuweisung zu separaten Features jede Komponente einzeln für die Installation oder die Installation ausgewählt werden kann, sodass der Benutzer die Kontrolle über die Integration des VSPackage in verschiedene Versionen von erhält [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . (Weitere Informationen zur Verwendung von Funktionen in Windows Installer Paketen finden Sie unter [Windows Installer Features](/windows/desktop/Msi/windows-installer-features) .)

![VS Shared VSPackage-Installer](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Wie in der Abbildung gezeigt, werden freigegebene Komponenten Teil des Feat_Common Features, das immer installiert ist. Wenn Sie die Feat_VS2002-und Feat_VS2003 Features sichtbar machen, können Benutzer bei der Installation auswählen, in welche Versionen von Visual Studio das VSPackage integriert werden soll. Benutzer können auch Windows Installer Wartungsmodus verwenden, um Funktionen hinzuzufügen oder zu entfernen. in diesem Fall werden die VSPackage-Registrierungsinformationen aus unterschiedlichen Versionen von Visual Studio hinzugefügt oder entfernt.

> [!NOTE]
> Wenn Sie die Anzeige Spalte einer Funktion auf 0 festlegen, wird Sie ausgeblendet. Ein Spaltenwert auf niedriger Ebene, z. b. 1, stellt sicher, dass er immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL-Eigenschaft](/windows/desktop/Msi/installlevel) und [Funktions Tabelle](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Szenario 2: frei gegebenes VSPackage-Update

In diesem Szenario wird eine aktualisierte Version des VSPackage-Installers in Szenario 1 ausgeliefert. Im Rahmen der Erörterung bietet das Update Unterstützung für Visual Studio, aber es kann auch ein einfacheres Sicherheitspatch oder ein Fehler Behebungs Service Pack sein. Windows Installer Regeln für die Installation neuerer Komponenten erfordern, dass unveränderte Komponenten, die bereits auf dem System vorhanden sind, nicht neu kopiert werden. In diesem Fall überschreibt ein System mit der Version 1,0, das bereits vorhanden ist, die aktualisierten Komponenten Comp_MyVSPackage.dll und ermöglicht es Benutzern, die neue Funktion Feat_VS2005 mit der Komponente Comp_VS2005_Reg hinzuzufügen.

> [!CAUTION]
> Wenn ein VSPackage von mehreren Versionen von gemeinsam genutzt wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , ist es von entscheidender Bedeutung, dass nachfolgende Versionen des VSPackage die Abwärtskompatibilität mit früheren Versionen von Visual Studio aufrechterhalten. Wenn Sie die Abwärtskompatibilität nicht beibehalten können, müssen Sie parallele private VSPackages verwenden. Weitere Informationen finden Sie [unter unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Vs Shared vs-Paket Update-Installer](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Dieses Szenario stellt ein neues VSPackage-Installationsprogramm dar und nutzt die Unterstützung von Windows Installer für kleinere Upgrades. Benutzer installieren einfach Version 1,1 und aktualisieren Version 1,0. Es ist jedoch nicht erforderlich, Version 1,0 auf dem System zu haben. Das gleiche Installationsprogramm installiert Version 1,1 auf einem System ohne Version 1,0. Der Vorteil der Bereitstellung von geringfügigen Upgrades auf diese Weise besteht darin, dass es nicht notwendig ist, ein Upgrade-Installationsprogramm und ein voll Produkt Installationsprogramm zu entwickeln. Ein Installer führt beide Aufträge aus. Eine Sicherheitslösung oder Service Pack kann stattdessen Windows Installer Patches nutzen. Weitere Informationen finden Sie unter [Patching und Upgrades](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Szenario 3: paralleles VSPackage

In diesem Szenario werden zwei VSPackage-Installationsprogramme dargestellt – eines für jede Version von Visual Studio .NET 2003 und Visual Studio. Jedes Installationsprogramm installiert ein paralleles oder privates VSPackage (eines, das speziell für eine bestimmte Version von Visual Studio erstellt und installiert wurde). Jedes VSPackage befindet sich in seiner eigenen Komponente. Folglich kann jeder einzeln mit Patches oder Wartungs Releases gewartet werden. Da die VSPackage-dll jetzt Versions spezifisch ist, ist es sicher, dass Sie Ihre Registrierungsinformationen in dieselbe Komponente wie die dll einschließen.

![Vs-paralleles vs-Paket-Installer](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Jedes Installationsprogramm enthält auch Code, der von den beiden Installationsprogrammen gemeinsam genutzt wird. Wenn der freigegebene Code an einem gemeinsamen Speicherort installiert ist, wird der freigegebene Code durch die Installation beider MSI-Dateien nur einmal installiert. Der zweite Installer erhöht lediglich einen Verweis Zähler für die Komponente. Der Verweis Zähler stellt sicher, dass, wenn eines der VSPackages deinstalliert wird, der freigegebene Code für das andere VSPackage beibehalten wird. Wenn das zweite VSPackage ebenfalls deinstalliert wird, wird der freigegebene Code entfernt.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Szenario 4: paralleles VSPackage-Update

In diesem Szenario hat das VSPackage für Visual Studio eine Sicherheits Anfälligkeit verursacht, und Sie müssen ein Update ausgeben. Wie in Szenario 2 können Sie eine neue MSI-Datei erstellen, mit der eine vorhandene Installation aktualisiert wird, die die Sicherheitskorrektur umfasst, und neue Installationen mit dem bereits vorhandenen Sicherheits Fix bereitstellen.

In diesem Fall ist das VSPackage ein verwaltetes VSPackage, das im globalen Assemblycache (GAC) installiert ist. Wenn Sie die Lösung neu erstellen, um den Sicherheitsfehler einzuschließen, müssen Sie den Revisionsnummern Teil der Versionsnummer der Assembly ändern. Die Registrierungsinformationen für die neue Assemblyversionsnummer überschreiben die vorherige Version, wodurch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Assembly geladen wird.

![Vs parallele vs-Paket Update-Installer](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Weitere Informationen zur Bereitstellung von parallelen Assemblys finden Sie unter [vereinfachen der Bereitstellung und lösen der DLL-Hell mit dem .NET Framework](/previous-versions/dotnet/articles/ms973843(v=msdn.10)).

## <a name="see-also"></a>Weitere Informationen

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)