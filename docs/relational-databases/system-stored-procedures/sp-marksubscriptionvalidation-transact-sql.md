---
title: sp_marksubscriptionvalidation (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1b088b43cfc625591d5160b6818949b0c933a696
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32997688"
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrassegna la transazione aperta corrente come transazione di convalida a livello di sottoscrizione per il Sottoscrittore specificato. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publication**=] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@subscriber**=] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è di tipo sysname e non prevede alcun valore predefinito.  
  
 [  **@destination_db=**] **'***destination_db***'**  
 Nome del database di destinazione. *destination_db* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Specifica un non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato per una pubblicazione a cui appartiene un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_marksubscriptionvalidation** viene utilizzata nella replica transazionale.  
  
 **sp_marksubscriptionvalidation** non supporta non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori.  
  
 Per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione non è possibile eseguire **sp_marksubscriptionvalidation** da una transazione esplicita. perché le transazioni esplicite non sono supportate attraverso la connessione al server collegato utilizzata per l'accesso al server di pubblicazione.  
  
 **sp_marksubscriptionvalidation** deve essere utilizzata in combinazione con [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), specificando il valore **1** per  *subscription_level*e può essere utilizzato con altre chiamate a **sp_marksubscriptionvalidation** per contrassegnare la transazione aperta corrente per altri sottoscrittori.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Esempio  
 È possibile applicare la query seguente al database di pubblicazione per inviare comandi di convalida a livello di sottoscrizione. Tali comandi vengono quindi intercettati dagli agenti di distribuzione dei Sottoscrittori specificati. Si noti che la prima transazione convalida l'articolo '**art1**', mentre la seconda transazione convalida'**art2**'. Si noti inoltre che le chiamate a **sp_marksubscriptionvalidation** e [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) sono state inserite in una transazione. È consigliabile solo una chiamata a [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) per ogni transazione. Infatti [sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) mantiene un blocco condiviso sulla tabella di origine per la durata della transazione. Le transazioni brevi consentono di ottenere la massima concorrenza.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Convalidare i dati replicati](../../relational-databases/replication/validate-replicated-data.md)  
  
  
