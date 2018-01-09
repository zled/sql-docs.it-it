---
title: Rimozione di un'estesa Stored Procedure da SQL Server | Documenti Microsoft
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
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 147091aee873f0c9b15c3b9934b8daf6c3acbe8a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Rimozione di una stored procedure estesa da SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 Per eliminare ogni funzione di stored procedure estesa in una definito dall'utente DLL stored procedure estesa, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] amministratore di sistema deve eseguire il **sp_dropextendedproc** stored procedure, specificando il nome di sistema di funzione e il nome della DLL in cui risiede la funzione. Ad esempio, questo comando rimuove la funzione **xp_hello**, che si trova in una DLL denominata xp_hello.dll, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** non elimina le stored procedure estese di sistema. Al contrario, l'amministratore di sistema può negare l'autorizzazione EXECUTE per la stored procedure estesa per il **pubblica** ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_dropextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
