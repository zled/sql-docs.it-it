---
title: Chiama una Stored Procedure (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b9f9456e5f916e886c366a292064d7ccd4dc5d8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412280"
---
# <a name="calling-a-stored-procedure-ole-db"></a>Esecuzione di una chiamata a una stored procedure (OLE DB)
  Una stored procedure può avere zero o più parametri. Può inoltre restituire un valore. Quando si usa il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client, è possibile passare parametri a una stored procedure:  
  
-   Specificando il valore dei dati a livello di codice.  
  
-   Utilizzando un marcatore di parametro (?) per specificare i parametri, associare una variabile di programma all'marcatore di parametro e quindi inserire il valore dei dati nella variabile di programma.  
  
> [!NOTE]  
>  Quando si esegue una chiamata alle stored procedure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando parametri denominati con OLE DB, i nomi dei parametri devono iniziare con il carattere '\@'. Si tratta di una restrizione specifica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client applica questa limitazione in modo più restrittivo rispetto a MDAC.  
  
 Per supportare i parametri, il **ICommandWithParameters** interfaccia viene esposta nell'oggetto comando. Per usare i parametri, il consumer descrive prima i parametri al provider chiamando il **ICommandWithParameters:: SetParameterInfo** metodo (o facoltativamente prepara un'istruzione di chiamata che chiama il  **GetParameterInfo** (metodo)). Il consumer crea quindi una funzione di accesso che specifica la struttura di un buffer e inserisce i valori dei parametri in questo buffer. Infine, passa l'handle della funzione di accesso e un puntatore al buffer in cui **Execute**. Nelle chiamate successive a **Execute**, il consumer inserisce i nuovi valori dei parametri nel buffer e le chiamate **Execute** con il puntatore di buffer e l'handle della funzione di accesso.  
  
 Un comando che chiama una stored procedure temporanea utilizzando i parametri prima di tutto è necessario chiamare **ICommandWithParameters:: SetParameterInfo** per definire le informazioni sui parametri, prima che il comando possa essere preparato correttamente. Questa operazione è necessaria perché il nome interno di una stored procedure temporanea è diverso dal nome esterno utilizzato da un client e SQLOLEDB non può eseguire una query sulle tabelle di sistema per determinare le informazioni sui parametri per una stored procedure temporanea.  
  
 Di seguito sono riportati i passaggi del processo di associazione dei parametri:  
  
1.  Completare le informazioni sui parametri in una matrice di strutture DBPARAMBINDINFO, ovvero nome del parametro, nome specifico del provider per il tipo di dati del parametro o nome del tipo di dati standard e così via. Ogni struttura della matrice descrive un solo parametro. Questa matrice viene quindi passata per il **SetParameterInfo** (metodo).  
  
2.  Chiamare il **ICommandWithParameters:: SetParameterInfo** metodo per descrivere i parametri al provider. **SetParameterInfo** specifica il tipo di dati nativo di ogni parametro. **SetParameterInfo** gli argomenti sono:  
  
    -   Numero di parametri per i quali impostare le informazioni sul tipo.  
  
    -   Matrice di numeri ordinali dei parametri per i quali impostare le informazioni sul tipo.  
  
    -   Matrice di strutture DBPARAMBINDINFO.  
  
3.  Creare una funzione di accesso di parametro usando il **IAccessor:: CreateAccessor** comando. La funzione di accesso specifica la struttura di un buffer e inserisce i valori dei parametri nel buffer. Il **CreateAccessor** comando crea una funzione di accesso da un set di associazioni. Queste associazioni vengono descritte dal consumer mediante una matrice di strutture DBBINDING. Ogni associazione associa un singolo parametro al buffer del consumer e contiene le seguenti informazioni:  
  
    -   Numero ordinale del parametro a cui viene applicata l'associazione.  
  
    -   Elemento da associare (valore dei dati, lunghezza e stato).  
  
    -   Offset nel buffer per ognuna di queste parti.  
  
    -   Lunghezza e tipo del valore dei dati esattamente come riportati nel buffer del consumer.  
  
     Una funzione di accesso viene identificata dal relativo handle di tipo HACCESSOR. Questo handle viene restituito per il **CreateAccessor** (metodo). Ogni volta che il consumer viene completata utilizzando una funzione di accesso, il consumer deve chiamare il **ReleaseAccessor** metodo per rilasciare la memoria vengono mantenuti.  
  
     Quando il consumer chiama un metodo, ad esempio **ICommand:: Execute**, passa l'handle a una funzione di accesso e un puntatore a un buffer. Il provider utilizza questa funzione di accesso per determinare il modo in cui trasferire i dati contenuti nel buffer.  
  
