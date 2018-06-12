---
title: ALTER DATABASE (Parallel Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b17fcc15be4c8faf496c469bb1e46fe2c6d42012
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34550492"
---
# <a name="alter-database-parallel-data-warehouse"></a>ALTER DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Modifica le opzioni relative alle dimensioni massime del database per le tabelle replicate, le tabelle distribuite e il log delle transazioni in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Usare questa istruzione per gestire le allocazioni dello spazio su disco per un database man mano che le sue dimensioni aumentano o diminuiscono. L'argomento descrive anche la sintassi correlata all'impostazione di opzioni di database in Parallel Data Warehouse. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Parallel Data Warehouse  
ALTER DATABASE database_name    
    SET ( <set_database_options>   | <db_encryption_option> )  
[;]  
  
<set_database_options> ::=   
{  
    AUTOGROW = { ON | OFF }  
    | REPLICATED_SIZE = size [GB]  
    | DISTRIBUTED_SIZE = size [GB]  
    | LOG_SIZE = size [GB]
    | SET AUTO_CREATE_STATISTICS { ON | OFF }
    | SET AUTO_UPDATE_STATISTICS { ON | OFF } 
    | SET AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database da modificare. Per visualizzare un elenco di database nell'appliance, usare [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 AUTOGROW = { ON | OFF }  
 Aggiorna l'opzione AUTOGROW. Quando l'opzione AUTOGROW è impostata su ON, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] aumenta automaticamente lo spazio allocato per le tabelle replicate, le tabelle distribuite e il log delle transazioni in modo da poter supportare l'aumento in termini di requisiti di archiviazione. Quando l'opzione AUTOGROW è impostata su OFF, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] restituisce un errore se le tabelle replicate, le tabelle distribuite o il log delle transazioni superano l'impostazione di dimensioni massime.  
  
 REPLICATED_SIZE = *size* [GB]  
 Specifica in gigabyte le nuove dimensioni massime per ogni nodo di calcolo per l'archiviazione di tutte le tabelle replicate nel database da modificare. Per pianificare lo spazio di archiviazione dell'appliance, è necessario moltiplicare il valore in REPLICATED_SIZE per il numero di nodi di calcolo nell'appliance.  
  
 DISTRIBUTED_SIZE = *size* [GB]  
 Specifica in gigabyte le nuove dimensioni massime per ogni database per l'archiviazione di tutte le tabelle distribuite nel database da modificare. Le dimensioni vengono distribuite su tutti i nodi di calcolo nell'appliance.  
  
 LOG_SIZE = *size* [GB]  
 Specifica in gigabyte le nuove dimensioni massime per ogni database per l'archiviazione dei log delle transazioni nel database da modificare. Le dimensioni vengono distribuite su tutti i nodi di calcolo nell'appliance.  
  
 ENCRYPTION { ON | OFF }  
 Imposta il database per l'utilizzo della crittografia (ON) o no (OFF). È possibile configurare la crittografica per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] solo quando l'opzione [sp_pdw_database_encryption](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e) è stata impostata su **1**. Prima di configurare la tecnologia Transparent Data Encryption, è necessario creare una chiave di crittografia del database. Per altre informazioni sulla crittografia del database, vedere [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  

 SET AUTO_CREATE_STATISTICS { ON | OFF } Quando l'opzione per la creazione automatica delle statistiche, AUTO_CREATE_STATISTICS, è impostata su ON, Query Optimizer crea le statistiche necessarie per colonne singole nel predicato di query, per migliorare le stime della cardinalità per il piano di query. Queste statistiche di colonna singola vengono create in colonne che ancora non dispongono di un istogramma in un oggetto statistiche esistente.

 Il valore predefinito è ON per i nuovi database creati dopo l'aggiornamento ad AU7. Il valore predefinito è OFF per i database creati prima dell'aggiornamento. 

 Per altre informazioni sulle statistiche, vedere [Statistiche](/sql/relational-databases/statistics/statistics)

 SET AUTO_UPDATE_STATISTICS { ON | OFF } Quando l'opzione per l'aggiornamento automatico delle statistiche, AUTO_UPDATE_STATISTICS, è impostata su ON, Query Optimizer determina se le statistiche possano non essere aggiornate, quindi ne esegue l'aggiornamento qualora vengano usate da una query. Le statistiche diventano obsolete in seguito a operazioni di inserimento, aggiornamento, eliminazione o unione che modificano la distribuzione dei dati nella tabella o nella vista indicizzata. Query Optimizer determina che le statistiche potrebbero non essere aggiornate contando il numero di modifiche apportate ai dati dopo l'ultimo aggiornamento delle statistiche e confrontando il numero di modifiche con una soglia basata sul numero di righe nella tabella o nella vista indicizzata.

 Il valore predefinito è ON per i nuovi database creati dopo l'aggiornamento ad AU7. Il valore predefinito è OFF per i database creati prima dell'aggiornamento. 

 Per altre informazioni sulle statistiche, vedere [Statistiche](/sql/relational-databases/statistics/statistics).


 SET AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF } L'opzione relativa all'aggiornamento asincrono delle statistiche, AUTO_UPDATE_STATISTICS_ASYNC, determina se Query Optimizer debba usare gli aggiornamenti sincroni o asincroni delle statistiche. L'opzione AUTO_UPDATE_STATISTICS_ASYNC si applica a oggetti statistiche creati per indici, colonne singole nei predicati di query e statistiche create con l'istruzione CREATE STATISTICS.

 Il valore predefinito è ON per i nuovi database creati dopo l'aggiornamento ad AU7. Il valore predefinito è OFF per i database creati prima dell'aggiornamento. 

 Per altre informazioni sulle statistiche, vedere [Statistiche](/sql/relational-databases/statistics/statistics).

  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione ALTER per il database.  
  
