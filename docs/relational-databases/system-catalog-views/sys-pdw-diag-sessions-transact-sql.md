---
title: sys.pdw_diag_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d515c217b6405061605f6191d0a3eaf8b72eadd8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni riguardanti le diverse sessioni di diagnostica che sono stati creati nel sistema.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Nome della sessione di diagnostica.<br /><br /> Chiave per la visualizzazione.||  
|**xml_data**|**nvarchar(4000)**|Payload XML che descrive la sessione.||  
|**is_active**|**bit**|Flag che indica se il flag è attivo.||  
|**host_address**|**nvarchar(255)**|Indirizzo del computer che ospita la definizione della sessione (nodo di controllo).||  
|**principal_id**|**int**|ID dell'utente che ha creato la sessione a livello di database.||  
|**database_id**|**int**|ID del database che è l'ambito della sessione di diagnostica.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
