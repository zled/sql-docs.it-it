---
title: La promozione delle transazioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
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
ms.openlocfilehash: b995753073a371b3eb6c27a4c50f3a5351b9dc73
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703202"
---
# <a name="transaction-promotion"></a>Promozione delle transazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Transazione *promozione* descrive una transazione lightweight locale che può essere automaticamente promossa a una transazione completamente distribuibile in base alle esigenze. Quando una stored procedure gestita viene richiamata all'interno di una transazione del database sul server, il codice CLR (Common Language Runtime) viene eseguito nel contesto di una transazione locale.  Se all'interno di una transazione del database viene aperta una connessione a un server remoto, la connessione al server remoto viene inserita nella transazione distribuita e la transazione locale viene promossa automaticamente a una transazione distribuita. La promozione delle transazioni riduce pertanto l'overhead delle transazioni distribuite posticipando la creazione di una transazione distribuita finché non si rende necessaria. Tale promozione è automatica, se è stata abilitata utilizzando il **integra** (parola chiave) e non richiede alcun intervento da parte dello sviluppatore. Il Provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce il supporto per la promozione delle transazioni, devono essere gestita tramite le classi in .NET Framework **SqlClient** dello spazio dei nomi.  
  
## <a name="the-enlist-keyword"></a>Parola chiave Enlist  
 Il **ConnectionString** proprietà di un **SqlConnection** oggetto supporta la **integra** (parola chiave), che indica se **SqlClient** individua i contesti transazionali e inserisce automaticamente la connessione in una transazione distribuita. Se questa parola chiave viene impostata su true (impostazione predefinita), la connessione viene inserita automaticamente nel contesto della transazione corrente del thread di apertura. Se invece la parola chiave viene impostata su false, la connessione SqlClient non interagisce con una transazione distribuita. Se **integra** non è specificato nella stringa di connessione, la connessione viene automaticamente inserita in una transazione distribuita se viene rilevata al momento dell'apertura della connessione.  
  
## <a name="distributed-transactions"></a>Transazioni distribuite  
 Le transazioni distribuite utilizzano in genere un numero elevato di risorse di sistema. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) gestisce tali transazioni e integra tutti gli strumenti di gestione delle risorse alle quali si accede dalle transazioni. Promozione delle transazioni, d'altro canto, è un tipo particolare di un **System. Transactions** transazione che delega in modo efficace il lavoro in una semplice [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] delle transazioni. **System. Transactions**, **SqlClient**, e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordinare le operazioni relative alla gestione della transazione, promuovendola a una piena transazione distribuita in base alle esigenze.  
  
 Il vantaggio di utilizzare la promozione delle transazioni è che quando si apre una connessione con un oggetto attivo **TransactionScope** transazione e non altre connessioni non sono aperte, del commit della transazione come tipo semplice, anziché provocare l'overhead aggiuntivo di una piena transazione distribuita. Per ulteriori informazioni **TransactionScope**, vedere [utilizzando System. Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione con CLR e transazioni](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
