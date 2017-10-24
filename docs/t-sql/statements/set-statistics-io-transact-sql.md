---
title: SET STATISTICS IO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_IO_TSQL
- IO
- IO_TSQL
- SET STATISTICS IO
dev_langs:
- TSQL
helpviewer_keywords:
- disk I/O statistics [SQL Server]
- I/O [SQL Server], disk activity information
- disks [SQL Server], statement statistics
- STATISTICS IO option
- statements [SQL Server], statistical information
- SET STATISTICS IO statement
- statistical information [SQL Server], disk activity
ms.assetid: 7033aac9-a944-4156-9ff4-6ef65717a28b
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 99e1dc183844f25002057b7cebd4729ff5f1bbe5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-statistics-io-transact-sql"></a>SET STATISTICS IO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Impone in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la visualizzazione di informazioni sulla quantità di attività del disco generata da istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET STATISTICS IO { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione STATISTICS IO è impostata su ON, vengono visualizzate informazioni statistiche. Quando è impostata su OFF, le informazioni non vengono visualizzate.  
  
 Quando l'opzione viene impostata su ON, tutte le successive istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] restituiscono le informazioni statistiche fino a quando l'opzione non viene reimpostata su OFF.  
  
 Nella tabella seguente viene visualizzato un elenco di elementi di output e la relativa descrizione.  
  
|Elemento di output|Significato|  
|-----------------|-------------|  
|**Tabella**|Nome della tabella.|  
|**Conteggio analisi**|Numero di ricerche/analisi avviate dopo aver raggiunto il livello foglia in qualsiasi direzione per recuperare tutti i valori in modo da costruire il set di dati finale per l'output.<br /><br /> Il conteggio analisi è 0 se l'indice utilizzato è univoco o cluster in una chiave primaria e si cerca un unico valore. Ad esempio `WHERE Primary_Key_Column = <value>`.<br /><br /> Il conteggio analisi è 1 quando si cerca un valore utilizzando un indice cluster non univoco definito in una colonna chiave non primaria. Questa operazione viene effettuata per verificare valori duplicati per il valore di chiave che si sta cercando. Ad esempio `WHERE Clustered_Index_Key_Column = <value>`.<br /><br /> Il conteggio analisi è N quando N è il numero di ricerche/analisi differenti avviate verso sinistra o destra nel livello foglia dopo aver individuato un valore di chiave utilizzando la chiave di indice.|  
|**letture logiche**|Numero di pagine lette dalla cache dei dati.|  
|**letture fisiche**|Numero di pagine lette dal disco.|  
|**letture read-ahead**|Numero di pagine inserite nella cache per la query.|  
|**letture logiche LOB**|Numero di **testo**, **ntext**, **immagine**, o un tipo di valori di grandi dimensioni (**varchar (max)**, **nvarchar (max)**, **varbinary (max)**) pagine lette dalla cache dei dati.|  
|**letture fisiche LOB**|Numero di **testo**, **ntext**, **immagine** o valori di grandi dimensioni tipo pagine lette dal disco.|  
|**letture read-ahead LOB**|Numero di **testo**, **ntext**, **immagine** o valori di grandi dimensioni digitare pagine inserite nella cache per la query.|  
  
 L'opzione SET STATISTICS IO viene impostata in fase di esecuzione, non in fase di analisi.  
  
> [!NOTE]  
>  Durante il recupero di colonne LOB da parte di istruzioni Transact-SQL, alcune operazioni di recupero possono richiedere più volte l'attraversamento dell'albero LOB. Per questo motivo SET STATISTICS IO può segnalare un numero di letture logiche superiore al previsto.  
  
## <a name="permissions"></a>Permissions  
 Per utilizzare l'opzione SET STATISTICS IO, gli utenti devono disporre delle autorizzazioni appropriate per eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Non sarà necessario disporre dell'autorizzazione SHOWPLAN.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato il numero di letture logiche e fisiche utilizzate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'elaborazione delle istruzioni.  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS IO ON;  
GO  
SELECT *   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS IO OFF;  
GO  
```  
  
 Set di risultati:  
  
```  
Table 'ProductCostHistory'. Scan count 1, logical reads 5, physical   
reads 0, read-ahead reads 0, lob logical reads 0, lob physical reads 0,   
lob read-ahead reads 0.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET STATISTICS TIME &#40; Transact-SQL &#41;](../../t-sql/statements/set-statistics-time-transact-sql.md)  
  
  

