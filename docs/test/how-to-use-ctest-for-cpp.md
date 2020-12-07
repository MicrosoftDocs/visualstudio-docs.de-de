---
title: Verwenden von CTest für C++
description: Hier erfahren Sie, wie Sie mit CTest Tests erstellen und ausführen. Diese Komponente ist standardmäßig in die Visual Studio-IDE integriert.
ms.custom: SEO-VS-2020
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5ed713e8b216d64816abd9e25d4d84ce53c44499
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329990"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Verwenden von CTest für C++ in Visual Studio 2017 und höher

CMake (einschließlich CTest) ist standardmäßig als Komponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Wenn Sie es auf Ihrem Computer installieren müssen, öffnen Sie das Visual Studio-Installerprogramm, klicken Sie auf die Schaltfläche **Desktopentwicklung mit C++**, und klicken Sie dann auf **Ändern**. Aktivieren Sie in der Liste der Workloadkomponenten **CMake-Tools für Windows**.

## <a name="to-write-tests"></a>Schreiben von Tests

Die CMake-Unterstützung in Visual Studio umfasst nicht das Visual Studio-Projektsystem. Aus diesem Grund können Sie CTest-Tests auf dieselbe Weise wie in einer CMake-Umgebung schreiben und konfigurieren. Verwenden Sie den Befehl `enable_testing()`, um Tests zu aktivieren, und den Befehl `add_test()` oder `gtest_discover_tests()`, um einen neuen Test hinzuzufügen. Weitere Informationen zu CTest finden Sie in der [CMake-Dokumentation](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Weitere Informationen zu CMake in Visual Studio finden Sie unter [CMake-Projekte in Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Ausführen von Tests

CTest ist vollständig im **Test-Explorer** integriert und unterstützt außerdem die Komponententestframeworks von Google und Boost. Diese Frameworks sind standardmäßig als Komponenten in der Workload **Desktopentwicklung mit C++** enthalten. Wenn Sie jedoch ein Projekt aus einer älteren Version von Visual Studio aktualisieren, müssen Sie diese Frameworks möglicherweise mithilfe des Visual Studio-Installer installieren.

Die folgende Abbildung zeigt die Ergebnisse eines CTest-Durchlaufs, der mit einem Google-Testframework ausgeführt wurde:

![CTest mit Google Test-Framework in Visual Studio](media/ctest-test-explorer.png)

Wenn Sie CTest, aber nicht die Google- oder Boost-Adapter verwenden, sehen Sie die Ergebnisse auf der CTest-Ebene statt auf der Ebene der einzelnen Testmethoden. Sie können ausführbare CTest-Dateien debuggen und diese durchlaufen, aber Stapelüberwachungen für einzelne Tests werden nicht unterstützt.

## <a name="see-also"></a>Siehe auch

- [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)
