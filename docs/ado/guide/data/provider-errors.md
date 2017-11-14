---
title: Errori del provider | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors collection [ADO]
- provider errors [ADO]
- event-related errors [ADO]
- errors [ADO], provider
- Error object [ADO], provider errors
ms.assetid: cc7d6ff9-2034-45c6-9d61-90b177010054
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c6e4934d8dc43c29629687a19a5d76ae46dab515
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="provider-errors"></a>Errori del provider
Quando si verifica un errore del provider, viene restituito un errore di run-time di -2147467259. Quando si riceve questo errore, controllare il **errori** insieme attivo **connessione** oggetto, che contiene uno o più errori che descrivono cosa è accaduto.  
  
## <a name="the-ado-errors-collection"></a>La raccolta di errori ADO  
 Poiché una particolare operazione ADO può generare più errori del provider, ADO espone una raccolta di oggetti di errore tramite il **connessione** oggetto. Questa raccolta non contiene oggetti se un'operazione vengono eseguite correttamente e che contiene uno o più **errore** oggetti se si è verificato un errore e il provider genera uno o più errori. Esaminare ogni oggetto error per determinare la causa esatta dell'errore.  
  
 Appena dopo aver completato la gestione degli eventuali errori che si sono verificati, è possibile cancellare la raccolta chiamando il **deselezionare** metodo. È particolarmente importante cancellare in modo esplicito il **errori** raccolta prima di chiamare il **Resync**, **UpdateBatch**, o **CancelBatch**metodo su un **Recordset** oggetto, il **aprire** metodo su un **connessione** dell'oggetto o impostare il **filtro** proprietà in un **Recordset** oggetto. Se si deseleziona la raccolta in modo esplicito, è possibile assicurarsi che qualsiasi **errore** oggetti nella raccolta vengono rimossi da un'operazione precedente.  
  
 Alcune operazioni possono generare avvisi a errori. Anche gli avvisi sono rappresentati da **errore** gli oggetti di **errori** insieme. Quando un provider aggiunge un avviso all'insieme, non genera un errore di run-time. Controllare il **conteggio** proprietà del **errori** insieme per determinare se un avviso è stato generato da un'operazione specifica. Se il conteggio è maggiore o uguale, un **errore** oggetto è stato aggiunto alla raccolta. Non appena è stato possibile determinare che il **errori** insieme contiene errori o avvisi, è possibile scorrere la raccolta e recuperare informazioni su ogni **errore** oggetto in esso contenuti. Breve esempio di Visual Basic seguente illustra questo processo:  
  
```  
' BeginErrorHandlingVB02  
Private Function DeleteCustomer(ByVal CompanyName As String) As Long  
    On Error GoTo DeleteCustomerError  
  
    rst.Find "CompanyName='" & CompanyName & "'"  
DeleteCustomerError:  
Dim objError As ADODB.Error  
Dim strError As String  
  
    If cnn.Errors.Count > 0 Then  
        For Each objError In cnn.Errors  
            strError = strError & "Error #" & objError.Number & _  
                " " & objError.Description & vbCrLf & _  
                "NativeError: " & objError.NativeError & vbCrLf & _  
                "SQLState: " & objError.SQLState & vbCrLf & _  
                "Reported by: " & objError.Source & vbCrLf & _  
                "Help file: " & objError.HelpFile & vbCrLf & _  
                "Help Context ID: " & objError.HelpContext  
        Next  
        MsgBox strError  
    End If  
End Function  
' EndErrorHandlingVB02  
```  
  
 La routine di gestione degli errori include un **per ogni** ciclo che esamina ogni oggetto di **errori** insieme. In questo esempio, accumula un messaggio per la visualizzazione. In un programma di lavoro, è necessario scrivere codice per eseguire un'attività appropriata per ogni errore, aprire ad esempio la chiusura di tutti i file e l'arresto del programma in modo ordinato.  
  
## <a name="the-error-object"></a>Oggetto Error  
 Esaminando un **errore** dell'oggetto, è possibile determinare l'errore si è verificato e più importante, quale applicazione o l'oggetto che ha causato l'errore. Il **errore** oggetto ha le proprietà seguenti:  
  
|Nome proprietà|Description|  
|-------------------|-----------------|  
|**Description**|Descrizione di testo dell'errore che si è verificato.|  
|**HelpContext, HelpFile**|Fa riferimento al file di argomento della Guida e Guida che contengono una descrizione dell'errore che si è verificato.|  
|**NativeError**|Il numero di errore specifico del provider.|  
|**Numero**|Un valore Long Integer che rappresenta il numero (elencati nel **ErrorValueEnum**) dell'errore che si è verificato.|  
|**Origine**|Indica il nome dell'applicazione che ha generato un errore o dell'oggetto.|  
|**SQLState**|Codice di errore di cinque caratteri che il provider restituisce durante il processo di un'istruzione SQL.|  
  
 ADO **errore** oggetto è molto simile a standard di Visual Basic **Err** oggetto. Le proprietà descrivono l'errore che si sono verificati. Oltre al numero dell'errore, è inoltre possibile ricevere due tipi correlati di informazioni. Il **NativeError** proprietà contiene un numero di errore specifico del provider in uso. Nell'esempio precedente, il provider è il Provider Microsoft OLE DB per SQL Server, in modo **NativeError** conterrà errori specifici di SQL Server. Il **SQLState** proprietà ha un codice di cinque lettere che descrive un errore in un'istruzione SQL.  
  
## <a name="event-related-errors"></a>Errori correlati agli eventi  
 Il **errore** oggetto viene utilizzato anche quando si verificano errori correlati agli eventi. È possibile determinare se si è verificato un errore del processo che ha generato un evento ADO controllando il **errore** oggetto passato come parametro di evento.  
  
 Se l'operazione che ha generato un evento è conclusa correttamente, il *adStatus* imposterà il parametro del gestore eventi *adStatusOK*. D'altra parte, se l'operazione che ha generato l'evento ha esito negativo, il *adStatus* parametro è impostato su *adStatusErrorsOccurred*. In tal caso, il *pError* parametro conterrà un **errore** oggetto che descrive l'errore.

