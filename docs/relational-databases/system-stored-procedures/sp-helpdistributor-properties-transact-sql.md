---
title: sp_helpdistributor_properties (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- sp_helpdistributor_properties_TSQL
- sp_helpdistributor_properties
helpviewer_keywords:
- sp_helpdistributor_properties
ms.assetid: ee267724-3244-49eb-84c9-f38dbefdd639
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0f839d230097300eb08c0042854ed00f3b4dd951
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32994468"
---
# <a name="sphelpdistributorproperties-transact-sql"></a>sp_helpdistributor_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà del server di distribuzione. La stored procedure viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdistributor_properties   
```  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**heartbeat_interval**|**int**|Periodo massimo in minuti durante il quale un agente può non registrare alcun messaggio sullo stato.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpdistributor_properties** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, i membri del **db_owner** o **replmonitor** ruolo predefinito del database sul database di distribuzione e gli utenti di elenco di accesso (PAL) per una pubblicazione che utilizza questo server di distribuzione può eseguire **sp_helpdistributor_properties**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_changedistributor_property &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)  
  
  
