---
title: "Opzione di configurazione del server external scripts enabled | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "external scripts enabled"
  - "external_scripts_enabled_TSQL"
helpviewer_keywords: 
  - "opzione external scripts enabled"
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Opzione di configurazione del server external scripts enabled
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Usare l'opzione **external scripts enabled** per abilitare l'esecuzione di script con determinate estensioni del linguaggio remote. Questa proprietà è disattivata per impostazione predefinita. Facoltativamente, il programma di installazione può impostare questa proprietà su true se è installato **Advanced Analytics Services** .  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 È necessario abilitare l'opzione external script enabled prima di eseguire uno script esterno usando la procedura **sp_execute_external_script**. Usare **sp_execute_external_script** per eseguire gli script scritti in un linguaggio supportato, ad esempio R. In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è costituito da un componente server installato con [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e da un set di strumenti della workstation e di librerie di connettività che connettono il data scientist all'ambiente ad alte prestazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Installare la funzionalità **Advanced Analytics Extensions** durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per abilitare l'esecuzione di script R. Per altre informazioni, vedere [Installing Previous Versions of SQL Server R Services](../Topic/Installing%20Previous%20Versions%20of%20SQL%20Server%20R%20Services.md).  
  
 Eseguire questo script per abilitare gli script esterni.  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE;  
```  
  
 È necessario riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per rendere effettiva questa modifica.  
  
## Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  