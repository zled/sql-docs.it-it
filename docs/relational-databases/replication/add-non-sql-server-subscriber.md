---
title: Aggiungere un Sottoscrittore non SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0f690b1f4b73fa532cdfa6c6d0b6eee883dc8b26
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="add-non-sql-server-subscriber"></a>Aggiungi Sottoscrittore non SQL Server
  La replica supporta la creazione di sottoscrizioni push delle pubblicazioni transazionali e snapshot per i Sottoscrittori Oracle e IBM DB2.  
  
## <a name="options"></a>Opzioni  
 **Tipo di Sottoscrittore da aggiungere**  
 Consente di selezionare un Sottoscrittore Oracle o IBM DB2. Per altre informazioni sul supporto per tali Sottoscrittori, vedere [Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Nome origine dati**  
 Nome utilizzato per individuare il database in rete. La replica genera una stringa di connessione per il database utilizzando il nome dell'origine dei dati in combinazione con l'account di accesso, la password e le eventuali opzioni di connessione specificate nella pagina **Sicurezza agente di distribuzione** di questa procedura guidata.  
  
> [!NOTE]  
>  The data source name and connection string are not validated by [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until the Distribution Agent attempts to initialize the subscription.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una sottoscrizione per un Sottoscrittore non SQL Server](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
