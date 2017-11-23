---
title: sp_requestpeerresponse (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords: sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d0a4009c5a6615a000989e2d41f2902ac37535f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sprequestpeerresponse-transact-sql"></a>sp_requestpeerresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quando viene eseguita da un nodo in una topologia peer-to-peer, questa procedura richiede una risposta da ogni altro nodo della topologia. Tramite l'esecuzione di questa procedura e l'analisi delle risposte corrispondenti è possibile verificare che tutti i precedenti comandi siano stati recapitati ai nodi che inviano una risposta. Questa stored procedure viene eseguita in qualsiasi database del nodo richiedente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_requestpeerresponse [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
    [ , [ @request_id = ] request_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione in una topologia peer-to-peer per cui si desidera verificare lo stato. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@description** =] **'***descrizione***'**  
 Informazioni specificate dall'utente che è possibile utilizzare per identificare le singole richieste di stato. *Descrizione* è **nvarchar (4000)**, con un valore predefinito è NULL.  
  
 [  **@request_id**  =] *request_id*  
 Restituisce l'ID della nuova richiesta. *request_id* è **int** ed è un parametro OUTPUT. Questo valore può essere utilizzato durante l'esecuzione [sp_helppeerresponses &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) per visualizzare tutte le risposte a una richiesta di stato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_requestpeerresponse** viene utilizzata nella replica transazionale peer-to-peer.  
  
 **sp_requestpeerresponse** viene utilizzato per garantire che tutti i comandi sono stati ricevuti da tutti gli altri nodi prima di ripristinare un database pubblicato in una topologia peer-to-peer. Inoltre, viene utilizzata durante la replica di modifiche DDL (Data Definition Language) apportate mentre un nodo era offline per stimare quando tali modifiche verranno recapitate agli altri nodi.  
  
 **sp_requestpeerresponse** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_requestpeerresponse**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_deletepeerrequesthistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
