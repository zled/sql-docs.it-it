---
title: sp_batch_params (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0327f7434458667490c0557a8a254accfcfe3bb6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spbatchparams-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di righe che contiene informazioni sui parametri inclusi un [!INCLUDE[tsql](../../includes/tsql-md.md)] batch. **sp_batch_params** solo analizza il batch specificato e restituisce informazioni sui valori dei parametri incorporati. e non esegue il batch, né modifica l'ambiente di esecuzione.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@tsqlbatch =**] **'***tsqlbatch***'**  
 È una stringa Unicode che contiene un [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione o batch per il parametro informazioni sono che si desidera. *TSqlBatch* è **nvarchar (max)** o implicitamente convertibile in **nvarchar (max)**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**PARAMETER_NAME**|**sysname**|Nome del parametro rilevato nel batch da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**COLUMN_TYPE**|**smallint**|Questo campo restituisce uno dei valori seguenti:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> Questa colonna è sempre 0.|  
|**DATA_TYPE**|**smallint**|Tipo di dati del parametro (codice integer per un tipo di dati ODBC). Se non è possibile effettuare il mapping di questo tipo di dati a un tipo ISO, il valore è NULL. Cui viene restituito il nome del tipo di dati nativi di **TYPE_NAME** colonna. Il valore è sempre NULL.|  
|**TYPE_NAME**|**sysname**|Rappresentazione in forma di stringa del tipo di dati visualizzato dal sistema DBMS sottostante. Questo valore è NULL.|  
|**PRECISIONE**|**int**|Numero di cifre significative. Il valore restituito per il **precisione** colonna è in base 10.|  
|**LENGTH**|**int**|Dimensioni di trasferimento dei dati. Questo valore è NULL.|  
|**SCALA**|**smallint**|Numero di cifre a destra del separatore decimale. Questo valore è NULL.|  
|**RADICE**|**smallint**|Base per i tipi di dati numerici. Questo valore è NULL.|  
|**AMMETTE VALORI NULL**|**smallint**|Specifica se i valori Null sono supportati o meno:<br /><br /> 1 = Per il parametro è possibile creare il tipo di dati con supporto per valori Null.<br /><br /> 0 = I valori Null non sono supportati.<br /><br /> Questo valore è NULL.|  
|**SQL_DATA_TYPE**|**smallint**|Valore del tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizzato nel campo TYPE del descrittore. Questa colonna corrisponde alla **DATA_TYPE** colonna, tranne che per il **datetime** e ISO **intervallo** tipi di dati. In questa colonna viene sempre restituito un valore. Questo valore è NULL.|  
|**SQL_DATETIME_SUB**|**smallint**|Il **datetime** o ISO **intervallo** sottocodice se il valore di **SQL_DATA_TYPE** è SQL_DATETIME o SQL_INTERVAL. Per i dati di tipi diversi da **datetime** e ISO **intervallo**, questa colonna è NULL. Questo valore è NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Lunghezza massima in byte di un **carattere** o **binario** parametro di tipo di dati. Per gli tutti gli altri tipi di dati, il valore di questa colonna è NULL. Il valore è sempre NULL.|  
|**ORDINAL_POSITION**|**int**|Posizione ordinale del parametro nel batch. Se il nome del parametro viene ripetuto più volte, questa colonna include il numero ordinale della prima occorrenza. Il primo parametro è associato al numero ordinale 1. In questa colonna viene sempre restituito un valore.|  
  
## <a name="permissions"></a>Permissions  
 Autorizzazione per l'esecuzione **sp_batch_params** è concessa al **pubblica**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente una query viene passata a `sp_batch_params`. Il set di risultati enumera l'elenco dei valori dei parametri incorporati.  
  
```  
DECLARE @SQLString nvarchar(500);  
/* Build the SQL string */  
SET @SQLString =  
     N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
     WHERE BusinessEntityID = @BusinessEntityID';  
EXECUTE sp_batch_params @SQLString;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di Stored procedure](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Esecuzione della Stored procedure procedure &#40; ODBC &#41;](http://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [Esecuzione della Stored procedure &#40; OLE DB &#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
