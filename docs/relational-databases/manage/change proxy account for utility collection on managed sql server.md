---
title: "Modificare l&#39;account proxy per il set di raccolta dell&#39;utilit&#224; in un&#39;istanza gestita di SQL Server (Utilit&#224; SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Modificare l&#39;account proxy per il set di raccolta dell&#39;utilit&#224; in un&#39;istanza gestita di SQL Server (Utilit&#224; SQL Server)
  In questo argomento viene descritto come modificare l'account proxy per il set di raccolta utilità in un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per modificare l'account proxy per il set di raccolta dell'utilità in un'istanza gestita di SQL Server  
  
1.  Rimuovere l'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   In **Esplora utilità** in SSMS fare clic sul nodo **Istanze gestite**.  
  
    -   Nella visualizzazione elenco di **Esplora utilità**, fare clic con il pulsante destro del mouse sul nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e scegliere **Rimuovi istanza gestita**. Per altre informazioni, vedere [Rimuovere un'istanza di SQL Server da Utilità SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Registrare nuovamente l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   In **Esplora utilità** in SSMS fare clic con il pulsante destro del mouse sul nodo **Istanze gestite** e scegliere **Aggiungi istanza gestita**.  
  
    -   Seguire le istruzioni nelle finestre visualizzate per completare la procedura guidata, specificando il nuovo account proxy.  
  
## Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Risoluzione dei problemi relativi a Utilità SQL Server](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  