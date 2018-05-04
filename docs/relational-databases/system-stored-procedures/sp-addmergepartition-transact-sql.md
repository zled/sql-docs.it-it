---
title: sp_addmergepartition (Transact-SQL) | Documenti Microsoft
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
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e04e556e663b83803e67c7afb7531869f210b7b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una partizione filtrata in modo dinamico per una sottoscrizione filtrata in base ai valori [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) o [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) nel Sottoscrittore. Questa stored procedure viene eseguita nel server di pubblicazione nel database da pubblicare e viene utilizzata per la generazione manuale di partizioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publication**=] **'***pubblicazione***'**  
 Pubblicazione di tipo merge su cui viene creata la partizione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito. Se *suser_sname* è specificato, il valore di *hostname* deve essere NULL.  
  
 [ **@suser_sname**=] **'***suser_sname***'**  
 È il valore utilizzato durante la creazione della partizione per una sottoscrizione filtrata in base al valore della [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) funzione nel Sottoscrittore. *SUSER_SNAME* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@host_name**=] **'***host_name***'**  
 È il valore utilizzato durante la creazione della partizione per una sottoscrizione filtrata in base al valore della [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) funzione nel Sottoscrittore. *HOST_NAME* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addmergepartition** viene utilizzata nella replica di tipo merge.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addmergepartition**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare uno Snapshot per una pubblicazione di tipo Merge con filtri con parametri](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
