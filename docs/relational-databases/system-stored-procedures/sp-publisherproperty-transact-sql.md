---
title: sp_publisherproperty (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7446f507b688010f3044ff237d778f9b31b54fe8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza o modifica le proprietà di server di pubblicazione per non[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione. Questa stored procedure viene eseguita nel database di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [**@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione eterogeneo. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [**@propertyname** =] **'***propertyname***'**  
 Nome della proprietà da impostare. *PropertyName* viene **sysname**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**xactsetbatching**|Indica se le transazioni nel server di pubblicazione sono raggruppate in set con consistenza transazionale per elaborazioni successive, noti come Xactset. Il valore **abilitato** significa che è possibile creare XactSet, ovvero l'impostazione predefinita. Il valore **disabilitato** significa che XactSet esistenti vengono elaborati da alcun nuovo XactSet viene creati.|  
|**xactsetjob**|Indica se è attivo il processo Xactset per la creazione di Xactset. Il valore **abilitato** significa che il processo Xactset viene eseguito periodicamente per la creazione di XactSet nel server di pubblicazione. Il valore **disabilitato** significa che il XactSet vengono creati solo dall'agente di lettura Log quando esegue il polling server di pubblicazione per le modifiche.|  
|**xactsetjobinterval**|Intervallo tra le esecuzioni del processo Xactset, espresso in minuti.|  
  
 Quando *propertyname* viene omesso vengono restituite tutte le proprietà impostabili.  
  
 [**@propertyvalue** =] **'***propertyvalue***'**  
 Nuovo valore per la proprietà. *PropertyValue* viene **sysname**, con valore predefinito è NULL. Quando *propertyvalue* viene omesso, l'impostazione corrente per la proprietà viene restituita.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Restituisce le proprietà delle pubblicazioni seguenti che è possibile impostare:<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**PropertyValue**|**sysname**|È l'impostazione corrente per la proprietà di **propertyname** colonna.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_publisherproperty** viene utilizzata nella replica transazionale per non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
 Quando solo *publisher* viene specificato, il set di risultati include le impostazioni correnti per tutte le proprietà che possono essere impostate.  
  
 Quando *propertyname* viene specificato, viene visualizzata solo la proprietà nel set di risultati.  
  
 Se si specificano tutti i parametri, la proprietà viene modificata e non viene restituito alcun set di risultati.  
  
 Quando si modifica il **xactsetjobinterval** proprietà per un processo in esecuzione, è necessario riavviare il processo per il nuovo intervallo diventino effettive.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server nel server di distribuzione possono eseguire **sp_publisherproperty**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare il processo del set di transazioni per un server di pubblicazione Oracle &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
