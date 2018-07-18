---
title: sys.dm_pdw_hadoop_operations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f158ac7c5904e54daf384ddbf8196dbf8fd5f66f
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36925972"
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni processo MapReduce è propagato ad Hadoop come parte dell'esecuzione un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] query su una tabella esterna Hadoop. Ogni processo MapReduce rappresenta uno dei predicati della query. Viene utilizzato solo quando la distribuzione del predicato è abilitata per le query su tabelle esterne di Hadoop.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|ID per questa operazione esterna Hadoop.|Stesso ID in [DM pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Indice del passaggio della query che fa riferimento a questa operazione di Hadoop.|Uguale a step_index nel [DM pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Descrive il tipo di operazione esterna.|'Operation Hadoop esterno'|  
|operation_name|**nvarchar(4000)**|L'ID di processo per un processo MapReduce. Questo valore viene restituito da Hadoop dopo [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] invia il processo.||  
|map_progress|**float**|La percentuale di dati di input che sono stati utilizzati finora dal processo di mapping.|Numero tra e includerlo, 0 e 100 in virgola mobile.|  
|reduce_progress|**int**|La percentuale del processo di riduzione che è stata completata...|Numero tra e includerlo, 0 e 100 in virgola mobile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
