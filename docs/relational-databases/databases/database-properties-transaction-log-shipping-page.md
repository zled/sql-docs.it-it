---
title: "Proprietà database (pagina Log shipping delle transazioni) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 884eedf748a6128374c5987857940d97eb2f17e7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="database-properties-transaction-log-shipping-page"></a>Proprietà database (pagina Log shipping)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare questa pagina per configurare e modificare le proprietà di log shipping per un database.  
  
 Per approfondimenti sui concetti correlati al log shipping, vedere [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Opzioni  
 **Abilita come database primario in una configurazione per il log shipping**  
 Consente di abilitare il database corrente come database primario per il log shipping. Selezionare l'opzione e quindi configurare le altre opzioni disponibili in questa pagina. Se si deseleziona questa casella di controllo, la configurazione di log shipping verrà eliminata per questo database.  
  
 **Impostazioni backup**  
 Fare clic su **Impostazioni backup** per configurare i parametri relativi alla pianificazione del backup, alla posizione, agli avvisi e all'archiviazione.  
  
 **Pianificazione backup**  
 Consente di visualizzare la pianificazione di backup attualmente selezionata per il database primario. Fare clic su **Impostazioni backup** per modificare queste impostazioni.  
  
 **Ultimo backup creato**  
 Indica l'ora e la data dell'ultimo backup del log delle transazioni del database primario.  
  
 **Istanze del server e database secondari**  
 Consente di elencare i server i e database secondari attualmente configurati per il database primario. Evidenziare un database secondario e quindi fare clic su **...** per modificarne i parametri associati.  
  
 **Aggiungi**  
 Fare clic su **Aggiungi** per aggiungere un database secondario alla configurazione per il log shipping per il database primario.  
  
 **Rimuovi**  
 Consente di rimuovere un database selezionato dalla configurazione di log shipping. Selezionare innanzitutto il database e quindi fare clic su **Rimuovi**.  
  
 **Usa un'istanza del server di monitoraggio**  
 Consente di impostare un'istanza del server di monitoraggio per la configurazione di log shipping. Selezionare la casella di controllo **Usa un'istanza del server di monitoraggio** e quindi fare clic su **Impostazioni** per specificare l'istanza del server di monitoraggio.  
  
 **Istanza server di monitoraggio**  
 Indica l'istanza del server di monitoraggio attualmente configurata per la configurazione di log shipping.  
  
 **Impostazioni**  
 Consente di configurare l'istanza del server di monitoraggio per una configurazione di log shipping. Fare clic su **Impostazioni** per configurare l'istanza del server di monitoraggio.  
  
 **Configurazione script**  
 Consente di generare uno script per la configurazione di log shipping con i parametri selezionati in precedenza. Fare clic su **Configurazione script**e quindi scegliere una destinazione di output per lo script.  
  
> [!IMPORTANT]  
>  Prima di generare uno script delle impostazioni per un database secondario, è necessario richiamare la finestra di dialogo **Impostazioni database secondario** . Questa operazione consente di connettersi al server secondario e di recuperare le impostazioni correnti del database secondario necessarie per generare lo script.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per il log shipping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)   
 [Tabelle di log shipping &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)  
  
  
