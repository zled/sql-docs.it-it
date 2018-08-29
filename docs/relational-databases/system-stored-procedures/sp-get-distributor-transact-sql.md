---
title: sp_get_distributor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 088b2d2c6e334d48fae3e9257f76c5fd8129c15d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021290"
---
# <a name="spgetdistributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Determina se in un server è installato un server di distribuzione. Questa stored procedure viene eseguita in qualsiasi database del computer in cui viene cercato il server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**installato**|**int**|**0** = No. **1** = Sì|  
|**server di distribuzione**|**sysname**|Nome del server di distribuzione|  
|**database di distribuzione installato**|**int**|**0** = No. **1** = Sì|  
|**è autore di distribuzione**|**int**|**0** = No. **1** = Sì|  
|**con server di pubblicazione di distribuzione remoto**|**int**|**0** = No. **1** = Sì|  
  
## <a name="remarks"></a>Note  
 **sp_get_distributor** viene usato principalmente dai [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in snapshot, transazionale e di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Qualsiasi utente può eseguire **sp_get_distributor**. Un set di risultati non NULL viene restituito quando la stored procedure viene eseguita dai membri del **db_owner** oppure **replmonitor** ruoli predefiniti del database nel database di distribuzione o i membri del  **db_owner** ruolo predefinito del database su almeno un database pubblicato. Un set di risultati non NULL viene restituito anche quando questa stored procedure viene eseguita dagli utenti nell'elenco di accesso (PAL) di almeno un database pubblicato o nell'elenco di accesso del database di distribuzione per un Server di pubblicazione non SQL, possono anche eseguire **sp _get_distributor**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Script di informazioni su database di distribuzione e server di pubblicazione](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
