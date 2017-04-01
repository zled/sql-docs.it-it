---
title: "Database crittografati con gruppi di disponibilit&#224; AlwaysOn (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Transparent Data Encryption, gruppi di disponibilità AlwaysOn"
  - "TDE, Gruppi di disponibilità AlwaysOn"
  - "Gruppi di disponibilità [SQL Server], interoperabilità"
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# Database crittografati con gruppi di disponibilit&#224; AlwaysOn (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento sono contenute informazioni su come utilizzare correttamente database crittografati o recentemente decrittografati con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Contenuto dell'argomento:**  
  
-   [Limitazioni e restrizioni](#Restrictions)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se un database viene crittografato o contiene una chiave di crittografia del database (DEK), non è possibile usare [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] o [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] per aggiungere il database a un gruppo di disponibilità. Anche se è stato decrittografato un database crittografato, i backup del log potrebbero contenere dati crittografati. In questo caso, la sincronizzazione dei dati iniziale completa potrebbe non riuscire sul database. Questo avviene perché l'operazione di ripristino del log potrebbe richiedere il certificato usato dalle chiavi di crittografia del database e tale certificato potrebbe non essere disponibile.  
  
     Affinché un database decrittografato sia idoneo a essere aggiunto a un gruppo di disponibilità usando la procedura guidata:  
  
    1.  Creare un backup del log del database primario.  
  
    2.  Creare un backup del log completo del database primario.  
  
    3.  Ripristinare il backup del database nell'istanza del server in cui è ospitata la replica secondaria.  
  
    4.  Creare un nuovo backup del log dal database primario.  
  
    5.  Ripristinare questo backup del log sul database secondario.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Utilizzare la Creazione guidata Gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utilizzare la procedura guidata Aggiungi database a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-database-to-availability-group-wizard-sql-server-management-studio.md)  
  
## Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
  
  