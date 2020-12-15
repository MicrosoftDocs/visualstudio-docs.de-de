---
title: 'Exemplarische Vorgehensweise: Erstellen eines Legacy sprach dienstangangs | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie mit den Managed Package Framework-Sprachklassen einen Sprachdienst in Visual c# implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fcc4004542f9a566d6c6bfa820cbb8c2e1846fa
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487932"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts
Die Verwendung der MPF-Sprachklassen (Managed Package Framework) zum Implementieren eines sprach Dienstanbieter in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ist unkompliziert. Sie benötigen ein VSPackage, um den Sprachdienst, den Sprachdienst und einen Parser für Ihre Sprache zu hosten.

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Stellen für die VSPackage-Projektvorlage
 Die Projektvorlage für das Visual Studio-Paket finden Sie an drei verschiedenen Vorlagen Positionen im Dialogfeld **Neues Projekt** :

1. Unter Visual Basic-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.

2. Unter C#-Erweiterungen. Die Standardsprache des Projekts ist C#.

3. Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C++.

### <a name="create-a-vspackage"></a>Erstellen eines VSPackages

1. Erstellen Sie ein neues VSPackage mit der Projektvorlage für das Visual Studio-Paket.

    Wenn Sie einem vorhandenen VSPackage einen Sprachdienst hinzufügen, überspringen Sie die folgenden Schritte, und wechseln Sie direkt zum Verfahren "Erstellen der Sprachdienst Klasse".

2. Geben Sie MyLanguagePackage als Namen für das Projekt ein, und klicken Sie auf **OK**.

    Sie können den gewünschten Namen verwenden. Diese Prozeduren werden hier als Name von MyLanguagePackage angenommen.

3. Wählen Sie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] als Sprache und die Option zum Generieren einer neuen Schlüsseldatei aus. Klicken Sie auf **Weiter**.

4. Geben Sie die entsprechenden Unternehmens-und Paketinformationen ein. Klicken Sie auf **Weiter**.

5. Wählen Sie **Menübefehl** aus. Klicken Sie auf **Weiter**.

    Wenn Sie keine Code Ausschnitte unterstützen möchten, klicken Sie einfach auf Fertigstellen, und ignorieren Sie den nächsten Schritt.

6. Geben Sie **Ausschnitt einfügen** als **Befehlsnamen** und als `cmdidInsertSnippet` Befehls- **ID** ein. Klicken Sie auf **Fertig stellen**.

    Der **Befehls Name** und die **Befehls-ID** können von Ihnen stammen, dies sind nur Beispiele.

### <a name="create-the-language-service-class"></a>Erstellen der Sprachdienst Klasse

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt MyLanguagePackage, wählen Sie **Hinzufügen**, **Verweis** aus, und wählen Sie dann die Schaltfläche **neuen Verweis hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.net** den Eintrag **Microsoft. VisualStudio. Package. LanguageService** aus, und klicken Sie auf **OK**.

     Dies muss nur einmal für das Sprachpaket Projekt durchgeführt werden.

3. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **Hinzufügen**, **Klasse** aus.

4. Stellen Sie sicher, dass in der Liste Vorlagen die Option **Klasse** ausgewählt ist.

5. Geben Sie **MyLanguageService.cs** als Namen der Klassendatei ein, und klicken Sie auf **Hinzufügen**.

     Sie können den gewünschten Namen verwenden. Diese hier beschriebenen Prozeduren werden `MyLanguageService` als Name angenommen.

6. Fügen Sie in der Datei MyLanguageService.cs die folgenden `using` Direktiven hinzu.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Ändern `MyLanguageService` Sie die Klasse, sodass Sie von der-Klasse abgeleitet wird <xref:Microsoft.VisualStudio.Package.LanguageService> :

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Positionieren Sie den Cursor auf "LanguageService", und wählen Sie im Menü **Bearbeiten**, **IntelliSense** die Option **abstrakte Klasse implementieren** aus. Dadurch werden die minimal erforderlichen Methoden zum Implementieren einer Sprachdienst Klasse hinzugefügt.

9. Implementieren Sie die abstrakten Methoden, wie unter [Implementieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/implementing-a-legacy-language-service2.md)beschrieben.

### <a name="register-the-language-service"></a>Registrieren des sprach Dienstanbieter

1. Öffnen Sie die Datei MyLanguagePackagePackage.cs, und fügen Sie die folgenden `using` Anweisungen hinzu:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registrieren Sie Ihre Sprachdienst Klasse wie unter [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service1.md)beschrieben. Dies umfasst die providexx-Attribute und die Abschnitte "Bereitstellen des sprach Dienstanbieter". Verwenden Sie MyLanguageService, wenn in diesem Thema testlanguageservice verwendet wird.

### <a name="the-parser-and-scanner"></a>Parser und Scanner

1. Implementieren Sie einen Parser und einen Scanner für Ihre Sprache, wie in [Legacy Sprachdienst Parser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)beschrieben.

     Wie Sie Ihren Parser und Scanner implementieren, ist vollkommen für Sie und geht über den Rahmen dieses Themas hinaus.

## <a name="language-service-features"></a>Sprachdienst Features
 Um die einzelnen Features im Sprachdienst zu implementieren, leiten Sie in der Regel eine Klasse von der entsprechenden MPF-Sprachdienst Klasse ab, implementieren alle abstrakten Methoden nach Bedarf und überschreiben die entsprechenden Methoden. Welche Klassen Sie erstellen und/oder davon ableiten, hängt von den Funktionen ab, die Sie unterstützen möchten. Diese Features werden ausführlich in Funktionen von [Legacy Sprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)erläutert. Das folgende Verfahren ist der allgemeine Ansatz für das Ableiten einer Klasse von den MPF-Klassen.

#### <a name="deriving-from-an-mpf-class"></a>Ableiten von einer MPF-Klasse

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **Hinzufügen**, **Klasse** aus.

2. Stellen Sie sicher, dass in der Liste Vorlagen die Option **Klasse** ausgewählt ist.

     Geben Sie einen geeigneten Namen für die Klassendatei ein, und klicken Sie auf **Hinzufügen**.

3. Fügen Sie in der neuen Klassendatei die folgenden `using` Direktiven hinzu.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Ändern Sie die Klasse, sodass Sie von der gewünschten MPF-Klasse abgeleitet wird.

5. Fügen Sie einen Klassenkonstruktor hinzu, der mindestens die gleichen Parameter wie der Basisklassenkonstruktor annimmt, und übergeben Sie die Konstruktorparameter an den Basisklassenkonstruktor.

     Der Konstruktor für eine Klasse, die von der-Klasse abgeleitet wird, könnte beispielsweise <xref:Microsoft.VisualStudio.Package.Source> wie folgt aussehen:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Wählen Sie im Menü **Bearbeiten**, **IntelliSense** die Option **abstrakte Klasse implementieren** aus, wenn die Basisklasse über abstrakte Methoden verfügt, die implementiert werden müssen.

7. Positionieren Sie andernfalls die Einfügemarke innerhalb der Klasse, und geben Sie die Methode ein, die überschrieben werden soll.

     Geben Sie beispielsweise `public override` ein, um eine Liste aller Methoden anzuzeigen, die in dieser Klasse überschrieben werden können.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)
