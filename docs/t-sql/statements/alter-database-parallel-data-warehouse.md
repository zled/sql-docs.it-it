---
title: ALTER DATABASE (Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 74b47bec1033728d47e5fe577af29c6d43e9af65
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-parallel-data-warehouse"></a>ALTER DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Modifica le opzioni di dimensioni massime del database per il log delle transazioni in tabelle replicate e tabelle distribuite [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Utilizzare questa istruzione per gestire le allocazioni di spazio su disco per un database, come aumenta o riduce le dimensioni.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Il nome del database da modificare. Per visualizzare un elenco di database nel dispositivo, utilizzare [Sys. Databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 AUMENTO AUTOMATICO DELLE DIMENSIONI = {ON | OFF}  
 Aggiorna l'opzione di aumento automatico delle dimensioni. Quando l'aumento automatico dimensioni sono impostata su ON, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] automaticamente aumenta lo spazio allocato per le tabelle replicate, tabelle distribuite e del log delle transazioni necessarie per supportare la crescita nei requisiti di archiviazione. Quando l'aumento automatico è disattivata, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] restituisce un errore se le tabelle replicate distribuiti tabelle o del log delle transazioni supera l'impostazione della dimensione massima.  
  
 REPLICATED_SIZE = *dimensioni* [GB]  
 Specifica i nuovo gigabyte massime per ogni nodo di calcolo per l'archiviazione di tutte le tabelle replicate nel database da modificare. Se si intende lo spazio di archiviazione di dispositivo, è necessario moltiplicare REPLICATED_SIZE per il numero di nodi di calcolo nel dispositivo.  
  
 DISTRIBUTED_SIZE = *dimensioni* [GB]  
 Specifica i nuovo gigabyte massimi per database per archiviare tutte le tabelle distribuite nel database da modificare. La dimensione è distribuita in tutti i nodi di calcolo nel dispositivo.  
  
 LOG_SIZE = *dimensioni* [GB]  
 Specifica i nuovo gigabyte massimi per database per archiviare tutti i registri delle transazioni nel database da modificare. La dimensione è distribuita in tutti i nodi di calcolo nel dispositivo.  
  
 CRITTOGRAFIA {ON | OFF}  
 Imposta il database per l'utilizzo della crittografia (ON) o no (OFF). La crittografia può essere configurata solo per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] quando [sp_pdw_database_encryption](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e) è stata impostata su **1**. Prima di configurare la crittografia trasparente dei dati, è necessario creare una chiave di crittografia del database. Per ulteriori informazioni sulla crittografia del database, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione ALTER per il database.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I valori per REPLICATED_SIZE DISTRIBUTED_SIZE e LOG_SIZE possono essere maggiore di, uguale o minore i valori correnti per il database.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Aumento delle dimensioni e operazioni di compattazione sono approssimative. Le dimensioni effettive risultante possono variare dai parametri di dimensione.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]non esegue l'istruzione ALTER DATABASE, come operazione atomica. Se l'istruzione viene interrotta durante l'esecuzione, rimane modifiche già apportate.  
  
## <a name="locking-behavior"></a>Comportamento di blocco  
 Acquisisce un blocco condiviso per l'oggetto DATABASE. È possibile modificare un database in uso da un altro utente per la lettura o scrittura. Sono incluse le sessioni che hanno rilasciato un [utilizzare](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) istruzione nel database.  
  
## <a name="performance"></a>Prestazioni  
 Compattazione di un database può richiedere una grande quantità di tempo e risorse di sistema, a seconda delle dimensioni dei dati effettivi all'interno del database e il livello di frammentazione del disco. Ad esempio, la compattazione di un database può richiedere diverse ore o più.  
  
## <a name="determining-encryption-progress"></a>Determinare lo stato di avanzamento di crittografia  
 Utilizzare la query seguente per determinare lo stato di avanzamento della crittografia trasparente dei dati di database come una percentuale:  
  
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
  
 Per un esempio completo che illustra tutti i passaggi dell'implementazione di Transparent Data Encryption, vedere [Transparent Data Encryption &#40; Transparent Data Encryption &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Modifica l'impostazione di aumento automatico delle dimensioni  
 Impostare l'aumento automatico delle dimensioni su ON per il database `CustomerSales`.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>B. Modifica l'archiviazione massima per le tabelle replicate  
 Nell'esempio seguente imposta il limite di archiviazione tabella replicata a 1 GB per il database `CustomerSales`. Questo è il limite di archiviazione per ogni nodo di calcolo.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>C. Modifica l'archiviazione massima per le tabelle distribuite  
 Nell'esempio seguente imposta il limite di archiviazione tabella distribuita 1000 GB (un terabyte) per il database `CustomerSales`. Questo è il limite di archiviazione combinato tra il dispositivo per tutti i nodi di calcolo, non il limite di archiviazione per ogni nodo di calcolo.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>D. Modifica l'archiviazione massima per il log delle transazioni  
 Nell'esempio seguente aggiorna il database `CustomerSales` avere massimo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dimensioni log delle transazioni di 10 GB per l'applicazione.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Crea DATABASE &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