4.  Completare la struttura DBPARAMS. Le variabili del consumer da quale parametro di input i valori vengono forniti e in quale parametro di output vengono scritti i valori vengono passate alla fase di esecuzione **ICommand:: Execute** nella struttura DBPARAMS. La struttura DBPARAMS include tre elementi:  
  
    -   Puntatore al buffer da cui il provider recupera i dati dei parametri di input e in cui il provider restituisce i dati dei parametri di output, in base alle associazioni specificate dall'handle della funzione di accesso.  
  
    -   Numero di set di parametri nel buffer.  
  
    -   Handle della funzione di accesso creato nel passaggio 3.  
  
5.  Eseguire il comando usando **ICommand:: Execute**.  
  
## <a name="methods-of-calling-a-stored-procedure"></a>Metodi per l'esecuzione di una chiamata a una stored procedure  
 Quando si esegue una stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta il:  
  
-   Sequenza di escape ODBC CALL.  
  
-   Sequenza di escape RPC (Remote Procedure Call).  
  
-   Istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)]EXECUTE.  
  
### <a name="odbc-call-escape-sequence"></a>Sequenza di escape ODBC CALL  
 Se si conosce le informazioni sui parametri, chiamare **ICommandWithParameters:: SetParameterInfo** metodo per descrivere i parametri al provider. In caso contrario, quando viene utilizzata la sintassi ODBC CALL per eseguire la chiamata a una stored procedure, il provider chiama una funzione di supporto per trovare le informazioni sui parametri della stored procedure.  
  
 Se non si è certi delle informazioni sui parametri (metadati dei parametri), è consigliata la sintassi ODBC CALL.  
  
 La sintassi generale per la chiamata a una stored procedure mediante la sequenza di escape ODBC CALL è:  
  
 {[**? =**]**chiamata * **procedure_name*[**(**[*parametro*] [**,**[*parametro*]]...** )**]}  
  
 Esempio:  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a>Sequenza di escape RPC  
 La sequenza di escape RPC è simile alla sintassi ODBC CALL della chiamata a una stored procedure. Se si chiama la stored procedure più volte, la sequenza di escape RPC offre le massime prestazioni tra i tre metodi utilizzati per chiamare una stored procedure.  
  
 Quando la sequenza di escape RPC viene utilizzata per eseguire una stored procedure, il provider non chiama la funzione di supporto per determinare le informazioni sui parametri (come avviene nel caso della sintassi ODBC CALL). La sintassi RPC è più semplice della sintassi ODBC CALL, pertanto il comando viene analizzato più velocemente, migliorando le prestazioni. In questo caso, è necessario fornire le informazioni sui parametri eseguendo **ICommandWithParameters:: SetParameterInfo**.  
  
 Per utilizzare la sequenza di escape RPC è necessario disporre di un valore restituito. Se la stored procedure non restituisce un valore, il server restituisce per impostazione predefinita il valore 0. Inoltre, non è possibile aprire un cursore [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nella stored procedure. La stored procedure viene preparata in modo implicito e la chiamata a **ICommandPrepare:: Prepare** avrà esito negativo. A causa dell'impossibilità di preparare una chiamata RPC, non è possibile richiedere i metadati della colonna; IColumnsInfo:: GetColumnInfo e IColumnsRowset:: GetColumnsRowset restituiranno DB_E_NOTPREPARED.  
  
 Se si conoscono tutti i metadati dei parametri, la sequenza di escape RPC è la modalità consigliata per eseguire le stored procedure.  
  
 Di seguito viene riportato un esempio di sequenza di escape RPC per la chiamata a una stored procedure:  
  
```  
{rpc SalesByCategory}  
```  
  
 Per un'applicazione di esempio che illustra una sequenza di escape RPC, vedere [eseguire una Stored Procedure &#40;utilizzando la sintassi RPC&#41; e processo di codici restituiti e parametri di Output &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).  
  
### <a name="transact-sql-execute-statement"></a>Istruzione Transact-SQL EXECUTE  
 La sequenza di escape ODBC CALL e la sequenza di escape RPC rappresentano i metodi preferiti per chiamare una stored procedure anziché [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) istruzione. Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client utilizza il meccanismo RPC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ottimizzare l'elaborazione del comando. Questo protocollo RPC migliora le prestazioni riducendo l'elaborazione dei parametri e l'analisi delle istruzioni eseguite sul server.  
  
 Questo è un esempio del [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** istruzione:  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure](stored-procedures.md)  
  
  
