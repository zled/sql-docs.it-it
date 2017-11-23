---
title: Durata delle transazioni | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 445984322c81766be4919cfda8b211a21e2519a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="transaction-lifetimes"></a>Durata delle transazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Un'importante differenza tra le transazioni avviate [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure e quelle avviate in codice gestito: codice common language runtime (CLR) non può sbilanciare lo stato della transazione in ingresso o uscita di una chiamata CLR. Tenere presenti le implicazioni seguenti correlate a questa differenza:  
  
-   È necessario eseguire il commit o il rollback di una transazione avviata all'interno di un frame CLR. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un errore quando si esce dal frame.  
  
-   Non è possibile eseguire il commit o il rollback di una transazione esterna all'interno del codice CLR.  
  
-   Un tentativo di esecuzione del commit di una transazione non avviato nella stessa procedura provoca un errore di runtime.  
  
-   Un tentativo di esecuzione del rollback di una transazione non avviato nella stessa procedura fa in modo che la transazione si blocchi, impedendo il verificarsi di qualsiasi altra operazione con effetto collaterale. La transazione viene interrotta fino a quando il codice CLR non abbandona l'ambito. Si noti che questo comportamento può risultare utile quando si rileva un errore all'interno della procedura e si desidera verificare che venga terminata l'intera transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione con CLR e transazioni](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
