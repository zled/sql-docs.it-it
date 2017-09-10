---
title: SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT
- SET_QUERY_GOVERNOR_COST_LIMIT_TSQL
- QUERY_GOVERNOR_COST_LIMIT
- QUERY_GOVERNOR_COST_LIMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT statement
- connections [SQL Server], overriding
- QUERY_GOVERNOR_COST_LIMIT option
- overriding connection values
ms.assetid: 3424bb44-6915-462d-a8d7-fe834af81387
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6090e52a9b3b2a701129e6cebeaa8460ab02fc43
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-querygovernorcostlimit-transact-sql"></a>SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esegue l'override attualmente configurato **di query governor cost limit** valore per la connessione corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET QUERY_GOVERNOR_COST_LIMIT value  
```  
  
## <a name="arguments"></a>Argomenti  
 *Valore*  
 Valore numerico o integer che specifica la periodo massimo consentito per l'esecuzione di una query. I valori vengono arrotondati per difetto al valore intero più vicino. I valori negativi vengono arrotondati a 0. Query Governor non consente l'esecuzione delle query il cui costo stimato supera tale valore. Se si specifica 0 (valore predefinito), Query Governor verrà disabilitato e sarà possibile eseguire tutte le query senza limiti di tempo.  
  
 Il costo delle query equivale al tempo trascorso, in secondi, stimato per l'esecuzione di una query in una configurazione hardware specifica.  
  
## <a name="remarks"></a>Osservazioni  
 L'opzione SET QUERY_GOVERNOR_COST_LIMIT viene utilizzata solo per la connessione corrente e solo per la durata della connessione corrente. Utilizzare il [configurare query governor cost limit opzione di configurazione del Server](../../database-engine/configure-windows/configure-the-query-governor-cost-limit-server-configuration-option.md)opzione di **sp_configure** per modificare a livello di server query governor cost valore limite. Per ulteriori informazioni sulla configurazione di questa opzione, vedere [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) e [opzioni di configurazione del Server &#40; SQL Server &#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 L'opzione SET QUERY_GOVERNOR_COST_LIMIT viene impostata in fase di esecuzione, non in fase di analisi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

