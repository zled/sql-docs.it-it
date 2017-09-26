---
title: "Query su Active Directory con l'attività Script | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee5a82829785e78554b105e1f3bf3bd24f05b778
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="querying-the-active-directory-with-the-script-task"></a>Esecuzione di query su Active Directory tramite l'attività Script
  Le applicazioni di elaborazione di dati aziendali, ad esempio i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], devono in genere elaborare i dati in modo diverso a seconda del grado, della posizione o di altre caratteristiche dei dipendenti archiviati in Active Directory. Active Directory è un [!INCLUDE[msCoName](../../includes/msconame-md.md)] servizio directory di Windows che fornisce un archivio centralizzato di metadati, non solo sugli utenti, ma anche su altre risorse organizzative, ad esempio computer e stampanti. Il **System. DirectoryServices** dello spazio dei nomi in Microsoft .NET Framework fornisce classi per l'utilizzo di Active Directory, che consentono di diretto l'elaborazione dei dati del flusso di lavoro in base alle informazioni in essa contenuti.  
  
> [!NOTE]  
>  Se si desidera creare un'attività da riutilizzare più facilmente con più pacchetti, è possibile utilizzare il codice di questo esempio di attività Script come punto iniziale per un'attività personalizzata. Per altre informazioni, vedere [Sviluppo di un'attività personalizzata](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Nell'esempio seguente vengono recuperati il nome, la posizione e il numero di telefono di un dipendente da Active Directory in base al valore della variabile `email`, che contiene l'indirizzo di posta elettronica del dipendente. I vincoli di precedenza del pacchetto possono utilizzare le informazioni recuperate per determinare, ad esempio, se inviare un messaggio di posta elettronica con priorità bassa o una pagina con priorità alta, in base alla posizione del dipendente.  
  
#### <a name="to-configure-this-script-task-example"></a>Per configurare l'esempio di attività Script  
  
1.  Creare le tre variabili stringa `email`, `name` e `title`. Immettere un indirizzo di posta elettronica aziendale valido come valore della variabile `email`.  
  
2.  Nel **Script** pagina del **Editor attività Script**, aggiungere il `email` variabile il **ReadOnlyVariables** proprietà.  
  
3.  Aggiungere il `name` e `title` variabili per il **ReadWriteVariables** proprietà.  
  
4.  Nel progetto di script, aggiungere un riferimento di **System. DirectoryServices** dello spazio dei nomi.  
  
5.  . Nel codice, utilizzare un **importazioni** per importare il **DirectoryServices** dello spazio dei nomi.  
  
> [!NOTE]  
>  Per eseguire correttamente lo script, è necessario che l'azienda utilizzi Active Directory nella propria rete e archivi le informazioni sui dipendenti utilizzati nell'esempio.  
  
### <a name="code"></a>Codice  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a>Risorse esterne  
  
-   Articolo tecnico relativo [l'elaborazione di informazioni di Active Directory in SSIS](http://go.microsoft.com/fwlink/?LinkId=199588), sul sito Web social.technet.microsoft.com  
  
  
