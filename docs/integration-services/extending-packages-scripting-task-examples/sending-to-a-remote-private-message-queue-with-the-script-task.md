---
title: "L'invio a una coda messaggi privata remota con l'attività Script | Documenti Microsoft"
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
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5ab9314ef0825486914d1801bfa2b9613883b43e
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Invio di messaggi a una coda privata remota tramite l'attività Script
  Accodamento messaggi (noto anche come MSMQ) consente agli sviluppatori di applicazioni di comunicare in modo rapido, semplice e affidabile con i programmi applicativi mediante l'invio e la ricezione di messaggi. Una coda di messaggi può trovarsi nel computer locale o in un computer remoto e può essere pubblica o privata. In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], la gestione connessione MSMQ e l'attività Message Queue non supportano l'invio a una coda privata su un computer remoto. Tuttavia, utilizzando l'attività Script, è possibile inviare facilmente un messaggio a una coda privata remota.  
  
> [!NOTE]  
>  Se si desidera creare un'attività da riutilizzare più facilmente con più pacchetti, è possibile utilizzare il codice di questo esempio di attività Script come punto iniziale per un'attività personalizzata. Per altre informazioni, vedere [Sviluppo di un'attività personalizzata](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Nell'esempio seguente usa una gestione connessione MSMQ esistente, insieme agli oggetti e metodi dello spazio dei nomi System. Messaging per inviare il testo contenuto in una variabile del pacchetto a una coda messaggi privata remota. La chiamata al metodo M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) della gestione connessione MSMQ restituisce un **MessageQueue** i cui **inviare** metodo esegue questa operazione.  
  
#### <a name="to-configure-this-script-task-example"></a>Per configurare l'esempio di attività Script  
  
1.  Creare una gestione connessione MSMQ con il nome predefinito. Impostare il percorso di una coda privata remota valida, nel formato seguente:  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Creare un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variabile denominata **MessageText** di tipo **stringa** per passare il testo del messaggio nello script. Immettere un messaggio predefinito come valore della variabile.  
  
3.  Aggiungere un'attività Script all'area di progettazione e modificarla. Nel **Script** scheda della finestra il **Editor attività Script**, aggiungere il `MessageText` variabile il **ReadOnlyVariables** proprietà per rendere disponibili all'interno dello script la variabile .  
  
4.  Fare clic su **modifica Script** per aprire la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] strumenti per l'editor di script Applications (VSTA).  
  
5.  Aggiungere un riferimento nel progetto di script per il **System. Messaging** dello spazio dei nomi.  
  
6.  Sostituire il contenuto della finestra dello script con il codice nella sezione seguente.  
  
## <a name="code"></a>Codice  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività Message Queue](../../integration-services/control-flow/message-queue-task.md)  
  
  
