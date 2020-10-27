---
title: Dialogfeld "Erweiterte Compilereinstellungen (Visual Basic)
description: Hier erfahren Sie, wie Sie das Dialogfeld „Erweiterte Compilereinstellungen“ verwenden können, um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: ghogen
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0335ee8ef1c385da13c2043ffcfa94c264a5934a
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92137037"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogfeld "Erweiterte Compilereinstellungen (Visual Basic)

Verwenden Sie das Dialogfeld **Erweiterte Compilereinstellungen** des **Projekt-Designers** , um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben. Dieses Dialogfeld gilt nur für Visual Basic-Projekte.

## <a name="to-access-this-dialog-box"></a>So öffnen Sie das Dialogfeld

1. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappe** ) aus.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften** . Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Kompilieren** .

3. Wählen Sie auf der Seite [„Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) die **Konfiguration** und **Plattform** aus. In vereinfachten Buildkonfigurationen werden die Listen **Konfiguration** und **Plattform** nicht angezeigt. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Klicken Sie auf **Erweiterte Kompilierungsoptionen** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optimierungen

Die folgenden Optionen geben Optimierungen an, die in einigen Fällen eine Programmdatei verkleinern kann, dazu führen, dass ein Programm schneller ausgeführt wird oder den Buildprozess beschleunigen können.

**Überprüfungen auf Ganzzahlüberlauf entfernen**

Standardmäßig ist dieses Kontrollkästchen deaktiviert, um Überprüfungen auf Ganzzahlüberlauf zu aktivieren. Aktivieren Sie dieses Kontrollkästchen, um die Überprüfungen auf Ganzzahlüberlauf zu entfernen. Wenn Sie dieses Kontrollkästchen aktivieren, werden Integerberechnungen möglicherweise beschleunigt. Wenn Sie jedoch die Überprüfung auf Überlauf und Datentypkapazitäten entfernen, werden womöglich falsche Ergebnisse gespeichert, ohne dass ein Fehler ausgelöst wird.

Wenn Überlaufbedingungen überprüft werden und eine ganzzahlige Operation überläuft, wird eine <xref:System.OverflowException>-Ausnahme ausgegeben. Wenn Überlaufbedingungen nicht aktiviert werden, lösen Überläufe bei ganzzahligen Operationen keine Ausnahme aus.

**Optimierungen aktivieren**

Standardmäßig ist dieses Kontrollkästchen deaktiviert, um Compileroptimierungen zu deaktivieren. Aktivieren Sie dieses Kontrollkästchen, um Compileroptimierungen zu aktivieren. Durch Compileroptimierungen wird Ihre Ausgabedatei kleiner, schneller und effizienter. Da Optimierungen jedoch zu Neuanordnung von Code in der Ausgabedatei führen können, können Compileroptimierungen das Debuggen erschweren.

 **DLL-Basisadresse**

Dieses Textfeld zeigt die DLL-Standardbasisadresse im Hexadezimalformat an. Sie können dieses Textfeld in Klassenbibliotheks- und Steuerelementbibliotheksprojekten verwenden, um die Basisadresse anzugeben, die verwendet werden soll, wenn die DLL erstellt wird.

 **Generieren von Debuginformationen**

Wählen Sie aus der Liste **None** (Keine), **Full** (Vollständig) oder **pdb-only** (nur pdb) aus. **None** (Keine) gibt an, das keine Informationen zum Debuggen generiert werden. **Full** (Vollständig) gibt an, dass vollständige Debuginformationen generiert werden. **pdb-only** (Nur PDB-Dateien) gibt an, dass nur PDB-Debuginformationen generiert werden. Der Standardwert für diese Option ist **Full** (Vollständig).

## <a name="compilation-constants"></a>Kompilierungskonstanten

Bedingte Kompilierungskonstanten haben einen ähnlichen Effekt wie das Verwenden einer [#Const](/dotnet/visual-basic/language-reference/directives/const-directive)-Präprozessoranweisung in einer Quelldatei, außer dass Konstanten öffentlich sind und für alle Dateien im Projekt gelten. Sie können die bedingten Kompilierungskonstanten zusammen mit der Direktive [#If...Then...#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) verwenden, um Quelldateien bedingt zu kompilieren. Weitere Informationen finden Sie unter [Bedingte Kompilierung](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **DEBUG-Konstante definieren**

In der Standardeinstellung ist diese Kontrollkästchen aktiviert und gibt an, dass eine DEBUG-Konstante festgelegt werden kann.

 **TRACE-Konstante definieren**

In der Standardeinstellung ist diese Kontrollkästchen aktiviert und gibt an, dass eine TRACE-Konstante festgelegt werden kann.

 **Benutzerdefinierte Konstanten**

Geben Sie in dieses Textfeld beliebige benutzerdefinierte Konstanten für Ihre Anwendung ein. Die Einträge müssen durch Kommas getrennt sein und folgendes Format vorweisen: **Name1="Wert1",Name2="Wert2",Name3="Wert3"**

## <a name="other-settings"></a>Weitere Einstellungen

**Serialisierungsassemblys generieren**

Diese Einstellung gibt an, ob der Compiler XML-Serialisierungsassemblys erstellen wird. Serialisierungsassemblys können die Startleistung von <xref:System.Xml.Serialization.XmlSerializer> verbessern, sofern Sie diese Klasse zum Serialisieren von Typen im Code verwendet haben. Der Standardwert für diese Option ist **Auto** . **Auto** gibt an, dass nur dann Serialisierungsassemblys generiert werden, wenn Sie <xref:System.Xml.Serialization.XmlSerializer> verwendet haben, um Typen in Ihrem Code in XML zu codieren. **Aus** gibt an, dass grundsätzlich keine Serialisierungsassemblys generiert werden, unabhängig davon, ob im Code <xref:System.Xml.Serialization.XmlSerializer> verwendet wird. **Ein** gibt an, dass immer Serialisierungsassemblys generiert werden. Serialisierungsassemblys tragen den Namen `TypeName`.XmlSerializers.dll.

## <a name="see-also"></a>Siehe auch

- [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
