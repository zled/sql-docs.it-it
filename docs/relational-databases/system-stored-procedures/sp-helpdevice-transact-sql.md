---
title: sp_helpdevice (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
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
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a39dcc6cd75837017826fdcf9b37ff7d6a3598c9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza informazioni sui dispositivi di backup di Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]È consigliabile utilizzare il [backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) vista del catalogo  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@devname =** ] **'***nome***'**  
 Nome del dispositivo di backup per il quale vengono visualizzate le informazioni. Il valore di *nome* è sempre **sysname**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nome_periferica**|**sysname**|Nome logico del dispositivo.|  
|**physical_name**|**nvarchar (260)**|Nome fisico del file.|  
|**Descrizione**|**nvarchar(255)**|Descrizione del dispositivo.|  
|**status**|**int**|Un numero che corrisponde alla descrizione dello stato di **descrizione** colonna.|  
|**CntrlType**|**smallint**|Tipo di controller del dispositivo:<br /><br /> 2 = dispositivo disco<br /><br /> 5 = dispositivo nastro|  
|**dimensioni**|**int**|Dimensioni del dispositivo espresse in pagine da 2 KB.|  
  
## <a name="remarks"></a>Osservazioni  
 Se *nome* è specificato, **sp_helpdevice** Visualizza informazioni sul dispositivo di dump specificato. Se *nome* non viene specificato, **sp_helpdevice** Visualizza informazioni su tutti i dispositivi di dump nel **backup_devices** vista del catalogo.  
  
 I dispositivi di dump vengono aggiunti al sistema tramite **sp_addumpdevice**.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzate le informazioni su tutti i dispositivi di dump in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
