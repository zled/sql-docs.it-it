---
title: ALTER DATABASE (Parallel Data Warehouse) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7db44d9c9f02618e4d95a9d3eb9dfc581438dea5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-parallel-data-warehouse"></a>ALTER DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Modifica le opzioni relative alle dimensioni massime del database per le tabelle replicate, le tabelle distribuite e il log delle transazioni in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Usare questa istruzione per gestire le allocazioni dello spazio su disco per un database man mano che le sue dimensioni aumentano o diminuiscono.  
  
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
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione ALTER per il database.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I valori di REPLICATED_SIZE DISTRIBUTED_SIZE e LOG_SIZE possono essere maggiore, uguali o minori dei valori correnti per il database.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Le operazioni di incremento e riduzione sono approssimative. Le dimensioni effettive ottenute possono variare rispetto ai parametri delle dimensioni.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] non esegue l'istruzione ALTER DATABASE come operazione atomica. Se l'istruzione viene interrotta durante l'esecuzione, le modifiche già apportate vengono mantenute.  
  
## <a name="locking-behavior"></a>Comportamento di blocco  
 Viene acquisito un blocco condiviso per l'oggetto DATABASE. Non è possibile modificare un database che un altro utente sta usando in modalità di lettura o scrittura. Sono incluse le sessioni che hanno rilasciato un'istruzione [USE](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) nel database.  
  
## <a name="performance"></a>Prestazioni  
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
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
