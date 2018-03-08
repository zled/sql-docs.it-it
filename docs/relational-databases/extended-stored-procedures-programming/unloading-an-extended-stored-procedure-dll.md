---
title: Lo scaricamento di un'estesa DLL di Stored Procedure | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bad1f82152cd21d4d5753225842b672016ccec2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Caricamento di una DLL di stored procedure estesa
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Carica una DLL della stored procedure estesa appena viene effettuata una chiamata a una delle funzioni della DLL. La DLL rimane caricata fino a che il server non viene spento o fino a che l'amministratore di sistema non utilizza l'istruzione DBCC per scaricarla. Ad esempio, questo comando Scarica il **xp_hello.dll**, consentendo all'amministratore di sistema di copiare una versione più recente di questo file nella directory senza arrestare il server:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
