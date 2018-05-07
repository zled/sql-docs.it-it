---
title: sys.pdw_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6f8281d520f64580af8432dbf2004227ce628d41
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Consente di archiviare proprietà per gli avvisi diversi che possono verificarsi nel sistema. si tratta di una tabella del catalogo per gli avvisi.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Identificatore univoco dell'avviso.<br /><br /> Chiave per la visualizzazione.|NOT NULL|  
|component_id|**int**|ID del componente di a che questo avviso si applica. Il componente è un identificatore del componente generale, ad esempio "Alimentatore," e non è specifico di un'installazione. Vedere [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Nome dell'avviso.|NOT NULL|  
|state|**nvarchar(32)**|Stato dell'avviso.|NOT NULL<br /><br /> I valori possibili sono:<br /><br /> 'Operational'<br /><br /> "Non operativo"<br /><br /> 'Danneggiato'<br /><br /> "Non riuscito"|  
|severity|**nvarchar(32)**|Gravità dell'avviso.|NOT NULL<br /><br /> I valori possibili sono:<br /><br /> 'Informativo'<br /><br /> 'Avviso'<br /><br /> 'Error'|  
|Tipo|**nvarchar(32)**|Tipo di avviso.|NOT NULL<br /><br /> I valori possibili sono:<br /><br /> StatusChange - è stato modificato lo stato del dispositivo.<br /><br /> Soglia - valore ha superato il valore di soglia.|  
|description|**nvarchar(4000)**|Descrizione dell'avviso.|NOT NULL|  
|condizione|**nvarchar(255)**|Tipo utilizzato quando = soglia. Definisce la modalità di calcolo della soglia di avviso.|NULL|  
|status|**nvarchar(32)**|Stato dell'avviso|NULL|  
|condition_value|**bit**|Indica se l'avviso è consentito durante il funzionamento del sistema.|NULL<br /><br /> Valori possibili<br /><br /> 0 - avviso non viene generato.<br /><br /> 1 - l'avviso viene generato.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
