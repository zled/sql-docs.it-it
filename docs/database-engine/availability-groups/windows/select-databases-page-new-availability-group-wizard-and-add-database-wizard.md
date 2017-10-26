---
title: "Pagina Selezione database (Creazione guidata gruppo di disponibilità/Aggiungi database) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.adddatabasewizard.selectdatabases.f1
- sql13.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a082f863c17e8de989ab40231c57b93e5d629f87
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="select-databases-page-new-availability-group-wizard-and-add-database-wizard"></a>Pagina Selezione database (Creazione guidata Gruppo di disponibilità/Aggiungi database)
  In questo argomento della Guida vengono descritte le opzioni della pagina **Specifica database** . Questo argomento si applica alla [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] e alla [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="PageOptions"></a> Opzioni di selezione dei database  
 Nella griglia **Database utente in questa istanza di SQL Server** è elencato ogni database utente locale. Le colonne sono le seguenti:  
  
 **Nome**  
 Visualizza il nome di un database utente locale.  

 **Dimensione**  
 Visualizza la dimensione del database, se è disponibile per la procedura guidata.  
  
 **Stato**  
 Visualizza un collegamento ipertestuale il cui testo indica se un determinato database soddisfa i prerequisiti per l'aggiunta a un gruppo di disponibilità. Se lo stato è "**Soddisfa i prerequisiti**" è possibile aggiungere il database al gruppo di disponibilità. Se un database non soddisfa tutti i prerequisiti, il collegamento ipertestuale **Stato** fornisce una breve spiegazione dei motivi per cui il database non è idoneo. Per ulteriori informazioni, fare clic sul collegamento ipertestuale.  
  
 È possibile lasciare la procedura guidata sulla pagina **Seleziona database** mentre si eseguono le operazioni necessari per soddisfare un prerequisito del database. Quando si torna alla pagina **Seleziona database** fare clic su **Aggiorna** per aggiornare la griglia.  
  
 **Password**  
 Se il database contiene una chiave master di database, immettere la password per tale chiave.  
  
 **Aggiorna**  
 Fare clic per aggiornare la griglia. Questa opzione è utile dopo avere eseguito un'operazione necessaria per soddisfare un prerequisito del database.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Usare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Usare la procedura guidata Aggiungi database a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  

