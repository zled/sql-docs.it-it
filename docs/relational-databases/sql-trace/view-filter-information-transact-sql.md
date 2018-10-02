---
title: Visualizzare informazioni sui filtri (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7c0c84e05b35d498b00e0cc78df756d223bdaad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632515"
---
# <a name="view-filter-information-transact-sql"></a>Visualizzare informazioni sui filtri (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene illustrata la procedura di utilizzo delle funzioni predefinite per la visualizzazione delle informazioni sui filtri di traccia.  
  
### <a name="to-view-filter-information"></a>Per visualizzare informazioni sui filtri  
  
1.  Eseguire **fn_trace_getfilterinfo** specificando l'ID della traccia per cui vuole ottenere informazioni sui filtri. La funzione restituisce una tabella con l'elenco dei filtri, le colonne cui i filtri sono applicati e i valori ai quali il filtro si applica.  
  
     Richiamare la funzione nel modo seguente:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