## <a name="error-messages"></a>messaggi di errore
Se le statistiche automatiche sono disabilitate e si tenta di modificare le impostazioni delle statistiche, PDW visualizza l'errore "Questa opzione non è supportata in PDW". L'amministratore di sistema può abilitare le statistiche automatiche abilitando l'opzione [AutoStatsEnabled](../../analytics-platform-system/appliance-feature-switch.md) della funzionalità.

## <a name="general-remarks"></a>Osservazioni generali  
 I valori di REPLICATED_SIZE DISTRIBUTED_SIZE e LOG_SIZE possono essere maggiore, uguali o minori dei valori correnti per il database.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Le operazioni di incremento e riduzione sono approssimative. Le dimensioni effettive ottenute possono variare rispetto ai parametri delle dimensioni.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non esegue l'istruzione ALTER DATABASE come operazione atomica. Se l'istruzione viene interrotta durante l'esecuzione, le modifiche già apportate vengono mantenute.  

Le impostazioni delle statistiche funzionano solo se l'amministratore ha abilitato le statistiche automatiche.  Per abilitare o disabilitare le statistiche automatiche, l'amministratore deve usare l'opzione [AutoStatsEnabled](../../analytics-platform-system/appliance-feature-switch.md) della funzionalità. 
  
## <a name="locking-behavior"></a>Comportamento di blocco  
 Consente di acquisire un blocco condiviso per l'oggetto DATABASE. Non è possibile modificare un database che un altro utente sta usando in modalità di lettura o scrittura. Sono incluse le sessioni che hanno rilasciato un'istruzione [USE](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) nel database.  
  
## <a name="performance"></a>restazioni  
 Per compattare un database possono essere necessari molto tempo e numerose risorse di sistema, a seconda delle dimensioni dei dati effettivi all'interno del database e del livello di frammentazione del disco. La compattazione di un database può richiedere fino a diverse ore di lavoro.  
  
## <a name="determining-encryption-progress"></a>Definizione dello stato di avanzamento della crittografia  
 Usare la query seguente per determinare lo stato di avanzamento della tecnologia Transparent Data Encryption sotto forma di percentuale:  
  
