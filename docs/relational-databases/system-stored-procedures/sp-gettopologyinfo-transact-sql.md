---
title: sp_gettopologyinfo (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_gettopologyinfo_TSQL
- sp_gettopologyinfo
helpviewer_keywords:
- sp_gettopologyinfo
ms.assetid: 8bbe8a06-a4aa-4219-8402-12db6a4682c6
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0ce0a01d74c16911586fca74237bc80d95fa21ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spgettopologyinfo-transact-sql"></a>sp_gettopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulla topologia di replica transazionale peer-to-peer. Eseguire [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) per raccogliere informazioni prima di eseguire questa procedura.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_gettopologyinfo [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @request_id=] *request_id*  
 ID di una richiesta di stato di topologia. *request_id* viene **int**, con un valore predefinito è NULL. Per ottenere un ID, utilizzare il @request_id parametro di output [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) o eseguire una query di [MSpeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) tabella di sistema.  
  
## <a name="result-sets"></a>Set di risultati  
 sp_gettopologyinfo restituisce un set di risultati con un'unica colonna XML. I dati nella colonna XML sono lo stesso quando i dati di [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) tabella di sistema.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 sp_gettopologyinfo viene utilizzato nella replica transazionale peer-to-peer. Eseguire [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) prima di eseguire sp_gettopologyinfo. Queste procedure vengono utilizzate dalla Configurazione guidata topologia peer-to-peer, ma possono anche essere utilizzate direttamente se si richiedono informazioni sulla topologia in un formato XML. Se si preferiscono risultati tabulari, eseguire una query di [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) tabella di sistema.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server sysadmin o al ruolo predefinito del database db_owner.  
  
## <a name="see-also"></a>Vedere anche  
 [Replica transazionale peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
