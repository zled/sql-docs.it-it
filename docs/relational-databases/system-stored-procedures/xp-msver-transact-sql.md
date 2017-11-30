---
title: xp_msver (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs: TSQL
helpviewer_keywords: xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57509a7787087d747ae84f0bed6c67e8e3cd0f67
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="xpmsver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulla versione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **xp_msver** restituisce inoltre informazioni sul numero di build corrente del server e informazioni sull'ambiente del server. Le informazioni che **xp_msver** restituisce può essere utilizzato all'interno di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni, batch, stored procedure e così via, per migliorare la logica per il codice indipendente dalla piattaforma.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *optname*  
 Nome di un'opzione. I possibili valori sono i seguenti.  
  
|Opzione/nome colonna|Description|  
|-------------------------|-----------------|  
|**ProductName**|Nome di prodotto. ad esempio, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProductVersion**|Versione del prodotto.|  
|**Lingua**|Lingua della versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Piattaforma**|Nome del sistema operativo, del produttore e del tipo di chip del computer che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Commenti**|Informazioni varie relative a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**CompanyName**|Nome del produttore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**FileDescription**|Sistema operativo.|  
|**FileVersion**|Versione dell'eseguibile di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**InternalName**|Nome interno [!INCLUDE[msCoName](../../includes/msconame-md.md)] di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio SQLSERVR.|  
|**LegalCopyright**|Informazioni legali sul copyright necessarie per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio Copyright© [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corp. 1988-2005.|  
|**LegalTrademarks**|Informazioni legali sul marchio di fabbrica necessarie per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] è un marchio registrato di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**OriginalFilename**|Nome del file eseguito all'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio Sqlservr.exe.|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**WindowsVersion**|Versione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows installata nel computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.|  
|**ProcessorCount**|Numero di processori del computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.|  
|**ProcessorActiveMask**|Indica i processori installati nel computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione che sono avviati e utilizzabili da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|  
|**ProcessorType**|Tipo di processore. Simile a **piattaforma**.|  
|**PhysicalMemory**|Quantità di RAM espressa in megabyte (MB) installata nel computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.|  
|**ID prodotto**|Numero di ID del prodotto (PID). Questo numero viene specificato durante l'installazione ed è riportato sull'etichetta della custodia del CD originale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="return-code-values"></a>Valori restituiti  
 1 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 **xp_msver**, senza alcun parametro, restituisce un set di risultati a quattro colonne in cui sono elencati tutti i valori di opzione. **xp_msver**, per qualsiasi parametro, restituisce quattro colonne set di risultati con i valori per tale opzione.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Estese generali Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