```  
WITH  
database_dek AS (  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id,  
        dek.encryption_state, dek.percent_complete,  
        dek.key_algorithm, dek.key_length, dek.encryptor_thumbprint,  
        type  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
    INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
        ON dek.database_id = node_db_map.database_id   
        AND dek.pdw_node_id = node_db_map.pdw_node_id  
    LEFT JOIN sys.pdw_database_mappings AS db_map  
        ON node_db_map .physical_name = db_map.physical_name  
    INNER JOIN sys.dm_pdw_nodes nodes  
        ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
),  
dek_percent_complete AS (  
    SELECT database_dek.database_id, AVG(database_dek.percent_complete) AS percent_complete  
    FROM database_dek  
    WHERE type = 'COMPUTE'  
    GROUP BY database_dek.database_id  
)  
SELECT DB_NAME( database_dek.database_id ) AS name,  
    database_dek.database_id,  
    ISNULL(  
       (SELECT TOP 1 dek_encryption_state.encryption_state  
        FROM database_dek AS dek_encryption_state  
        WHERE dek_encryption_state.database_id = database_dek.database_id  
        ORDER BY (CASE encryption_state  
            WHEN 3 THEN -1  
            ELSE encryption_state  
            END) DESC), 0)  
        AS encryption_state,  
dek_percent_complete.percent_complete,  
database_dek.key_algorithm, database_dek.key_length, database_dek.encryptor_thumbprint  
FROM database_dek  
INNER JOIN dek_percent_complete   
    ON dek_percent_complete.database_id = database_dek.database_id  
WHERE type = 'CONTROL';  
```  
  
 Per un esempio completo che illustra tutti i passaggi di implementazione della tecnologia TDE, vedere [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Modifica dell'impostazione AUTOGROW  
 Impostare l'opzione AUTOGROW su ON per il database `CustomerSales`.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>B. Modifica dell'archiviazione massima per le tabelle replicate  
 Nell'esempio seguente il limite di archiviazione delle tabelle replicate viene impostato su 1 GB per il database `CustomerSales`. È il limite di archiviazione per ogni nodo di calcolo.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>C. Modifica dell'archiviazione massima per le tabelle distribuite  
 Nell'esempio seguente il limite di archiviazione delle tabelle distribuite viene impostato su 1000 GB (1 TB) per il database `CustomerSales`. È il limite di archiviazione combinato dell'appliance per tutti i nodi di calcolo, non il limite di archiviazione per ogni nodo di calcolo.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>D. Modifica dell'archiviazione massima per il log delle transazioni  
 Nell'esempio seguente il database `CustomerSales` viene aggiornato perché le dimensioni massime del log delle transazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] siano di 10 GB per l'applicazione.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  

### <a name="e-check-for-current-statistics-values"></a>E. Controllo dei valori correnti delle statistiche

La query seguente restituisce i valori correnti delle statistiche per tutti i database. Il valore 1 indica che la funzionalità è attivata e 0 indica che la funzionalità è disattivata.

```sql
SELECT NAME,
    is_auto_create_stats_on,
    is_auto_update_stats_on,
    is_auto_update_stats_async_on
FROM sys.databases;
```
### <a name="f-enable-auto-create-and-auto-update-stats-for-a-database"></a>F. Abilitazione della creazione e dell'aggiornamento automatici delle statistiche per un database
Usare l'istruzione seguente per abilitare la creazione e l'aggiornamento automatici delle statistiche in modo asincrono per il database CustomerSales.  L'istruzione crea e aggiorna le statistiche di colonna singola necessarie per creare piani di query di qualità elevata.

```sql
ALTER DATABASE CustomerSales
    SET AUTO_CREATE_STATISTICS ON;
ALTER DATABASE CustomerSales
    SET AUTO_UPDATE_STATISTICS ON; 
ALTER DATABASE CustomerSales
    SET AUTO_UPDATE_STATISTICS_ASYNC ON;
```
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
