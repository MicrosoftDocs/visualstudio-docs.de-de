---
title: IPython REPL (Interaktives Fenster)
description: Verwenden des interaktiven Visual Studio-Fensters im IPython-Modus als benutzerfreundliche interaktive Entwicklungsumgebung mit Funktionen für interaktives paralleles Computing.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e53ef96ad8fab8b26f04ccd5f7f0488d1f0d6985
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974080"
---
# <a name="use-ipython-in-the-interactive-window"></a>Verwenden von IPython im interaktiven Fenster

Das **interaktive** Visual Studio-Fenster im IPython-Modus ist eine erweiterte, benutzerfreundliche und interaktive Entwicklungsumgebung, die über Interactive Parallel Computing-Features verfügt. Dieser Artikel führt Sie durch die Verwendung von IPython im **interaktiven** Visual Studio-Fenster. In diesem sind alle regulären Features des [interaktiven](python-interactive-repl-in-visual-studio.md) Fensters ebenfalls verfügbar.

Für diese exemplarische Vorgehensweise muss die [Anaconda](https://www.continuum.io)-Umgebung installiert sein, die IPython und die benötigten Bibliotheken enthält.

> [!Note]
> IronPython unterstützt IPython nicht, obwohl Sie es auf dem Formular **Interactive-Optionen** auswählen können. Weitere Informationen finden Sie unter [Funktionsanforderung](https://github.com/Microsoft/PTVS/issues/84).

1. Öffnen Sie Visual Studio, wechseln Sie zum Fenster **Python-Umgebungen**  (**Ansicht** > **Weitere Fenster** > **Python-Umgebungen**), und wählen Sie eine Anaconda-Umgebung aus.

2. Überprüfen Sie die Registerkarte **Pakete (Conda)** (die als **pip** oder **Pakete** angezeigt werden kann) für diese Umgebung, um sicherzustellen, dass `ipython` und `matplotlib` aufgeführt sind. Wenn dies nicht der Fall ist, installieren Sie sie hier. (Weitere Informationen finden Sie unter [Fenster „Python-Umgebungen“ auf der Registerkarte „Pakete“](python-environments-window-tab-reference.md).)

3. Wählen Sie die Registerkarte **Übersicht** aus, und klicken Sie auf **Interaktiven IPython-Modus verwenden**. (Wählen Sie in Visual Studio 2015 **Interaktive Optionen konfigurieren** aus, um das Dialogfeld **Optionen** zu öffnen. Legen Sie anschließend den **Interaktiven Modus** auf **IPython** fest, und klicken Sie auf **OK**.)

4. Klicken Sie auf **Interaktives Fenster öffnen**, um das **interaktive** Fenster im IPython-Modus aufzurufen. Sie müssen das Fenster eventuell zurücksetzen, wenn Sie gerade den interaktiven Modus geändert haben. Gegebenenfalls müssen Sie die **EINGABETASTE** drücken, wenn nur eine >>>-Eingabeaufforderung angezeigt wird, damit eine Eingabeaufforderung wie **In [2]** angezeigt wird.

    ![Das interaktive Fenster im IPython-Modus](media/ipython-repl-03.png)

5. Geben Sie den folgenden Code ein:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Nach Eingabe der letzten Zeile sollte ein Inlinediagramm angezeigt werden (dessen Größe Sie bei Bedarf ändern können, indem Sie an der unteren rechten Ecke ziehen).

    ![Inlinediagramm im interaktiven Fenster](media/ipython-repl-04.png)

7. Statt den Code in die REPL einzugeben, können Sie ihn im Editor schreiben, ihn auswählen, mit der rechten Maustaste klicken und den Befehl **An interaktives Fenster senden** auswählen (oder **STRG**+**EINGABETASTE** drücken). Versuchen Sie, den folgenden Code in eine neue Datei im Editor einzufügen, indem sie ihn mit **STRG**+**A** auswählen und anschließend an das **interaktive** Fenster senden. (Visual Studio sendet den Code als Einheit, um zu vermeiden, dass Sie temporäre oder unvollständige Diagramme erhalten. Visual Studio öffnet ein **interaktives** Fenster für die Umgebung, die im Fenster **Python-Umgebungen** als Standardeinstellung festgelegt ist, wenn Sie gerade kein Python-Projekt mit einer anderen Umgebung geöffnet haben.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Senden von Code aus dem Editor an das interaktive Fenster](media/ipython-repl-05.png)

8. Wenn die Diagramme außerhalb des **interaktiven** Fensters angezeigt werden sollen, führen Sie den Code stattdessen mit dem Befehl **Debuggen** > **Starten ohne Debuggen** aus.

IPython verfügt über viele weitere nützliche Features, wie z.B. Escapevorgang zur Shell des Betriebssystems, Variablenersetzung, Ausgabenerfassung usw. Weitere Informationen finden Sie in der [IPython documentation (IPython Dokumentation)](https://ipython.org/documentation.html).

## <a name="see-also"></a>Siehe auch

- Die [Data Science Virtual Machine von Azure](/azure/machine-learning/data-science-virtual-machine/overview) ist für die Ausführung von Jupyter-Notebooks zusammen mit einer großen Bandbreite anderer Data Science-Tools vorkonfiguriert.
