---
title: Erstellen eines Auslastungstest-Plug-Ins
description: Lernen Sie, ein Auslastungstest-Plug-In zu erstellen, um Code während der Ausführung des Auslastungstests zu unterschiedlichen Zeiten auszuführen, was die Funktionalität des Auslastungstests erweitern oder ändern kann.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f8ba810665bce520b82777512b396a693e580a0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878005"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Vorgehensweise: Erstellen eines Auslastungstest-Plug-Ins

Sie können ein Auslastungstest-Plug-In erstellen, um während des Auslastungstests Code zu verschiedenen Zeitpunkten auszuführen. Mithilfe von erstellten Plug-Ins können die integrierten Funktionen des Auslastungstests erweitert oder bearbeitet werden. Sie können z. B. Code für ein Auslastungstest-Plug-In schreiben, um während der Ausführung des Auslastungstests das Testmuster festzulegen oder zu bearbeiten. Hierzu müssen Sie eine Klasse erstellen, die von der <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>-Schnittstelle erbt. Diese Klasse muss die <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*>-Methode dieser Schnittstelle implementieren. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Sie können auch Plug-Ins für Webleistungstests erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Webleistungstest-Plug-Ins](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>So erstellen Sie ein Auslastungstest-Plug-In in C#
<!-- markdownlint-enable MD003 MD020 -->

1. Öffnen Sie ein Webleistungs- und Auslastungstestprojekt, das einen Webleistungstest enthält.

2. Fügen Sie dem Testprojekt einen Auslastungstest hinzu, und konfigurieren Sie ihn für die Ausführung eines Webleistungstests.

     Weitere Informationen finden Sie unter [Schnellstart: Erstellen eines Auslastungstestprojekts](../test/quickstart-create-a-load-test-project.md).

3. Fügen Sie der Projektmappe ein neues **Klassenbibliotheksprojekt** hinzu. (Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** und anschließend **Neues Projekt** aus.)

4. Klicken Sie im **Projektmappen-Explorer** in der neuen Klassenbibliothek mit der rechten Maustaste auf den Ordner **Verweise**, und wählen Sie **Verweis hinzufügen** aus.

   Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

5. Klicken Sie auf die Registerkarte **.NET**, scrollen Sie nach unten, und wählen Sie dann **Microsoft.VisualStudio.QualityTools.LoadTestFramework** aus.

6. Klicken Sie auf **OK**.

   Der Verweis auf **Microsoft.VisualStudio.QualityTools.LoadTestFramework** wird zum Ordner **Verweis** im **Projektmappen-Explorer** hinzugefügt.

7. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den obersten Knoten des Webleistungs- und Auslastungstestprojekts, das den Auslastungstest enthält, zu dem Sie das Plug-In für Auslastungstests hinzufügen möchten. Klicken Sie anschließend auf **Verweis hinzufügen**.

   Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

8. Klicken Sie auf die Registerkarte **Projekte**, und wählen Sie das Klassenbibliotheksprojekt aus.

9. Klicken Sie auf **OK**.

10. Fügen Sie im **Code-Editor** eine `using`-Anweisung für den <xref:Microsoft.VisualStudio.TestTools.LoadTesting>-Namespace hinzu.

11. Implementieren Sie die <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>-Schnittstelle für die Klasse, die im Klassenbibliotheksprojekt erstellt wurde. Beachten Sie hierzu die Beispielimplementierung im folgenden Abschnitt.

12. Nachdem Sie den Code verfasst haben, erstellen Sie das neue Projekt.

13. Klicken Sie mit der rechten Maustaste auf den obersten Knoten des Auslastungstests, und klicken Sie anschließend auf **Auslastungstest-Plug-In hinzufügen**.

     Das Dialogfeld **Auslastungstest-Plug-In hinzufügen** wird angezeigt.

14. Wählen Sie unter **Plug-In auswählen** die Klasse des Auslastungstest-Plug-Ins aus.

15. Legen Sie im Bereich **Eigenschaften für das ausgewählte Plug-In** die Anfangswerte fest, die das Plug-In zur Laufzeit verwenden soll.

    > [!NOTE]
    > Sie können beliebig viele Plug-In-Eigenschaften verfügbar machen. Die Eigenschaften müssen dazu lediglich öffentlich, festlegbar und von einem Basistyp (z. B. "Integer", "Boolean" oder "String") sein. Sie können die Eigenschaften des Webleistungstest-Plug-Ins auch zu einem späteren Zeitpunkt im Fenster **Eigenschaften** ändern.

16. Klicken Sie auf **OK**.

     Das Plug-In wird dem Ordner **Auslastungstest-Plug-Ins** hinzugefügt.

    > [!WARNING]
    > Möglicherweise erhalten Sie eine Fehlermeldung wie die folgende, wenn Sie einen Webleistungstest oder einen Auslastungstest ausführen, der das Plug-In verwendet:
    >
    > **Fehler bei der Anforderung: Ausnahme im Ereignis \<plug-in>: Die Datei oder Assembly '\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' oder eine ihrer Abhängigkeiten konnte nicht geladen werden. Das System konnte die angegebene Datei nicht finden.**
    >
    > Ein solcher Fehler wird verursacht, wenn Sie an einem der Plug-Ins Codeänderungen vornehmen und eine neue DLL-Version **(Version=0.0.0.0)** erstellen, während das Plug-In weiterhin auf die ursprüngliche Plug-In-Version verweist. Um dieses Problem zu beheben, führen Sie folgende Schritte aus:
    >
    > 1. Im Webleistungs- und Auslastungstestprojekt wird in Verweisen eine Warnung angezeigt. Entfernen Sie den Verweis auf die Plug-In-DLL, und fügen Sie ihn wieder hinzu.
    > 2. Entfernen Sie das Plug-In aus dem Test oder vom entsprechenden Speicherort, und fügen Sie es dann wieder hinzu.

## <a name="example"></a>Beispiel

Im folgenden Code wird ein Auslastungstest-Plug-In dargestellt, das nach dem Auftreten eines LoadTestFinished-Ereignisses benutzerdefinierten Code ausführt. Wenn dieser Code auf einem Test-Agent auf einem Remotecomputer ausgeführt wird und der Test-Agent nicht über einen localhost-SMTP-Dienst verfügt, wird für den Auslastungstest der Status "In Bearbeitung" beibehalten, und es wird eine Meldung angezeigt.

> [!NOTE]
> Für den folgenden Code müssen Sie einen Verweis auf System.Windows.Forms hinzufügen.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Es gibt acht Ereignisse, die bei einem Auslastungstest auftreten und im Auslastungstest-Plug-In behandelt werden können, um benutzerdefinierten Code während eines Auslastungstests auszuführen. Im Folgenden werden die Ereignisse aufgelistet, die einen Zugriff auf verschiedene Phasen des Auslastungstestlaufs ermöglichen:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [How to: Erstellen eines Webleistungstest-Plug-Ins](../test/how-to-create-a-web-performance-test-plug-in.md)
