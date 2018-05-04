---
title: sp_script_synctran_commands (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3705a28d85c7375aad701d77a517719778954c25
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spscriptsynctrancommands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Genera uno script che contiene il **sp_addsynctrigger** chiamate da applicare nei Sottoscrittori per le sottoscrizioni aggiornabili. È presente **sp_addsynctrigger** chiamare per ogni articolo nella pubblicazione. Lo script generato contiene inoltre il **sp_addqueued_artinfo** chiamate che creano la **MSsubsciption_articles** tabella in cui è necessaria per elaborare le pubblicazioni in coda. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione per cui si desidera creare lo script. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@article** =] **'***articolo***'**  
 Nome dell'articolo per cui si desidera creare lo script. *articolo* viene **sysname**, il valore predefinito è **tutti**, che consente di specificare tutti gli articoli vengono inseriti nello script.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="results-set"></a>Set di risultati  
 **sp_script_synctran_commands** restituisce un set di risultati è costituito da una singola **nvarchar(4000** colonna. Il set di risultati forma gli script completi necessari per creare entrambe le **sp_addsynctrigger** e **sp_addqueued_artinfo** chiamate da applicare nei Sottoscrittori.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_script_synctran_commands** viene utilizzata nella replica snapshot e transazionale.  
  
 **sp_addqueued_artinfo** viene utilizzato per le sottoscrizioni aggiornabili in coda.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_script_synctran_commands**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
