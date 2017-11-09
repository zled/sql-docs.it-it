---
title: CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16ef8191-7587-45a3-9ee9-7d99b7088de3
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0318d108d6dfaaa374af9a1ab8a148ff960dfcd
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-remote-table-as-select-parallel-data-warehouse"></a>CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Seleziona i dati da un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database e copia i dati in una nuova tabella in un punto di migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in un server remoto. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Usa il dispositivo, con tutti i vantaggi MPP elaborazione delle query, per selezionare i dati per la copia remota. Utilizzare questa opzione per gli scenari che richiedono [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità.  
  
 Per configurare il server remoto, vedere "Copia della tabella remota" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE REMOTE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name     AT ('<connection_string>')  
    [ WITH ( BATCH_SIZE = batch_size ) ]  
    AS <select_statement>  
[;]  
  
<connection_string> ::=   
    Data Source = { IP_address | hostname } [, port ]; User ID = user_name ;Password = password;  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Il database per creare la tabella remota. *database_name* è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. Il valore predefinito è il database predefinito per l'account di accesso utente nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
 *schema_name*  
 Lo schema per la nuova tabella. Il valore predefinito è lo schema predefinito per l'account di accesso utente nella destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
 *table_name*  
 Il nome della nuova tabella. Per informazioni su consentiti nomi di tabella, vedere "Regole di denominazione degli oggetti" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 La tabella remota viene creata come un heap. Non dispone di vincoli check o trigger. Le regole di confronto delle colonne della tabella remota corrisponde alle regole di confronto delle colonne della tabella di origine. Questo vale per le colonne di tipo **char**, **nchar**, **varchar**, e **nvarchar**.  
  
 *stringa_connessione*  
 Una stringa di caratteri che specifica il `Data Source`, `User ID`, e `Password` parametri per la connessione al server remoto e del database.  
  
 La stringa di connessione è un elenco delimitato da punto e virgola di coppie chiave / valore. Parole chiave non sono rilevanti. Gli spazi tra coppie chiave / valore vengono ignorati. Tuttavia, i valori possono essere tra maiuscole e minuscole, a seconda dell'origine dati.  
  
 *Data Source*  
 Il parametro che specifica il nome o l'indirizzo IP e TCP il numero di porta per il punto di migrazione remoto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *nome host* o *indirizzo_IP*  
 Nome del computer server remoto o l'indirizzo IPv4 del server remoto. Gli indirizzi IPv6 non sono supportati. È possibile specificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza nel formato denominata **nome_computer ome_istanza** o **IP_address\Instance_Name**. Il server deve essere remoto e pertanto non può essere specificato come (local).  
  
 TCP *porta* numero  
 Il numero di porta TCP per la connessione. Per un'istanza di SQL Server che non è in ascolto sulla porta predefinita 1433, è possibile specificare un numero di porta TCP compreso tra 0 e 65535. Ad esempio: **ServerA, 1450** o **10.192.14.27,1435**  
  
> [!NOTE]  
>  È consigliabile connettersi a un server remoto utilizzando l'indirizzo IP. A seconda della configurazione di rete, la connessione utilizzando il nome del computer potrebbero richiedere passaggi aggiuntivi per utilizzare il server DNS non strumento per risolvere il nome server corretto. Questo passaggio non è necessario quando ci si connette con un indirizzo IP. Per ulteriori informazioni, vedere "Utilizzo di un server d'inoltro DNS per i nomi DNS Non accessorio Resolve (Analitica Platform System)" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 *USER_NAME*  
 Un valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nome account di accesso di autenticazione. Numero massimo di caratteri è 128.  
  
 *password*  
 Password di accesso. Numero massimo di caratteri è 128.  
  
 *batch_size*  
 Il numero massimo di righe per batch. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Invia le righe in batch nel server di destinazione. *Batch_size* è un numero intero positivo > = 0. Valore predefinito è 0.  
  
 CON *common_table_expression*  
 Indica un set di risultati denominato temporaneo, noto come espressione di tabella comune (CTE). Per ulteriori informazioni, vedere [con common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 Selezionare \<select_criteria > il predicato della query che specifica quali dati popolerà la nuova tabella remota. Per informazioni sull'istruzione SELECT, vedere [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È necessario:  
  
-   Autorizzazione SELECT per ogni oggetto nella clausola SELECT.  
  
-   È richiesta l'autorizzazione CREATE TABLE nel database SMP di destinazione.  
  
-   È necessario ALTER, INSERT e le autorizzazioni SELECT per lo schema di destinazione SMP.  
  
## <a name="error-handling"></a>Gestione degli errori  
 Se la copia dei dati al database remoto non riesce, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] verrà interrompere l'operazione, registrare un errore e tentare di eliminare la tabella remota. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]non garantisce una pulizia corretta della nuova tabella.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 **Server di destinazione remoto**:  
  
