---
title: FULLTEXTCATALOGPROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXTSERVICEPROPERTY_TSQL
- FULLTEXTSERVICEPROPERTY
dev_langs: TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- FULLTEXTSERVICEPROPERTY function
- services [SQL Server], full-text search properties
- test
ms.assetid: b7dcacb0-af83-4807-9d1e-49148b56b59c
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fef0f88dae810c78aed8133164699734cd92993f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="fulltextserviceproperty-transact-sql"></a>FULLTEXTSERVICEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni correlate alle proprietà del motore di ricerca full-text. Queste proprietà possono essere impostate e recuperate tramite **sp_fulltext_service**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FULLTEXTSERVICEPROPERTY ('property')  
```  
  
## <a name="arguments"></a>Argomenti  
 *proprietà*  
 Espressione che contiene il nome della proprietà full-text a livello del servizio. Nella tabella seguente vengono descritte le proprietà e le informazioni restituite.  
  
> [!NOTE]  
>  Le seguenti proprietà verranno rimossa in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **ConnectTimeout**, **DataTimeout**, e **ResourceUsage**. Evitare di utilizzare queste proprietà in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui vengono utilizzate.  
  
|Proprietà|Valore|  
|--------------|-----------|  
|**Valore ResourceUsage**|Viene restituito 0. Supportata unicamente per compatibilità con le versioni precedenti.|  
|**ConnectTimeout**|Viene restituito 0. Supportata unicamente per compatibilità con le versioni precedenti.|  
|**IsFulltextInstalled**|Indica se il componente full-text è installato o meno nell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = Il componente full-text non è installato.<br /><br /> 1 = Il componente full-text è installato.<br /><br /> NULL = Input non valido o errore.|  
|**DataTimeout**|Viene restituito 0. Supportata unicamente per compatibilità con le versioni precedenti.|  
|**LoadOSResources**|Indica se i word breaker e i filtri del sistema operativo sono registrati e utilizzati in questa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa proprietà è disabilitata per impostazione predefinita per impedire modifiche accidentali del comportamento in seguito ad aggiornamenti al sistema operativo. L'attivazione dell'utilizzo delle risorse del sistema operativo consente l'accesso alle risorse per le lingue e i tipi di documenti registrati nel servizio di indicizzazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] per cui non è installata una risorsa specifica dell'istanza. Se si abilita il caricamento delle risorse del sistema operativo, verificare che le risorse del sistema operativo sono file binari firmati attendibili; in caso contrario, non potranno essere caricati quando **VerifySignature** è impostato su 1.<br /><br /> 0 = Utilizza solo i filtri e i word breaker specifici per questa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = Carica i filtri e i word breaker del sistema operativo.|  
|**VerifySignature**|Specifica se solo i file binari firmati vengono caricati dal servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search. Per impostazione predefinita vengono caricati solo i file binari firmati attendibili.<br /><br /> 0 = Non verificare se i file binari sono firmati o meno.<br /><br /> 1 = Verifica che vengano caricati solo i file binari firmati attendibili.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene controllato se vengono caricati solo file binari firmati e il valore restituito indica che la verifica non è in fase di esecuzione.  
  
```  
SELECT fulltextserviceproperty('VerifySignature');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
0  
```  
  
 Si noti che per ripristinare il valore predefinito di verifica della firma 1, è possibile utilizzare l'istruzione `sp_fulltext_service` seguente:  
  
```  
EXEC sp_fulltext_service @action='verify_signature', @value=1;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [FULLTEXTCATALOGPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)  
  
  
