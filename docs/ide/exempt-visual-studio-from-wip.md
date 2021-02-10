---
title: Ausnahme von Windows Information Protection
description: Erfahren Sie, wie Sie Visual Studio als Windows Information Protection-Ausnahme-App definieren, sodass Visual Studio weiterhin Unternehmensdaten verwenden kann.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ff233b959b4ad691646c5e47c659b398b283b5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898005"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurieren von Visual Studio als Ausnahme-App von WIP

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) dient zum Schutz des Verlusts von Unternehmensdaten über Apps, die vom Unternehmen nicht kontrolliert werden können, wie z.B. E-Mails, soziale Medien und die öffentliche Cloud. WIP bietet Schutz vor versehentlichem Datenverlust auf unternehmenseigenen und persönlichen Geräten, ohne dass Änderungen in Ihrer Umgebung oder anderen Apps erforderlich sind.

Mit *WIP-fähigen* Apps soll eine Weiterleitung von Unternehmensdaten an ungeschützte Netzwerkadressen und eine Verschlüsselung personenbezogener Daten verhindert werden. Da es sich bei Visual Studio nicht um eine WIP-fähige App handelt, kann sie nur dann in WIP-fähigen Umgebungen ausgeführt werden, wenn Sie sie als Ausnahme-App festlegen. Führen Sie die Schritte in diesem Artikel aus, um Visual Studio auf einem WIP-fähigen Computer zu aktivieren.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Konfigurieren von Visual Studio als Ausnahme-App von WIP

Sie können Visual Studio von WIP-Einschränkungen ausnehmen, jedoch weiterhin die Verwendung von Unternehmensdaten zulassen. Ausnahme-Apps von WIP können über eine IP-Adresse oder einen Hostnamen eine Verbindung mit Unternehmenscloudressourcen herstellen. Es wird keine Verschlüsselung angewendet, und die App kann auf lokale Dateien zugreifen.

Führen Sie die [Schritte zum Festlegen einer Desktop-App als Ausnahme](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy) aus, um Visual Studio von WIP auszunehmen.

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Erstellen einer AppLocker-Richtliniendatei als Ausnahme von WIP

Da Visual Studio mehrere Binärdateien enthält, müssen Sie eine [AppLocker-Richtliniendatei als Ausnahme von WIP erstellen](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). Mit AppLocker können Sie für sämtliche Dateien in einem Ordner automatisch Regeln generieren.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Hinzufügen von AppCompat zur Richtlinie für Unternehmenscloudressourcen

Führen Sie die folgenden [Schritte aus, um zu definieren, wo Ihre geschützten Apps Unternehmensdaten finden und senden können](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data), wenn Sie angeben möchten, wo Visual Studio in Ihrem Netzwerk auf Unternehmensdaten zugreifen kann. Stellen Sie sicher, dass die Zeichenfolge /\*AppCompat\*/ zur Einstellung hinzugefügt wird, wenn Windows keine Verbindungen zu Cloudressourcen über eine IP-Adresse mehr blockieren soll.

## <a name="see-also"></a>Weitere Informationen

- [App-Verhalten mit WIP](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
