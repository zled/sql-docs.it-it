---
title: Tabelle (Transact-SQL) di Integration Services | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server Integration Services system tables
- system tables [SQL Server], Integration Services
- system tables [Integration Services]
- SSIS, system tables
ms.assetid: 683b181b-0091-4a9c-86db-bc577af43cec
caps.latest.revision: 21
author: douglasl
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a5349b8f36bc5abd9b61d5bd4d1677b3344c528
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="integration-services-tables-transact-sql"></a>Tabelle Integration Services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Negli argomenti di questa sezione vengono descritte le tabelle di sistema del database msdb in cui sono archiviate le informazioni utilizzate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [sysssislog](../../relational-databases/system-tables/sysssislog-transact-sql.md)  
 Contiene una riga per ogni voce di log generata da un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in fase di esecuzione.  
  
 Questa tabella viene utilizzata solo quando i pacchetti utilizzano il provider di log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [sysssispackagefolders](../../relational-databases/system-tables/sysssispackagefolders-transact-sql.md)  
 Contiene una riga per ogni cartella logica utilizzata dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per organizzare i pacchetti. I valori di colonna definiscono le relazioni padre/figlio tra cartelle nidificate.  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] visualizza i pacchetti archiviati in una visualizzazione gerarchica quando ci si connette al servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [sysssispackages](../../relational-databases/system-tables/sysssispackages-transact-sql.md)  
 Include una riga per ogni pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Questa tabella viene utilizzata solo quando si archiviano pacchetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
