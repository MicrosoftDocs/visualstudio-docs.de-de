---
title: 'Gewusst wie: Verwenden von Assistenten mit Projektvorlagen'
description: Erfahren Sie, wie Sie die IWizard-Schnittstelle im Visual Studio SDK verwenden, die es Ihnen ermöglicht, benutzerdefinierten Code auszuführen, wenn ein Benutzer ein Projekt aus einer Vorlage erstellt.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21e0e35b43fc3b94a8d029c97f56bd573ebac95f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996369"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Gewusst wie: Verwenden von Assistenten mit Projektvorlagen

Visual Studio stellt die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle bereit, die, falls sie implementiert ist, das Ausführen von benutzerdefiniertem Code beim Erstellen eines Projekts aus einer Vorlage ermöglicht.

Die Anpassung der Projektvorlage kann verwendet werden, um eine benutzerdefinierte Benutzeroberfläche anzuzeigen, die Benutzereingaben sammelt, um die Vorlage anzupassen, zusätzliche Dateien zur Vorlage hinzuzufügen oder eine beliebige andere Aktion, die für ein Projekt zulässig ist.

Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstellen Methoden werden zu verschiedenen Zeitpunkten aufgerufen, während das Projekt erstellt wird, sobald der Benutzer im Dialogfeld **Neues Projekt** auf **OK** klickt. Die Namen der einzelnen Methoden der Schnittstelle beschreiben jeweils den Zeitpunkt, zu dem sie aufgerufen werden. Visual Studio ruft z. b. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> sofort auf, wenn das Projekt erstellt wird, sodass es einen guten Speicherort zum Schreiben von benutzerdefiniertem Code zum Erfassen von Benutzereingaben ist.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Erstellen eines Projektvorlagen Projekts mit einem VSIX-Projekt

Sie beginnen mit dem Erstellen einer benutzerdefinierten Vorlage mit dem Projektvorlagen Projekt, das Bestandteil des Visual Studio SDK ist. In diesem Verfahren verwenden wir ein c#-Projektvorlagen Projekt, aber es gibt auch ein Projektvorlagen Projekt Visual Basic. Dann fügen Sie der Projekt Mappe, die das Projektvorlagen Projekt enthält, ein VSIX-Projekt hinzu.

