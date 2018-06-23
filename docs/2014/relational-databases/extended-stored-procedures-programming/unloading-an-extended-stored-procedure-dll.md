---
title: Lo scaricamento di un'estesa DLL di Stored Procedure | Documenti Microsoft
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 78d3e74d7316b31143253a2c1bd7c33d08b012f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156925"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Caricamento di una DLL di stored procedure estesa
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Carica una DLL della stored procedure estesa appena viene eseguita una chiamata a una delle funzioni della DLL. La DLL rimane caricata fino a che il server non viene spento o fino a che l'amministratore di sistema non utilizza l'istruzione DBCC per scaricarla. Ad esempio, questo comando Scarica la **xp_hello. dll**, consentendo all'amministratore di sistema di copiare una versione più recente di questo file nella directory senza arrestare il server:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
