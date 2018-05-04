---
title: Promozione delle transazioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 742ff5f5785fea2c3652fc88e78d5cefc2090281
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="transaction-promotion"></a>Promozione delle transazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Transazione *promozione* descrive una transazione lightweight locale che può essere promossa automaticamente a una transazione completamente distribuibile in base alle esigenze. Quando una stored procedure gestita viene richiamata all'interno di una transazione del database sul server, il codice CLR (Common Language Runtime) viene eseguito nel contesto di una transazione locale.  Se all'interno di una transazione del database viene aperta una connessione a un server remoto, la connessione al server remoto viene inserita nella transazione distribuita e la transazione locale viene promossa automaticamente a una transazione distribuita. La promozione delle transazioni riduce pertanto l'overhead delle transazioni distribuite posticipando la creazione di una transazione distribuita finché non si rende necessaria. Tale promozione è automatica, se è stato abilitato utilizzando il **integra** (parola chiave) e non richiede alcun intervento da parte dello sviluppatore. Il Provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce il supporto per la promozione delle transazioni tramite le classi in .NET Framework **SqlClient** dello spazio dei nomi.  
  
## <a name="the-enlist-keyword"></a>Parola chiave Enlist  
 Il **ConnectionString** proprietà di un **SqlConnection** oggetto supporta la **integra** (parola chiave), che indica se **SqlClient** individua i contesti transazionali e inserisce automaticamente la connessione in una transazione distribuita. Se questa parola chiave viene impostata su true (impostazione predefinita), la connessione viene inserita automaticamente nel contesto della transazione corrente del thread di apertura. Se invece la parola chiave viene impostata su false, la connessione SqlClient non interagisce con una transazione distribuita. Se **integra** non è specificato nella stringa di connessione, la connessione viene automaticamente inserita in una transazione distribuita se viene rilevata in fase di apertura della connessione.  
  
## <a name="distributed-transactions"></a>Transazioni distribuite  
 Le transazioni distribuite utilizzano in genere un numero elevato di risorse di sistema. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) gestisce tali transazioni e integra tutti gli strumenti di gestione delle risorse alle quali si accede dalle transazioni. Promozione delle transazioni, d'altra parte, è un tipo particolare di un **System. Transactions** transazione che i delegati in modo efficace il lavoro da una semplice [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] delle transazioni. **System. Transactions**, **SqlClient**, e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordinare le operazioni relative alla gestione della transazione, promuovendola a una piena transazione distribuita in base alle esigenze.  
  
 Il vantaggio dell'utilizzo di promozione delle transazioni è che quando viene aperta una connessione con un oggetto attivo **TransactionScope** transazione e non altre connessioni sono aperte, il commit della transazione come tipo semplice, anziché l'overhead di una piena transazione distribuita. Per ulteriori informazioni su **TransactionScope**, vedere [utilizzando System. Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le transazioni e integrazione con CLR](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
