---
title: "Propriet&#224; server di distribuzione, Generale | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distproperties.general.f1"
helpviewer_keywords: 
  - "Proprietà server di distribuzione - finestra di dialogo"
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propriet&#224; server di distribuzione, Generale
  La pagina **Generale** della finestra di dialogo **Proprietà server di distribuzione** consente di aggiungere ed eliminare i database di distribuzione e di impostarne le relative proprietà.  
  
 Nel database di distribuzione vengono archiviati i metadati e i dati di cronologia relativi a tutti i tipi di replica, nonché le transazioni per la replica transazionale. In molti casi, è sufficiente un singolo database di distribuzione. Se tuttavia un singolo server di distribuzione viene utilizzato da più server di pubblicazione, è opportuno creare un database di distribuzione per ogni server di pubblicazione, in modo da garantire che il flusso di dati di ogni database di distribuzione risulti distinto.  
  
## Opzioni  
 **Database**  
 Il **database** proprietà griglia vengono visualizzate le proprietà name e conservazione dei database di distribuzione nel server di distribuzione. **Periodo memorizzazione transazioni** è il numero delle transazioni vengono archiviate per la replica transazionale (memorizzazione delle transazioni è noto anche come memorizzazione della pubblicazione). **Periodo memorizzazione cronologia** equivale invece al periodo di tempo per cui rimangono archiviati i metadati della cronologia per ogni tipo di replica. Per ulteriori informazioni sulla memorizzazione di distribuzione, vedere [disattivazione e scadenza della sottoscrizione](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 Fare clic sul pulsante delle proprietà (**...**) nei **database** griglia delle proprietà per avviare il **proprietà Database di distribuzione** la finestra di dialogo.  
  
 **Nuovi**  
 Fare clic su questo pulsante per creare un nuovo database di distribuzione.  
  
 **Delete**  
 Selezionare un database di distribuzione esistente nel **database** griglia delle proprietà e fare clic su **eliminare** per eliminare il database. Non è possibile eliminare il database di distribuzione se ne esiste uno solo, poiché ogni server di distribuzione deve disporre di almeno un database di distribuzione. Per eliminare tutti i database di distribuzione, è necessario disabilitare la distribuzione nel computer. Per ulteriori informazioni, vedere [Disattiva pubblicazione e distribuzione](../../relational-databases/replication/disable-publishing-and-distribution.md).  
  
 **Impostazioni predefinite profili**  
 Fare clic per accesso profili agenti di replica nel **Profili agenti** la finestra di dialogo. Per ulteriori informazioni sui profili, vedere [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## Vedere anche  
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  