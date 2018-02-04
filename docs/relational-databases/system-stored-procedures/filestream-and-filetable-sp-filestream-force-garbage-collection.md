---
title: sp_filestream_force_garbage_collection (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_filestream_force_garbage_collection
- sp_filestream_force_garbage_collection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILESTREAM [SQL Server]
- sp_filestream_force_garbage_collection
ms.assetid: 9d1efde6-8fa4-42ac-80e5-37456ffebd0b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d424bb470ac9da5edc6b314e62ffaa2e1e72b923
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="filestream-and-filetable---spfilestreamforcegarbagecollection"></a>FileStream e FileTable - sp_filestream_force_garbage_collection
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Forza il Garbage Collector di FILESTREAM all'esecuzione, eliminando qualsiasi file FILESTREAM non necessario.  
  
 Non è possibile rimuovere un contenitore FILESTREAM finché il Garbage Collector non ha completato la rimozione di tutti i file eliminati all'interno di esso. Il Garbage Collector di FILESTREAM viene eseguito automaticamente. Tuttavia, se è necessario per rimuovere un contenitore prima il garbage collector ha eseguito, è possibile utilizzare sp_filestream_force_garbage_collection per eseguire manualmente il garbage collector.  
  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_filestream_force_garbage_collection  
    [ @dbname = ]  'database_name',  
    [ @filename = ] 'logical_file_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 **@dbname** = *database_name***'**  
 Indica il nome del database in cui eseguire il Garbage Collector.  
  
> [!NOTE]  
>  *dbname* è **sysname**. Se viene omesso, verrà considerato il database corrente.  
  
 **@filename** = *logical_file_name*  
 Indica il nome logico del contenitore FILESTREAM in cui eseguire il Garbage Collector. **@filename**è facoltativo. Se non viene specificato alcun nome di file logico, il garbage collector Elimina tutti i contenitori FILESTREAM nel database specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
  
|||  
|-|-|  
|Valore|Descrizione|  
|0|Operazione riuscita|  
|1|Operazione non riuscita|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Valore|Description|  
|-----------|-----------------|  
|*file_name*|Indica il nome del contenitore FILESTREAM|  
|*num_collected_items*|Indica il numero di elementi FILESTREAM (file/directory) che sono stati sottoposti a Garbage Collection (eliminati) in questo contenitore.|  
|*num_marked_for_collection_items*|Indica il numero di elementi FILESTREAM (file/directory) che sono stati contrassegnati per il Garbage Collection in questo contenitore. Questi elementi non sono ancora stati eliminati, ma potrebbero essere idonei per l'eliminazione dopo la fase garbage collection.|  
|*num_unprocessed_items*|Indica il numero di elementi FILESTREAM (file o directory) idonei che non sono stati elaborati per il Garbage Collection in questo contenitore FILESTREAM. Gli elementi possono non essere elaborati per i vari motivi, tra cui:<br /><br /> File che devono essere bloccati perché non è stato eseguito un checkpoint o backup del log.<br /><br /> File nel modello di recupero FULL o BULK_LOGGED.<br /><br /> È presente una transazione attiva con esecuzione prolungata.<br /><br /> Il processo di lettura log repliche non è stata eseguita. Vedere il white paper [FILESTREAM Storage in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=209156) per ulteriori informazioni.|  
|*last_collected_xact_seqno*|Restituisce l'ultimo numero di sequenza del file di log (LSN) corrispondente fino a cui i file sono stati sottoposti a Garbage Collection per il contenitore FILESTREAM specificato.|  
  
## <a name="remarks"></a>Osservazioni  
 Esegue in modo esplicito l'attività Garbage Collector per FILESTREAM per il completamento nel database richiesto (e il contenitore FILESTREAM). I file che non sono più necessari vengono rimossi dal processo di Garbage Collection. Il tempo necessario per il completamento di questa operazione dipende dalle dimensioni dei dati FILESTREAM in tale database o contenitore nonché dalla quantità di attività DML recentemente eseguita sui dati FILESTREAM. Sebbene questa operazione possa essere eseguita con il database in modalità online, ciò potrebbe influire sulle prestazioni del database durante l'esecuzione a causa delle varie attività I/O eseguite dal processo di Garbage Collection.  
  
> [!NOTE]  
>  Si consiglia di eseguire questa operazione solo quando è necessario e in orario diverso da quello lavorativo.  
  
È possibile eseguire contemporaneamente più chiamate di questa stored procedure solo in contenitori separati o database separati.  

A causa di operazioni in fase di 2, la stored procedure deve essere eseguita due volte per eliminare effettivamente i file Filestream sottostanti.  

Operazione di Garbage Collection (GC) si basa sul troncamento del log. Pertanto, se i file sono stati eliminati di recente in un database con modello di recupero con registrazione completa, sono GC ed solo dopo che viene eseguito un backup del log di tali parti del log delle transazioni e la parte del log è contrassegnata come inattiva. In un database con modello di recupero con registrazione minima, si verifica un troncamento del log dopo un `CHECKPOINT` è stata eseguita sul database.  


## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo del database db_owner.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti viene eseguito il Garbage Collector per i contenitori FILESTREAM nel database `FSDB`.  
  
### <a name="a-specifying-no-container"></a>A. Specifica di nessun contenitore  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB';  
```  
  
### <a name="b-specifying-a-container"></a>B. Specifica di un contenitore  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB',
    @filename = N'FSContainer';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Archiviazione FILESTREAM in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=209156)  
  
  
