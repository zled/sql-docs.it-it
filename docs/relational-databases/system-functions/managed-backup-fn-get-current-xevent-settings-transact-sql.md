---
title: managed_backup.fn_get_current_xevent_settings (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs: TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
caps.latest.revision: "11"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd569f74e53d5b556f7ec8a4c1f3c02b7d574742
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce 1 riga per ogni tipo di evento esteso supportato da Smart Admin.  
  
 Utilizzare questa funzione per restituire o rivedere le impostazioni di eventi estesi correnti per identificare il tipo di eventi che sono configurabili e le configurazioni correnti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> Argomenti  
 Questa funzione non dispone di alcun argomento.  
  
## <a name="table-returned"></a>Tabella restituita  
 I canali operativi, analitici e di amministrazione degli eventi estesi necessari sono abilitati per impostazione predefinita e non configurabili.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Tipo di evento esteso|  
|is_configurable|NVARCHAR(128)|È impostato su **True** se l'evento è configurabile, altrimenti è impostato su **False**.|  
|is_enabled|NVARCHAR(128)|Viene impostato su True se l'evento è abilitato; in caso contrario, viene impostato su False. Utilizzare smart_admin.sp_set_parameter per abilitare gli eventi di debug.|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Richiede **selezionare** autorizzazioni nella funzione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti gli eventi estesi con lo stato corrente.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
