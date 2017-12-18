---
title: Pagina Immetti password (Aggiungi replica) | Microsoft Docs
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
caps.latest.revision: "7"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 774b8f7513cb49f2a4a04393c160df82f4b7962f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="enter-passwords-page-add-replica-wizard"></a>Pagina Immetti password (Aggiungi replica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento della Guida descrive le opzioni della pagina **Immetti password**. Questo argomento si applica alla [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Se le repliche selezionate nella pagina **Specifica repliche** contengono database con una chiave master del database, viene visualizzata la pagina Immetti password.  
  
## <a name="enter-passwords-options"></a>Opzioni Immetti password  
 Nella griglia **Database utente in questa istanza di SQL Server** è elencato ogni database utente locale. Le colonne sono le seguenti:  
  
 **Nome**  
 Visualizza il nome di un database utente locale.  
  
 **Dimensione**  
 Visualizza la dimensione del database, se è disponibile per la procedura guidata.  
  
 **Stato**  
 Indica **Password obbligatoria** per i database con una chiave master del database. Dopo avere immesso la password per le chiavi master di database nella colonna **Password** , fare clic su **Aggiorna**. Se le password sono state immesse correttamente, la colonna **Stato** visualizza **Password immessa**.  
  
 Se il database non ha una chiave master di database, la colonna **Stato** visualizza **Password non obbligatoria**.  
  
 **Password**  
 Se la colonna **Stato** visualizza **Password obbligatoria**, immettere la password per la chiave master del database.  
  
 **Aggiorna**  
 Fare clic per aggiornare la griglia. Ciò è utile dopo avere immesso le password necessarie.  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Utilizzare la procedura guidata Aggiungi replica a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
