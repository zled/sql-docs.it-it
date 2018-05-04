---
title: sys.service_contract_usages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- service_contract_usages
- sys.service_contract_usages
- sys.service_contract_usages_TSQL
- service_contract_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_usages catalog view
ms.assetid: 20af425e-1152-4a46-b1ac-94cff5fc9f02
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bb0bb4ad2002f42f42028b40e8626d515918c2d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysservicecontractusages-transact-sql"></a>sys.service_contract_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa vista del catalogo contiene una riga per coppia (servizio, contratto).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|Identificatore del servizio che utilizza il contratto. Non ammette i valori Null.|  
|**service_contract_id**|**int**|Identificatore del contratto utilizzato dal servizio. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
