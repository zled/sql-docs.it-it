---
title: Visualizzare informazioni sui filtri (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fa38ab23b96bcde8046a4607442b67110cd2d2a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077752"
---
# <a name="view-filter-information-transact-sql"></a>Visualizzare informazioni sui filtri (Transact-SQL)
  In questo argomento viene illustrata la procedura di utilizzo delle funzioni predefinite per la visualizzazione delle informazioni sui filtri di traccia.  
  
### <a name="to-view-filter-information"></a>Per visualizzare informazioni sui filtri  
  
1.  Eseguire **fn_trace_getfilterinfo** specificando l'ID della traccia per cui vuole ottenere informazioni sui filtri. La funzione restituisce una tabella con l'elenco dei filtri, le colonne cui i filtri sono applicati e i valori ai quali il filtro si applica.  
  
     Richiamare la funzione nel modo seguente:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
