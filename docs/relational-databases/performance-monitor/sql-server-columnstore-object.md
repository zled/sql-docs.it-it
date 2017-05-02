---
title: Oggetto Columnstore di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 418dddd9e87b490170b6d07c03d93a6eea912edf
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-columnstore-object"></a>SQL Server, oggetto Columnstore
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  L'oggetto **SQLServer:Columnstore** fornisce i contatori per monitorare l'esecuzione dell'indice columnstore in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Nella tabella seguente sono descritti i contatori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Columnstore** counters.  
  
|Contatori Columnstore|Descrizione|  
|--------------------------|-----------------|  
|**Rowgroup differenziali chiusi**|Numero di rowgroup differenziali chiusi.|  
|**Rowgroup differenziali compressi**|Numero di rowgroup differenziali compressi.|  
|**Rowgroup differenziali creati**|Numero di rowgroup differenziali creati.|  
|**Percentuale riscontri nella cache di segmenti**|Percentuale di segmenti di colonna trovati nel pool columnstore senza dover eseguire una lettura dal disco.|  
|**Base riscontri nella cache di segmenti**|Solo per uso interno.|
|**Letture segmenti/sec**|Numero di letture fisiche di segmenti eseguite.|  
|**Totale buffer di eliminazione migrati**|Numero di operazioni di pulizia del buffer di eliminazione eseguite dal motore di tuple.|  
|**Totale valutazioni dei criteri di unione**|Numero di valutazioni eseguite per i criteri di unione per columnstore.|  
|**Totale rowgroup compressi**|Numero totale di rowgroup compressi.|  
|**Rowgroup totali adatti per l'operazione di unione**|Numero di rowgroup di origine adatti per l'operazione MERGE dall'avvio di SQL Server.|  
|**Totale rowgroup compressi tramite l'operazione MERGE**|Numero di rowgroup di destinazione compressi creati con l'operazione MERGE dall'avvio di SQL Server.|  
|**Totale rowgroup di origine uniti**|Numero di rowgroup di origine uniti dall'avvio di SQL Server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  