1. Erstellen Sie ein c#-Projektvorlagen Projekt (Wählen Sie in Visual Studio **Datei**  >  **neu**  >  **Projekt** aus, und suchen Sie nach "Projektvorlage"). Nennen Sie Sie **MyProjectTemplate**.

   > [!NOTE]
   > Möglicherweise werden Sie aufgefordert, das Visual Studio SDK zu installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Fügen Sie ein neues VSIX-Projekt in derselben Projekt Mappe wie das Projektvorlagen Projekt hinzu (Wählen Sie in **Projektmappen-Explorer** den Knoten Projekt Mappe aus, klicken Sie mit der rechten Maustaste, und wählen Sie neues Projekt **Hinzufügen**  >  **New Project** aus, und suchen Sie nach "VSIX". Nennen Sie Sie **myprojectwizard.**

3. Legen Sie das VSIX-Projekt als Startprojekt fest. Wählen Sie in **Projektmappen-Explorer** den Knoten VSIX-Projekt aus, klicken Sie mit der rechten Maustaste, und wählen Sie **als Startprojekt festlegen** aus.

4. Fügen Sie das Vorlagen Projekt als Medienobjekt des VSIX-Projekts hinzu. Suchen Sie in **Projektmappen-Explorer** unter dem VSIX-Projekt Knoten nach der Datei " *Source. Extension. vsixmanifest* ". Doppelklicken Sie darauf, um Sie im Manifest-Editor zu öffnen.

5. Wählen Sie im Manifest-Editor die Registerkarte **Assets** auf der linken Seite des Fensters aus.

6. Wählen Sie auf der Registerkarte **Objekte** die Option **neu** aus. Wählen Sie im Fenster **Neues Objekt hinzufügen** für das Feld Typ den Eintrag **Microsoft. VisualStudio. ProjectTemplate** aus. Wählen Sie im Feld **Quelle** **ein Projekt in der aktuellen Projekt Mappe aus**. Wählen Sie im Feld **Projekt** den Wert **MyProjectTemplate** aus. Klicken Sie dann auf **OK**.

7. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio wird geöffnet. (Dies kann einige Minuten dauern.)

8. Versuchen Sie in der zweiten Instanz von Visual Studio, ein neues Projekt mit der neuen Vorlage zu erstellen (**Datei**  >  **neu**  >  **Projekt**, suchen Sie nach "MyProject"). Das neue Projekt sollte mit einer Klasse mit dem Namen **Class1** angezeigt werden. Sie haben jetzt eine benutzerdefinierte Projektvorlage erstellt. Das Debugging wird jetzt beendet.

## <a name="create-a-custom-template-wizard"></a>Assistent zum Erstellen einer benutzerdefinierten Vorlage

In diesem Verfahren wird gezeigt, wie Sie einen benutzerdefinierten Assistenten erstellen, der vor der Erstellung des Projekts ein Windows Form öffnet. Das Formular ermöglicht Benutzern das Hinzufügen eines benutzerdefinierten Parameter Werts, der dem Quellcode während der Projekt Erstellung hinzugefügt wird.

1. Richten Sie das VSIX-Projekt ein, damit eine Assembly erstellt werden kann.

2. Wählen Sie in **Projektmappen-Explorer** den Knoten VSIX-Projekt aus. Unten **Projektmappen-Explorer** sollte das Fenster **Eigenschaften** angezeigt werden. Wenn dies nicht der Fall ist **View**, wählen Sie  >  **Eigenschaften Fenster** anzeigen aus, oder drücken Sie **F4**. Wählen Sie im Fenster **Eigenschaften** die folgenden Felder aus `true` :

   - **Assembly in VSIX-Container einschließen**

   - **Debugsymbole in VSIX-Container einschließen**

   - **Debugsymbole in lokale VSIX-Bereitstellung einschließen**

3. Fügen Sie die Assembly als Medienobjekt zum VSIX-Projekt hinzu. Öffnen Sie die Datei " *Source. Extension. vsixmanifest* ", und wählen Sie die Registerkarte **Objekte** aus. Wählen Sie im Fenster **Neues Objekt hinzufügen** für **Typ** die Option **Microsoft. VisualStudio. Assembly** aus, wählen Sie für **Quelle** **ein Projekt in der aktuellen Projekt** Mappe aus, und wählen Sie für **Projekt** den Eintrag **myprojectwizard** aus.

4. Fügen Sie dem VSIX-Projekt die folgenden Verweise hinzu. (Klicken Sie in **Projektmappen-Explorer** unter dem Knoten VSIX-Projekt auf **Verweise**, klicken Sie mit der rechten Maustaste, und wählen Sie **Verweis hinzufügen** aus.) Suchen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Framework** die Assembly **System. Windows Forms** , und wählen Sie Sie aus. Suchen und wählen Sie außerdem die **System** -und **System. Drawing** -Assemblys aus. Wählen Sie nun die Registerkarte **Erweiterungen** aus. Suchen Sie die Assembly **EnvDTE** , und wählen Sie Sie aus. Suchen Sie außerdem die Assembly **Microsoft. VisualStudio. templatewizardinterface** , und wählen Sie Sie aus. Klicken Sie auf **OK**.

5. Fügen Sie dem VSIX-Projekt eine Klasse für die Implementierung des Assistenten hinzu. (Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den VSIX-Projekt Knoten, und wählen Sie **Hinzufügen**, **Neues Element** und dann **Klasse** aus.) Nennen Sie die Klasse **wizardimplementation**.

6. Ersetzen Sie den Code in der Datei *WizardImplementationClass.cs* durch den folgenden Code:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    Das **UserInputForm** -Element, auf das in diesem Code verwiesen wird, wird später implementiert.

    Die `WizardImplementation`-Klasse enthält Methodenimplementierungen für alle Member von <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. In diesem Beispiel führt nur die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode eine Aufgabe aus. Alle anderen Methoden bleiben entweder ohne Wirkung oder geben `true` zurück.

    Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode nimmt vier Parameter an:

   - Einen <xref:System.Object>-Parameter, der in das <xref:EnvDTE._DTE>-Stammobjekt umgewandelt werden kann, um die Anpassung des Projekts zu ermöglichen.

   - Einen <xref:System.Collections.Generic.Dictionary%602>-Parameter, der eine Auflistung aller vordefinierten Parameter in der Vorlage enthält. Weitere Informationen zu Vorlagen Parametern finden Sie unter [Vorlagen Parameter](../ide/template-parameters.md).

   - Einen <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>-Parameter, der Informationen zur Art der verwendeten Vorlage enthält.

   - Ein <xref:System.Object> Array, das eine Reihe von Parametern enthält, die von Visual Studio an den Assistenten übermittelt werden.

     In diesem Beispiel wird dem <xref:System.Collections.Generic.Dictionary%602>-Parameter ein Parameterwert aus dem Benutzereingabeformular hinzugefügt. Jede Instanz des `$custommessage$`-Parameters im Projekt wird durch den vom Benutzer eingegebenen Text ersetzt.

7. Erstellen Sie jetzt das **UserInputForm**. Fügen Sie in der Datei *WizardImplementation.cs* nach dem Ende der-Klasse den folgenden Code hinzu `WizardImplementation` .

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Das Benutzereingabeformular stellt ein einfaches Formular zur Eingabe eines benutzerdefinierten Parameters bereit. Das Formular enthält ein Textfeld mit dem Namen `textBox1` und eine Schaltfläche mit dem Namen `button1`. Wenn auf die Schaltfläche geklickt wird, wird der Text aus dem Textfeld im `customMessage`-Parameter gespeichert.

## <a name="connect-the-wizard-to-the-custom-template"></a>Verbinden des Assistenten mit der benutzerdefinierten Vorlage

Damit Ihre benutzerdefinierte Projektvorlage den benutzerdefinierten Assistenten verwenden kann, müssen Sie die Assistenten-Assembly signieren und einige Zeilen zu Ihrer benutzerdefinierten Projektvorlage hinzufügen, damit Sie wissen, wo Sie die Implementierung des Assistenten finden, wenn ein neues Projekt erstellt wird.

1. Signieren Sie die Assembly. Wählen Sie im **Projektmappen-Explorer** das VSIX-Projekt aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Projekteigenschaften** aus.

2. Wählen Sie im Fenster **Projekteigenschaften** die Registerkarte **Signierung** aus. Aktivieren Sie auf der Registerkarte **Signierung** die Option **Assembly signieren**. Wählen Sie im Feld **Schlüsseldatei mit starkem Namen auswählen** die Option aus **\<New>** . Geben Sie im Fenster Schlüssel für einen **starken Namen erstellen** im Feld **Schlüssel Dateiname den Namen** **Key. snk** ein. Deaktivieren Sie das Feld **meine Schlüsseldatei mit einem Kennwort schützen** .

3. Wählen Sie im **Projektmappen-Explorer** das VSIX-Projekt aus, und suchen Sie das **Eigenschaften** Fenster.

4. Legen Sie das Feld **Buildausgabe in Ausgabeverzeichnis kopieren** auf **true** fest. Dadurch kann die Assembly in das Ausgabeverzeichnis kopiert werden, wenn die Projekt Mappe neu erstellt wird. Er ist noch in der `.vsix` Datei enthalten. Sie müssen die Assembly sehen, um den Signatur Schlüssel zu ermitteln.

5. Generieren Sie die Projektmappe neu.

6. Sie finden die Datei Key. snk nun im Projektverzeichnis myprojectwizard (*\<your disk location> \myprojecttemplate\myprojectwizard\key.snk*). Kopieren Sie die Datei *Key. snk* .

7. Wechseln Sie zum Ausgabeverzeichnis, und suchen Sie die Assembly (*\<your disk location> \ MyProjectTemplate/#b0*). Fügen Sie die Datei *Key. snk* hier ein. (Dies ist nicht unbedingt erforderlich, aber die folgenden Schritte werden dadurch vereinfacht.)

8. Öffnen Sie ein Befehlsfenster, und wechseln Sie in das Verzeichnis, in dem die Assembly erstellt wurde.

9. Suchen Sie das *sn.exe* Signier Tool. Beispielsweise würde auf einem Windows 10 64-Bit-Betriebssystem ein typischer Pfad wie folgt lauten:

     *C:\Programme (x86) \Microsoft sdks\windows\v10.0a\bin\netfx 4.6.1 Tools*

     Wenn Sie das Tool nicht finden können, führen Sie aus, **wobei/R. sn.exe** im Befehlsfenster ausgeführt wird. Notieren Sie sich den Pfad.

10. Extrahieren Sie den öffentlichen Schlüssel aus der Datei *Key. snk* . Geben Sie im Befehlsfenster ein.

     **\<location of sn.exe>\sn.exe-p key. snk outfile. Key.**

     Vergessen Sie nicht, den Pfad *sn.exe* in Anführungszeichen einzuschließen, wenn die Verzeichnisnamen leer sind.

11. Das öffentliche Schlüssel Token aus der Ausgabedatei erhalten Sie:

     **\<location of sn.exe>\sn.exe-t outfile. Key.**

     Vergessen Sie auch hier nicht die Anführungszeichen. Eine Zeile in der Ausgabe sollte wie folgt angezeigt werden.

     **Öffentliches Schlüssel Token ist \<token>**

     Notieren Sie sich diesen Wert.

12. Fügen Sie der *VSTEMPLATE* -Datei der Projektvorlage den Verweis auf den benutzerdefinierten Assistenten hinzu. Suchen Sie im **Projektmappen-Explorer** die Datei namens *MyProjectTemplate. vstemplate*, und öffnen Sie Sie. Fügen Sie nach dem Ende des \<TemplateContent> Abschnitts den folgenden Abschnitt hinzu:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Dabei ist **myprojectwizard** der Name der Assembly, und **Token** ist das Token, das Sie im vorherigen Schritt kopiert haben.

13. Speichern Sie alle Dateien im Projekt, und erstellen Sie Sie neu.

## <a name="add-the-custom-parameter-to-the-template"></a>Hinzufügen des benutzerdefinierten Parameters zur Vorlage

In diesem Beispiel zeigt das Projekt, das als Vorlage verwendet wird, die Meldung an, die im Benutzereingabe Formular des benutzerdefinierten Assistenten angegeben ist.

1. Wechseln Sie in der **Projektmappen-Explorer** zum Projekt **MyProjectTemplate** , und öffnen Sie *Class1.cs*.

2. Fügen Sie der `Main`-Methode der Anwendung die folgende Codezeile hinzu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Der `$custommessage$`-Parameter wird beim Erstellen eines Projekts aus der Vorlage durch den im Benutzereingabeformular eingegebenen Text ersetzt.

Hier ist die vollständige Codedatei, bevor Sie in eine Vorlage exportiert wird.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Verwenden des benutzerdefinierten Assistenten

Nun können Sie ein Projekt aus der Vorlage erstellen und den benutzerdefinierten Assistenten verwenden.

1. Erstellen Sie die Lösung neu, und starten Sie das Debugging. Eine zweite Instanz von Visual Studio sollte angezeigt werden.

2. Erstellen Sie ein neues MyProjectTemplate-Projekt. (**Datei**  >  **Neu**  >  **Project**).

3. Suchen Sie im Dialogfeld **Neues Projekt** nach "MyProject", um die Vorlage zu suchen, geben Sie einen Namen ein, und klicken Sie auf **OK**.

     Das Benutzereingabeformular des Assistenten wird geöffnet.

4. Geben Sie einen Wert für den benutzerdefinierten Parameter ein, und klicken Sie auf die Schaltfläche.

     Das Benutzereingabeformular des Assistenten wird geschlossen, und aus der Vorlage wird ein Projekt erstellt.

5. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Quell Code Datei, und klicken Sie auf **Code anzeigen**.

     Beachten Sie, dass `$custommessage$` durch den im Benutzereingabeformular des Assistenten eingegebenen Text ersetzt wurde.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [WizardExtension-Element (Visual Studio-Vorlagen)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)
