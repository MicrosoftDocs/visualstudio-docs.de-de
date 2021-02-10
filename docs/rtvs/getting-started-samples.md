---
title: R-Beispielprojekte
description: Ein Index einer Sammlung von Beispielen für den Einstieg in R und Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0ed322a03d056f72ac2246e96d3aaeefa8f557c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967019"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Beispielprojekte für R Tools für Visual Studio

Mit dieser Sammlung von Beispielen können Sie mit R, R Tools für Visual Studio (RTVS) und Microsoft Machine Learning Server beginnen:

1. Laden Sie die [ZIP-Beispieldatei](https://github.com/Microsoft/RTVS-docs/archive/master.zip) herunter, und extrahieren Sie sie in einem Ordner Ihrer Wahl.
1. Öffnen Sie `examples/Examples.sln`, um zwei Ordner im Projekt anzuzeigen:

    - *Erster Einblick in R* enthält einfache Anleitungen für Einsteiger in R.
    - *MRS and Machine Learning* enthält Beispiele zur Verwendung von R und Microsoft Machine Learning Server für das maschinelle Lernen.

## <a name="a-first-look-at-r"></a>Erster Einblick in R

Dieses Beispiel bietet eine detaillierte Einführung in R über die umfangreichen Kommentare in den zwei Quelldateien. Um die beste Erfahrung zu erzielen, platzieren Sie den Cursor auf der Datei und drücken Sie STRG+EINGABETASTE, um den Code zeilenweise an das **R Interactive**-Fenster zu senden. (Zeilen, die Pakete installieren, können zum Abschließen ein oder zwei Minuten benötigen.)

- `1-Getting Started with R.R` deckt viele Grundlagen von R ab, einschließlich die Verwendung von Paketen, das Laden und Analysieren von Daten und das Zeichnen.

    ![Beispielausgabe des Beispiels „1-Getting Started with R.R“](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` führt das „ggplot2“-Grafikpaket ein, das für seine visuell ansprechenden Zeichnungen und die einfache Syntax bekannt ist. Diese Beispiel stellt Erdbebendaten aus Fiji visuell dar.

    ![Beispielausgabe aus dem Beispiel „2-Introduction to ggplot2.R“](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server und maschinelles Lernen

Diese Sammlung von Beispielen zeigt, wie Sie R zum Erstellen von Modellen für das maschinelle Lernen verwenden und wie Sie von [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server) profitieren können.

Öffnen Sie die Datei wie gewohnt, setzen Sie den Cursor an den Anfang, und durchlaufen Sie den Code dann Zeile für Zeile mit **STRG**+**EINGABETASTE**. Die Markdowndateien in jedem Ordner enthalten ebenfalls weitere Details.

- `Benchmarks` führt eine Reihe intensiver, paralleler, linearer Algebraberechnungen aus, um die Leistungssteigerungen darzustellen, die mithilfe der Verwendung von Microsoft R Open und der Intel Math Kernel Library (MLK) ermöglicht werden. Mit simulierten Daten vergleichen die Benchmarks speziell Matrix Berechnungen in einem Thread im Vergleich zu zwei.

    ![Benchmark-Beispielzeichnung](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` erstellt ein Vorhersagemodell für die Nachfrage mithilfe von Microsoft ML Server für Fahrradverleihe, die auf Verlaufsdaten basieren.

- `Data_Exploration` enthält drei Skripts:

  - `Import Data from URL.R` zeigt, wie eine durch die URL identifizierte Datendatei in R geladen wird.
  - `Import Data from URL to xdf.R` zeigt, wie Sie eine durch die URL identifizierte Datendatei als XDF in Microsoft ML Server laden.
  - `Using ggplot2.R` ist eine Erweiterung des `A First Look at R/2-Introduction to ggplot2.R`-Beispiels, das Ihnen einen tieferen Einblick in die Funktionalität von „ggplot2.R“ bietet, einschließlich des interaktiven 3D-Zeichnens.

      ![Ausgabe eines „ggplot2.R“-Beispiels](media/samples-3d-interactive.png)

- `Datasets` enthält drei *CSV*-Dateien, die von anderen Beispielen verwendet werden.
- `Flight_Delays_Prediction_with_R` und `Flight_Delays_Prediction_with_MRS` zeigen, wie Verspätungen bei Flügen mithilfe von R, des maschinellen Lernens sowie mithilfe der historischen Echtzeitleistung und Wetterdaten vorhergesagt werden.
- `Machine learning` enthält drei Beispiele für das Erlernen der Vorhersage von Flugverspätungen, Immobilienpreisen und Fahrradvermietungen. Zusammen veranschaulichen diese Beispiele die Anwendung von R und Microsoft Machine Learning Server auf reale Probleme. Es wird auch gezeigt, wie Sie mehrere beliebte Modelle für das maschinelle Lernen verwenden können und diese als Azure-Webdienst mithilfe eines [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/)-Arbeitsbereichs bereitstellen können.

- `R_MRO_MRS_Comparison` ist ein Vergleich mit sechs Teilen, der die Ähnlichkeiten und Unterschiede von R, Microsoft R Open und Microsoft ML Server mit Befehlen, Syntax, Konstrukten und Leistung darstellt.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Was ist so besonders an Microsoft R Open und Microsoft ML Server?

[Microsoft R Open](https://mran.revolutionanalytics.com/download/), die Verteilung von R von Microsoft, unterscheidet sich in zwei wichtigen Punkten von [CRAN R](https://cran.r-project.org/):

1. [Bessere Rechnungsleistung](https://mran.revolutionanalytics.com/rro/#intelmkl1) unter Verwendung der [Intel Math Kernel Libraries](https://software.intel.com/intel-mkl). Diese Bibliotheken sind als kostenloser Download unter Microsoft für die Verwendung mit Microsoft R Open erhältlich.

1. [Reproduzierbares R-Toolkit](https://mran.revolutionanalytics.com/rro/#reproducibility) stellt sicher, dass die Bibliotheken, die Sie zum Erstellen Ihres R-Programms verwendet haben, immer für andere Personen verfügbar sind, die Ihre Arbeit reproduzieren möchten.

[Microsoft ML Server (MLS)](/machine-learning-server/what-is-machine-learning-server) ist eine Erweiterung von R, mit der Sie mehr Daten schneller verarbeiten können. R enthält dadurch zwei leistungsstarke Funktionen:

1. Größere Datasets ohne RAM-Einschränkungen. ML Server kann out-of-memory-Daten aus einer Vielzahl von Quellen verarbeiten, einschließlich Hadoop-Clustern, -Datenbanken und -Data Warehouses.

1. Parallele Mehrkernverarbeitung. MLS kann Berechnungen effektiv über alle verfügbaren Berechnungsressourcen verteilen. MLS erhält auf Ihrer persönlichen Arbeitsstation oder einem Remotecluster schneller eine Antwort.

Der folgende Vergleich zeigt, dass MLS und MRO mit MKL eine weitaus bessere Berechnungsleistung im Zusammenhang mit bestimmten Matrixberechnungen im Vergleich zu R und MRO ohne MKL haben. In dieser Berechnung werden simulierte Daten verwendet:

![Vergleich von MLS und MRO mit MKL zu R und MRO ohne MKL](media/samples-speed-comparison.png)

Einen technischen Vergleich von R mit MRO und MLS finden Sie in der [detaillierten Diskussion von Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) zu diesem Thema.

In der folgenden Abbildung wird dann die verstrichene Zeit in Sekunden verglichen, die zum Erstellen von logistischen Regressionsmodellen verwendet wird, um Flugverspätungen von mehr als 15 Minuten vorherzusagen.  Die verstrichene Zeit, die in CRAN R verwendet wird, erhöht sich signifikant, wenn eine niedrige Anzahl von Zeilen erhöht wird, während MLS nur etwa zweimal erhöht wird. Weitere Informationen zu diesem Benchmark finden Sie im Beispiel *Benchmarks/rxGlm_benchmark.R*.

![„rxGlm“-Benchmark](media/samples-rxGLM-benchmark.png)
