---
title: Sys.destination_data_spaces (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.destination_data_spaces
- destination_data_spaces_TSQL
- destination_data_spaces
- sys.destination_data_spaces_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.destination_data_spaces catalog view
ms.assetid: 92df932b-ad5c-43f8-81f4-b158823ab189
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e6169dc0957ba14fa2f38589ccdbaff34d03bb5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysdestinationdataspaces-transact-sql"></a>sys.destination_data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni destinazione dello spazio dei dati di uno schema di partizionamento.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**partition_scheme_id**|**int**|ID dello schema di partizionamento dello spazio dei dati.|  
|**destination_id**|**int**|ID (ordinale in base 1) del mapping delle destinazioni, univoco nello schema di partizionamento.|  
|**data_space_id**|**int**|ID dello spazio dei dati a cui vengono mappati i dati per la destinazione dello schema.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** . Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
