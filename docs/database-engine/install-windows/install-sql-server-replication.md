---
title: "Installare la replica di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "componenti [replica di SQL Server]"
  - "installazioni della riga di comando [replica di SQL Server]"
  - "installazione della replica"
  - "replica [SQL Server], installazione"
  - "prompt dei comandi [replica di SQL Server]"
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
caps.latest.revision: 41
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 41
---
# Installare la replica di SQL Server
  I componenti della replica possono essere installati mediante l'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o dal prompt dei comandi. L'installazione della replica può essere eseguita durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure durante la modifica di un'istanza esistente.  
  
 Dopo aver installato i componenti della replica, è necessario configurare il server per poter utilizzare la replica. Per altre informazioni, vedere [Configura distribuzione](../../relational-databases/replication/configure-distribution.md) nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Se si installano componenti di replica quando si modifica un'istanza esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent al termine dell'installazione, per fare in modo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent riconosca i sottosistemi dell'agente di replica e sia in grado di chiamare gli agenti di replica dai passaggi di processo.  
  
## Installazione della replica mediante l'utilizzo del programma di installazione  
 **Per installare la replica durante l'installazione di una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   Per installare i componenti della replica, inclusi gli oggetti RMO (Replication Management Objects), selezionare **Replica di SQL Server** nella pagina **Selezione funzionalità** dell'Installazione guidata.  
  
## Installazione della replica dal prompt dei comandi  
 **Per installare la replica durante l'installazione di una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   Vedere [Installare SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
## Vedere anche  
 [Installare SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)   
 [Installazione di SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
  