---
title: sp_helparticlecolumns (Transact-SQL) | Documenti Microsoft
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
- sp_helparticlecolumns
- sp_helparticlecolumns_TSQL
helpviewer_keywords:
- sp_helparticlecolumns
ms.assetid: 9ea55df3-2e99-4683-88ad-bde718288bc7
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e5d332023296687f2a18d06abf0a1585c24cfca4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sphelparticlecolumns-transact-sql"></a>sp_helparticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce tutte le colonne della tabella sottostante. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione. Per i server di pubblicazione Oracle questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helparticlecolumns [ @publication = ] 'publication'   
        , [ @article = ] 'article'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =**] **'***pubblicazione***'**  
 Nome della pubblicazione in cui è contenuto l'articolo. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo per cui vengono restituite le colonne. *articolo* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@publisher**=] **'***publisher***'**  
 Specifica un non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere specificato quando viene pubblicato l'articolo richiesto da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (colonne non pubblicate) o **1** (colonne pubblicate)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id di colonna**|**int**|Identificatore della colonna.|  
|**column**|**sysname**|Nome della colonna.|  
|**Pubblicato**|**bit**|Indica se la colonna è pubblicata:<br /><br /> **0** = No<br /><br /> **1** = Sì|  
|**tipo di server di pubblicazione**|**sysname**|Tipo di dati della colonna nel server di pubblicazione.|  
|**Tipo di sottoscrittore**|**sysname**|Tipo di dati della colonna nel Sottoscrittore.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helparticlecolumns** viene utilizzata nella replica snapshot e transazionale.  
  
 **sp_helparticlecolumns** è utile per controllare una partizione verticale.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database o l'elenco di accesso per la pubblicazione corrente può eseguire **sp_helparticlecolumns**.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire e modificare un filtro di colonna](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
