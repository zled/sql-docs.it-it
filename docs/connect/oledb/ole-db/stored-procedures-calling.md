---
title: Chiamare una Stored Procedure (OLE DB) | Documenti Microsoft
description: Esecuzione di una chiamata a una stored procedure (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [OLE DB Driver for SQL Server], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6f4ee66e9f1eaf37f78e3a0a4a326655554c58f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="stored-procedures---calling"></a>Stored procedure - chiamata
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Una stored procedure può avere zero o più parametri. Può inoltre restituire un valore. Quando si utilizza il Driver OLE DB per SQL Server, è possibile passare parametri a una stored procedure:  
  
-   Specificando il valore dei dati a livello di codice.  
  
-   Utilizzando un marcatore di parametro (?) per specificare i parametri, associare una variabile di programma all'marcatore di parametro e quindi inserire il valore dei dati nella variabile di programma.  
  
> [!NOTE]  
>  Quando si esegue una chiamata alle stored procedure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando parametri denominati con OLE DB, i nomi dei parametri devono iniziare con il carattere '@'. Si tratta di una restrizione specifica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il Driver OLE DB per SQL Server applica questa limitazione in modo più restrittivo rispetto a MDAC.  
  
 Per supportare i parametri, il **ICommandWithParameters** viene esposta l'interfaccia per l'oggetto comando. Per utilizzare i parametri, il consumer descrive prima i parametri al provider chiamando il **ICommandWithParameters:: SetParameterInfo** metodo (o facoltativamente prepara un'istruzione di chiamata che chiama il **GetParameterInfo** (metodo)). Il consumer crea quindi una funzione di accesso che specifica la struttura di un buffer e inserisce i valori dei parametri in questo buffer. Infine, passa l'handle della funzione di accesso e un puntatore al buffer a **Execute**. Nelle chiamate successive a **Execute**, il consumer inserisce i nuovi valori dei parametri nel buffer e chiama **Execute** con il puntatore del buffer e di handle di funzione di accesso.  
  
 Innanzitutto è necessario chiamare un comando che chiama una stored procedure temporanea utilizzando parametri **ICommandWithParameters:: SetParameterInfo** per definire le informazioni sui parametri, prima che il comando può essere preparato. Questo avviene perché il nome interno per una stored procedure temporanea è diverso dal nome esterno utilizzato da un client e MSOLEDBSQL non è possibile eseguire una query di tabelle di sistema per determinare le informazioni sui parametri per una stored procedure temporanea.  
  
 Di seguito sono riportati i passaggi del processo di associazione dei parametri:  
  
1.  Completare le informazioni sui parametri in una matrice di strutture DBPARAMBINDINFO, ovvero nome del parametro, nome specifico del provider per il tipo di dati del parametro o nome del tipo di dati standard e così via. Ogni struttura della matrice descrive un solo parametro. Questa matrice viene quindi passata al **SetParameterInfo** metodo.  
  
2.  Chiamare il **ICommandWithParameters:: SetParameterInfo** per descrivere i parametri al provider. **La funzione SetParameterInfo** specifica il tipo di dati nativi di ogni parametro. **La funzione SetParameterInfo** gli argomenti sono:  
  
    -   Numero di parametri per i quali impostare le informazioni sul tipo.  
  
    -   Matrice di numeri ordinali dei parametri per i quali impostare le informazioni sul tipo.  
  
    -   Matrice di strutture DBPARAMBINDINFO.  
  
3.  Creare una funzione di accesso parametro utilizzando il **IAccessor:: CreateAccessor** comando. La funzione di accesso specifica la struttura di un buffer e inserisce i valori dei parametri nel buffer. Il **CreateAccessor** comando crea una funzione di accesso da un set di associazioni. Queste associazioni vengono descritte dal consumer mediante una matrice di strutture DBBINDING. Ogni associazione associa un singolo parametro al buffer del consumer e contiene le seguenti informazioni:  
  
    -   Numero ordinale del parametro a cui viene applicata l'associazione.  
  
    -   Elemento da associare (valore dei dati, lunghezza e stato).  
  
    -   Offset nel buffer per ognuna di queste parti.  
  
    -   Lunghezza e tipo del valore dei dati esattamente come riportati nel buffer del consumer.  
  
     Una funzione di accesso viene identificata dal relativo handle di tipo HACCESSOR. Questo handle viene restituito dal **CreateAccessor** metodo. Ogni volta che il consumer termina con una funzione di accesso, il consumer deve chiamare il **ReleaseAccessor** metodo per rilasciare la memoria vengono mantenuti.  
  
     Quando il consumer chiama un metodo, ad esempio **ICommand:: Execute**, passa l'handle per una funzione di accesso e un puntatore a un buffer. Il provider utilizza questa funzione di accesso per determinare il modo in cui trasferire i dati contenuti nel buffer.  
  
4.  Completare la struttura DBPARAMS. Le variabili del consumer dal quale parametro di input vengono estratti i valori e per il parametro di output vengono scritti i valori vengono passate in fase di esecuzione per **ICommand:: Execute** nella struttura DBPARAMS. La struttura DBPARAMS include tre elementi:  
  
    -   Puntatore al buffer da cui il provider recupera i dati dei parametri di input e in cui il provider restituisce i dati dei parametri di output, in base alle associazioni specificate dall'handle della funzione di accesso.  
  
    -   Numero di set di parametri nel buffer.  
  
    -   Handle della funzione di accesso creato nel passaggio 3.  
  
5.  Eseguire il comando usando **ICommand:: Execute**.  
  
## <a name="methods-of-calling-a-stored-procedure"></a>Metodi per l'esecuzione di una chiamata a una stored procedure  
 Quando si esegue una stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il Driver OLE DB per SQL Server supporta il:  
  
-   Sequenza di escape ODBC CALL.  
  
-   Sequenza di escape RPC (Remote Procedure Call).  
  
-   Istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)]EXECUTE.  
  
### <a name="odbc-call-escape-sequence"></a>Sequenza di escape ODBC CALL  
 Se si conosce le informazioni sui parametri, chiamare **ICommandWithParameters:: SetParameterInfo** per descrivere i parametri al provider. In caso contrario, quando viene utilizzata la sintassi ODBC CALL per eseguire la chiamata a una stored procedure, il provider chiama una funzione di supporto per trovare le informazioni sui parametri della stored procedure.  
  
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
  
 Per un'applicazione di esempio che illustra una sequenza di escape RPC, vedere [eseguire una Stored Procedure & #40; Tramite la sintassi RPC & #41; ed elaborare restituito codici e i parametri di Output & #40; OLE DB & #41; ](../../oledb/ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).  
  
### <a name="transact-sql-execute-statement"></a>Istruzione Transact-SQL EXECUTE  
 La sequenza di escape ODBC CALL e la sequenza di escape RPC rappresentano i metodi preferiti per chiamare una stored procedure anziché [EXECUTE](../../../t-sql/language-elements/execute-transact-sql.md) istruzione. Il Driver OLE DB per SQL Server utilizza il meccanismo RPC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ottimizzare l'elaborazione del comando. Questo protocollo RPC migliora le prestazioni riducendo l'elaborazione dei parametri e l'analisi delle istruzioni eseguite sul server.  
  
 Questo è un esempio del [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** istruzione:  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure](../../oledb/ole-db/stored-procedures.md)  
  
  
