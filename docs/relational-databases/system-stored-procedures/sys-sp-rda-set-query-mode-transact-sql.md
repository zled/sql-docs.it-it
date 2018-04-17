---
title: sys.sp_rda_set_query_mode (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a803ed67f498a04c56700129869140e3b8c4eda1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="syssprdasetquerymode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Specifica se le query sui database abilitati per l'estensione corrente e le relative tabelle restituiscono dati locali e remoti (impostazione predefinita) o solo i dati locali.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @mode = ] *@mode*  
 È uno dei valori seguenti.  
  
-   **DISABILITATO** esito negativo di tutte le query sulle tabelle abilitate per l'estensione.  
  
-   **LOCAL_ONLY** le query sulle tabelle abilitate per l'estensione restituiscono solo dati locali.  
  
-   **LOCAL_AND_REMOTE** le query sulle tabelle abilitate per l'estensione restituiscono dati locali e remoti. Questo è il comportamento predefinito.  
  
 [ @force = ]  *@force*  
 È un valore di bit facoltativo che è possibile impostare su 1 se si desidera modificare la modalità query senza convalida.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="remarks"></a>Osservazioni  
 Le seguenti stored procedure estese, inoltre, impostare la modalità query per un database abilitato per l'estensione.  
  
-   **sp_rda_deauthorize_db**  
  
     Dopo aver eseguito **sp_rda_deauthorize_db** , esito negativo di tutte le query su tabelle e database abilitati per l'estensione. Vale a dire la modalità query è DISABILITATO. Per uscire da questa modalità, effettuare una delle seguenti operazioni.  
  
    -   Eseguire [Sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) riconnettersi al database Azure remoto. Questa operazione automaticamente Reimposta la modalità query LOCAL_AND_REMOTE, ovvero il comportamento predefinito per l'estensione Database. Ovvero, le query restituiscono risultati dai dati locali e remoti.  
  
    -   Eseguire [sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) con l'argomento LOCAL_ONLY per consentire le query di continuare a eseguire solo i dati locali.  
  
-   **sp_rda_reauthorize_db**  
  
     Quando si esegue [Sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) per ristabilire la connessione al database Azure remoto, questa operazione reimposta automaticamente la modalità query LOCAL_AND_REMOTE, ovvero il comportamento predefinito per L'estensione Database. Ovvero, le query restituiscono risultati dai dati locali e remoti.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
