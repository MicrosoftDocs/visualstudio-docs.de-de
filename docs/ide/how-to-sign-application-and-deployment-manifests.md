---
title: 'Vorgehensweise: Signieren von Anwendungs- und Bereitstellungsmanifesten'
description: In diesem Artikel erfahren Sie mehr über die Anforderungen für die Signierung für die Veröffentlichung von ClickOnce-Anwendungs- und -Bereitstellungsmanifesten. Für Anwendungen, die auf EXE-Dateien basieren, ist die Signierung optional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5568961cc8b527ecd724ab9a1d26ab4a641696b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869283"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Vorgehensweise: Signieren von Anwendungs- und Bereitstellungsmanifesten

Wenn Sie eine Anwendung mit der ClickOnce-Bereitstellung veröffentlichen möchten, müssen Anwendungs- und Bereitstellungsmanifeste mit einem öffentlichen/privaten Schlüsselpaar und unter Verwendung von Authenticode signiert werden. Sie können die Manifeste mit einem Zertifikat aus dem Windows-Zertifikatspeicher oder einer Schlüsseldatei signieren.

Weitere Informationen über die ClickOnce-Bereitstellung finden Sie unter [ClickOnce security and deployment (ClickOnce-Sicherheit und Bereitstellung)](../deployment/clickonce-security-and-deployment.md).

Das Signieren der ClickOnce-Manifeste ist für *EXE*-basierte Anwendungen optional. Weitere Informationen finden Sie im Abschnitt „Generieren von unsignierten Manifesten“ in diesem Dokument.

