---
title: Durata delle transazioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 290d4c43767ba7e1c6f784c84473e9a05503af54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213041"
---
# <a name="transaction-lifetimes"></a>Durata delle transazioni
  Vi è un'importante differenza tra le transazioni avviate nelle stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] e quelle avviate in codice gestito: il codice CLR (Common Language Runtime) non può sbilanciare lo stato della transazione all'immissione o all'uscita di una chiamata CLR. Tenere presenti le implicazioni seguenti correlate a questa differenza:  
  
-   È necessario eseguire il commit o il rollback di una transazione avviata all'interno di un frame CLR. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un errore quando si esce dal frame.  
  
-   Non è possibile eseguire il commit o il rollback di una transazione esterna all'interno del codice CLR.  
  
-   Un tentativo di esecuzione del commit di una transazione non avviato nella stessa procedura provoca un errore di runtime.  
  
-   Un tentativo di esecuzione del rollback di una transazione non avviato nella stessa procedura fa in modo che la transazione si blocchi, impedendo il verificarsi di qualsiasi altra operazione con effetto collaterale. La transazione viene interrotta fino a quando il codice CLR non abbandona l'ambito. Si noti che questo comportamento può risultare utile quando si rileva un errore all'interno della procedura e si desidera verificare che venga terminata l'intera transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione con CLR e transazioni](../native-client-ole-db-transactions/transactions.md)  
  
  
