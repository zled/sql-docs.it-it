---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00919111d7df7f3e6a3077a5c99e355c93abacad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver1793"></a>MSSQLSERVER_1793
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1793|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Testo del messaggio|Impossibile eliminare l'indice '%.*ls'. Schema di partizione non specificato per i dati FILESTREAM.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio viene visualizzato quando si tenta di eliminare un indice cluster in una tabella che contiene dati FILESTREAM e si specifica una clausola **MOVE TO** per i dati di base, ma non si specifica una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
## <a name="user-action"></a>Azione dell'utente  
Quando si elimina un indice cluster in una tabella che contiene dati FILESTREAM, utilizzare una delle opzioni seguenti:  
  
-   Specificare sia una clausola **MOVE TO** per i dati di base sia una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
-   Non specificare una clausola **MOVE TO** per i dati di base né una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
L'esempio seguente ha esito negativo in quanto viene specificato uno schema di partizione per i dati di base, ma non per i dati FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
L'esempio seguente ha esito positivo in quanto viene specificata sia una clausola **MOVE TO** per i dati di base sia una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
L'esempio seguente ha anch'esso esito positivo in quanto non viene specificata né una clausola **MOVE TO** per i dati di base né una clausola **FILESTREAM_ON** per i dati FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