Weitere Informationen zum Erstellen von Schlüsseldateien finden Sie unter [Vorgehensweise: Erstellen eines öffentlichen bzw. privaten Schlüsselpaars](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> Visual Studio unterstützt nur PFX-Schlüsseldateien (Personal Information Exchange) mit der Erweiterung *.pfx*. Sie können jedoch andere Typen von Zertifikaten aus dem Windows-Zertifikatspeicher des aktuellen Benutzers auswählen, indem Sie auf der Seite **Signierung** der Projekteigenschaften auf **Aus Speicher auswählen** klicken.

## <a name="sign-using-a-certificate"></a>Signieren mithilfe eines Zertifikats

1. Navigieren Sie zum Fenster „Projekteigenschaften“. Klicken Sie hierzu im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus. Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.

2. Klicken Sie auf die Schaltfläche **Aus Speicher auswählen**.

     Das Dialogfeld **Zertifikat auswählen** wird mit dem Inhalt des Windows-Zertifikatspeichers angezeigt.

    > [!TIP]
    > Wenn Sie auf **Klicken Sie hier, um Zertifikateigenschaften anzuzeigen** klicken, wird das Dialogfeld **Zertifikatdetails** angezeigt. Dieses Dialogfeld enthält ausführliche Informationen zu dem Zertifikat sowie zusätzliche Optionen. Klicken Sie auf **Zertifikate**, um weitere Hilfeinformationen anzuzeigen.

3. Wählen Sie das Zertifikat aus, mit dem Sie die Manifeste signieren möchten.

4. Zudem können Sie im Textfeld **Timestampserver-URL** die Adresse eines Timestampservers angeben. Dabei handelt es sich um einen Server, der einen Timestamp bereitstellt, mit dem angegeben wird, zu welchem Zeitpunkt das Manifest signiert wurde.

## <a name="sign-using-an-existing-key-file"></a>Signieren mithilfe einer vorhandenen Schlüsseldatei

1. Aktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.

2. Klicken Sie auf die Schaltfläche **Aus Datei wählen**.

     Das Dialogfeld **Datei auswählen** wird angezeigt.

3. Suchen Sie im Dialogfeld **Datei auswählen** den Speicherort der zu verwendenden Schlüsseldatei (*PFX*-Datei), und klicken Sie dann auf **Öffnen**.

    > [!NOTE]
    > Diese Option kann nur bei Dateien mit der Erweiterung *.pfx* verwendet werden. Speichern Sie Schlüsseldateien oder Zertifikate in einem anderen Format im Windows-Zertifikatspeicher, und wählen Sie das Zertifikat aus, das im vorhergehenden Verfahren beschrieben wurde. Zu den Funktionen des ausgewählten Zertifikats sollten auch Codesignaturen gehören.

     Das Dialogfeld **Kennwort zum Öffnen der Datei eingeben** wird angezeigt. (Wenn die *PFX*-Datei bereits im Windows-Zertifikatspeicher gespeichert oder nicht kennwortgeschützt ist, werden Sie nicht zur Eingabe eines Kennworts aufgefordert.)

4. Geben Sie das Kennwort für den Zugriff auf die Schlüsseldatei ein, und drücken Sie dann die **EINGABETASTE**.

> [!NOTE]
> Die *PFX*-Datei kann keine Informationen zur Zertifikatsverkettung enthalten. Wenn dies allerdings der Fall ist, tritt der folgende Importfehler auf: **Das Zertifikat und der private Schlüssel für die Entschlüsselung wurden nicht gefunden.** Sie können den *Certmgr.msc* verwenden und die [Option deaktivieren](/previous-versions/aa730868(v=vs.80)), dass **alle Zertifikat beim Exportieren der PFX-Datei einbezogen werden**, um die Informationen zur Zertifikatsverkettung zu entfernen.

## <a name="sign-using-a-test-certificate"></a>Signieren mithilfe eines Testzertifikats

1. Aktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.

2. Klicken Sie zum Erstellen eines neuen Zertifikats zum Testen auf die Schaltfläche **Testzertifikat erstellen**.

3. Geben Sie im Dialogfeld **Testzertifikat erstellen** ein Kennwort ein, um das Testzertifikat zu schützen.

## <a name="generate-unsigned-manifests"></a>Generieren von unsignierten Manifesten

Das Signieren der ClickOnce-Manifeste ist für *EXE*-basierte Anwendungen optional. In den folgenden Anleitungen wird dargestellt, wie unsignierte ClickOnce-Manifeste generiert werden.

> [!IMPORTANT]
> Unsignierte Manifeste können die Entwicklung und das Testen der Anwendung vereinfachen. Unsignierte Manifeste führen in einer Produktionsumgebung jedoch zu beträchtlichen Sicherheitsrisiken. Ziehen Sie die Verwendung unsignierter Manifeste nur in Betracht, wenn die ClickOnce-Anwendung auf Computern in einem Intranet ausgeführt wird, das vollständig vom Internet oder anderen Quellen bösartigen Codes abgeschirmt ist.

Standardmäßig werden durch ClickOnce automatisch signierte Manifeste generiert, sofern nicht mindestens eine Datei ausdrücklich aus dem generierten Hash ausgeschlossen wird. Wenn alle Dateien im Hash eingeschlossen sind, werden beim Veröffentlichen der Anwendung somit signierte Manifeste erstellt. Dies gilt auch, wenn das Kontrollkästchen **ClickOnce-Manifeste signieren** deaktiviert ist.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>So generieren Sie nicht signierte Manifeste und schließen alle Dateien in den generierten Hash ein

1. Zum Generieren nicht signierter Manifeste, die alle Dateien im Hash enthalten, müssen Sie die Anwendung zunächst mit signierten Manifesten veröffentlichen. Signieren Sie daher zunächst die ClickOnce-Manifeste, indem Sie eines der oben aufgeführten Verfahren ausführen, und veröffentlichen Sie dann die Anwendung.

2. Deaktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.

3. Setzen Sie die Veröffentlichungsversion zurück, damit nur eine Version der Anwendung verfügbar ist. Standardmäßig wird die Revisionsnummer der Veröffentlichungsversion von Visual Studio bei jedem Veröffentlichen einer Anwendung automatisch erhöht. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Veröffentlichen Sie die Anwendung.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>So generieren Sie nicht signierte Manifeste und schließen eine oder mehrere Dateien aus dem generierten Hash aus

1. Deaktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.

2. Öffnen Sie das Dialogfeld **Anwendungsdateien**, und legen Sie **Hash** für die Dateien auf **Ausschließen** fest, die Sie aus dem generierten Hash ausschließen möchten.

    > [!NOTE]
    > Durch Ausschließen einer Datei aus dem Hash wird ClickOnce so konfiguriert, dass das automatische Signieren von Manifesten deaktiviert wird. Daher muss nicht zuerst mit signierten Manifesten veröffentlicht werden, wie es im vorhergehenden Verfahren der Fall war.

3. Veröffentlichen Sie die Anwendung.

## <a name="see-also"></a>Siehe auch

- [Assemblys mit starken Namen](/dotnet/framework/app-domains/strong-named-assemblies)
- [How to: Erstellen eines öffentlichen/privaten Schlüsselpaars](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Seite „Signierung“, Projekt-Designer](../ide/reference/signing-page-project-designer.md)
- [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)
