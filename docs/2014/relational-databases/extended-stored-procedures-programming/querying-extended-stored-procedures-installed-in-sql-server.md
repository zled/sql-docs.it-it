---
title: L'esecuzione di query Extended Stored procedure installate in SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0714011cb2ba76220517c02fe3d946556610869e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298321"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Esecuzione di query su stored procedure estese installate in SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Oggetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utente autenticato può visualizzare attualmente definito stored procedure estese e il nome della DLL per ciascuna delle quali appartiene eseguendo il **sp_helpextendedproc** procedure di sistema. Ad esempio, l'esempio seguente restituisce le DLL a cui **xp_hello** appartiene:  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Se **sp_helpextendedproc** viene eseguita senza specificare una stored procedure estesa, tutte le stored procedure estese e le relative DLL sono visualizzati.  
  
> [!IMPORTANT]  
>  Verranno restituite le informazioni solo per le stored procedure estese di cui l'utente connesso è il proprietario o di cui dispone delle autorizzazioni appropriate. Solo i membri del **sysadmin** ruolo predefinito del server e il **db_owner**, **db_securityadmin**e il **db_ddladmin** predefinito del database i ruoli è possono visualizzare informazioni per tutte le stored procedure estese.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
