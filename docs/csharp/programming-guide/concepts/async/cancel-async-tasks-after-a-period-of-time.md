---
title: Annuler des tâches asynchrones après une période spécifique (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 55cf6b960752b36a1bfbd8ede25d7693225fbb20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325706"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Annuler des tâches asynchrones après une période spécifique (C#)
Si vous ne souhaitez pas attendre la fin d’une opération asynchrone, vous pouvez l’annuler après une période spécifique à l’aide de la méthode <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>. Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas terminées au terme de la période indiquée par l’expression `CancelAfter`.  
  
 Cet exemple s’appuie sur le code développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites web et afficher la longueur du contenu de chacun d’eux.  
  
> [!NOTE]
>  Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.  
  
## <a name="downloading-the-example"></a>Téléchargement de l'exemple  
 Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.  
  
1.  Décompressez le fichier que vous avez téléchargé, puis démarrez Visual Studio.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**.  
  
3.  Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez décompressé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningCS.  
  
4.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du projet **CancelAfterTime**, puis choisissez **Définir comme projet de démarrage**.  
  
5.  Appuyez sur la touche F5 pour exécuter le projet.  
  
     Appuyez sur les touches Ctrl+F5 pour exécuter le projet sans le déboguer.  
  
6.  Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web.  
  
 Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.cs à la fin de cette rubrique.  
  
## <a name="building-the-example"></a>Génération de l’exemple  
 L’exemple de cette rubrique s’appuie sur le projet développé dans [Annuler une tâche asynchrone ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pour annuler une liste de tâches. Il utilise la même interface utilisateur, bien que le bouton **Annuler** ne soit pas utilisé explicitement.  
  
 Pour générer vous-même l’exemple, suivez les instructions pas à pas de la section « Téléchargement de l’exemple », mais choisissez **CancelAListOfTasks** comme **Projet de démarrage**. Ajoutez les changements de cette rubrique à ce projet.  
  
 Pour spécifier une durée maximale avant que les tâches ne soient marquées comme annulées, ajoutez un appel à `CancelAfter` à `startButton_Click`, comme l’illustre l’exemple suivant. L’ajout est signalé par des astérisques.  
  
```csharp  
private async void startButton_Click(object sender, RoutedEventArgs e)  
{  
    // Instantiate the CancellationTokenSource.  
    cts = new CancellationTokenSource();  
  
    resultsTextBox.Clear();  
  
    try  
    {  
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You  
        // can adjust the time.)  
        cts.CancelAfter(2500);  
  
        await AccessTheWebAsync(cts.Token);  
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";  
    }  
    catch (OperationCanceledException)  
    {  
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
  
    cts = null;   
}  
```  
  
 Exécutez le programme plusieurs fois pour vérifier qu’il peut afficher la sortie pour tous les sites web, aucun site web ou certains sites web. La sortie suivante est un exemple.  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>Exemple complet  
 Le code suivant est le texte complet du fichier MainWindow.xaml.cs de l’exemple. Des astérisques marquent les éléments ajoutés pour cet exemple.  
  
 Notez que vous devez ajouter une référence pour <xref:System.Net.Http>.  
  
 Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterTime  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You  
                // can adjust the time.)  
                cts.CancelAfter(2500);  
  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;   
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // Note that the Cancel button cancels all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
  
    // Sample Output:  
  
    // Length of the downloaded string: 35990.  
  
    // Length of the downloaded string: 407399.  
  
    // Length of the downloaded string: 226091.  
  
    // Downloads canceled.  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone avec Async et Await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Procédure pas à pas : accès au web avec Async et Await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Annuler une tâche async ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [Ajuster une application Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Exemple Async : ajuster une application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
