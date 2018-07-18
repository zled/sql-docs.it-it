---
title: Using System. Transactions | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b6a16064cbff2b859f627271784d170b0c812078
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-systemtransactions"></a>Utilizzo di System.Transactions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il **System. Transactions** spazio dei nomi fornisce un framework di transazioni che è completamente integrato con ADO.NET e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integrazione common language runtime (CLR). Il **Transactions** rende un blocco di codice transazionale elencando implicitamente le connessioni in una transazione distribuita. È necessario chiamare il **completa** metodo alla fine del blocco di codice contrassegnato mediante il **TransactionScope**. Il **Dispose** metodo viene richiamato quando l'esecuzione del programma lascia un blocco di codice, la transazione non viene più utilizzata se il **completa** non viene chiamato. Se è stata generata un'eccezione che determina l'uscita del codice dall'ambito, la transazione non viene più utilizzata.  
  
 Si consiglia di utilizzare un **utilizzando** blocco per garantire che il **Dispose** metodo viene chiamato sul **TransactionScope** oggetto quando il **utilizzando**blocco viene chiuso. Impossibile eseguire il commit o il rollback delle transazioni in sospeso può compromettere notevolmente le prestazioni perché il timeout predefinito per il **TransactionScope** è un minuto. Se non si utilizza un **utilizzando** istruzione, è necessario eseguire le operazioni in un **provare** bloccare e chiamare in modo esplicito il **Dispose** metodo il **infine**blocco.  
  
 Se si verifica un'eccezione all'interno di **TransactionScope**, la transazione viene contrassegnata come incoerente e viene interrotta. Viene eseguito il rollback quando il **TransactionScope** è stato eliminato. Se non si verifica alcuna eccezione, viene eseguito il commit delle transazioni partecipanti.  
  
 **TransactionScope** deve essere utilizzato solo quando le origini dati locali e remoti o gestori di risorse esterni sono a cui si accede. In questo modo **TransactionScope** comporta sempre promozione delle transazioni, anche se è utilizzato solo all'interno di una connessione di contesto.  
  
> [!NOTE]  
>  Il **TransactionScope** classe crea una transazione con un **System.Transactions.Transaction.IsolationLevel** di **Serializable** per impostazione predefinita. A seconda dell'applicazione, è possibile abbassare il livello di isolamento per evitare che si verifichi un numero elevato di contese.  
  
> [!NOTE]  
>  È consigliabile eseguire solo aggiornamenti, inserimenti ed eliminazioni all'interno di transazioni distribuite sui server remoti in quanto tali operazioni comportano un notevole consumo di risorse del database. Se l'operazione viene effettuata sul server locale, non è necessario eseguire una transazione distribuita ed è sufficiente una transazione locale. Le istruzioni SELECT potrebbero bloccare inutilmente risorse del database e in alcuni scenari può essere necessario utilizzare le transazioni per le operazioni di selezione. Tutto il lavoro che non riguarda il database deve essere svolto all'esterno dell'ambito della transazione, a meno che non coinvolga altri gestori di risorse inclusi nella transazione. Sebbene un'eccezione all'interno dell'ambito della transazione impedisca l'esecuzione del commit, il **TransactionScope** classe non è disponibile il rollback delle modifiche al codice apportate all'esterno dell'ambito della transazione se stesso. Se è necessario eseguire un'azione quando viene eseguito il rollback della transazione, è necessario scrivere la propria implementazione del **System.Transactions.IEnlistmentNotification** interfaccia ed integrarla esplicitamente nella transazione.  
  
## <a name="example"></a>Esempio  
 Per funzionare con **System. Transactions**, è necessario disporre di un riferimento al file System.Transactions.dll.  
  
 Nel codice seguente viene illustrato come creare una transazione che può essere promossa su due istanze diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Queste istanze vengono rappresentate da due diversi **SqlConnection** oggetti, incapsulati in un **TransactionScope** blocco. Il codice crea il **TransactionScope** blocco con un **utilizzando** istruzione e viene aperta la prima connessione elencarla automaticamente nel **TransactionScope**. La transazione viene integrata inizialmente come transazione lightweight, non come transazione completamente distribuita. Il codice presuppone l'esistenza della logica condizionale, omessa per brevità. Si apre la seconda connessione solo se necessario, integrandola nel **TransactionScope**. Quando la connessione è aperta, la transazione viene promossa automaticamente a una transazione completamente distribuita. Il codice richiama quindi **TransactionScope.Complete**, che esegue il commit della transazione. Il codice elimina le due connessioni in uscita di **utilizzando** istruzioni per le connessioni. Il **TransactionScope.Dispose** metodo per il **TransactionScope** viene chiamato automaticamente al termine del **utilizzando** bloccare per il  **TransactionScope**. Se è stata generata un'eccezione in qualsiasi punto di **TransactionScope** blocco **completa** non viene chiamato e transazione distribuita verrà eseguito il rollback quando il **TransactionScope**  è stato eliminato.  
  
 Visual Basic  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 C#  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le transazioni e integrazione con CLR](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
