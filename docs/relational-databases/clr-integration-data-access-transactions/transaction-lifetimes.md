---
title: Durata delle transazioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86ac25a9f820bd64d9c15c8f43e97cccb6e1fb96
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="transaction-lifetimes"></a>Durata delle transazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vi è un'importante differenza tra le transazioni avviate nelle stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] e quelle avviate in codice gestito: il codice CLR (Common Language Runtime) non può sbilanciare lo stato della transazione all'immissione o all'uscita di una chiamata CLR. Tenere presenti le implicazioni seguenti correlate a questa differenza:  
  
-   È necessario eseguire il commit o il rollback di una transazione avviata all'interno di un frame CLR. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un errore quando si esce dal frame.  
  
-   Non è possibile eseguire il commit o il rollback di una transazione esterna all'interno del codice CLR.  
  
-   Un tentativo di esecuzione del commit di una transazione non avviato nella stessa procedura provoca un errore di runtime.  
  
-   Un tentativo di esecuzione del rollback di una transazione non avviato nella stessa procedura fa in modo che la transazione si blocchi, impedendo il verificarsi di qualsiasi altra operazione con effetto collaterale. La transazione viene interrotta fino a quando il codice CLR non abbandona l'ambito. Si noti che questo comportamento può risultare utile quando si rileva un errore all'interno della procedura e si desidera verificare che venga terminata l'intera transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Le transazioni e integrazione con CLR](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
