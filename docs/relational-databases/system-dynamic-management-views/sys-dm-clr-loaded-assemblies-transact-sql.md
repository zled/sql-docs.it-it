---
title: Sys.dm clr_loaded_assemblies (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_clr_loaded_assemblies
- sys.dm_clr_loaded_assemblies_TSQL
- dm_clr_loaded_assemblies_TSQL
- sys.dm_clr_loaded_assemblies
dev_langs: TSQL
helpviewer_keywords: sys.dm_clr_loaded_assemblies dynamic management view
ms.assetid: 8523d8db-d8a0-4b1f-ae19-6705d633e0a6
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44005aa828f6c8225832f961a7f32b8be8c5566e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmclrloadedassemblies-transact-sql"></a>sys.dm_clr_loaded_assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni assembly gestito dall'utente nello spazio degli indirizzi del server. Utilizzare questa visualizzazione per comprendere e risolvere i problemi di integrazione con CLR gestito oggetti di database che sono in esecuzione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Gli assembly sono costituiti da file DLL di codice gestito utilizzati per definire e distribuire gli oggetti di database gestito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ogni volta che un utente esegue uno di questi oggetti di database gestito, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il CLR caricano l'assembly in cui l'oggetto di database gestito viene definito e i relativi riferimenti. L'assembly rimane caricato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per migliorare le prestazioni. In seguito sarà infatti possibile chiamare gli oggetti di database gestito contenuti nell'assembly senza che sia necessario ricaricare l'assembly. L'assembly non viene scaricato finché la quantità di memoria in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non risulta insufficiente. Per ulteriori informazioni sugli assembly e l'integrazione con CLR, vedere [ambiente ospitato CLR](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md). Per ulteriori informazioni sugli oggetti di database gestiti, vedere [compilazione di oggetti di Database con Common Language Runtime &#40; Common Language Runtime &#41; Integrazione](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md).  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|ID dell'assembly caricato. Il **assembly_id** può essere utilizzato per cercare ulteriori informazioni sull'assembly nella [Assemblies &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) vista del catalogo. Si noti che il [!INCLUDE[tsql](../../includes/tsql-md.md)] [Assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) catalogo Mostra gli assembly nel database corrente. Il **sqs.dm_clr_loaded_assemblies** visualizzazione Mostra tutti gli assembly caricati nel server.|  
|**appdomain_address**|**int**|Indirizzo del dominio dell'applicazione (**AppDomain**) in cui l'assembly viene caricato. Tutti gli assembly di proprietà di un singolo utente vengono sempre caricati nello stesso **AppDomain**. Il **appdomain_address** può essere usato per cercare ulteriori informazioni sul **AppDomain** nel [Sys.dm clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md) visualizzazione.|  
|**load_time**|**datetime**|Ora di caricamento dell'assembly. Si noti che l'assembly rimane caricato finché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eccessivo della memoria e scarica il **AppDomain**. È possibile monitorare **load_time** per comprendere la frequenza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proviene eccessivo della memoria e scarica il **AppDomain**.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="remarks"></a>Osservazioni  
 Il **dm_clr_loaded_assemblies** Vista dispone di una relazione molti-a-uno con **dm_clr_appdomains**. Il **dm_clr_loaded_assemblies. assembly_id** Vista presenta una relazione uno-a-molti con **assembly_id**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come visualizzare dettagli relativi a tutti gli assembly del database corrente che sono attualmente caricati.  
  
```  
 SELECT a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
FROM sys.dm_clr_loaded_assemblies AS l   
INNER JOIN sys.assemblies AS a  
ON l.assembly_id = a.assembly_id;  
```  
  
 Nell'esempio seguente viene illustrato come visualizzare i dettagli del **AppDomain** in cui è caricato un assembly specificato.  
  
```  
SELECT appdomain_id, creation_time, db_id, user_id, state  
FROM sys.dm_clr_appdomains AS a  
WHERE appdomain_address =   
(SELECT appdomain_address   
 FROM sys.dm_clr_loaded_assemblies  
 WHERE assembly_id = 555);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Common Language Runtime relative viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
