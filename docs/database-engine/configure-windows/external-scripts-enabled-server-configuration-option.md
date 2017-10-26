---
title: Opzione di configurazione del server external scripts enabled | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 08/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 74f73ab33a010583b4747fcc2d9b35d6cdea14a2
ms.openlocfilehash: 282f50334b59e2d41e2fcac7e33835859bdffe12
ms.contentlocale: it-it
ms.lasthandoff: 08/04/2017

---
# <a name="external-scripts-enabled-server-configuration-option"></a>Opzione di configurazione del server external scripts enabled
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Usare l'opzione **external scripts enabled** per abilitare l'esecuzione di script con determinate estensioni del linguaggio remote. Questa proprietà è DISATTIVATA per impostazione predefinita. Quando **Advanced Analytics Services** è installato, il programma di installazione può impostare facoltativamente questa proprietà su true.  
  

 È necessario abilitare l'opzione external script enabled prima di eseguire uno script esterno usando la procedura **sp_execute_external_script** . Usare **sp_execute_external_script** per eseguire gli script scritti in un linguaggio supportato, ad esempio R. In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è costituito da un componente server installato con [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]e da un set di strumenti della workstation e di librerie di connettività che connettono il data scientist all'ambiente ad alte prestazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Installare la funzionalità **Advanced Analytics Extensions** durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per abilitare l'esecuzione di script R. Per altre informazioni, vedere [Installing Previous Versions of SQL Server R Services](http://msdn.microsoft.com/library/48380645-9e72-4744-bebb-1c1fd8a18c43).  
  
 Per abilitare gli script esterni, eseguire lo script seguente:  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE WITH OVERRIDE;  
```  
  
 È necessario riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per rendere effettiva questa modifica.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  

