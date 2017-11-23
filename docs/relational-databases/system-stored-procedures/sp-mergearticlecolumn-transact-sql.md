---
title: sp_mergearticlecolumn (Transact-SQL) | Documenti Microsoft
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
- sp_mergearticlecolumn
- sp_mergearticlecolumn_TSQL
helpviewer_keywords: sp_mergearticlecolumn
ms.assetid: b4f2b888-e094-4759-a472-d893638995eb
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 083d6d27d9417a76f9cafc1c3726e3f7c10df6d7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spmergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Suddivide una pubblicazione di tipo merge in partizioni verticali. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_mergearticlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column'  
    [ , [ @operation = ] 'operation'   
    [ , [ @schema_replication = ] 'schema_replication' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =**] **'***pubblicazione***'**  
 Nome della pubblicazione. *Pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article =**] **'***articolo***'**  
 Nome dell'articolo della pubblicazione. *articolo* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@column =**] **'***colonna***'**  
 Identifica le colonne su cui creare la partizione verticale. *colonna* è **sysname**, con un valore predefinito è NULL. Se NULL e `@operation = N'add'`, per impostazione predefinita all'articolo vengono aggiunte tutte le colonne della tabella di origine. *colonna* non può essere NULL quando *operazione* è impostato su **eliminare**. Per escludere le colonne da un articolo, eseguire **sp_mergearticlecolumn** e specificare *colonna* e `@operation = N'drop'` per ogni colonna da rimuovere dall'oggetto specificato *articolo*.  
  
 [  **@operation =**] **'***operazione***'**  
 Stato della replica. *operazione* è **nvarchar (4)**, con valore predefinito è ADD. **aggiungere** contrassegna la colonna per la replica. **eliminare** Cancella la colonna.  
  
 [  **@schema_replication=**] **'***schema_replication***'**  
 Specifica che le modifiche dello schema verranno propagate quando verrà eseguito l'agente di merge. *schema_replication* è **nvarchar (5)**, con un valore predefinito è FALSE.  
  
> [!NOTE]  
>  Solo **FALSE** è supportato per *schema_replication*.  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Abilita o disabilita la funzionalità che consente di invalidare uno snapshot. *force_invalidate_snapshot* è un **bit**, il valore predefinito è **0**.  
  
 **0** specifica che le modifiche apportate all'articolo di merge non provocherà lo snapshot.  
  
 **1** specifica che le modifiche apportate all'articolo di merge potrebbero invalidare lo snapshot potrebbe non essere valido, e se è questo il caso, il valore **1** concede l'autorizzazione per l'esecuzione del nuovo snapshot.  
  
 [  **@force_reinit_subscription =]***force_reinit_subscription*  
 Abilita o disabilita la funzionalità che consente di reinizializzare la sottoscrizione. *force_reinit_subscription* è di tipo bit il valore predefinito è **0**.  
  
 **0** indica che le modifiche apportate all'articolo di merge non comportano la reinizializzazione della sottoscrizione.  
  
 **1** specifica che le modifiche apportate all'articolo di merge possono causare la reinizializzazione della sottoscrizione e se è questo il caso, il valore **1** concede l'autorizzazione per la reinizializzazione della sottoscrizione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_mergearticlecolumn** viene utilizzata nella replica di tipo merge.  
  
 Non è possibile eliminare una colonna Identity dall'articolo se viene utilizzata la gestione automatica degli intervalli di valori Identity. Per altre informazioni, vedere [Replicare colonne Identity](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Se un'applicazione imposta una nuova partizione verticale dopo la creazione dello snapshot iniziale, è necessario generare un nuovo snapshot e riassociarlo a ogni sottoscrizione. Gli snapshot vengono associati alla successiva esecuzione pianificata dell'agente snapshot e di distribuzione o di merge.  
  
 Se si utilizza il rilevamento a livello di riga per il rilevamento dei conflitti (impostazione predefinita), la tabella di base può includere fino a 1.024 colonne, che devono tuttavia essere filtrate dall'articolo in modo da pubblicare un massimo di 246 colonne. Se viene utilizzato il rilevamento a livello di colonna, nella tabella di base possono essere incluse al massimo 246 colonne.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_mergearticlecolumn**.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire e modificare un filtro di Join tra articoli di Merge](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Filtrare i dati pubblicati](../../relational-databases/replication/publish/filter-published-data.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
