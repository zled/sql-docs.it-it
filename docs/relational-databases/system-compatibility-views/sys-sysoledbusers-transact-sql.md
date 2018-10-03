---
title: Sys. sysoledbusers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 71d04ef07053eb893a98d654424eb49b61f0c7e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809139"
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Questa tabella di sistema di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] è disponibile come vista in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per motivi di compatibilità con le versioni precedenti. È consigliabile usare [viste del catalogo](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) invece.  
  
 È contenuta una riga per il mapping di ogni utente e password per il server collegato specificato. **sysoledbusers** viene archiviato nel **master** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|ID di sicurezza (SID) del server.|  
|**rmtloginame**|**nvarchar (** 128 **)**|Nome dell'account di accesso remoto che **loginsid** esegue il mapping a per collegato **rmtservid**.|  
|**rmtpassword**|**nvarchar (** 128 **)**|Restituisce NULL.|  
|**loginsid**|**varbinary(** 85 **)**|SID dell'account di accesso locale su cui eseguire il mapping.|  
|**status**|**smallint**|Se uguale a 1, per il mapping è necessario utilizzare le credenziali dell'utente.|  
|**ChangeDate**|**datetime**|Data dell'ultima modifica delle informazioni sul mapping.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
