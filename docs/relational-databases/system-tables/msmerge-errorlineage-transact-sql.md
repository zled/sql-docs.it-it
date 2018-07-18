---
title: MSmerge_errorlineage (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d147e8e73ee7b153ce14d3ffd6d9082095ac1a68
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33004728"
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_errorlineage** tabella contiene righe che sono state eliminate nel Sottoscrittore, ma la cui eliminazione non viene propagata al server di pubblicazione. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Valore integer assegnato alla tabella pubblicata per la replica di tipo merge. Corrisponde al campo nome alternativo di **sysmergearticles** tabella.|  
|**rowguid**|**uniqueidentifier**|Identificatore di riga.|  
|**derivazione**|**varbinary(501)**|Archivia un elenco di cronologia dei Sottoscrittori e dei server di pubblicazione in cui sono stati eseguiti aggiornamenti a una riga. Consente di rilevare e risolvere eventuali situazioni di conflitto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
