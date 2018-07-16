---
title: Lo scaricamento di un'estesa DLL della Stored Procedure | Microsoft Docs
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
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b4d63dd96af63319d728e75df3534d07c6c51a17
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316221"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Caricamento di una DLL di stored procedure estesa
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Carica una DLL della stored procedure estesa appena viene effettuata una chiamata a una delle funzioni della DLL. La DLL rimane caricata fino a che il server non viene spento o fino a che l'amministratore di sistema non utilizza l'istruzione DBCC per scaricarla. Ad esempio, questo comando Scarica i **xp_hello. dll**, consentendo all'amministratore di sistema copiare una versione più recente di questo file nella directory senza spegnere il server:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
