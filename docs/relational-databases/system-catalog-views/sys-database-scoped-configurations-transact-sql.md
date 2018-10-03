---
title: Sys. database_scoped_configurations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 350f3af1bfd6e2765f74d074727577541378d2e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733836"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni configurazione. 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|ID dell'opzione di configurazione.|  
|**name**|**nvarchar(60)**|Il nome dell'opzione di configurazione. Per informazioni sulle configurazioni possibili, vedere [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**Valore**|**sqlvariant**|Il valore impostato per questa opzione di configurazione per la replica primaria.|  
|**value_for_secondary**|**sqlvariant**|Il valore impostato per questa opzione di configurazione per le repliche secondarie.|  
|**elevate_online**|**nvarchar(60)** |Il database con ambito di set predefinito per l'opzione per operazioni sugli indici online |
|**elevate_resumable**|nvarchar(60)|Il database con ambito di set predefinito per l'opzione resumable per operazioni sugli indici| 
  
##  <a name="Permissions"></a> Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="remarks"></a>Note  
 Quando viene restituito NULL come valore per **value_for_secondary**, ciò significa che il database secondario viene impostato alla replica primaria.  
 
 Le impostazioni di configurazione con ambito database saranno trasferite insieme al database. Ciò significa che quando un database viene ripristinato o collegato, le impostazioni di configurazione esistenti non vengono modificate.
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
