---
title: DBCC SHRINKLOG (Azure SQL Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f572bdbf8a0606c6652de4838b7b72664040156a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-shrinklog-azure-sql-data-warehouse"></a>DBCC SHRINKLOG (Azure SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Riduce le dimensioni del log delle transazioni *tra il dispositivo* per l'oggetto corrente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] database. I dati viene deframmentati per compattare il log delle transazioni. Nel corso del tempo, il log delle transazioni di database può diventare frammentato e inefficiente. Utilizzare DBCC SHRINKLOG per ridurre la frammentazione e ridurre le dimensioni del log.
  
![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
DIMENSIONI = { *target_size* [MB | **GB** | TB]} | **Predefinito**.  
*target_size* è la dimensione desiderata per il log delle transazioni, in tutti i nodi di calcolo, al termine dell'esecuzione DBCC SHRINKLOG. È un numero intero maggiore di 0.  
Le dimensioni del log viene misurata in megabyte (MB), gigabyte (GB) o terabyte (TB). È la dimensione complessiva del log delle transazioni in tutti i nodi di calcolo.  
Per impostazione predefinita, DBCC SHRINKLOG consente di ridurre il log delle transazioni per le dimensioni del log archiviate nei metadati per il database. Le dimensioni del log dei metadati sono determinata dal parametro LOG_SIZE [CREATE DATABASE &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) o [ALTER DATABASE &#40; Azure SQL Data Warehouse &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md). DBCC SHRINKLOG riduce le dimensioni del log delle transazioni per il valore predefinito quando dimensioni `SIZE=DEFAULT` è specificato, oppure quando il `SIZE` clausola viene omessa.
  
WITH NO_INFOMSGS  
Nei risultati DBCC SHRINKLOG non vengono visualizzati i messaggi informativi.  
  
## <a name="permissions"></a>Permissions  
È richiesta l'autorizzazione ALTER SERVER STATE.
  
## <a name="general-remarks"></a>Osservazioni generali  
DBCC SHRINKLOG non modifica le dimensioni del log archiviate nei metadati per il database. I metadati continua a contenere il parametro LOG_SIZE che è stato specificato nell'istruzione CREATE DATABASE o ALTER DATABASE.
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Compattare il log delle transazioni per le dimensioni originali specificata dal DATABASE di creare.  
Si supponga che il log delle transazioni per il database di indirizzi è stato impostato su 100 MB, quando è stato creato il database di indirizzi. Ovvero, l'istruzione CREATE DATABASE per gli indirizzi era LOG_SIZE = 100 MB. A questo punto, si supponga che il file di log ha raggiunto su 150 MB e si desidera compattare nuovamente a 100 MB.
  
Ognuna delle istruzioni seguenti si tenterà di compattare il log delle transazioni per il database di indirizzi per la dimensione predefinita di 100 MB. Se la compattazione del log a 100 MB comporta la perdita di dati, DBCC SHRINKLOG verrà compattare il log per il più piccolo possibile, dimensioni maggiori di 100 MB, senza perdita di dati.
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  

