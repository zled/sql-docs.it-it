---
title: sp_polybase_join_group | Microsoft Docs
ms.custom: 
ms.date: 05/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sp_polybase_join_group
helpviewer_keywords:
- PolyBase
ms.assetid: 48066431-fed2-4a8a-85af-ac704689e183
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f6e4a77e5ce1341269bf9220c5d2a5305b4c314
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="polybase-stored-procedures---sppolybasejoingroup"></a>Stored procedure di PolyBase - sp_polybase_join_group
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Aggiunge un'istanza di SQL Server come nodo di calcolo a un gruppo di PolyBase per il calcolo di scalabilità orizzontale.  
  
 L'istanza di SQL Server deve disporre di [PolyBase](../../relational-databases/polybase/polybase-guide.md) funzionalità installata.  PolyBase consente l'integrazione di origini dati non SQL Server, ad esempio l'archiviazione blob di Hadoop e Azure. Vedere anche [sp_polybase_leave_group &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>Argomenti  
 *@head_node_address* = N'*head_node_address*'  
 Il nome del computer che ospita il nodo head di SQL Server del gruppo di scalabilità orizzontale di PolyBase. *@head_node_address*è nvarchar (255).  
  
 *@dms_control_channel_port* = dms_control_channel_port  
 La porta in cui è in esecuzione il canale di controllo per il nodo head PolyBase Data Movement Service. *@dms_control_channel_port*è un unsigned int16. Il valore predefinito è **16450**.  
  
 *@head_node_sql_server_instance_name* = head_node_sql_server_instance_name  
 Il nome dell'istanza di SQL Server del nodo head del gruppo di scalabilità orizzontale di PolyBase. *@head_node_sql_server_instance_name*è nvarchar (16).  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="remarks"></a>Osservazioni  
 Dopo aver eseguito la stored procedure, arrestare il motore PolyBase e riavviare PolyBase Data Movement Service nel computer. Per verificare eseguire sulla seguente DMV nel nodo head: **Sys.dm exec_compute_nodes**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio viene aggiunto il computer corrente come nodo di calcolo a un gruppo di PolyBase.  Il nome del nodo head è **HST01** e il nome dell'istanza di SQL Server nel nodo head è **MSSQLSERVER**.  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