-   TCP è l'impostazione predefinita e protocollo è supportato solo per la connessione a un server remoto.  
  
-   Il server di destinazione deve essere un server non strumento. CREATE REMOTE TABLE non può essere utilizzato per copiare dati da un dispositivo a un altro.  
  
-   L'istruzione CREATE REMOTE TABLE solo crea nuove tabelle. Pertanto, la nuova tabella non può già esistere. Il database remoto e lo schema deve esistere.  
  
-   Il server remoto deve disporre di spazio disponibile per archiviare i dati che vengono trasferiti dal dispositivo per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database remoto.  
  
 **Istruzione SELECT**:  
  
-   Le clausole ORDER BY e TOP non sono supportate nei criteri di selezione.  
  
-   CREATE REMOTE TABLE non può essere eseguita all'interno di una transazione attiva o quando è attiva l'impostazione di AUTOCOMMIT OFF per la sessione.  
  
 [SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) non ha alcun effetto in questa istruzione. Per ottenere un comportamento simile, utilizzare [torna all'inizio &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
## <a name="locking-behavior"></a>Comportamento di blocco  
 Dopo aver creato la tabella remota, la tabella di destinazione non è bloccata fino a quando non viene avviata la copia. Pertanto, è possibile che un altro processo eliminare la tabella remota dopo averlo creato e prima che venga avviata la copia. In questo caso, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] genererà un errore e la copia avrà esito negativo.  
  
## <a name="metadata"></a>Metadati  
 Utilizzare [sys.dm_pdw_dms_workers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md) per visualizzare lo stato di avanzamento della copia dei dati selezionati al server remoto SMP. Le righe con tipo PARALLEL_COPY_READER contengono queste informazioni.  
  
## <a name="security"></a>Security  
 CREATE REMOTE TABLE Usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione per connettersi all'istanza remota [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza; non utilizza l'autenticazione di Windows.  
  
 Il [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] rete con connessione esterna deve proteggere tramite firewall, con l'eccezione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] porte porte amministrative e porte di gestione.  
  
 Per evitare la perdita di dati accidentali, l'account utente che è possibile copiare dal dispositivo per il database di destinazione deve avere solo le autorizzazioni minime necessarie nel database di destinazione.  
  
 Le impostazioni di connessione consentono di connettersi a migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza con SSL di proteggere i dati di nome e una password utente, ma con i dati effettivi inviati non crittografati in testo non crittografato. In questo caso, un utente malintenzionato può intercettare il testo dell'istruzione CREATE REMOTE TABLE, che contiene il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nome utente e password per accedere a migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza. Per evitare questo rischio, utilizzare la crittografia dei dati per la connessione a migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
##  <a name="Examples"></a> Esempi  
  
### <a name="a-creating-a-remote-table"></a>A. Creazione di una tabella remota  
 Questo esempio viene creato un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chiamata la tabella remota SMP `MyOrdersTable` sul database `OrderReporting` e schema `Orders`. Il `OrderReporting` database si trova in un server denominato `SQLA` in ascolto sulla porta predefinita 1433. La connessione al server utilizza le credenziali dell'utente `David`, la cui password è `e4n8@3`.  
  
```  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
AS SELECT <select_criteria>;  
```  
  
### <a name="b-querying-the-sysdmpdwdmsworkers-dmv-for-remote-table-copy-status"></a>B. L'esecuzione di query di sys.dm_pdw_dms_workers DMV per lo stato di copia tabella remota  
 Questa query viene illustrato come visualizzare lo stato di copia per copiare una tabella remota.  
  
```  
SELECT * FROM sys.dm_pdw_dms_workers   
WHERE type = 'PARALLEL_COPY_READER';  
```  
  
### <a name="c-using-a-query-join-hint-with-create-remote-table"></a>C. Con un hint di join di query CREATE REMOTE TABLE  
 Questa query Mostra la sintassi di base per l'utilizzo di un hint di join della query con CREATE REMOTE TABLE. Dopo che la query viene inviata al nodo di controllo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in esecuzione nei nodi di calcolo, verrà applicata la strategia di join hash durante la generazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] piano di query. Per ulteriori informazioni sull'hint di join e come utilizzare la clausola OPTION, vedere [clausola OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
USE ssawPDW;  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
    AS SELECT T1.* FROM OrderReporting.Orders.MyOrdersTable T1   
    JOIN OrderReporting.Order.Customer T2  
    ON T1.CustomerID=T2.CustomerID OPTION (HASH JOIN);  
```  
  
  


